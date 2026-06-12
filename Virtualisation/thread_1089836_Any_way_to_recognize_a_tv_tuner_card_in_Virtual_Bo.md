---
title: "Any way to recognize a tv tuner card in Virtual Box?"
date: 2009-03-07
forum: Virtualisation
---

### Post by Committed on 2009-03-07
I'm trying to use Mediaportal in winxp on virtual box but can't find a way to recognize my Avermedia M791 tuner card.  It's not supported by mythtv or I'd just run straight from ubuntu.  

Just seeing if it's possible before I go and buy another tuner card.

---

### Post by arm-c on 2009-03-07
Sounds like it is an internal card.

If, however, it is an external USB card, you could install the non-open source version of VirtualBox from the Sun Microsystems and pass the USB device through to the Virtual Machine.

Don't think this will help... but a shot.. and if not you... maybe someone else.

---

### Post by Committed on 2009-03-07
It's an internal card.  I don't think it can be done but I thought I'd ask.  For $42 I might as well just get a Hauppauge pvr 150 off ebay.

Thanks.

---

### Post by T.J. on 2009-03-07
Sorry to say that would be a "no". VirtualBox creates "virtual hardware" so that you can run your guest OS.

The good part of that is that if VirtualBox says it will run an OS it will, even your guest OS has hardware support for your real hardware or not.  The bad part is your real hardware is hidden behind the "virtual hardware".  You can do some hardware OpenGL acceleration, but that's about it.

VirtualBox is not meant to replace a normal Windows installation for running multimedia.  It's more for programming and things like that.

Chin up though!  You might be able to get a Linux driver for regular Ubuntu.

---

### Post by Committed on 2009-03-07
I'm only using VB as a test and to see if it will run quickbooks(which it did) and to see if I can run my current TV tuner, which I can't.  Everything else I do is through linux.  But this machine came with Vista home premium and the AVermedia m791 tv tuner card.  I used that a lot as a dvr and for watching live tv as I worked.  

Now that I mainly use linux(still have dual boot to Vista), I still want TV so I guess I just need to pony up for a supported card.  Mythtv shows this one as not supported, and search's have said the same as well as my own efforts to get it running.  For now I have to boot back to Vista to record my programs.  Man how I hate going back there.

---

### Post by T.J. on 2009-03-07
> 
Now that I mainly use linux(still have dual boot to Vista), I still want TV so I guess I just need to pony up for a supported card.  Mythtv shows this one as not supported, and search's have said the same as well as my own efforts to get it running.

I'm afraid so. Sorry!

> For now I have to boot back to Vista to record my programs.  Man how I hate going back there.

You and me both!  I only keep it around for DirectX games and for certain websites that only work in Windows plugins.  I feel your pain.

---

### Post by philip82284 on 2010-01-28
did you try tvtime ?maybe you can get it running with that inside of ubuntu ?

---

