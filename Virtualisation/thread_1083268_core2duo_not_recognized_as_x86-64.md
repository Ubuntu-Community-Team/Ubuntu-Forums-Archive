---
title: "core2duo not recognized as x86-64"
date: 2009-02-28
forum: Virtualisation
---

### Post by zorkerz on 2009-02-28
My 2.2Ghz intel T7500 cpu was just replaced with the same cpu. I put my hardrive back in the computer and started ubuntu 8.10 x86-64. Then when trying to start my x86-64 jaunty jackalope guest I recieved an error.
```

This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```

Virtualbox still has checked Enable _VT_-x/AMD-v

It appears my bios was reset along the way. I went back into it and enabled intel virtualization.

Im not sure what else could be wrong?

---

### Post by amauk on 2009-02-28
If your host OS is 64bit Intrepid and that boots fine then this seems to be purely a virtualbox issue

Can I suggest you reinstall virtualbox (be sure not to delete the VDI harddisks for any guests)

---

### Post by zorkerz on 2009-02-28
I can try this but im unclear as to why it would change anything.

My hardrive was not altered because I did not send it with the computer for repairs. The hardware should be the same make/model just different actual pieces. Could there be some settings set when virtual was installed that now need to be different?

---

### Post by bodhi.zazen on 2009-02-28
I agree, this is an issue with virtualbox.

I do not know why it happens, but virtualbox does a poor job, IMO, detecting 64 bit CPU (I have seen it fail on several CPU) and actually the error message you are posting in my experience is quite common with virtual box (as I have seen it on 3 of 5 64 bit CPU I have tested VirtualBox on).

My solution, although it does not necessarily help you, is to use KVM, OpenVZ, or VMWare.

---

### Post by amauk on 2009-02-28
> **zorkerz said:**
> I can try this but im unclear as to why it would change anything.

My hardrive was not altered because I did not send it with the computer for repairs. The hardware should be the same make/model just different actual pieces. Could there be some settings set when virtual was installed that now need to be different?it's the only thing I can suggest

You can boot a 64bit OS fine
so it's not a hardware / BIOS issue

maybe (purely guessing) virtualbox does some kind of hardware hash thing...
changing hardware may invalidate the hash

again, reinstalling VB is the onl thing I can suggest

---

### Post by zorkerz on 2009-03-01
I was planning on reinstalling virtualbox today but decided to try it one more time. To my surprise it loaded the x86-64 jaunty guest without giving the error. As far as I can figure I have not changed anything since last night, I barely even used the computer. 

Its good that this works now but I don't like missing out on the satisfaction of knowing what was required for the fix.

Thanks for all your input.

---

