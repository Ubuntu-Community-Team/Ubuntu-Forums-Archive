---
title: "Linux is 'outta there!'"
date: 2010-08-23
forum: Testimonials &amp; Experiences
---

### Post by decoherence on 2010-08-23
So says my Dad who runs a small business doing what amounts to super high-end PowerPoints for the Investor Relations departments of various companies. He had an OS X box which he used to run a virtual machine with Win XP and Office 2003 (i think it was 03.) He liked the fact that he had a 'virus proof' system to do all his internet-related activities on. Because many of his clients had upgraded to Win 7 and PowerPoint 2007 or even 2010, he decided it was time for an upgrade. 

At the same time but for unrelated reasons I gave him a Dell workstation that was cast off from my work and suggested he try running Windows 7 VM from an Ubuntu host. He liked the idea of being able to use a free virus proof system to run the programs he needed to run for his job.

Well, he has now kicked it to the ground. The problem? The connection provided by VirtualBox's guest tools between the linux host and windows guest is amazingly slow, by which I mean Windows 7 will copy a file (of any size) only after a minutes long delay and Nautilus just times out. He does his email on the linux side. The files he gets sent need to be opened on the Windows side. Is he to copy, using this abnormally slow connection, every file from the linux host to the windows guest when on his old system he had no problem accessing the files directly between the host and guest systems? Nope. He's gonna turf linux and install Win7 directly.

*ADD: note this is NOT the -ose version of VirtualBox but the evil Oracle version.*

Unfortunately I'm not in a position to troubleshoot the problem but the point is that this is a problem and for my Dad that's a failing grade. Granted he was pretty stressed at the time so I'm wondering if I might just suggest using email in Windows as a temporary workaround but that will no doubt cause complications further down the line...

So there ya go. No real point. Just sharing an experience and current thoughts. I probably will get a chance to troubleshoot the issue before he nukes the system and I'll check if there are any related bugs. Things my dad would never put up with. Maybe he just shouldn't use Linux. But his Windows systems always end up buggering up somehow and the Mac version of Office isn't an option due to compatibility issues with his clients. And he loves GNOME. Thoughts?

---

### Post by DrMelon on 2010-08-23
Sounds more like the VM software's fault to be honest. Contact the developer of said software and explain your issue.

---

### Post by decoherence on 2010-08-23
> **DrMelon said:**
> Sounds more like the VM software's fault to be honest. Contact the developer of said software and explain your issue.

I agree, it is the VM's guest tools that are the likely culprit. Unfortunately that doesn't mean much to my Dad who needs a working system now. I just hope he isn't permanently soured on linux.

---

### Post by ST3ALTHPSYCH0 on 2010-08-23
I would've recommended Vmware player. IME it's a much better performer.

---

### Post by blur xc on 2010-08-23
I use Vbox a lot, with both windows host, linux guest, and vice versa, and I've never noticed what you are talking about.  Are you using a shared folder for moving files in between the guest and the host or a usb drive?  Usb ports can be a bit goofy, and sometimes you might have a hard time getting usb 2.0 to work, and might be stuck with 1.1 speeds...  Anyway, give shared folders a try- create some bookmarks (nautilus) and favorites (windows explorer) for fast access.  Permissions might be a problem, but asking around in the vbox forums will get you past that, hopefully.

Good luck-
BM

---

### Post by KdotJ on 2010-08-23
> **blur xc said:**
> I use Vbox a lot, with both windows host, linux guest, and vice versa, and I've never noticed what you are talking about.  Are you using a shared folder for moving files in between the guest and the host or a usb drive?  Usb ports can be a bit goofy, and sometimes you might have a hard time getting usb 2.0 to work, and might be stuck with 1.1 speeds...  Anyway, give shared folders a try- create some bookmarks (nautilus) and favorites (windows explorer) for fast access.  Permissions might be a problem, but asking around in the vbox forums will get you past that, hopefully.

Good luck-
BM

