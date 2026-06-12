---
title: "Existing Windows 7 x64 install in VM Application"
date: 2011-08-26
forum: Virtualisation
---

### Post by Anreill on 2011-08-26
My work computer currently dual boots Win7x64 and Ubuntu 11.04. I'd like to be able to access the Windows partition in a VM (VMWare Player/VirtualBox) WITHOUT doing a conversion to VM.

The issue I run into is this. I prefer Linux to Windows, but I need Windows for work. I also game on this machine once a week with my boss and some friends (Small IT company, so no policies to deal with.) So for the sake of being able to use my preferred OS, access Windows alongside Linux, and be able to still dual boot so I can game sometimes I'm hoping there's some way to do this.

I've poked around a bit online trying to figure it out, but none of the information I've found quite fits my situation. Tutorials are for the wrong version of Ubuntu, or the wrong version of Windows, or some other variant. Is it possible to do this cleanly and without any serious repercussions? One of the articles I found said that you had to repair Windows every time you actually booted into it normally, I would prefer to avoid that kind of thing.

Cliffnotes:
- Dual booting Ubuntu and Windows 7 x64.
- Want to continue to have full dual boot functionality AND be able to access the Windows desktop while I'm in Ubuntu.

Any suggestions or links would be much appreciated. I'm quite capable with Linux/Windows/VMs, this is just something I've never even considered doing before.

---

### Post by Jake.Debord on 2011-08-26
Just to clarify... You want to run the same instance of win7 in a VM but also dual boot and keep them in sync?

---

### Post by Anreill on 2011-08-26
Yup.

---

### Post by Jake.Debord on 2011-08-26
First let me just say it's not advised. 

That being said, I've heard about the windows repair problem, but I think with two hardware profiles that may be an acceptable work around.

 Have you looked at this page?
[http://forums.virtualbox.org/viewtopic.php?f=2&t=8458](http://forums.virtualbox.org/viewtopic.php?f=2&t=8458)

That would be a good start. I know it says Vista, but I don't think win7 would be much different. Although, I'm human and could be wrong.

---

### Post by dcstar on 2011-08-29
> **Jake.Debord said:**
> First let me just say it's not advised. 
.........

That's because it's basically insane.

Using a filesystem that still can be accessed by the host OS (which assumes it has **exclusive** access and control of the it) while at the same time have a VM also running which **also** assumes it has exclusive access and control of the filesystem is a recipe for disaster.

The Internet is full of posts of people who have been silly enough to do this and have major issues including loss of everything.

---

### Post by tweezak on 2011-09-24
I saw a recommendation elsewhere that if you are going to do this you should add the windows partitions to fstab with the read only flag to prevent data corruption.

---

