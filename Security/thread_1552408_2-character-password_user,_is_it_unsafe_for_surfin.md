---
title: "2-character-password user, is it unsafe for surfing web?"
date: 2010-08-13
forum: Security
---

### Post by Ve5ahchoo8ah on 2010-08-13
hi
I have a 2-character password both for my user and the root. (and they are same)
nobody has physical access to my computer. I use my computer for surfing web. is this something unsafe? how can it damage me or give an advantage to a hacker on the Internet?
:confused:

(come on! I start my computer, I should enter my password. I want to correct the clock, I should enter password. I want to start my firewall, I should enter password. I want to install a program, I should enter password and so on! If I choose a 10-character pass, by the end of the month I'll have spend the time for writing a book for entering my password over and over!) :P

---

### Post by WinstonChurchill on 2010-08-13
If I understand you right, a secure password bothers you because it takes you time to type in. A much more secure alternative (although not as secure as having to enter your password) is to edit the /etc/sudoers file such that your username (or a group that your username is a member of) doesn't have to enter a password to sudo (do privileged things like setting the clock) once logged in.

The short password for your username, although not a very good idea, is not the end of the world. However, you should NOT set such a lame password for root, and you really shouldn't enable root at all: if, as you say, this computer is only for web browsing, there is absolutely no reason to.

See: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Ve5ahchoo8ah on 2010-08-13
thanks, but can you describe me how can it make trouble for me?
for example can a hacker log into my system? (while I have firewall and no running web service) and if I use a 10-character password it will stop the hacker from loging into my computer?!

---

### Post by WinstonChurchill on 2010-08-13
> **samic130 said:**
> thanks, but can you describe me how can it make trouble for me?
for example can a hacker log into my system? (while I have firewall and no running web service) and if I use a 10-character password it will stop the hacker from loging into my computer?!
The default desktop install of Ubuntu 10.04 does not have any remote-login services running, so nobody can really "log in" in the usual sense. But, remember that web browsers can be exploited as well (Yea, even the godly Firefox...), and that the severity of such an exploit could be much worse if your passwords are easy to guess.

Let's say, for example, that some website you're visiting managed to exploit a buffer-overrun vulnerability in Firefox (See [http://insecure.org/stf/smashstack.html](http://insecure.org/stf/smashstack.html) if you're not familiar with such things) - as you're browsing the web, Firefox is running as your username, so whatever arbitrary code this malicious website is running on your machine is limited by your user privileges. However, if your passwords are easily guess-able, the exploit could su or sudo to root and have control over your entire system (To to this, it would only need to guess your user password). This is a reason that the scheme I mentioned in the previous post is not as secure as having to enter your password - if you can sudo without password, so can anything that exploits something running as your username. 

That's a somewhat crude example (Linux has defenses built-in against a lot of exploits like this, and the sudo command makes it hard to brute-force passwords (although, even a good alphanumeric-symbol 2 character password only has ~9000 possibilities)), but the crux of the argument is that there may be venerabilities out there that we haven't found yet, and that if some malicious website (or whatever) manages to find these and exploit them, having a secure password may very well help deter them from doing any huge damage.

---

### Post by bodhi.zazen on 2010-08-13
> **WinstonChurchill said:**
> The default desktop install of Ubuntu 10.04 does not have any remote-login services running, so nobody can really "log in" in the usual sense. But, remember that web browsers can be exploited as well (Yea, even the godly Firefox...), and that the severity of such an exploit could be much worse if your passwords are easy to guess.

Let's say, for example, that some website you're visiting managed to exploit a buffer-overrun vulnerability in Firefox (See [http://insecure.org/stf/smashstack.html](http://insecure.org/stf/smashstack.html) if you're not familiar with such things) - as you're browsing the web, Firefox is running as your username, so whatever arbitrary code this malicious website is running on your machine is limited by your user privileges. However, if your passwords are easily guess-able, the exploit could su or sudo to root and have control over your entire system (To to this, it would only need to guess your user password). This is a reason that the scheme I mentioned in the previous post is not as secure as having to enter your password - if you can sudo without password, so can anything that exploits something running as your username. 

That's a somewhat crude example (Linux has defenses built-in against a lot of exploits like this, and the sudo command makes it hard to brute-force passwords (although, even a good alphanumeric-symbol 2 character password only has ~9000 possibilities)), but the crux of the argument is that there may be venerabilities out there that we haven't found yet, and that if some malicious website (or whatever) manages to find these and exploit them, having a secure password may very well help deter them from doing any huge damage.

A shorter answer is :

The #1 security hole on any OS, windows or otherwise, is weak passwords. Weak passwords are much much much easier to exploit then flaws in the underlying code or social engineering.

---

### Post by cariboo on 2010-08-13
> (come on! I start my computer, I should enter my password. I want to correct the clock, I should enter password. I want to start my firewall, I should enter password. I want to install a program, I should enter password and so on! If I choose a 10-character pass, by the end of the month I'll have spend the time for writing a book for entering my password over and over!)

To stop having to correct your clock, use an ntp server. You don't need to start a firewall everytime you boot you computer if you type:

```
sudo ufw enable
```

the firewall rules are enabled until you disable them, even after a reboot:

```
sudo ufw enable
[sudo] password for me: 
Firewall is active and enabled on system startup
```

After the system is initially setup, how often do you install programs. If you are installing many programs from the command line, use:

```
sudo -i
```

BTW after using a nothing but a Linux variant for a couple of months, you don't even have to remember your password, you fingers do it for you. :)

---

### Post by Ve5ahchoo8ah on 2010-08-14
thanks all

---

