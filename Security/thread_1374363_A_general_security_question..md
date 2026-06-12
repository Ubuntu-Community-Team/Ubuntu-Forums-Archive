---
title: "A general security question."
date: 2010-01-06
forum: Security
---

### Post by boosterjet on 2010-01-06
Hi, 

I have just managed to get my Karmic installation working properly (one more small problem to fix later) however I have been working with Windows XP where I run Zone Alarm's Forcefield and Security Suite which has proved extremely effective protection for my Windows system. 

After reading through this forum and Ubuntu's documents on just how secure the linux system is I am still a little reluctant to switch completely to Ubuntu. I do most of my banking and bill paying by internet and so am naturally worried about system security. I have installed the Gufw firewall, does any body have any other recommendations for anti-virus/spyware or anything else they feel I should run to feel reasonably secure. My Windows security systems are not compatible with Linux. I really do like set and forget systems that tend to look after themselves.:D

Many Thanks John

---

### Post by sisco311 on 2010-01-06
In order to secure your system you have to understand how it works.

Security softwares are not magical tools (this is true for Windows softwares as well;)). You have to set them up properly and monitor them from time to time.

Check out:
[thread=510812]Ubuntu Security[/thread]

---

### Post by running_rabbit07 on 2010-01-06
I found this [post by Bodhi]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236") to be very comforting and informational. I have been reading his Security threads and must say that I feel he knows his stuff with Network Security.

> **bodhi.zazen said:**
> Depends on how paranoid you are. I know coming from windows you feel the need to check these things, but, root kit checkers and antivirus give so many warnings and false positives they just do not help that much.

As I see you are interested in security I suggest you look at the big security sticky and work you way though it.

Then go ahead and run tiger (see security stick for info on tiger) and the root kit checks, and antivirus on a FRESH INSTALL OR LIVE CD, then on your desktop, if nothing else to get a sense of how these tools work, what a "normal system" looks like, what the reports from these tools look like.

Then decide for yourself if you wish to use them long term.

My experience was, in the absence of running a server, relax and enjoy Linux.

For your situation, I advise you look at :

[COLOR=DarkOrange]**ufw, noscript, and apparmor**[/COLOR], those will give you more bang for you time then rk hunters, tiger, or antivirus.

ufw, noscript, and apparmor prevent the damage in the first place, the other tools detect the problem (if you are lucky) after it is too late. Anyone with more experience then a "script kiddie" will evade the rk hunters anyway, and the logs I have seen from compromised systems were:

1. not discovered by a rk hunter or antivirus. The were detected by somebody who knows their system, what "normal" is, and that "something" was different.

2. The actions of the crackers would not trip a rk hunter.

In order to detect a modern intruder you need to be able to read the logs, read bash_history, identify who is logged in, or recognize that those files have been altered.

Learn these commands :

```
w
last
ps aux #(or variants)
top
```Learn to read the logs !!!

---

### Post by 3rdalbum on 2010-01-06
> **boosterjet said:**
> I really do like set and forget systems that tend to look after themselves.:D

Then you'll love Ubuntu.

Ubuntu, unlike Windows, does not listen to incoming connections unless you explicitly activate them. This means that you DON'T need a firewall on Ubuntu, as long as you haven't turned on Remote Desktop or installed any server software.

Firefox can't be taken over unless:

1. You go to a disreputable website
2. That website knows of an exploit for the current version of Firefox on Linux, and uses it (unlikely, there are none in-the-wild as far as I can see)
3. That exploit gets past Ubuntu's AppArmour security profile for Firefox that restricts what certain applications can do.

In short, Linux is virtually a set-and-forget operating system. Just keep it up to date and don't do anything stupid like disable security systems or install server software that you don't know how to use.

---

### Post by 3rdalbum on 2010-01-06
> **boosterjet said:**
> does any body have any other recommendations for anti-virus/spyware or anything else they feel I should run to feel reasonably secure.

Why would you need anti-virus and anti-spyware? There are no viruses or spyware that work on today's Linux distributions. There are rootkits, but they can only be installed on poorly-secured servers.

---

### Post by tubbygweilo on 2010-01-06
> **boosterjet said:**
> ... After reading through this forum and Ubuntu's documents on just how secure the linux system is I am still a little reluctant to switch completely to Ubuntu. I do most of my banking and bill paying by internet and so am naturally worried about system security...

John, Some would suggest using a [live cd]("http://www.itnews.com.au/News/157767,nsw-police-dont-use-windows-for-internet-banking.aspx") is quite a safe way to pay bills and such but can be a pain each time something needs to be done. You can have faith in a standard Ubuntu install coupled with at least the Noscript, Adblock+ addons to Firefox. I would expect one of the bigger problems you and many others face is clicking on a suspect link and falling for some form of social engineering tick but this risk is minimised by running from bookmarks with a recently updated Ubuntu & Mozilla Firefox.

Keep safe.

---

### Post by slowth5 on 2010-01-06
Hi boosterjet, I was worried about system security when I switched to ubuntu from Windows, but I now realize that fear was unfounded. 

The Windows security tools are detrimental because they provide a false sense of security. Identifying all of the malware written for Windows is a monumental task, and the AV heuristics, while constantly improving, are just not up to snuff.

I'll parrot bodhi.zazen because it's just solid advice, be proactive and use ufw, noscript, and apparmor. When used properly these programs will lock your system down. 

Windows is a security minefield.

---

### Post by running_rabbit07 on 2010-01-07
> **slowth5 said:**
> Windows is a security minefield.

I think they had job security in mind for their AV and Network security contractors.

---

### Post by kentechy on 2010-01-07
[http://techreviews.in/installing-free-bitdefender-anti-virus-on-ubuntu-904/](http://techreviews.in/installing-free-bitdefender-anti-virus-on-ubuntu-904/)

Check out the link above.  I run the free version of Bitdefender.  It seems to work well and doesn't slow Ubuntu down, as far as I can tell.  Many say that antivirus software is not necessary for Ubuntu but I figure it can't hurt.  Hope this helps you out.

God Bless...

---

### Post by boosterjet on 2010-02-03
Thank you all, much happier.
John

---

### Post by lucasart on 2010-02-13
> **boosterjet said:**
> Hi, 
I have installed the Gufw firewall, does any body have any other recommendations for anti-virus/spyware or anything else they feel I should run to feel reasonably secure.
Many Thanks John

You don't need to install anything. Antivirus will just slow down your system. The most forcefull way to protect yourself is to close all incoming connections. Open a terminal and type:
```

sudo ufw enable

```
(and type your password)
As for viruses, they can only execute on Windows!

The last thing to worry about now is websites with executable content like Java script. Quite simply Java is not installed on Ubuntu and Java script doesn't work: a good riddance!
Otherwise have a look at the security options in Firefox.

---

### Post by BigCityCat on 2010-02-13
What I do like about bit defender is that I can scan my windows drive when I'm using Kubuntu. Which is like 95% of the time.

---

