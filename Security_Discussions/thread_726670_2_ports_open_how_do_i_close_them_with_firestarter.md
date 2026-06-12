---
title: "2 ports open how do i close them with firestarter"
date: 2008-03-16
forum: Security Discussions
---

### Post by corkscrew on 2008-03-16
I'm  a newbie trying to secure my new linux box. I've read all the stuff about ubuntu not opening any ports, but if i go to shields up it says ports 22 and 23 are open. how can i close these with firestarter? i've looked through the manual but can't find anything

---

### Post by corkscrew on 2008-03-16
I'm a newbie trying to secure my new linux box. I've read all the stuff about ubuntu not opening any ports, but if i go to shields up it says ports 22 and 23 are open. how can i close these with firestarter? i've looked through the manual but can't find anything

---

### Post by bsharp on 2008-03-16
Those 2 ports are open because of the SSH server (which is included by default) that is running, which allows you to remotely control your computer via terminal(port 22). IMAP is used for mail(port 23).

I believe to close them you need to stop the services running on those ports, but there isn't much of a security risk of leaving them open.

---

### Post by handydan918 on 2008-03-16
There isn't much risk to port 22 ***_if you have a strong password._***
I left port 22 open overnight once and logged several attempts (from China and Mexico) to access the system. Port 22 get knocked all the time.
If you must leave port 22 open, use fail2ban.
And don't use dictionary words for passwords. Use alpha-numeric upper and lower case with a few symbols, ideally 12 characters or more.

---

### Post by Patrick-Ruff on 2008-03-16
12 characters or more for a root password? that's a bit overboard don't you think?  

I'm pretty sure the average user can get away with 6-10 characters alphanumeral, but 12 is just crazy man.

---

### Post by kevdog on 2008-03-17
Dont run ssh on port 22.  That is crazy.  Run it on a different port like 2222 or higher.  This way most script kiddies will not try to connect since most are configured to go after common ports.

---

### Post by corkscrew on 2008-03-17
ok so how do i close port 22?

---

### Post by ramjet_1953 on 2008-03-17
If you do the following, I think port 22 will be closed:

Navigate to [COLOR="Blue"]System>Preferences>Control Centre[/COLOR]

Scroll down to I[COLOR="Blue"]nternet & Network[/COLOR]

Click on [COLOR="Blue"]Remote Desktop[/COLOR]

When the window opens, look at the [COLOR="Blue"]Sharing[/COLOR] Option.

Make sure that the box that says "Allow other users to share your desktop" is [COLOR="Red"]un-checked[/COLOR]

Regards,
Roger :cool:

---

### Post by Oldsoldier2003 on 2008-03-17
> **Patrick-Ruff said:**
> 12 characters or more for a root password? that's a bit overboard don't you think?  

I'm pretty sure the average user can get away with 6-10 characters alphanumeral, but 12 is just crazy man.

my root password is 17 characters strong passphrase...

---

### Post by ramjet_1953 on 2008-03-17
Don't forget that when you do a port scan with Shields-Up behind a router, that you get a report for the router, not your PC.

Regards,
Roger :cool:

---

### Post by Oldsoldier2003 on 2008-03-17
> **ramjet_1953 said:**
> Don't forget that when you do a port scan with Shields-Up behind a router, that you get a report for the router, not your PC.

Regards,
Roger :cool:

+1, I spent about two days trying to explain that to someone once :) the only correct info from shields up is on the ports you have forwarded to a specific machine. and yes any dsl gateway that supports sharing the internet connection  is considered a router for this answer :)

---

### Post by daengbo on 2008-03-17
To close the ports,
apt-get remove openssh-server dovecot-imapd

Of course, then you won't have IMAP or SSH on your machine.
Is this a server? Do you use Evolution or Thunderbird with IMAP? If so, you may not want to   use the command above.

---

### Post by bodhi.zazen on 2008-03-17
> **corkscrew said:**
> I'm a newbie trying to secure my new linux box. I've read all the stuff about ubuntu not opening any ports, but if i go to shields up it says ports 22 and 23 are open. how can i close these with firestarter? i've looked through the manual but can't find anything

Those ports are open because you installed some servers.

Here is a link on security to get you started :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[uwiki]AdvancedOpenSSH[/uwiki]

> **bsharp said:**
> Those 2 ports are open because of the SSH server (which is included by default) that is running, which allows you to remotely control your computer via terminal(port 22). IMAP is used for mail(port 23).

I believe to close them you need to stop the services running on those ports, but there isn't much of a security risk of leaving them open.

Just for clarification : Neither of those ports are open with a default install of Ubuntu. The ssh server is NOT installed by default.

---

### Post by p_quarles on 2008-03-17
Are you behind a router? If so, closing those ports with iptables won't have any effect. Closing them on your router would.

---

### Post by handydan918 on 2008-03-17
> **Patrick-Ruff said:**
> 12 characters or more for a root password? that's a bit overboard don't you think?  

I'm pretty sure the average user can get away with 6-10 characters alphanumeral, but 12 is just crazy man.

You're Using Ubuntu. You don't ***_have_*** a root password. You have sudo instead. 
That password is the only thing that stands between you and a bruteforce attack if you have port 22 open.
So go ahead, use your puppies birthday, or whatever. 
Not me. I used Microsoft long enough to become allergic to pwnage.

---

### Post by bodhi.zazen on 2008-03-17
Threads merged.

@ corkscrew : Please do not start start multiple threads on the same subject.

---

