---
title: "Ubuntu and Mir Question"
date: 2013-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by 7nXwYdh on 2013-09-09
Hello,

I'm a little confused about all this stuff that's happening with Mir, and I have a question. I use Ubuntu for gaming and I have an AMD GPU. Using proprietary drivers is much, much preferable than the open source drivers when using X, and I can only assume that this would be the same when using Mir. I know that in Ubuntu 13.10, Mir will be the default display server, and will be able to fallback to X in case I wanted to use AMD's proprietary drivers (which only support X.org). However I saw that in Ubuntu 14.04, the X fallback will be removed. Assuming AMD doesn't release Mir-compatible drivers (which seems likely at the moment), does this mean I couldn't use AMD's proprietary drivers? If that's the case, what would I do for gaming? Would the open source drivers be my only option?

Thanks! :)

---

### Post by Beren Camlost on 2013-09-09
I go with 12.04.3 LTS.

Long support, rock solid, works well with proprietary drivers.

---

### Post by monkeybrain20122 on 2013-09-09
In 13.10 it will fall back to pure X if you use the closed source driver so there shouldn't be a difference unless the system doesn't detect your card, but if it doesn't fallback to X automatically you can probably still do it manually with some command line mumbo jumbos (If I understand correctly it is possible to fallback to X manually even for open drivers). So there will likely be good times for another 10 months :) 

I don't know what is going to happen in 14.04. They say X fall back will be removed if they get proprietary driver support for Mir. So if no proprietary driver support then it would be X fall back, but what if there are  drivers  for Mir but are buggy or feature incomplete?? (Most likely as it takes time to get these things right) It sounds reckless to me to remove X fallback for the LTS. So if things break at that point I guess it is either 12.04.5 or bye bye Ubuntu. :(

---

### Post by 7nXwYdh on 2013-09-09
> **monkeybrain20122 said:**
> It sounds reckless to me to remove X fallback for the LTS. So if things break at that point I guess it is either 12.04.5 or bye bye Ubuntu. :(
I definitely agree with that. Honestly, I think Mir would be fine if they just kept the X fallback in place and never removed it so that Ubuntu would still work on a vast amount of hardware, even hardware that many not have a Mir-compatible driver. If they are going to remove the X fallback at a time where it a decent number of people stranded and looking for another distro, then I definitely don't like this. Of course, Intel announced they weren't going to support Mir, so I hope Canonical makes the right decision and keep the X fallback preferably for the foreseeable future...I guess we will see! :/

---

### Post by ZoiaGuyver on 2013-09-09
The post by monkeybrain is pretty much spot on, if your using the proprietary drivers you will just be running X same as always.

The talk on 14.04 at the moment is still being discussed, nothing is set in concrete, so things could change for the LTS. Please remember though that the change to Mir doesn't just affect us, It also will have an effect on Valve. Canonical has said they are in talks with the GPU manufacturers for Mir support, I would also say they are probably talking to Valve about this aswell for input from what they need.

The initial driver releases are always a little quirky, but given the speed that the drivers seem to be progressing at the moment It shouldn't be long before the drivers became stable and feature complete (this is based on things going well at the base aswell). Having Mir in 13.10 also means that Nvidia and AMD have a chance to test Mir before the LTS release and maybe get everything set up.

---

### Post by 7nXwYdh on 2013-09-09
Yeah, the main thing I'm concerned with is [Intel's pulling of Mir support]("http://www.omgubuntu.co.uk/2013/09/intel-remove-xmir-support-in-xorg-video-driver")...hopefully that all works itself out as well :/

---

### Post by ZoiaGuyver on 2013-09-09
As far as the support goes the patches for the open source driver will still be applied (downstream) before end-users get it. You wont notice it, Nvidia and AMD have made no comment either way on Wayland or Mir recently. Nvidia said a while back they had no plans to support Wayland in the proprietary drivers. AMD afaik hasn't said anything at all either way, but AMD is a lot more open than Nvidia in the sense of drivers.

