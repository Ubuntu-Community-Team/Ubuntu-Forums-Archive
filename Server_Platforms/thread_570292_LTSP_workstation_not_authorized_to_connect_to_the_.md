---
title: "LTSP workstation not authorized to connect to the server"
date: 2007-10-08
forum: Server Platforms
---

### Post by mthaddon on 2007-10-08
Hi Folks,

I'm trying to get LTSP setup so I can demo it for a talk I'm doing in a few days, and I'm about 99% of the way there (I think).

I have LTSP installed, and my test client can boot from the tftp server. The problem I'm having is a message saying that:

"This workstations is not authorized to connect to the server" (I get this just after entering my username and password at gdm - although I think strictly speaking it may be kdm).

I saw the comment on this bug [https://bugs.launchpad.net/bugs/144296](https://bugs.launchpad.net/bugs/144296) recommending to run sudo ltsp-update-sshkeys && sudo ltsp-update-image, which I did, but am still getting the error message...

Any ideas?

Thanks, Tom

---

### Post by maybeway36 on 2007-10-08
hmm... Well, it is technically ldm. That sounds very perplexing indeed.
Did you try another computer?

---

### Post by mthaddon on 2007-10-08
Unfortunately I don't have another computer to test it on yet... Might be able to remedy that later today...

---

### Post by Athanasius on 2007-11-05
I have the same problem, I have updated the ssh keys and everything but the problem still persists.  I did not have this problem using feisty and edubuntu works just fine (but I don't want to use it).

---

### Post by mthaddon on 2007-11-06
> **Athanasius said:**
> I have the same problem, I have updated the ssh keys and everything but the problem still persists.  I did not have this problem using feisty and edubuntu works just fine (but I don't want to use it).

My problem was related to a bug which was caused by my /opt/ltsp being a symlink - there are two plugins that use "find" to get the paths of the chroots used by ltsp, and if this directory is a symlink "find" doesn't cross the symlink.

---

### Post by Dzenhax on 2007-11-17
mthaddon,

     I'm using edubuntu 7.10 and am having the same problem.  I'm still learning so could you please tell me how you fixed the symlink problem?  Let me know what commands to type.

     I mistype the dhcp config file and it took me three hours to find that problem.  When I saw the thin client boot up I was overjoyed.  So not being able to log sucked really bad.

Thanks for any help.

---

### Post by mthaddon on 2007-11-17
Are you sure /opt/ltsp is a symlink? If not, post the output of "ls -lh /opt/ltsp".

If it a symlink, there are two ways to fix it:

1. Make sure /opt/ltsp is not a symlink. You can do this by creating the symlink to /opt instead of /opt/ltsp, foir instance. I can't really give you step by step instructions for this without knowing your filesystem layout. Just post if you like.

2. Add a trailing slash to the "find" comands in two scripts:

sudo gedit /usr/sbin/ltsp-update-keys

Look for:

CHROOTS=$(find ${BASE} -mindepth 1 -maxdepth 1 -type d 2>/dev/null | \

Change to:

CHROOTS=$(find ${BASE}/ -mindepth 1 -maxdepth 1 -type d 2>/dev/null | \

Save and close

sudo gedit /usr/sbin/ltsp-update-kernels

Look for:

ALL_CHROOTS=${ALL_CHROOTS:-"$(find $BASE -mindepth 1 -maxdepth 1 -type d | \

Change to:

ALL_CHROOTS=${ALL_CHROOTS:-"$(find ${BASE}/ -mindepth 1 -maxdepth 1 -type d | \

Save and close.

Let me know if that works for you.

---

### Post by Dzenhax on 2007-11-18
Mthaddon,

     Thanks for the reply.  I got it working.  The problem ended up being me misconfiguring the DHCP server.  Once I straightened that out it worked fine.  I took me three hours and another thin client to figure out that one number mistake.

     I'm still having issues.  If you have time please take a look at my post at [http://ubuntuforums.org/showthread.php?t=616214](http://ubuntuforums.org/showthread.php?t=616214) .  This is one of my two last hurdles before I can feel I did a decent job with my project.

Thanks again.

---

### Post by ahmadzainul on 2008-05-05
its work for me. Tank you. But How to get better resolution instead of 600 X 800

---

### Post by gravometric on 2008-05-05
I had this same issue.  Checked that /opt/ltsp was not a sym link, it wasn't.

The problem I had was the router installed to subnet my classroom was issuing IP addresses in the same scope.  I think that after the TFTP client booted, the computer gets another IP address to actually use for the operating system and the router was being Discovered and Requested to for the IP address instead of the Edubuntu server.  

I disabled the DHCP service on the IPCop (Router) and my terminals stopped giving me this message and started acting normal.

hth,
Grav

---

### Post by acesabe on 2008-05-07
Same server connection error here - perhaps different reason.

Running 8.04 64bit server, ran the ltsp-build command to create the thin client environment, then realized this creates a 64bit thin term environ - which of course is useless, unless you happen to be running a suite of 64bit clients?!! So i deleted the /opt/ltsp/amd64/ folder and contents, then recreated the correct environ with the --arch i386 (i think - am away from server now).
All is well until the server connection error at client login screen - running ltsp-update-image now fails due to missing /opt/ltsp/amd64/ folder....

---

### Post by acesabe on 2008-05-07
OK - solution is to use the **-a** appendage to specify alternate architecture:

$ **sudo ltsp-update-image -a i386**  in my case

---

