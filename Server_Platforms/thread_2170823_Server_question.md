---
title: "Server question"
date: 2013-08-27
forum: Server Platforms
---

### Post by ben15 on 2013-08-27
Hello,

I have a home server that is running Ubuntu Server 12.04. I am currently using Samba as my share program. I was wondering, is there a better share program? One that can connect to multiple remote client OS's (I would like to connect it to: Linux Ubuntu/Mint laptops, Windows laptops, Android phone and tablet, and PS3)?

Thanks,
Ben

---

### Post by ian-weisser on 2013-08-27
It depends what you mean by "better". Easy to administer? Low overhead?

It also depends on what kinds of services your server offers. Printing? File storage? Shared applications? Backups?

---

### Post by Ben_Cousins on 2013-08-27
From what I understand, Samba allows multiple platforms to connect to it. I'm not sure about PS3, though.

---

### Post by wildmanne39 on 2013-08-27
*Thread moved to **Server Platforms**.*

---

### Post by nerdtron on 2013-08-27
Have you tried Nas4Free? Easy to install and is dedicated to serving multiple clients. Low overhead and has a great Web GUI to configure samba share (not just samba share, nfs, etc.).
But you'll need a spare thumb drive to install it.
[http://www.nas4free.org/](http://www.nas4free.org/)
Seems like the main website is down.
[http://sourceforge.net/projects/nas4free/](http://sourceforge.net/projects/nas4free/)

---

### Post by Bucky Ball on 2013-08-27
Hi Ben15 and welcome to the forums. Just a heads up. You will have much better luck getting assistance by using descriptive thread titles in future. Generic titles like 'Server question' or 'need help' or 'video problem' tell us nothing. Be specific. Your thread is in the server sub-forum so we would be expecting a server question.

Cheers and good luck. ;)

PS: If you want to change thread title and can't, PM me a couple of suggstions and will do it for you.

(* Suggestion: 'How do I share programs with multiple remote clients using Samba?' ... or something like that. You might also like to check out the last link in my signature. ;))

---

### Post by ben15 on 2013-08-29
I appreciate the answers, and apologize for being so vague. What I meant by "better" is one that will communicate across the various platforms I listed. Samba lets my laptop see the server, but not any of my other devices. 

The server was just my desktop converted into a storage/media/print server. I was basically trying to build a home cloud. I basically got tired of troubleshooting every time something went wrong, and digging through the configuration files for script errors. It was requiring more time than I had, so I just installed a desktop version of Ubuntu. I'll get back to it eventually, but right now I just don't have time. The final issue (the proverbial straw that broke the camel's back... odd that it happened on a Wednesday) was CUPS. It was working fine, I could print to both printers from all of the computers connected. All of the sudden, it just quit working, neither of the printers would accept jobs. So, I have a desktop again. 

As I said, I appreciate the help.
Ben

---

### Post by capscrew on 2013-08-29
> **ben15 said:**
> I appreciate the answers, and apologize for being so vague. What I meant by "better" is one that will communicate across the various platforms I listed. Samba lets my laptop see the server, but not any of my other devices. 

The server was just my desktop converted into a storage/media/print server. I was basically trying to build a home cloud. I basically got tired of troubleshooting every time something went wrong, and digging through the configuration files for script errors. It was requiring more time than I had, so I just installed a desktop version of Ubuntu. I'll get back to it eventually, but right now I just don't have time. The final issue (the proverbial straw that broke the camel's back... odd that it happened on a Wednesday) was CUPS. It was working fine, I could print to both printers from all of the computers connected. All of the sudden, it just quit working, neither of the printers would accept jobs. So, I have a desktop again. 

As I said, I appreciate the help.
Ben

It might help if you consider what a "server" really is.  By that I mean the process running in the background waiting for the clients request for service.  These servers are created for each protocol (i.e. SMB, HTTP, NFS, DHCP, DNS, etc.).  There can be many servers running on your OS.  It doesn't matter whether the distro is Ubuntu Server Edition or Ubuntu Desktop Edition.  The kernel is the same.  Only the installed packages and configuration is different.

In short, "The Server" is really a bunch of server processes running on one host.  This is a good thing.  The protocols sometimes are "mutually exclusive".  it's one or the other in those programs.  If my Samba Server crashes I don't want it taking down the whole system.

---

### Post by SeijiSensei on 2013-08-29
> **ben15 said:**
> One that can connect to multiple remote client OS's (I would like to connect it to: Linux Ubuntu/Mint laptops, Windows laptops, Android phone and tablet, and PS3)?

You can connect all of those with Samba, except the PS3.  Connecting to a Samba server from Android runs up against security limitations, in that you cannot mount the share into the filesystem except on a rooted device.  However you can copy files back and forth to your phone with an Android SMB client like [AndSMB]("https://play.google.com/store/apps/details?id=lysesoft.andsmb&hl=en").  

The PS/3 prefers to use the "DLNA" protocol.  It also supports only a narrow range of video formats.  One solution is to run [ps3mediaserver]("http://www.ps3mediaserver.org/") on your machine as well as Samba.

On Kubuntu you can use smb:// URLs in the file manager, Dolphin.  I believe GNOME programs like Nautilus provide the same option.  On my Kubuntu machines, opening smb://server/share prompts for a username and password then logs me into Samba.  You can also mount Samba shares when the network starts up using an entry in [/etc/fstab]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

---

### Post by CharlesA on 2013-08-29
> **SeijiSensei said:**
> 
The PS/3 prefers to use the "DLNA" protocol.  It also supports only a narrow range of video formats.  One solution is to run [ps3mediaserver]("http://www.ps3mediaserver.org/") on your machine as well as Samba.

+1. I have heard miniDLNA works well too.

---

### Post by houstonbofh on 2013-08-30
Fpr systems to communicate, you just need compatible protocols on each end.  Linux is nice in that it supports most of them.  Windows not so much...  The nicer thing is that Linux can "serve" more than one file sharing protocol.  I connect to my media pc (server) with samba, ssh, nfs and ftp, depending on where I am coming from.

---

### Post by 1clue on 2013-08-30
Not much to add here, other than that you can serve multiple protocols *over the same set of directories.*

You might consider a cifs (samba) share of your root shared directory, and then have some subdirectory of that as the base for things like your phone or PS3.  That way your bigger hardware which can navigate more easily can get at everything, and the other devices can get where they have to go without a lot of fuss.

---

