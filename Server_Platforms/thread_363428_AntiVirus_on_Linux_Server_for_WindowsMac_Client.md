---
title: "AntiVirus on Linux Server for Windows/Mac Client"
date: 2007-02-16
forum: Server Platforms
---

### Post by hblaw on 2007-02-16
I am planning to build a Linux server for file sharing at home. (Basically using samba) 

I will be using linux server to download things (movies, applications, etc) via bittorrent, http, ftp, etc from the internet and I will use windows/mac machine (laptop) to access those files via intranet.

I am really new to building a server/security, but I am planning to use Ubuntu (since I use Ubuntu desktop ver on my laptop for a while and it works great).  I think my plan is quite simple to implement.  My concern is whether I can install an antivirus app on the linux server that can scan windows/mac/linux virus so that I can be assured that the files on the linux server will not be infected.  Later if my windows box is caught by virus and after formatting and re-installation I can use the files on the linux server without fear. - any ideas?


Best Regards,
HB

---

### Post by kidders on 2007-02-17
Hi there,

I once tried hooking ClamAV up to Samba to have files scanned in real time, as they were read/written by remote users. I liked the idea of making virus protection the file server's responsibility. Performance was an absolute disaster though ... so I wouldn't recommend doing that! The main problems were a client-crashingly long delay while large files were scanned, and difficulty preventing multiple (sometimes simultaneous) scans of the same files.

To be honest, since Windows is the only OS that really *needs* good virus protection, I would suggest installing a free, lightweight virus scanner on all your Windows boxes. If you felt the need, you could supplement that with 3am scans of the files being served by your Samba server, every second day or so.

---

### Post by hblaw on 2007-02-17
So, in linux there is nothing like Nortorn's real time virus scan? I would like something like that, and I can also schedule a full scan at 3am every other day. Any commercial product? (Prohibiting expensive?)

---

### Post by kidders on 2007-02-17
> **hblaw said:**
> So, in linux there is nothing like Nortorn's real time virus scan?I don't know of any (a virus scanner for Linux is, after all, of very limited use!), but Vexira turned up when I did some googling. Perhaps it would do the trick?

---

### Post by hblaw on 2007-02-18
Well, a virus scanner for Linux surely is meaningless. But you have to protect windows box in the intranet. :)

I just hope there is something like Norton on my linux server. hihi. Thanks for your reply and I'll check Vexira.

---

### Post by kidders on 2007-02-18
Exactly. One other thing you might want to consider is virus/spam/malware protection for email. Even if you're not running a mail server on your own box, you can use tools like fetchmail to transfer mail from multiple remote accounts into a local one, filtering it for crap in the process.

I suspect you will find that real-time virus scanning over Samba will hit you with a noticeable performance penalty. I'd be interested to know if it's tolerable (assuming Vexira is even any good!).

One other issue occurred to me the last time I tried centralising virus protection. If a Windows box that isn't running anti-virus software downloads an infected file from the web, not only will it become infected, but any computer it directly shares (ie without going via the server) the file with will be compromised as well. Depending on how well protected you want your Windows boxes to be, you may find that the number of possible infection vectors is just *so* high that running multiple independent virus scanners on each box could be a necessary evil. :-(

---

