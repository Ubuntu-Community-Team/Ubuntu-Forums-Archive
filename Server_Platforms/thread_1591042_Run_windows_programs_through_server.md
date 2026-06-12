---
title: "Run windows programs through server"
date: 2010-10-08
forum: Server Platforms
---

### Post by Rihoj on 2010-10-08
hello all. 
I am relativly new but can easily follow instructions, am runninng ubuntu server 10.04 with a shared hard drive. 
i would like to install programs on the server and run them on my win. cmp

---

### Post by bcdudley on 2010-10-08
Check out Wubi maybe.

---

### Post by Rihoj on 2010-10-08
Thanks but not quite what i want. I wamt to be on my win. comp, but launch my programs from the ubuntu server, or go to my win laptop and launch the same pgm w/o installing on both cmps just server.

---

### Post by CharlesA on 2010-10-08
> **Rihoj said:**
> hello all. 
I am relativly new but can easily follow instructions, am runninng ubuntu server 10.04 with a shared hard drive. 
i would like to install programs on the server and run them on my win. cmp

What sort of programs do you want to run on it?

If you have them on the same machine, the only way to have them both running at the same time is to run it as a virtual machine using something like VMWare or VirtualBox.

> **bcdudley said:**
> Check out Wubi maybe.

Wubi is a way of dual booting, so you won't have both OSes running at the same time.

---

### Post by Rihoj on 2010-10-08
Just about any program, open office, ms office, anti virus programs, firefox, opera, safari, notepad++, and if possible various games.

---

### Post by CharlesA on 2010-10-08
Do you have 2 separate machines?

---

### Post by Rihoj on 2010-10-08
i have three. 
1. Ubuntu server 10.04
2. Windows vista (desktop)
3. windows 7 (laptop)
all on a router

---

### Post by arrrghhh on 2010-10-08
Well if the apps are portable, then you can put the files on your server and run them on your Windows machines over samba...

That would be about the only way I'm thinking this setup would work.  I run installers over the network all the time, works great.  However, I run my applications locally...

---

### Post by CharlesA on 2010-10-08
Oh I See.

You can forward X over ssh then.

It works ok for small apps, but I doubt it'll handle games.

You'd need Putty and XMing on the Windows boxes.

---

### Post by SeijiSensei on 2010-10-08
I believe that the OP wants to run multiple instances of Windows programs that have somehow been installed on a central server.  The short answer to his/her question is no.  

First off, for proprietary software, this practice would be illegal in most jurisdictions.  Imagine if an office of 500 people could share a single copy of Microsoft Office without some special restrictions to enforce a license at every desktop.  Your scheme of a central shared copy circumvents the "one licensed copy per CPU" model that underpins proprietary computing.  In the olden days, some programs' licenses allowed users to install an unlimited number of copies under the provision that only one copy would be used at a time.  Not surprisingly, users violated the terms of this agreement left and right and gave copies of these programs to friends and relatives.  So, nowadays, commercial software is generally licensed per-CPU and not per-user.

That still leaves software like OpenOffice where a single copy could quite legally be used by a limitless number of people.  Regardless of the legalities, Windows software expects to install itself on a single machine and write its configuration information into the local Registry and folders.  While we might imagine a shared Registry of some sort, that's not how Windows software works.

You can do this with Linux, though, using something like a "[terminal server]("http://www.ltsp.org")."  I don't think that makes sense in the case you describe either.

---

### Post by Rihoj on 2010-10-08
The terminal server actually is the closest thing I have found. Ty. 
I understand about the legality of some of the software, and so yes those apps would be an issue, but would the ts work how i asked

---

### Post by SeijiSensei on 2010-10-09
LTSP would work for a system sharing only *nix software.  It won't work for sharing Windows software unless perhaps you could do something tricky by sharing a Wine installation.  That's just speculation on my part, though.

Again the best solution is to install the programs on all the Windows computers.  If you've asked this question in an effort to avoid licensing restrictions, we really can't help you any further.

---

### Post by CharlesA on 2010-10-09
> **seijisensei said:**
> 
again the best solution is to install the programs on all the windows computers.  If you've asked this question in an effort to avoid licensing restrictions, we really can't help you any further.

+1.

---

### Post by The Cog on 2010-10-09
Here is a good description of a windows terminal server. 
[http://en.wikipedia.org/wiki/Remote_Desktop_Services](http://en.wikipedia.org/wiki/Remote_Desktop_Services) 
I don't know what the licensing costs would be, but I think it would be based on the number of concurrent users and the number of CPUs. Maybe the article says - I didn't read it all. I don't know whether it would be too expensive for use at home. You would be able to use Ubuntu as a client to connect to the server, using Ubuntu's Remote Desktop Viewer. 

If it's just you using the programs, maybe just use remote desktop viewer to drive the applications on the one machine that they're installed on.

---

### Post by Rihoj on 2010-10-09
Thank you all very much. Just so you know I am not trying to avoid licensing, it is that my desktop has a very small hdd, and i was trying to relieve that. 
I am going to do more research into ltsp.

---

### Post by bcdudley on 2010-10-11
Sorry, been away for a couple days. Another program you should consider looking at is 2X. It uses TS to allow you to port a single app instead of the entire desktop. They have Windows and Linux Clients. The server portion now only works with Windows, but they used to have a Linux server as well. You may be able to find an old copy floating around somewhere.

The software is free for up to 3 clients. We use the full paid version on our network and it is great software.

---

### Post by koenn on 2010-10-11
> **Rihoj said:**
> Thank you all very much. Just so you know I am not trying to avoid licensing, it is that my desktop has a very small hdd, and i was trying to relieve that. 
I am going to do more research into ltsp.

If it's just about  disk space,  you could, on your laptop, map a drive letter (say, N: or S: ) to a samba share on, the server (or you might try an NTFS symlink to it).
Then, still on your laptop, when you install programs, make them install in a subdirectory on N: (in stead of the standaard C:\Program Files or whatever it's now called). You will still end up with some additional disk usage on your laptop (registry keys, dll's in the Windows dir, ...) but the bulk of the program will be on your server.

Old trick, probably still works for a lot of programs. 


Technically, you're only *storing* them on the server, they still run on (= are executed by) your laptop.

---

### Post by Rihoj on 2010-10-12
> **koenn said:**
> If it's just about disk space, you could, on your laptop, map a drive letter (say, N: or S: ) to a samba share on, the server (or you might try an NTFS symlink to it).
Then, still on your laptop, when you install programs, make them install in a subdirectory on N: (in stead of the standaard C:\Program Files or whatever it's now called). You will still end up with some additional disk usage on your laptop (registry keys, dll's in the Windows dir, ...) but the bulk of the program will be on your server.
 
Old trick, probably still works for a lot of programs. 
 
 
Technically, you're only *storing* them on the server, they still run on (= are executed by) your laptop.
 
Thank you, I thought about that, and we trying to avoid it, just because of the local files for some programs. I have done that with some of them, and just delt with the others. (I didn't want to reinstall ubuntu after I got most of my server setup with web, printer, and files.) Thank you everyone.

---

