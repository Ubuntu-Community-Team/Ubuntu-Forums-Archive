---
title: "live cd security"
date: 2010-03-11
forum: Security
---

### Post by Fika on 2010-03-11
Is an ubuntu live cd totally secure from intrusion? 

Stated another way, even if someone knows my ip address, can the live cd environment be hacked into in any way so that another could monitor what I am doing on my computer? 

From my understanding the live cd is read only, so that would prevent anything malicious being installed on it. I am curious if there are other ways a box running a live cd could be tapped into.

---

### Post by tubbygweilo on 2010-03-11
A few recent [thoughts]("http://ubuntuforums.org/showthread.php?t=1420187") on using live cd vs guest account to stay safe and secure while browsing. Although not exactly answers to your question it may help in some way.

---

### Post by abohsin on 2010-03-11
Hi,

Let us put some facts, this is purely a personal experience (winxp,win vista, win 7, win2003,fc10,fc11,fc12,ubuntu koala):
1. In general, any linux is much more secure than windows.
2. Live cds are a small version of the operating system.
3. The purpose of live cds is to try the version, then when comfortable u install it; or u can install it to a usb to have it portable with you.
4. Live cds, since they are linux, they are secure by nature. But, u must know that root and live user have blank passwords, they are not updated with latest security updates. So if u wish to use a live cd (install to hdd or live usb) you must change passwords for live user and root, and keep up to date with security updates.
5. Security is a concept, and not a brand.

So in short, live cds are secure, but you must use your mind when deciding to permanently use to keep yourself secure.

---

### Post by Fika on 2010-03-11
Linux might be more secure than windows, but that doesn't mean it is worry free secure. 

All the time consuming system hardening of ubuntu that has to be done is a headache to someone who is not technically minded. 

I've personally been hacked into a number of times using a default install of ubuntu. I am now using a live cd for 'secure' browsing, hence my question. 

I didn't think anything could be installed during a live cd session. Isn't that the meaning of 'read-only'?

---

### Post by bodhi.zazen on 2010-03-11
> **Fika said:**
> Is an ubuntu live cd totally secure from intrusion?

No , the only totally secure computer is one that is disconnected from the internet, turned off, and locked in a vault.

> Stated another way, even if someone knows my ip address, can the live cd environment be hacked into in any way so that another could monitor what I am doing on my computer?How does knowing your ipaddress allow you to crack into a computer ? The ip address of every public web server is known.

People can only crack into a computer system via a small number of methods, basically physical access, social engineering, cracking into a running server, or taking advantage of coding holes.

> From my understanding the live cd is read only, so that would prevent anything malicious being installed on it. I am curious if there are other ways a box running a live cd could be tapped into.Why would you think that ?

Boot the live CD, open a terminal, and type :

```
sudo apt-get update
sudo apt-get install vim
```The Live CD is read only, meaning when you shut it down none of your changes, to themes, installed applications, or documents are changed.

The live CD is insecure in many ways, one of which is the fact that no password is required for root access.

Furthermore , the packages are old and not up to date in terms of the latest security and other patches.

This means , if there is a faulty version of Firefox on the Live CD , that allows one to exploit firefox, and run arbitrary code, the cracker then has full access as the default user has root access with no password.

With all that in mind, this is not windows. Ubuntu out of the box is, IMO, more secure then a hardened version of Windows. There are no significant open ports and ther are no known active Linux viruses (you system has been patched to all known viruses as of the day the iso was made, but not beyond that date).

If you are interested in Security, start with :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

If you want a more secure Live CD, I strongly suggest Zenix.

Zenix is based on Ubuntu and has apparmor and a firewall active by default (unlike the Ubuntu Live CD).

[http://zenix-os.net/](http://zenix-os.net/)

---

### Post by km0r3 on 2010-03-11
> **Fika said:**
> Is an ubuntu live cd totally secure from intrusion? 

No. There doesn't exist something like total security.

Simple example:
You boot up with Ubuntu's 9.10 Live CD, which contains a lot of outdated software and use it. This can be abused.

Now if you really insist using a no-compromised system, then using a Live Distribution sounds reasonable, but I repeat: *There's no such thing as "totally secure"*.
> 
Stated another way, even if someone knows my ip address, can the live cd environment be hacked into in any way so that another could monitor what I am doing on my computer? 

There are a lot of other ways penetrating into your system, without necessarily knowing your IP address.
There are a lot of treats in the Internet.

> 
From my understanding the live cd is read only, so that would prevent anything malicious being installed on it. I am curious if there are other ways a box running a live cd could be tapped into.
Wrong. Now I don't want to lie, but I think when you boot up a Live CD everything gets written to RAM, and when you switch off your Computer all of the information stored on RAM will be gone. That's how it's working. So it's very possible to write.

[CENTER]Best security practice #1:


[SIZE=6]**Common Sense**[/SIZE]
[/CENTER]

---

### Post by bodhi.zazen on 2010-03-11
> **Fika said:**
> Linux might be more secure than windows, but that doesn't mean it is worry free secure. 

As I indicated, no OS is completely secure, they all have potential exploits.

> All the time consuming system hardening of ubuntu that has to be done is a headache to someone who is not technically minded. 

That is all one can do, make it as difficult as possible for a cracker to exploit the system. One can not ever completely secure a computer connected to the internet. This is true of any OS.

> I've personally been hacked into a number of times using a default install of ubuntu. I am now using a live cd for 'secure' browsing, hence my question. 

How were you hacked ? What server were you running ? What ports did you forward from your router ? What makes you think you were cracked ?

I would answer and fix those questions.

> I didn't think anything could be installed during a live cd session. Isn't that the meaning of 'read-only'?

IMO you need to learn how security works. A live CD is always going to be less secure then an installed updated OS, if for no other reason then the packages are out of date and you have not performed security updates.

In terms of installing applications, see my post.

In terms of security, although I understand your concerns, a Live CD is not really the solution, you need to understand how you were cracked and plug the hole.

Any effort you put into hardening a Live CD is, IMO, much better spent in learning how Linux security works and hardening an installed OS.

---

