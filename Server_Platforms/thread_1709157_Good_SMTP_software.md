---
title: "Good SMTP software?"
date: 2011-03-17
forum: Server Platforms
---

### Post by nkae100 on 2011-03-17
I have been running MERCURY SMTP server for quite some years now. I liked it so much that I was running it in WINE on my Linux system.

Recently I went out out and bought a copy of Windows 7 Home Premium as I couldn't stand being able to play iD Software games on my Linux machine only (iD are a great company).

Booting into Windows meant my servers were down, as they ran from my Linux partition, so this is what I proposed:

[http://i54.tinypic.com/n2juo3.png](http://i54.tinypic.com/n2juo3.png)

The issue I faced was that MERCURY is not fully Windows 7 compatible and the mail client that works with it PMAIL is not able to map source directories through the network.

I pissed off PMAIL for Thunderbird and haven't looked back. Its cross-platform too. :) ... amd trying to get MERCURY working has exceeded its worthiness.

What I'm after now is freeware (preferably open sourced) SMTP software that can run both natively on Linux and Windows, as this would allow me to **** off the virtual machine.
I also don't have allot of time in life like I use to, so I am also looking for something very easy and simple to setup and use - something with a GUI.

Does anyone know any software that suits this description?

---

### Post by hawk2010 on 2011-03-18
Highly recommend Postfix and Dovecot(POP/IMAP)

---

### Post by SeijiSensei on 2011-03-18
I'd be surprised if there's a cross-platform SMTP server solution. A quick search pretty much confirmed that Postfix is *nix-only, and the same is true for sendmail.  Along with exim, those are the big-three of *nix SMTP exchangers.  

Do you not have an old PC somewhere that you could put a copy of Ubuntu server on?  Even a PIII with 256M of memory would work for your needs. That would be a much more manageable solution than trying to run servers in a dual-boot environment.  

You might get away with running VirtualBox inside Windows 7 and creating an Ubuntu virtual machine on which you could run Postfix.  But I always find routing packets from the outside to the VM a somewhat dicey affair.  The times I've gotten it working, I've been running an Ubuntu guest on an Ubuntu host, so I know how to play with the routing tables until things work correctly.  I'd be at a loss to figure out how to set up routing correctly with an Ubuntu guest in a Win7 host.

---

### Post by jmacgowan on 2011-03-18
What about running Win7 inside virtualbox?
[http://www.virtualbox.org/](http://www.virtualbox.org/)
 
If you just want to be able to play your games, this set up should work.  In fact, it's how I do it.  I don't run games on my server...but my desktop is set-up this way and it works pretty well.

---

### Post by nkae100 on 2011-03-18
I just spent 8 hours yesterday pulling my hair out trying to route traffic from host to virtual machines. Its a nightmare and very unreliable.
My mail client also didn't like mapping to network drives.

I've found software called Xeams. Its closed-source, but it is cross-platform. What really takes the cake is that it can only run as root!!! Their technical support are pretty thick, check this out its unbelievable:

[http://xeams.com/app?operation=forum&st=viewOneArticle&id=659](http://xeams.com/app?operation=forum&st=viewOneArticle&id=659)

I am also using Thunderbird as the mail client as that is also cross platform.

I've put a symbolic link in place of mailbox files with the Linux install of, to map to the Windows Xeams Mailbox files.

I've got problems at the moment that I've spent hours on.

I am able to send mail from Thunderbird to the outside world and able to receive mail. The SMTP module is fine. I can also see that the mail is being saved fine too.
Xeams is **** house compared to what I was using before (MERCURY) in terms of letting me see verbose output. All I basically see is 'message ok'. FFS this really pisses me off, never the less I am past the stage of being fussy.

I've posted my issue on a Mozilla fan-based forum (as Mozilla's sucks - couldn't even find it)
[http://forums.mozillazine.org/viewtopic.php?f=39&t=2135171&p=10551221#p10551221](http://forums.mozillazine.org/viewtopic.php?f=39&t=2135171&p=10551221#p10551221)

---

### Post by jmacgowan on 2011-03-19
I'm still not sure about what exactly it is that you want to do.  Using the same software for two different bootable partitions because you want 100% uptime while you play your games is... kinda ludicrous.  If you know how to set up and administer something a particular way (as you did with the Mercury set-up) why go through all this?  

Either just run Postfix+Dovecot or your old Mercury setup on in linux then fire up the VM with Win7 when you want to play games.  The mail server never changes that way, and it's always up.  Either I am really missing something, or you like torturing yourself?

---

### Post by nkae100 on 2011-03-19
> Either just run Postfix+Dovecot or your old Mercury setup on in linux then fire up the VM with Win7 when you want to play games

Either I am really missing something, or you like torturing yourself?

I've got with MERCURY (Windows app) on the Windows partition and MERCURY in the VM within Linux - mapping to the windows partition configuration files.

The reason I chose this way is because I needed a server up and running ASAP. Most Linux applications have hundreds of pages long manuals. I didn't have time for this.

Also you were missing something. Booting up a Windows 7 virtual machine to play games isn't going to help. VirtualBox (the VM software I use) cannot access DirectX DirectDraw and has limited Direct3D memory to 128MB of memory.

Anyway, my problems are all solved.

---

