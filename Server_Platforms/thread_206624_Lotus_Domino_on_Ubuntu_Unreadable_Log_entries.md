---
title: "Lotus Domino on Ubuntu: Unreadable Log entries"
date: 2006-06-30
forum: Server Platforms
---

### Post by Juerg on 2006-06-30
I have installed Lotus Domino 701 (and I also tried with 655) on Ubuntu 6.06 Server. The installation and setup works well and I don't get any error messages.

The Domino server seems to be operating OK, i.e. Notes Dababases can be accessed, etc. However the Domino log file gets filled up with unreadable messages like:

0.06.2006 17:26:05   05:01
13:52
30.06.2006 17:26:18   13:29
13:52
13:52
30.06.2006 17:26:21   13:29
30.06.2006 17:26:21   13:29
13:52
30.06.2006 17:26:40   13:29
13:52
13:52
30.06.2006 17:26:43   13:29
30.06.2006 17:26:43   13:29
30.06.2006 17:26:52   33:07: 0A:4C
13:52
30.06.2006 17:27:02   13:29
13:52
30.06.2006 17:27:04   13:29
13:52
....

All log entries are of this type, none of them are readable. I tried with the newest Domino 7 server and with Domino 6.5.5 - with the same result. :confused: 

What could be the reason for this? How can I find out what to do about this? All help will be much appreciated

Juerg

---

### Post by dro0g on 2006-06-30
I don't mean to be a pain in the ***, I appreciate the spirit of getting something to run on an OS it's not designed to run on (I myself was one of the first people to get the R5 Linux beta running under Linux emulation in FreeBSD) However, I think you'll find Domino runs better under Redhat, or if you're looking for something free as in beer, CentOS (full binary compat. with Redhat) 

If you're looking to run this as a production or even dev server, that's the route I would go. If you're just experimenting, awesome and good luck and I have no idea what could be causing those log file entries :)

-Dro0g <used to support around 10k users on Domino on Linux>

---

### Post by Juerg on 2006-07-02
Thank you for your advice. Well, if I can't find out why the log is showing unreadable entries, I don't really have a choice. :(  I'll definitely have to switch the distribution to CentOS.

I am neither a Linux nor a Lotus Domino specialist, however I was hoping to be able to re-use my Debian knowledge. The Domino server will have almost no load: 3 LAN-users and about 100 remote users replicating about twice per week via modem or ISDN. This is the reason I was hoping to get it up and running on an unsupported distro.

Juerg

---

### Post by tester321 on 2008-03-31
(I know this thread is almost 2 yrs old) ... but

In case anyone cares, I got Domino r5 and r6 to run on Debian 4.0 (Etch) and OpenSUSE (10.1, 10.2), no issues.

In fact, it has run on Debian 4.0 as a VMware Virtual Machine on top of VMware 1.0.4 running on OpenSUSE 10.1.

It works, and works very well -- no crashes at all.

Would love to run it as a FreeBSD VM, but don't have time to play with that right now.

---

