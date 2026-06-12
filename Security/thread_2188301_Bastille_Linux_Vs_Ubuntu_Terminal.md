---
title: "Bastille Linux Vs Ubuntu Terminal"
date: 2013-11-16
forum: Security
---

### Post by kingcobraa on 2013-11-16
Hi,

I was looking for a way to secure Ubuntu 12.04 Desktop version LTS-V.

Then I read about Bastille Linux and how powerful it is however I wonder.

Using  Terminal : Is there a way to secure/Harden Ubuntu desktop using  terminal/CLI without using Bastille Linux, where it would be understood  that we end up with the same if not better security level than using  Bastille Linux?

Curious to know the commands that we could use to harden it i.e using CLI only.

---

### Post by houstonbofh on 2013-11-16
What do you want to harden?  By default, Ubuntu installs with almost nothing listening on any ports.  If you install other services, it is usually because you want them to work, so "hardening"" is not the answer there.

What specifically are you trying to do, and why?

---

### Post by kingcobraa on 2013-11-16
Hi,

Many thanks for responding. 

In short I want to harden  my own computers using CLI instead of using  downloaded security  programs. Can someone post all the commands to do  this?

Points to  be noted: Basically no computer user whether a novice or an  expert will  use a barebones linux install without some or a very high  level of  customization, this tends to either strengthen or weaken  security on the  host computer.

Hence the task today is to accomplish with terminal/CLI what Bastille Linux is capable of accomplishing.

I guess the same applies with the multitude of security programs that exist out there that :

1) Search and identify vulnerabilities.

2) Rectify the vulnerabilities.

3) Monitor for any major or minor changes to the OS.

This  is what I am trying to accomplish but using only CLI. One thing I  have  started loathing with these security tools is downloading and  installing  this and that software for this and that purpose and it only  uses space  on my disk and then there is a learning curve to it which  is sometimes  steep, the programs provide a good amount of usability via  a GUI yes no  doubt but then why not DIY?. The CLI is built into Linux  and can do the  same thing (if not better) isn't it??

PLUS The end result is that  we have more control as we know what  changes we have made but we don't  know what changes they have made  unless they tell us or we go looking  for the changes THEN sometimes in  the process of installing their software we don't know if there are any  bugs.

Hope that explains.

---

### Post by deadflowr on 2013-11-16
Did you try reading through this sticky
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Some points in there covering what you're asking about.

As far as a security goes, though, the end-user can make or break all plans.

---

### Post by sandyd on 2013-11-16
> **kingcobraa said:**
> Hi,

Many thanks for responding. 

In short I want to harden  my own computers using CLI instead of using  downloaded security  programs. Can someone post all the commands to do  this?

Points to  be noted: Basically no computer user whether a novice or an  expert will  use a barebones linux install without some or a very high  level of  customization, this tends to either strengthen or weaken  security on the  host computer.

Hence the task today is to accomplish with terminal/CLI what Bastille Linux is capable of accomplishing.

I guess the same applies with the multitude of security programs that exist out there that :

1) Search and identify vulnerabilities.

2) Rectify the vulnerabilities.

3) Monitor for any major or minor changes to the OS.

This  is what I am trying to accomplish but using only CLI. One thing I  have  started loathing with these security tools is downloading and  installing  this and that software for this and that purpose and it only  uses space  on my disk and then there is a learning curve to it which  is sometimes  steep, the programs provide a good amount of usability via  a GUI yes no  doubt but then why not DIY?. The CLI is built into Linux  and can do the  same thing (if not better) isn't it??

PLUS The end result is that  we have more control as we know what  changes we have made but we don't  know what changes they have made  unless they tell us or we go looking  for the changes THEN sometimes in  the process of installing their software we don't know if there are any  bugs.

Hope that explains.
There is a reason why tools such as Bastille Linux are preferred - they are regularly tested and screened for bugs and issues by the community. If you setup a DIY system, there is no guarantee that it is free of bugs/issues.

Then, back on topic....
1. Make sure your system is updated
You can setup automatic security updates by running
```

sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
``` (while choosing yes at the prompt)
2. Enable Firewall
You can use either iptables or ufw
I like iptables, but thats just because I'm used to using csf/lfd....
There are plenty of guides on the internet that show you how to deny all traffic by default except for established sessions, so I wont cover this here

3. Setup GrSecurity and PAX
Heres a guide -> [http://www.insanitybit.com/2013/06/15/configuring-grsecurity-is-easier-new-autoconfig/](http://www.insanitybit.com/2013/06/15/configuring-grsecurity-is-easier-new-autoconfig/)
Read more about GrSecurity [here]("http://grsecurity.net/")

4. Write your own apparmor rules
Ubuntu runs a MAC (Mandatory Access Control) system called Apparmor. By default, applications such as rhythmbox, pidgin, .etc .etc have read access to lots of areas of your system. You can write apparmor rules to secure them.

There are a few more things that you can read over at [http://www.insanitybit.com/2012/12/17/hardening-ubuntu-linux/](http://www.insanitybit.com/2012/12/17/hardening-ubuntu-linux/)

---

### Post by houstonbofh on 2013-11-17
You still have not said what you want to do.  You have just said what tools you want to use.

What services are on this system that you want secured?  What threats are you concerned with?

Just saying "I want to harden my server" is nothing.  That can be anything from "Unplug the Ethernet cable" to doing nothing because you have no services listening...

---