Where things get a little foggy is when you think about the interfaces they use, I'll try not to get to technical about it, but both Wayland and Mir use OpenGL/ES and KMS/DRI2 which are all supported kernel wise, and the proprietary drivers (atleast from the last I checked) use both KMS/DRI2 the only difference between them as a user is the actual OpenGL side. Nvidia uses its own OpenGL librarys as does AMD, thats where the problem is with both as far as supporting Wayland/Mir for things like Gaming. (very simplified explanation, but hopefully it can help).

The arguments at the moment are not really something that an end-user should worry about. For devs or people that use OpenGL a lot (programming wise, not use as in gaming wise) its more of a problem. It's more about politics and standards than anything else. 

Rest assured that Canonical/Ubuntu will still have Mir, providing we all use it and its still used by OEMs and Vendors the Proprietary drivers will have no choice but to support it.

---

### Post by grahammechanical on 2013-09-10
Can I make a small but I think a significant point? Ubuntu 13.10 will not have MIR as the default display server. It will have Xmir as a replacement for Xserver. Ubuntu desktop will not get MIR and Unity 8 until 14.10 is released. That is the convergence target for Ubuntu Desktop.

 Ubuntu 14.04 will have Unity 7 as 13.04 presently does and Xmir and Xserver as fallback. Remember, 14.04 is LTS and that means stability before experimentation. Support for Xserver will stop during 2014. So, do not expect Xserver code to be in 14.10. And do not expect Compiz code to be in 14.10 for MIR will have replaced it. That is the plan.

At this moment there is no rush to put MIR into the Desktop. The effort is going towards the Ubuntu Touch Platform. In November install the Ubuntu 14.10 development branch and see how things develop. Get on the "bleeding edge." The Saucy Salamander development branch has already had Xmir available through a PPA. Now it ihas Xmir available through installing unity-system-compositor from the archives.

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

Regards.

---

### Post by craig10x on 2013-09-10
Didn't Canonical say they will provide the necessary patches to ubuntu to make mir work with the intel drivers?  Pretty sure i read that...
They would have to, since there are no optional drivers on intel the open source and proprietary are the same...that's why none are offered if you run intel on ubuntu...
So if no fallback is provided, and they didn't do that, no computers with intel would work on ubuntu...They surely wouldn't do that...

---

### Post by Beren Camlost on 2013-09-10
Canonical will provide the patches needed for Intel hardware to work, but that won't help those of us with Nvidia or AMD cards and rely on hardware accelerated graphic drivers.

---

### Post by ZoiaGuyver on 2013-09-10
grahammechanical I think your understanding of exactly what Xmir is and does is off, Xmir is a nested/rootless X server running ontop of Mir (much like how Mac OS X handles X11) that allows X clients to communicate with Mir as the compositor. Xmir has no function at all outside of Mir, unity-system-compositor as a component is Mir.

I.e 13.10 its Mir > Xmir > X-Program, it is not Xserver > Xmir > Program or even Xmir > Program.

14.04 its Mir > Program. Xmir is reliant on Mir to do the job of compositor.

Oh something I forgot to add in 13.10 Xmir (as far as I have found out) is running as a "full screen" window with "sub windows" as it were. Mir is still drawing the stuff to the screen and relaying the commands.

---

### Post by King Dude on 2013-09-10
Personally, I don't care for Mir at all. I'd have much rather have it that Wayland is used instead.

---

### Post by ZoiaGuyver on 2013-09-10
King Dude that is you opinion and I respect that, Myself on the other hand would prefer to have a choice, I don't run only Ubuntu (although Ubuntu is my daily machine). I would like to see Mir and Wayland on equal grounds and give my approval or disapproval based on actual merit. I have tested Wayland and even in its current release state it is unusable due not to Wayland itself, but the lack of a compositor (gnome/kde will fix that). I have also tested Mir and although Mir is still flaky at the moment in certain places it is actually quite usable (unless you try Unity8), I was really surprised.

Ubuntu hopefully will continue to support both Wayland and Mir as a choice for the users and the derivatives.

---

