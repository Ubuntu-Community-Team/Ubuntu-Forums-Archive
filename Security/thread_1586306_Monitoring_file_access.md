---
title: "Monitoring file access"
date: 2010-10-01
forum: Security
---

### Post by mlk20 on 2010-10-01
Hello all,

At our company we have a central server with client files. This server has a SSH server installed, and through Nautilus all employees can access the files. However, I have a few questions:

1. Most employees need access to all folders, because they might use them at some point in time. However, I want to make sure they are not accessing things they do not need. How can I do this? For instance, if somebody copies all of the folders to his/her computer, I want to be able to see this in some sort of log. Can this be done? Copying and accessing in general is what is of my concern.
2. Some employees only need access to specific folders. Can this be easily configured with SFTP? 
3. Some also use SSH and type commands which I want to check every now and then (e.g. to make sure an intern is not again copying information or accessing folders they should not be in). What is a good way to do this?

Thanks for any help!

---

### Post by unspawn on 2010-10-03
> **mlk20 said:**
> Most employees need access to all folders, because they might use them at some point in time.
You mean most employees [S]need[/S] don't need access to all folders, because they [S]might[/S] should ask for permission [S]at some point in time[/S] when access is required?..


> **mlk20 said:**
> Some employees only need access to specific folders. Can this be easily configured with SFTP?
SFTP requires SSH so a chroot should work and server side file level access permissions apply so group ownership (rigid, limited) and ACLs (more flexible) may help. 


> **mlk20 said:**
> I want to make sure they are not accessing things they do not need. (..) For instance, if somebody copies all of the folders to his/her computer, I want to be able to see this in some sort of log. (..) Copying and accessing in general is what is of my concern.
For instance 'man sftp-server' shows you'll be able to log detailed information about transactions, GRSecurity-enabled kernels provide improved logging in comparison to "vanilla" ones (you don't need to activate the whole RBAC for that) and then there's custom Auditd rules (see CAPP, LSPP and NISPOM rulesets for examples) or even something inotify-based. In terms of performance it may make sense to use a separate logging server. Do realize logging does not cover everything. If you fail read reports (or fail to address issues that aren't subject to logging) then no logging will help: technology is not *the* solution but a part of it. 


HTH

---

### Post by mlk20 on 2010-10-03
Thanks a lot! I will be reading about what you mentioned. 

> You mean most employees need don't need access to all folders, because they might should ask for permission at some point in time when access is required?..

I guess we really should give certain people access to all folders. Sometimes there is nobody else at the office, and a client calls and they will need to get the client files. This should be instant and they should not depend on others to give them access. So that is why there should be control and checks rather than limited permissions.

What we are really worried about is that somebody does a copy/paste of all or may client files. This has happened before so our primary objective is to see who is copying what files. I'll learn the manuals to see if this can be easily tracked...

---

### Post by unspawn on 2010-10-03
> **mlk20 said:**
> our primary objective is to see who is copying what files. I'll learn the manuals to see if this can be easily tracked...
Looking for "the perfect audit trail" you'll find Linux doesn't provide much logging out of the box so that needs addressing. Copying, and I don't mean read and write syscalls, will be way harder to prove. For instance one can read a file from the server and:
- paste file contents in say web-based email, docs.google or social networking. 
Sure you can correlate events between server and client and scan network traffic but *the actual act of copying* you can not easily log AFAIK. This means for instance that if an employee left his/her workstation unlocked and unattended you might not be able prove it was this particular employee unless you have other means of monitoring. Or else how about reading the file from the server and:
- send it to a remote server as HTTP requests,
- transmit wirelessly to a close by AP,
- make it a password-protected attachment (AV scanners don't like that),
- append it to another file (image will display just fine), 
- write contents to a file on removable media and then delete it (what to look for?),
- write contents past the last partition (where to look?),
- make it an EXIF tag, 
- scribble inside a book cover, newspaper crossword puzzle or inside a boot, 
- convert it to a movie and upload it to whatevertube,
- photograph contents using a (phone) cam,
- read out loud and record voice or use a phone,
- print it out,
and that's just a few (flashing office lights, using morse code, braille, OK, I'll stop now). 


> **mlk20 said:**
> What we are really worried about is that somebody does a copy/paste 
How "worried" are you actually then? I mean if you can't then that's cool but if you *can* put a price tag on data confidentiality in terms of compliance, liability, real or estimated damages due to copying data then maybe rethinking priorities may be in order?..

---

### Post by mlk20 on 2010-10-03
Thanks for thinking with me here!

Well, let's see. Ideally, when we have more capacity we would limit access and have somebody in charge of providing access as it is needed. But this will be when time and resources permit so. For the moment, the solution needs to be practical and that means providing access to all folders. 

The people using the system are not too technical nor will they think that we are monitoring this that much. So the most probable risk is that someone goes to Nautilus which we use to browse the server (through SFTP), and just does a copy/paste of the folders/files they are interested in. This would then go to a USB or is in some other way taken out of the office. But it is at this point where I want to be monitoring. Who is copying what file?

I am currently practicing with the log level setting in SFTP to see what I can get from there...

---

### Post by mlk20 on 2010-10-10
I've been trying to get this work but no luck. The only info I get from the log of SFTP is not detailed enough to see what files people actually opened/copied. Currently, my focus is on getting info on what people have accessed (open/copy). Something like:

Oct 10 14:21 192.168.1.103 OPEN FILE: /home/shared/client1/overview.doc
Oct 10 14:53 192.168.1.103 OPEN FILE: /home/shared/client1/timetable.doc
Oct 10 15:33 192.168.1.103 OPEN FILE: /home/shared/client1/contract.doc
Oct 10 16:31 192.168.1.103 OPEN FILE: /home/shared/client2/intro.doc

Well, you get the idea. Is there any way to get this info from the system? Any software that can accomplish this?

---

### Post by SeijiSensei on 2010-10-10
If these are one-way transactions, where staff members download files from the server but don't need to upload to it, I'd suggest using HTTP with "basic authentication" instead of FTP.  Apache will log every download in its access log, and if you use simply basic authentication, it will log the user name of each transaction as well.  If you're worried about password security, you can use HTTPS with a self-signed certificate.

If you want to enable both uploading and downloading, you can use the [DAV]("http://httpd.apache.org/docs/2.0/mod/mod_dav.html") protocol with Apache.

---

### Post by unspawn on 2010-10-11
> **mlk20 said:**
> (..) The only info I get from the log of SFTP is not detailed enough to see what files people actually opened/copied. (..)
Why? It actually says "OPEN". Note in my previous post I told you copying will be way harder to *prove* as there is no "copy system call".


> **mlk20 said:**
> Is there any way to get this info from the system? Any software that can accomplish this?
How about FUSE LoggedFS: [http://www.linuxquestions.org/questions/linux-security-4/auditd-missing-syscalls-813645/#post4001946](http://www.linuxquestions.org/questions/linux-security-4/auditd-missing-syscalls-813645/#post4001946) ?

---

