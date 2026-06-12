---
title: "seahorse took over an hour to create a PGP key"
date: 2009-04-25
forum: Security
---

### Post by Panarchy on 2009-04-25
Hello

SeaHorse on Jaunty 9.04 within a VMware Workstation 6.5.2 (Vista x64) image took over 20min to generate a PGP key (default settings, except with explanation, expiry date & 4096)

Anyone else experienced this issue?

If so, is it something which can be fixed?

Panarchy

PS: 512MB of RAM (default VMware Settings for 9.04 i386)

---

### Post by Panarchy on 2009-04-28
***bump***

---

### Post by ikonia on 2009-04-29
virtualization + low ram can often have an effect on entropy generation. 

As no-one else has reported this and there is no bugs logged that I can see for this I suggest your kit is just lacking horse power - and/or your VM does not have the grunt on top of that.

---

### Post by Panarchy on 2009-04-29
Everything seems pretty high specs on my end, for a virtual machine.

Should I lodge a bug?

---

### Post by wirelessmonkey on 2009-04-29
I agree with Ikonia, and if you add a 4096 bit key, I'd expect to see a long keygen time.

---

### Post by ikonia on 2009-04-30
its not a bug - your VM is low spec, I don't know the spec of your host system overall, I don't know how many virtual CPUS are assigned to your VM, or the speed of them, but from what you've said - it's normal, your on a low spec machine creating large entropy

---

### Post by Panarchy on 2009-04-30
> **ikonia said:**
> its not a bug - your VM is low spec, I don't know the spec of your host system overall, I don't know how many virtual CPUS are assigned to your VM, or the speed of them, but from what you've said - it's normal, your on a low spec machine creating large entropy

I'd think my specs would be about average?

---

### Post by ikonia on 2009-04-30
as I've said the only thing you've said is your VM has 512 of ram - keep in mind that's not the key factor here, nor does that make an "average" machine.

1.) the host machine is important as that is the thing that will get sliced up for a VM. 

2.) the resources allocated to a VM (ram for example) are just disk swap files, very little is actually real ram unless you create resource pools, which I don't think you can do with VM ware workstation

3.) you have not said how much CPU you have given your VM (a key factor in entropy) - and keep in mind point 1.) - the ammount you give the VM can only be taken from what's availble on your host

4.) you are doing a much bigger than average entropy generation 



couple the 4 factors together and you have your reason

This is not a bug - and if it was a bug it would be a bug with vmware's resource alloction - but it's not, as it's not a bug. 


As always with your posts, READ the responses given to you when you ask a question, I mentioned these things in a less formal laid out manner in an early post and you just responded with "I think my machine is average".

---

### Post by ikonia on 2009-04-30
double post - sorry

---

