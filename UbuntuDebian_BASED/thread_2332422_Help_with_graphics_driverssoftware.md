---
title: "Help with graphics drivers/software"
date: 2016-07-31
forum: Ubuntu/Debian BASED
---

### Post by chris331 on 2016-07-31
Hello all!  Hopefully the forums will let me post - I've been having trouble recently.
Well, this community has been so helpful and knowledgeable that I thought I'd put this problem I'm having on the table to see
what you all can come up with.
It is a graphics and/or hardware acceleration problem.  
I honestly don't know what the exact problem is, but I know that I can't run anything that requires 3d graphics rendering, such as games that I would like to play.

I put this in Debian because I'm running Kali 2.0 Rolling release distribution, which is based on Debian wheezy/jessie.

Here is some output from my terminal regarding the issue:

```

root@KandA: ~# glxinfo
name of display: :0
Error: couldn't find RGB GLX visual or fbconfig

root@KandA: ~# glxgears
Error: couldn't get an RGB, Double-buffered visual


```

The machine I'm running my OS on is an older model Acer laptop.  It has the Intel B960 processor, 2.2Ghz, 2MB L3 cache.

It has 2 cores, 2 threads.
It runs Intel HD graphics.
The only advanced technologies it has is "Enhanced Intel Speedstep, Intel Fast Memory Access, and Intel Flex Memory.
So, it doesn't have virtualization capabilities.

I'm adding this because I tried to use virtualbox to run an Ubuntu virtual machine for playing games that require a good graphics engine, but 
because it doesn't have virtualization I can't really run a VM with much success.

I tried downloading the latest drivers for Intel HD graphics, but they aren't available via the aptitude/apt-get packages, and when I try to download the source and build it, there
are always dependencies that I lack, and can't get except by downloading with 'wget,' and in the end don't work themselves.

Is there anyone willing to help me troubleshoot my problem with me?  I'm running out of ideas.
I'll download a game, or software, and give the error output.  I'll give you guys any information you require to help me troubleshoot this.

I've been trying to make this work for a month, and am starting to realize that I can't have the penetration testing capabilites, AND the graphics capabilities too..

Any help will be appreciated.
Thank you.

---

### Post by howefield on 2016-07-31
> **chris331 said:**
> I put this in Debian because I'm running Kali 2.0 Rolling release distribution, which is based on Debian wheezy/jessie.

Almost correct, thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by chris331 on 2016-07-31
> **howefield said:**
> Almost correct, thread moved to the "*Ubuntu/Debian BASED*" forum.

Thank you sir.

---

### Post by yoshii on 2016-08-02
I think this might have to do with the typical recent graphics hardware incompatibilities introduced with v16.04 of Ubuntu and there's not much workarounds yet either.  But I'm not really sure.  I thought the issue only affected AMD / ATI / Radeon graphics hardwares.  Also there are some xorg version compatibility issues which affect graphics card use of other types. 

I would check the v16.04 release notes for starters and see what you can find there.  
I am basing all this on the assumption that Kali is based upon Ubuntu.

---

