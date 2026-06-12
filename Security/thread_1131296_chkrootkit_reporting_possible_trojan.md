---
title: "chkrootkit reporting possible trojan"
date: 2009-04-20
forum: Security
---

### Post by frankwakeman on 2009-04-20
Today after relying on nothing but the Gufw firewall I installed chkrootkit. I've just run it for the first time and all the results are innocent enough except this:

Checking `lkm'... You have 4 process hidden for readdir command
You have 4 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

Is it nothing to be concerned about i.e. would a freshly installed Ubuntu 8.10 give the same result? I know these things can be a bit sensitive, so to speak, and I had become quite relaxed with the idea of Linux's security strengths.

I have no idea what we are meant to do after running this program though, and chkrootkit is a Terminal-operated program which leaves me in the dark a bit.

Thanks in advance.

---

### Post by brian_p on 2009-04-20
> **frankwakeman said:**
> 

Checking `lkm'... You have 4 process hidden for readdir command
You have 4 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

Is it nothing to be concerned about i.e. would a freshly installed Ubuntu 8.10 give the same result?

[http://www.chkrootkit.org/faq/](http://www.chkrootkit.org/faq/)

---

### Post by lensman3 on 2009-04-21
It is a false positive.  I've had that message disappear later and I haven't done or changed anything.

Try running chkroot manually. (I run mine from a root cron every 3 hours).

---

### Post by skunkbad on 2009-04-21
What are the chances of getting an actual rootkit on a Ubuntu only system? I'm just browsing the forums, and this is the first I've heard of potential rootkits on Ubuntu.

---

### Post by lensman3 on 2009-04-21
Google "chkrootkit" and download the tar ball.  There is a README (which is fairly close to a FAQ).  The web site has a FAQ.  

I don't think it is very common.  Linux has less than 10 percent of the computer OS base, so it is not very "profitable" if a system is compromised.

Hope this helps.

---

### Post by frankwakeman on 2009-04-22
chkrootkit is in Synaptic, so no need to fiddle with tarballs.

---

### Post by jimv on 2009-04-22
The likelihood that you have a virus or trojan is about zero.  You're better off not worrying about running chkrootkit and not stressing yourself out.

---

### Post by iponeverything on 2009-04-22
> **skunkbad said:**
> What are the chances of getting an actual rootkit on a Ubuntu only system? I'm just browsing the forums, and this is the first I've heard of potential rootkits on Ubuntu.

I have been using linux since 1993 and have tell you that rootkit'ed machines are not uncommon. 

Who are at the most risk:

- Someone with a public IP address directly connected to internet running 

- Someone with a firewall router with default password in place.

a) a web server (it is very easy to write bad php code)
b) other publicly accessible services like a database, dns server, mail server, ssh server - etc.

Here is why -- service misconfiguration, weak passwords (databases and local accounts accessible through ssh) - and poorly written php code.

mitigation is fairly strait forward. Run nmap from another machine on your network - baring that that, from the machine itself against itself. 

Limit access to services to just those ip addresses needing them.

create strong passwords.

The default ubuntu desktop install does quite well -- the problem comes in when person has a weak password and installs an ssh server or enables vnc.

Many times the compromised linux machines go unnoticed for long time because they often used as stepping stones to cover tracks.

You do not what your box to be used to break into the system of a defence contractor or government entity -- believe me.

---

### Post by iponeverything on 2009-04-22
> **jimv said:**
> The likelihood that you have a virus or trojan is about zero.  You're better off not worrying about running chkrootkit and not stressing yourself out.

A viruses or trojans is not the primary vector for rootkits under linux or UNIX system. Your right in that viruses or trojans are not likely though. 

The primary vectors are server misconfiguration, weak passwords and un-patched vulnerabilities.

---

### Post by frankwakeman on 2009-04-25
I reinstalled the O.S. and then chkrootkit from scratch, ran it three times and got the same LKM 3 to 5 processes warning last night, so I'm taking that as proof that they're false positives.  Pardon me if my enquiry made anyone, newbie or otherwise, anxious.

I imagine someone might want to say a trojan may reside on the hard drive after the new installation was made (?) but I'd have to take that as mischief-making, I don't want to start thinking about security, as like anyone it's why I got bored of maintaining Windows.

---

### Post by HermanAB on 2009-04-25
Hmm, chrootkit is basically junkware.  Don't use it.  It is just a waste of time.

---

