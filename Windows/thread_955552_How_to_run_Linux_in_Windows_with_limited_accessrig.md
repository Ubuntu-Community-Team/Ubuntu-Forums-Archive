---
title: "How to run Linux in Windows with limited access/rights"
date: 2008-10-22
forum: Windows
---

### Post by Lazy-buntu on 2008-10-22
How could you run Linux (like Puppy Linux) on a computer running Windows, but here's the thing:

1. Live Media is a no go (network boot)
2. You cannot install VMware or any other .exe (but portable apps--.paf.exe--from portableapps.com work for some reason)


I was wondering if this was even possible. Maybe run virtual box/VMware off a USB stick if that's possible. 

Any ideas?

---

### Post by DGortze380 on 2008-10-22
> **Lazy-buntu said:**
> How could you run Linux (like Puppy Linux) on a computer running Windows, but here's the thing:

1. Live Media is a no go (network boot)
2. You cannot install VMware or any other .exe (but portable apps--.paf.exe--from portableapps.com work for some reason)


I was wondering if this was even possible. Maybe run virtual box/VMware off a USB stick if that's possible. 

Any ideas?

That's messy. Haha.

Ok. If you want to run Linux inside Windows you have to run a Virtual Machine. Which means you have to install some kind of virtualization software. I don't think you can just install to a USB and plug it into the system, I'm 99% sure that won't work.  Good luck, I'd be interested if you found a way around this.

---

### Post by bodhi.zazen on 2008-10-22
This is possible, but it sounds very much like you are trying to do something on a private network you should not be doing.

This kind of activity is not supported on these forums and I would direct you to your network administrator.

---

### Post by jdong on 2008-10-22
I have reluctantly moved and re-opened this thread due to an ongoing Resolution Center complaint. Please abide by forum rules in entailing discussion.

Thanks.

---

### Post by Lazy-buntu on 2008-10-22
Let me explicitly state this: How to run Linux in Windows with limited access/rights **(without doing anything illegal, gaining additional system rights, or anything else that falls in the shady area).**

I'm just looking to run a light Linux distro through virtualization or off a USB stick without booting into it. I would like to be able to save changes to the virtualized OS too, like added applications (i.e. if I install the gnome version of solitaire I want it to be there the next time I lauch the OS).

---

### Post by KiwiNZ on 2008-10-22
I will add , 

Anyone advising how to give unauthorised access to protected systems will be dealt with in accordance to the Code of Conduct.

@ Lazy-buntu if you get sanctions imposed by the Organisation concerned for unauthorised systems access that shall be your responsibility. Ubuntu Forums will in no way be held responsible for  your actions.

---

### Post by Lazy-buntu on 2008-10-22
I completely agree that network/system integrity is a very sensitive subject. I do not want to step on anybody's toes, so please be careful about what you're posting.

I will double check with the IT department before I attempt anything posted here, because I am not looking to break any rules.


I would rather bring a laptop than risk anything, but still I am curious if the original topic is possible.

Edit: the forum admins had some insight on the second page here--http://ubuntuforums.org/showthread.php?t=955673--about running virtualization software. I invite them to elaborate on the topic here. I was doubting the ability to run VMware from a USB stick to begin with, but maybe there's a portable solution out there.

---

### Post by Lazy-buntu on 2008-10-22
I sent IT an email, and I got a surprising response back from the IT personel:

"We have no problem with that.  I myself fine Windows unusable, so I definitely understand.

From a lab perspective, Engineering Tech controls those, so from a desktop perspective I'm not sure what their policy is.  However, knowing the guy over there I'd be shocked if he had any issues with it.  I'd say go ahead with it, as long as you're not an emacs user! :)

-Jim R.
 Network Administrator"

I was kind of expecting a "Geek Squad" type reply, but now that I know I'm free to try it out, I'd like some feedback from the community about their experiences.

I'm shooting for a portable Linux solution you don't have to boot into, or necessarily have to install anything with a .exe extension. It doesn't even have to be on a USB stick. I can save it to my fileserver space...which is about 8GB I think.

---

### Post by kellemes on 2008-10-22
> **Lazy-buntu said:**
> I got a surprising response back from the IT personel:

"We have no problem with that.  I myself fine Windows unusable, so I definitely understand.

From a lab perspective, Engineering Tech controls those, so from a desktop perspective I'm not sure what their policy is.  However, knowing the guy over there I'd be shocked if he had any issues with it.  I'd say go ahead with it, as long as you're not an emacs user! :)

-Jim R.
 Network Administrator"

Not sure if this is what you're looking for.
[http://www.pendrivelinux.com/2007/09/19/portable-qemu-persistent-pendrivelinux/]("http://www.pendrivelinux.com/2007/09/19/portable-qemu-persistent-pendrivelinux/")

Obviously I don't know if it's allowed nor if it will work in this protected environment you work with.

---

### Post by Lazy-buntu on 2008-10-22
I think you have to boot into that, so that wouldn't work.

I tried that on my own computer, and I couldn't even get it to boot.

---

### Post by bodhi.zazen on 2008-10-22
If you have the green light ask them to install (or give you the rights to install) VMWare or VirtualBox (whichever best serves your needs).

The other option is, as has been mentioned, use qemu. qemu does not require you to install anything and can be run from a pen drive. There are instructions on the link you were given already. As has been mentioned, you will probably find qemu to be slow, even on modern hardware and a fast CPU.

---