+1 for shared folder. 
I have this with all of my hosts/guests and the speed is not at issue at all. The setup and usage of said shared folders is well documented in the virtualbox help that's comes with the install

---

### Post by MarcusW on 2010-08-23
Try using SFTP instead (provided with openssh-server). Set up automatically after installing that package, then just connect from the windows guest to the adress that's the "gateway" on your local connection.

---

### Post by decoherence on 2010-08-23
Are you guys talking about the shared folder you set up in the VM's configuration? Because that's the one that's working so badly for my Dad. I might try doing a manual network share but my experience with connecting Windows 7 to samba hasn't been great.

As far as VMWare Player goes, I pretty much wish I had suggested anything other than what I did, including VMWare player. At this point I've had lousy experiences with all of the popular hypervisors and what odd behavior happens to strike you depends on the vm you're running, its hypervisor, the version of its hypervisor and about ten billion other things. VirtualBox had been working well for me so I suggested it (I also don't have the problem my dad does, but i'm not running windows 7.) A year ago it might've been VMWare. Now it might be VMWare again, we'll see.

Sorry, just getting frustrated on behalf of my dad. Thanks for reading and I'll let y'all know if we manage to save the linux install ;)

---

### Post by decoherence on 2010-08-23
> **MarcusW said:**
> Try using SFTP instead (provided with openssh-server). Set up automatically after installing that package, then just connect from the windows guest to the adress that's the "gateway" on your local connection.

In my experience ssh is the most reliable and I was thinking about doing what you suggest. But what about from the Windows side? I assume you can run openssh server on Windows? And is there a client that integrates nicely in to explorer? If there is something that offers the functionality of gvfs or kioslaves on Windows then I think we have a winner.

Okay, going to google now.

ADD: Okay, I see WinSCP which offers an 'exlorer-like' interface but I was really hoping more for the ability to extend Map Network Drive to use ssh. Not having luck finding anything like that, though. Stoopid windows.

---

### Post by blur xc on 2010-08-23
vbox manual- [http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

lots of extra info if you google around.

BM

---

### Post by MarcusW on 2010-08-24
> **decoherence said:**
> In my experience ssh is the most reliable and I was thinking about doing what you suggest. But what about from the Windows side? I assume you can run openssh server on Windows? And is there a client that integrates nicely in to explorer? If there is something that offers the functionality of gvfs or kioslaves on Windows then I think we have a winner.

Okay, going to google now.

ADD: Okay, I see WinSCP which offers an 'exlorer-like' interface but I was really hoping more for the ability to extend Map Network Drive to use ssh. Not having luck finding anything like that, though. Stoopid windows.

Yeah, I think you'll have to use WinSCP or Filezilla. Another alternative is setting up a ftp server, without password, that only accepts connections from the guest windows IP. Windows explorer can handle that.

---

### Post by decoherence on 2010-08-24
HM... I think we've reached the point where we just tell VirtualBox to take a hike and see if we have better luck with VMWare or whatever. Thanks for the suggestions anyway! I'm sure they would work but they introduce too many factors in case something else goes wrong, keeping in mind I won't be around to fix it and my Dad has little experience with linux and VMs.

Any suggestions? Yes I know they all suck/work fine depending on the tides ;) Anything that works especially well/badly with 10.04 64-bit (oops, shoulda mentioned that earlier... yes, it's 64-bit host and win7 64-bit guest)

BTW, after using Win7 and Office 2010, he was so horrified that he's decided against installing them on real hardware. Office 2010 doesn't fix any of the problems he was hoping it would and introduces a pile of new problems like bitmapping text at the wrong time. So he may end up running his XP/2003 stuff on the same box. This is why I don't like PAYING for software (with some expections, of course.)

---

### Post by julianb on 2010-08-24
You mentioned MS Office apps - if your dad needs Office 2003 or 2007, but doesn't need other Windows apps, he could run them in Ubuntu with Crossover Linux.

---

