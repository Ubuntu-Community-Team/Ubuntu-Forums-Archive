---
title: "missing /sbin/init file on my server"
date: 2007-04-21
forum: Server Platforms
---

### Post by erikringmar on 2007-04-21
Dear all,

I can't reboot my server and the VPSlink people tell me there is a /sbin/init file missing.  Is there anything I can do about this (or ask VPSlink to do).  I can't get in via Putty or SSH.  Unfortunately I don't have a very recent backup of the site.  Is there a way to reinstall the OS without wiping all my personal files from the server?

thanks for any suggestions,

Erik

---

### Post by codingmaster on 2007-04-21
Hi!

I don't know the VPSlink services, but many hosters offer the possibility to use a debug mode. 

Normally you can boot into this services, actually an iso image, that should be installed, will be loaded.

This would be already give you everything you need to recover your files, because you can switch to the tty on the iso image (does not matter which linux distro), then you can mount your filesystem rw and get the missing files from this iso image or download the missing deb package and extract the missing files.

Using the iso of the system you have installed is always a good way :)

Btw, did you delete /sbin/init?

Good luck!

Best regards, Georgy Berdyshev

---

### Post by erikringmar on 2007-04-21
Hi there,

Thanks for very quick and encouraging reply.  I'll let VSPlink know what you suggest -- let's hope they'll reply in a positive mode.  Since I have neither putty nor SSH access there isn't much I can do.

The weird thing is I didn't delete the /sbin/init file (at least not knowingly).  Is there a reason why this could happen?  (The only thing I can think of is that I was trying to run Bttorrent from the command line on the server and I had some segmentation and memory issues an the whole thing stopped functioning).

I'd love to hear your input on this,

Erik

---

### Post by codingmaster on 2007-04-21
Hello!

It is really strange, normally those things should not happen.

When you did not delete it on purpose and I also doubt that the bittorent client deleted it.

There can be some mistakes that have occured during VPSlink working on your server.

Actually they should provide some access for you to those files, because everything is running virtually and a good hoster offers a rescue console to the user.

What about backups?

Do you have some backup space or does VPSlink backup the virtual servers?

I guess they will ask you to pay money, and it is really not a big deal for them to recover your files, actually everything is there, just your system does not boot.

When you will get access to a rescue mode or a system installation, they will normally use the same space for you virtualized.

Depending on their solutions, they really will be able to recover your files.

But at least ask them about /sbin/init.

They should recover it, there is really no need for a complete reinstallation.

One thing that can also be: some mistakes done by them or a hard disk failure that occurs on the location of /sbin/init and therefore the file is just not there.

Best regards, Georgy Berdyshev

---

### Post by erikringmar on 2007-04-21
Dear Georgy,

Thanks for reply.  I quoted your comments back to VPSlink and they got back to me and said that "we have now restored your sbin/init."  I restarted Mysql etc and everything now seems to be in order.  Great.  Your words obviously forced some guy into action.  

Still it makes me wonder what could have gone wrong.  VPSlink is supposed to be a reputable company.  It's worrying that it could have been their fault.

You have no idea how relieved I am.  I have 100 students at the university where I teach who depend on this site and there's an exam on Wednesday next week ...

People like you restore my faith in mankind.

yours ever,

Erik

---

### Post by codingmaster on 2007-04-22
Hello!

Nice to hear, that I have helped!
Sometimes those companies really need to have told, what they actually have to do for free!!!

Really, I work with lots of customers (mainly ISP + programming for huge companies) and I really do not behave like this.

Well, when they notice that the person at the other end of the phone line knows, what he is talking about, they get afraid really fast :) and do what they need to do.

Really, a few minutes recovering /sbin/init vs. delting your vserver: yes for them it is obvious what to do: clicking on server reinstallation button (takes one second), but you lose your data in this way.

At least everything works again :)

> You have no idea how relieved I am. I have 100 students at the university where I teach who depend on this site and there's an exam on Wednesday next week ...

People like you restore my faith in mankind.

yours ever,

Erik

I hope that the exam will be a success and also that many students will pass!

Thanks a lot!

Regards, Georgy Berdyshev

---

