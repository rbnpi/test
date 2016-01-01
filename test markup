Recently I tried some old files on SP 2.9 amd 2.8 which I wrote using SP2.7
They worked fine on a Rpasberry Pi2 on 2.7 but break up on 2.8 and 2.9
Any idea why the performance should be worse? (I know they could be written differently now, but it would be nice to have a version that works on all these systems.
They perform fine on all versioon under Mac OSX.

```
#This works fine on SP2.7 but falls over in 2.8 and 2.9  on a Pi2 Any idea why?
#Works fine on OSX all versions.

inst=:ambi_glass_rub
samplepitch=:fs5

#this function plays the sample at the relevant pitch for the note desired
#the note duration is used to set up the envelope parameters
define :pl do |inst,samplepitch,nv,dv|
  shift=note(nv)-note(samplepitch)
  sample inst,rate: (pitch_to_ratio shift),sustain: 0.8*dv,release: 0.2*dv
end

#this function plays an array of notes and associated array of durations
define :plarray do |inst,samplepitch,narray,darray|
  narray.zip(darray) do |nv,dv|
    if nv != :r
      pl(inst,samplepitch,note(nv),dv)
    end
    sleep dv
  end
end

n1=scale(:c3,:major,num_octaves: 4) #set up 2 voices each with 4 octaves
d1=[0.3]*n1.length #durations for all notes the same
n2=n1.reverse



#play them. works fine in sp2.7 Breaks up in 2.8 and 2.9
in_thread do
  plarray(inst,samplepitch,n1,d1)
end
plarray(inst,samplepitch,n2,d1)
```
