---
title: "antivirus for ubuntu"
date: 2009-03-17
forum: Security
---

### Post by bcbotha on 2009-03-17
I know that most viruses are written for windows and therefore don't affect linux, however i'm dual booting ubuntu and vista. i want to know is there an antivirus i can install on ubuntu to search my windows partition and my linux partition to delete any windows viruses?
i know clamwin, avg and kaspersky apperntly have a linux download but how good are they? and where and how could i download them from?

thanks

---

### Post by buldozerceto on 2009-03-17
Out of those kasperksy is the best.

---

### Post by bodhi.zazen on 2009-03-17
IMO antivirus on Windows is best.

Antivirus on Linux has a lot of false positives.

---

### Post by HermanAB on 2009-03-17
The best way to fix broken Windows is with a CDROM bootable version of Windows called BartPE.  

My experience with Clam Antivirus on a Linux mail server is good.  The Windoze machines keep working properly for years on end.  Viruses do not get through.

Cheers,

Herman

---

### Post by twindragon89 on 2009-03-18
[FONT="Century Gothic"][/FONT]Well I think they already made an Anti virus for Linux OS. It's impossible that they have didn't made one yet Linux is already known Operating system and its impossible that a no programmer hasn't developed a Virus for the Linux.

---

### Post by ruel- on 2009-03-18
Linux antivirus don't detect windows viruses, they only detect rootkits, backdoors, and linux trojans..

---

### Post by bcbotha on 2009-03-18
I know ClamAV is an officially-supported package in the Ubuntu repositories.
but what about kaspersky and avg, where do hey fit in?

---

### Post by bcbotha on 2009-03-18
what linux anti viruses are there that detect rootkits, backdoors, linux trojans and the like?

---

### Post by ruel- on 2009-03-18
clam AV, avast, kaspersky, nod.. 

here take a look:

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by bodhi.zazen on 2009-03-18
> **ruel- said:**
> Linux antivirus don't detect windows viruses, they only detect rootkits, backdoors, and linux trojans..

That is not true. Most , if not all, linux anti virus will search for windows viruses. The most common use is in fact to run clamav on a linux mail or file server servicing windows clients.

I do not think they detect rootkits, backdoors, or trojans, although they may check for some.

Really you should read the stickies at the top of these forums: Ubuntu security, apparmor, and intrusion detection.

---

### Post by ruel- on 2009-03-18
oh, you're right.. sorry :\

Linux Antivirus is designed specially for Windows Viruses,(file servers, mailing servers, and Network w/ windows OS installed)..

And maybe its IDS that look for those stuff I said, I'm not really a computer security expert, but I need to be one, I usually just step into web application layer for security, but not yet for the physical nor the OS itself..

anyway, thanks for the correction! :)

---

### Post by jadhav333 on 2009-03-18
> **bcbotha said:**
> I know that most viruses are written for windows and therefore don't affect linux, ...

This is a very common statement I have seen on the internet.. the emphasis on 'most'.. 

Does that mean there are 'some' viruses that are indeed written for linux?

In that case, How do we protect ourselves from these?

Are we just closing our eyes and assuming that we are safe from viruses? 

What is stopping a anti-linux user/hacker to write and distribute a virus written specifically for linux, even as we read this post. 

Can we take 'false?' comfort in the knowledge that linux is and will always remain virus free?

Pls share anything you know in this aspect.

Thanks
// jadhav333

---

### Post by ruel- on 2009-03-18
> **jadhav333 said:**
> This is a very common statement I have seen on the internet.. the emphasis on 'most'.. 

Does that mean there are 'some' viruses that are indeed written for linux?

In that case, How do we protect ourselves from these?

Are we just closing our eyes and assuming that we are safe from viruses? 

What is stopping a anti-linux user/hacker to write and distribute a virus written specifically for linux, even as we read this post. 

Can we take 'false?' comfort in the knowledge that linux is and will always remain virus free?

Pls share anything you know in this aspect.

Thanks
// jadhav333

this article helped me alot regarding this matter:
[http://www.techthrob.com/2009/03/02/do-i-need-an-antivirus-program-on-linux/](http://www.techthrob.com/2009/03/02/do-i-need-an-antivirus-program-on-linux/)

---

### Post by jadhav333 on 2009-03-18
> **ruel- said:**
> this article helped me alot regarding this matter:
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

I dont see any information related to virus on that link.. can you elaborate, please?

---

### Post by ruel- on 2009-03-18
I copied the wrong link from the wrong tab.. xD

sorry :p

[http://www.techthrob.com/2009/03/02/do-i-need-an-antivirus-program-on-linux/](http://www.techthrob.com/2009/03/02/do-i-need-an-antivirus-program-on-linux/)

---

### Post by jadhav333 on 2009-03-18
The provided link states the same fact: that the linux av programs are designed to detect windows viruses on connected windows m/c..

lets get Windows out of the picture..

My point was, why do we assume that nobody will ever come up with a linux virus designed to affect linux m/c? 

or Is it that such a virus can never be written, due to linux architecture, security features, blah, blah , whatever...

regards
// jadhav333

---

### Post by ruel- on 2009-03-18
there are linux viruses/worms out there, they infect using vulnerabilities most specifically in kernels, so when there is a live vulnerability in the system, somebody can code a script or program to exploit it, and use that machine to infect others.

If you get the logic, you will understand what I'm trying to say.. :)

---

### Post by bcbotha on 2009-03-18
but then what antivirus program is there to detect and delete those worms and viruses exploiting holes and problems in the kernel or OS as a whole?

---

### Post by bodhi.zazen on 2009-03-18
Please read the stickies at the top of this forum.

Linux is not Windows.

In Windows, known holes in the code go unpatched for decades, thus you need third p art applications to patch them, such as a firewall and antivirus.

In Linux, known holes are patched much more rpaidly, sometimes within hours.

Likewise Linux security is different and uses different tools. We have things like iptables, snort, OSSEC, and SELinux and AppArmor.

I am going to close this thread now because as is all too common the discussion is going in circles.

---

