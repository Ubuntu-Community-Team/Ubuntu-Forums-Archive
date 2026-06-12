---
title: "My UBUNTU 10.10 PC got a virus?"
date: 2011-04-22
forum: Security
---

### Post by riderepe on 2011-04-22
I have been a LINUX User for quite a few years and I have never had this problem. I was coding using Qt Creator and the editor began to type "You have been taken over." I have seen this on Windows but never LINUX. I have to assume that I brought it in via an e-mail. I have an external firewall on my router. I used ClamAV to check my system but this like closing the barn door after the horses are out. A few days latter I was coding and Qt Creator started to try to echo PASSWORD and USER. I ended up reinstalling Ubuntu Studio reformatting everything. I have backups of my critical stuff. Is Clam AV the way to go with scanners or is there something else?
Thanks

---

### Post by tgm4883 on 2011-04-22
> **riderepe said:**
> I have been a LINUX User for quite a few years and I have never had this problem. I was coding using Qt Creator and the editor began to type "You have been taken over." I have seen this on Windows but never LINUX. I have to assume that I brought it in via an e-mail. I have an external firewall on my router. I used ClamAV to check my system but this like closing the barn door after the horses are out. A few days latter I was coding and Qt Creator started to try to echo PASSWORD and USER. I ended up reinstalling Ubuntu Studio reformatting everything. I have backups of my critical stuff. Is Clam AV the way to go with scanners or is there something else?
Thanks

sounds more like an attacker was logged into your system than a virus. If a virus was on the machine it surely wouldn't be doing that stuff where you could see it.

Did you have VNC or some other remote connection software installed?

---

### Post by iissmart on 2011-04-22
> **riderepe said:**
> A few days latter I was coding and Qt Creator started to try to echo PASSWORD and USER.

They can't get your password through 'echo', so don't worry about that part.

---

### Post by riderepe on 2011-04-22
Thank you for replying.
I would never leave LINUX  or even threaten to.I like it too  much

I don't believe that any one was logged into my system. it is a very small small home network. I'm wired into though router is wireless, but is WPA protected and I haven't shared the password. 

I did get an e-mail form someone unknown to me asking to be a friend on facebook and I did open the note. In the windows world this would be the obvious culprit.

I was just hopping there's a e-mail scanner to put me at ease.

---

### Post by collisionystm on 2011-04-22
Clamav is fine.

Put a Firewall in place on your machine. Use Firestarter or gufw
Block all inbound connections.

By Default your IPtables are allowing all traffic. Use these programs to fix that.

You could also use AVAST

Or my Favorite

```

http://www.eset.com/us/home/nod32-antivirus-for-linux

```

---

### Post by tgm4883 on 2011-04-22
> **riderepe said:**
> Thank you for replying.
I would never leave LINUX  or even threaten to.I like it too  much

It's a signature

---

### Post by DodgeV83 on 2011-04-22
> **riderepe said:**
> I have been a LINUX User for quite a few years and I have never had this problem. I was coding using Qt Creator and the editor began to type "You have been taken over." I have seen this on Windows but never LINUX. I have to assume that I brought it in via an e-mail. I have an external firewall on my router. I used ClamAV to check my system but this like closing the barn door after the horses are out. A few days latter I was coding and Qt Creator started to try to echo PASSWORD and USER. I ended up reinstalling Ubuntu Studio reformatting everything. I have backups of my critical stuff. Is Clam AV the way to go with scanners or is there something else?
Thanks

That doesn't sound like the behavior of a virus/malware. It *does* sound like the behavior of someone remotely connecting to your machine. 

Click System -> Preferences -> Remote Desktop

Is "Allow others" checked here? If so, does it say anyone can access, or only people on your local network? I understand you already reformatted, but it's still worth a look.

---

### Post by dacoolio on 2011-04-23
I would make sure your current password is different than your initial install's password, and hopefully whoever is on your system won't be able to get back on.

It sounds like a remote desktop viewer, VNC type thing. The first step would be to (obviously) disconnect from the network until you have everything secured.

I would use some type of firewall. My favorite is Gufw, which is a GUI for ufw. Setting the ruleset to "Deny" rather than reject would be a good idea, because rather than reject the connection outright, it just lets the request be silently dropped, making it appear that you're still offline. Hope this helped and good luck :)

---

### Post by HermanAB on 2011-04-23
Hmm, judging by numerous similar events logged on Ubuntu Forums, you probably played with VNC in the past and left the server running (it uses Plug and Play to open a home router), you are probably using a home router with Plug and Play enabled and you are probably using a super kewl four character password...

---

### Post by Spyderkid on 2011-04-25
first thing first...

>you don't get things like that on linux viruses. If you are so unlucky to get a virus it will just do things like clogging up RAM or causing computer to shutdown etc...

>Clam AV only detects windows viruses so you don't pass them on to a windows user via email. (the windows viruses can sit on top of image files etc)

>this sounds like a hack or a joke one by the software application you have.

>you can't get linux Malware or clever stuff like that, you can only get destructive viruses as said earlier.

>the only way you could of got a virus was by running a download from the internet as a root user (sudo)

>SOLUTION: install FireWall(ufw) from software centre) if its a hacker that'll stop him

---

### Post by MasterTech515 on 2011-04-26
> **Spyderkid said:**
> first thing first...
 
>SOLUTION: install FireWall(ufw) from software centre) if its a hacker that'll stop him
 
[SIZE=2]I doubt it would stop a hacker. You really have only two choices left:
- Figure out if somebody is remotely accessing your system
- Re-install everything and hope that they don't hack you again
[/SIZE]

---

### Post by rookcifer on 2011-04-26
> **MasterTech515 said:**
> [SIZE=2]I doubt it would stop a hacker. You really have only two choices left:
- Figure out if somebody is remotely accessing your system
- Re-install everything and hope that they don't hack you again
[/SIZE]

Option 3 -- Figure out how they got in and take precautions so it doesn't happen again.  In this case, this involves not running an open VNC server.

---

### Post by Spyderkid on 2011-04-29
if you really want to make a strong firewall you can find an old computer, install IP-COP linux on it. (its a firewall linux OS) configure it, connect it to the router. then you can remove the keyboard and screen and speakers ( you don't need them on the IPCOP) then just switch it on.

That would probably stop a hacker pretty well i would of thought.

---

