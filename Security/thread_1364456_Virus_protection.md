---
title: "Virus protection"
date: 2009-12-25
forum: Security
---

### Post by Virtueofselfishness on 2009-12-25
does ubuntu really need an antivirus and a firewall?

i heard its rare for ubuntu to get virus's 

i was wondering if i needed them or if i am ok

or should i just install just incase

---

### Post by teage3 on 2009-12-25
The firewall, Allways!.
As for the antivirus, I have clamav. I use it. I have had virus on ubuntu before and removed it with clamav. Thing is though, all the virus's i have had where no threat to my computer because it is usually a infected .exe file in one of the programs i install under wine. The virus is there under wine and thats really as far as it goes. But i would install the antivirus if i where you. Not that you have to worry so much about yer linux but, if you use a windoze emulator (like wine) then you dont want to transfer files one day and infect someone elses computer with the infected from yer machine. ;)

---

### Post by lovinglinux on 2009-12-25
First I would like to apologize in advance for my response. This has been asked and answered so many times that I will give you the search link.

Short answers:

anti-virus = no
firewall = probably not, most likely no

Here is the search link:

[http://tinyurl.com/yzwr74h](http://tinyurl.com/yzwr74h)

---

### Post by lovinglinux on 2009-12-25
> **teage3 said:**
> The firewall, Allways!.

Why?

[list][*] not really necessary if you have a router
[*] if you don't have any server running, then all unrequested incoming connections are rejected, so you don't need a firewall
[*] if you have a server running, then the firewall is only useful if you want to allow access to certain machines, while blocking others[/list]

---

### Post by Virtueofselfishness on 2009-12-25
no need to apologize

i knew i could find it since its a really common question

but i just wanted to be on the safe side

---

### Post by bodhi.zazen on 2009-12-26
Antivirus : There are no known active viruses for Linux. Most of the past viruses were more "proof of concept" and your system has been patched long ago.

Firewall: Depends, a better question is what do you want to do with a firewall ? Unlilke other OS, with a default install of Ubuntu there are no significant listening servers, so all your ports are closed.

I think you are much better off working your way through this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by sourcenaut on 2009-12-26
I don't think clamav is really needed, but a firewall should always be included.  There are so many exploits for web clients, I don't think even a firewall can protect you.

Use apparmor.

---

### Post by cariboo on 2009-12-26
Why set firewall rules when you aren't running any servers? If there is nothing listening, nothing needs to be blocked.

---

### Post by teage3 on 2009-12-26
Its obvious this is debatable. Maybe just depends on what you are doing. But in which case with any debatable question where as you cant get an exact answer, do what makes you feel safe. It most definitely will not hurt anything by having an active firewall. Just (sudo ufw enable) it and be done.

---

### Post by lisati on 2009-12-26
IMO, the main value of anti-virus on a Linux system is helping you avoid spreading something nasty accidentally and to help repair Windows systems e.g. if you're dual-booting.

Your first line of defense should be educating the users of your system to be smart with what they look at.

---

### Post by Trisket on 2009-12-26
Avast has a linux edition thats free.. not really necessary though..

---

