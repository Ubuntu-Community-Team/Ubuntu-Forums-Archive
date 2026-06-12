---
title: "Help with Remote Access 'hack-proof' (bad exp. with Teamviewer)"
date: 2015-06-01
forum: Security
---

### Post by Sileobax on 2015-06-01
Hi,
I'm new registered user but 'old viewer' of the forum and 'old' user of ubuntu.

I usually access my PC01 via teamviewer (I use windows and ubuntu), and recently I noticed I had another connection running to my pc so I asked to someone that was in the local to take away the ethernet cable of it. The name of the connection/user in connection was: "0".

I checked the logs and I see a ton of logs from the ID of my PC02 (that I use to access), to my PC01. But in the middle I have 3 ID's that was never mine (from my PC02), those accessed 2 times for just 3 mins, and another time, some days later for almost 1h!! and at hour I wasn't there for real.

I had reinstalled the SO 2 days ago and still nothing installed almost, and no one had ID neither access that PC, only me!!

I would like to see what you guys think (since normally ppl around here have good advice and solved me a lot of problems already/made me more wise :D), and what I should do to keep my connection safe, VNC, ThighVNC ?


Thanks for the patience

EDIT: btw, already changed all password and I gonna reinstall the SO from scratch. I was checking this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-remote-access-for-the-gnome-desktop-on-centos-7) what do you guys think ? is enough ?

---

### Post by Sileobax on 2015-06-01
sorry for the double post,
60 views and not a single person can tell me something ? have I said something wrong ?

---

### Post by howefield on 2015-06-01
> **Sileobax said:**
> sorry for the double post,
60 views and not a single person can tell me something ? have I said something wrong ?

A common misconception, only 4 people have viewed your thread in the very short time that it has been posted. Just be patient, if someone can help you they'll be along soon enough.

---

### Post by Sileobax on 2015-06-01
ok thank you for the answer and sorry for that, but I swear here shows 60 views :X but like you say, probably misconception

---

### Post by coffeecat on 2015-06-01
The 60 views represent views from "guests" - that is people not logged in or even search engine spiders. You won't get any replies from any of them. But don't worry, members are beginning to have a look. Since howefield posted, three more logged in members have viewed the thread.

---

### Post by HermanAB on 2015-06-02
Well, Teamviewer and VNC are dangerous things that should be used with care, only activated when you really need it, and you should use a very long password, in excess of 12 characters (with complexity) or excess of 16 characters (without complexity).

If you use a short password, then you *will* get hacked, since there are automated scripts out there, that will try every short password very rapidly.

---

### Post by steeldriver on 2015-06-02
I don't think long VNC passwords really add security - IIRC only the first 8 characters are used, and the string is merely base64 encoded rather than hashed

AFAIK the only way to make VNC remotely (pun intended?) secure is to tunnel it over SSH. Then it essentially becomes as secure as your SSH connection, and the same measures can be applied as for plain SSH i.e.
[LIST]
[*]disable password-based SSH authentication in favor of key-based
[*]run some kind of anti-bruteforce measure such as fail2ban
[*]disable root SSH login (should be disabled by default)
[/LIST]

Some 3rd party solutions implement SSH tunelling behind the scenes for you (I believe x2go is one such) or at least make it easier to configure via their client interface.

---

### Post by Sileobax on 2015-06-03
thank you for your share of advice,
yesterday I started striving to put a ssh with only keys (generated in ubuntu too), and afaik the SSH is not vulnerable still right ? if I do all inside of it, I'm 'almost secure' (since there is no security 100% granted after all :X)

but after I came up with an idea that I dunno if better... use NeoRouter or Hamachi (?) so I could have 2 pc's (windows and ubuntu) in the same network and could easily use the VNC/remote desktop.. or should I really stick with the ssh (by installing Cygwin+OpenSSH on Windows) 

once again, thanks for the share of advice :)

EDIT: after search a couple of things around internet I found that is even more dangerous have hamachi rather than do port-forwarding, and that NeoRouter have some encryptation mechanisms (using AES in some parts of it, but key of 256)

---

### Post by steeldriver on 2015-06-03
You don't need cygwin on the Windows side - I would suggest just using PuTTY with whatever regular VNC client you like. Some Windows clients may have built-in SSH support - it's a while since I looked.

BTW it sounds like you are using this just to connect between 2 PCs on your home LAN? if that's the case, it should be sufficient to secure your *network* i.e. make sure there are no open / forwarded ports on your router - and optionally set up the machine firewalls to only accept connections from addresses inside the LAN

---

### Post by HermanAB on 2015-06-03
One problem with VNC is that it uses UPnP to automatically open up and port forward your home router, thus making your LAN machine vulnerable to the Wide Wild World.

BTW, UltraVNC supports longer passwords, but I would not really recommend any flavour of VNC.  SSH is best.

---

### Post by CharlesA on 2015-06-03
> **HermanAB said:**
> One problem with VNC is that it uses UPnP to automatically open up and port forward your home router, thus making your LAN machine vulnerable to the Wide Wild World.

Depending on how it's configured, but yeah, that can easily happen.

I used to use NoMachine, but haven't touched it in a while. If you need a remote connection, it is usually a good idea to launch it yourself after SSHing in or only launch it when needed. If you have it running all the time, it could be accessed without you knowing.

As far as TeamViewer goes, that seems to be realitively secure. Are you sure you haven't connected from another machine? The Machine ID is based off the hardware in the machine IIRC, so that might account for the unusual IDs, though it is unlikely.

---

### Post by Sileobax on 2015-06-04
thanks for the answers,
no, I just logged in from that ID, plus the name of the user was '0' instead of the name I normally use. For what I think, could be for have the 4PIN password activated (even if using my own password there).

I wanna connect a Windows and a Ubuntu machine, between them and both directions. My idea is have a SSH server in both of them, connect via ssh and after, use VNC, like this I think would be secure right ? (considering using ThightVNC)

As a SSH Server for Windows, I was used to OpenSSH but I readed a recent post that concerns me a little ([http://ubuntuforums.org/showthread.php?t=2280779](http://ubuntuforums.org/showthread.php?t=2280779)), anyone have experience/recomendation of some SSH Server for Win ? (I'm looking at: MobaSSH, FreeSSHd, Bitvise) (dunno if should put this question in other subforum of this forum)

---

### Post by CharlesA on 2015-06-06
It would be better to just use a VPN in that case instead of SSH. Less overhead/work.

---

