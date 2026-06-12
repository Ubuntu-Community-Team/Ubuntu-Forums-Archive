---
title: "Sticky note widget with the text &quot;ssh&quot; appeared on my desktop...  How?"
date: 2010-09-16
forum: Security
---

### Post by soulspit on 2010-09-16
Hi everyone,

Yesterday I installed an SSH server (openssh-server) on my laptop, for various reasons.  Today, I was using my laptop, minding my own business, and then a sticky note widget on the KDE desktop appeared containing just the text 'ssh'.  I have never used the note widget before, didn't know it existed, and 'ssh' was not in my clipboard or anything, and I am struggling to understand how this could have happened accidentally.  This happened before I had a chance to/before I learned how to make SSH more secure (by disabling remote root login, enabling a maximum number of authentication tries, etc) which I immediately did, and restarted the SSH server.

This sequence of events leads me to believe that, a) something supernatural just occurred, or b) somehow someone or some bot SSHed into my system and managed to open up a sticky note, either to remind me to secure SSH or perhaps to make me aware of the fact that my system's security has now been compromised.  Like I said, I really can't see how this could have happened by accident (though boy will I feel silly if there is an easy explanation I've missed).

None of these explanations seem likely.  Has anyone ever seen anything like this happen?  After securing SSH and making my passwords stronger and all, should I carry on as normal or (ugh) assume something nasty happened and re-install my system?

Thanks for your help, I'm a little bewildered.


edit: I had a look at /var/log/auth.log, and I can't see anything suspicious, though I don't know what exactly to look for, and my log level in my SSH config was set to INFO (I've now set it to VERBOSE).  In fact, there is not a single entry in the log during the time in which the note appeared, so unless something was planted earlier and popped up the sticky later, however it happened it didn't end up in that log.  Is this a fruitless and silly line of inquiry?

---

### Post by CharlesA on 2010-09-16
Do you have VNC enabled or SSH open to the internet?

---

### Post by soulspit on 2010-09-16
VNC is not enabled (or, at least, I never did anything to enable it and never installed anything relevant to it) but SSH is open to the Internet by default, right?  I had installed openssh-server but hadn't yet changed any of the default options.  (I have, now, though).

Actually, come to think of it, that reminds me of something that makes it impossible this came from the Internet: I'm on a wireless router!  Unless there's something I don't know about, I believe that if someone tried to SSH into this computer from the Internet, my router wouldn't know which LAN IP address to forward the port to.  Though my router's firewall is disabled (I was having problems with it) I have no port-forwarding rules that forward any ports to the affected laptop, so it is invisible to the outside world, correct?  A couple obscure ports are forwarded to some other computers on my LAN, but it seems beyond the realm of possibility that something hacked into another computer on my LAN and then messed with this otherwise-invisible laptop.  And my wireless network is secure.

So... it must have been something else.  Supernatural or accident.  I'm still bewildered, but not worried any more.

---

### Post by cariboo on 2010-09-16
You can check your router for open/forwarded ports using [canyouseeme]("http://canyouseeme.org/").

---

### Post by soulspit on 2010-09-16
Thanks, that's a really useful site.  Strangely, though, I can't find any ports except port 80 which are open.  But something must be wrong, because the port by which I can remotely SSH into *another *computer on my LAN (not the computer which had the stick note appear) is shown as not accessible (connection timed out).  I know this port is open because I have used it from outside my LAN (ie my neighbor's unsecured wireless).

Other ports for which I have port forwarding rules set up on the router come up as connection time out as well.  Maybe my ISP blocks non-port-80 traffic from just this particular website?  Certainly, the default port of 22 which my sticky-noted laptop would have been SSHed into before I changed the settings, that is shown as blocked (connection refused).  More evidence that this strange occurrence did not come through SSH.

---

### Post by CharlesA on 2010-09-16
By "open to the internet" I meant, was it accessible from outside your local network.

For it to be accessible, you'd have to forward port 22 on the router. :)

So that's a no, I'm guessing maybe you hit a shortcut key or something?

---

### Post by soulspit on 2010-09-16
Yeah, that makes sense.  So no, SSH was not open to the internet, nor was anything else (though other computers on my LAN are, hopefully securely so).

What's strange is that I can't find any shortcut keys for the notes widget.  And how would the text 'ssh' end up in the note when that next was not in my clipboard or clipboard history?  It all seems so unlikely.  I suppose it will remain a mystery... but at least I wasn't hacked.  Thanks for your help guys.  

If something similarly inexplicable happens again I might start believing in ghosts.

---

### Post by CharlesA on 2010-09-16
I was guessing that it was somehow opened when you were trying to ssh in or something.

*shrugs*

If it happens again, I'd do a reinstall, but that's just the paranoid in my talking. :P

---

### Post by soulspit on 2010-09-16
> **CharlesA said:**
> If it happens again, I'd do a reinstall, but that's just the paranoid in my talking. :P

I'm not sure which I'm more afraid of, ghosts, hackers, or invisible shortcuts that open up programs I've never used :shock:

---

### Post by CharlesA on 2010-09-16
> **soulspit said:**
> I'm not sure which I'm more afraid of, ghosts, hackers, or invisible shortcuts that open up programs I've never used :shock:
Definitely invisible shortcuts!

---

### Post by The Cog on 2010-09-17
Try the command:
**grep ssh /var/log/auth.log**
and see if there are any logins you can't explain.

P.S.
The other common unwanted access method is VNC, which you can enable from the menu System->Preferences->Remote Desktop. I heard recently that if you check allow other users to access your desktop, it will use UPnP to set up port forwarding through the router to itself so that anyone on the internet can access it. The fact that it does that without warning and that you can't disable the behaviour is a little disturbing to my mind.

---

### Post by cariboo on 2010-09-17
> **The Cog said:**
> Try the command:
**grep ssh /var/log/auth.log**
and see if there are any logins you can't explain.

P.S.
The other common unwanted access method is VNC, which you can enable from the menu System->Preferences->Remote Desktop. I heard recently that if you check allow other users to access your desktop, it will use UPnP to set up port forwarding through the router to itself so that anyone on the internet can access it. The fact that it does that without warning and that you can't disable the behaviour is a little disturbing to my mind.

If you have UPnP disabled in the router, you are safe.

---

### Post by CharlesA on 2010-09-18
> **The Cog said:**
> 
P.S.
The other common unwanted access method is VNC, which you can enable from the menu System->Preferences->Remote Desktop. I heard recently that if you check allow other users to access your desktop, it will use UPnP to set up port forwarding through the router to itself so that anyone on the internet can access it. The fact that it does that without warning and that you can't disable the behaviour is a little disturbing to my mind.

It's fine as long as you don't click on "configure the network automagically" and have UPNP enabled on the router.

If you disable UPNP, you are fine. You are also fine if you don't tell it to configure the network automagically. ;)

---

### Post by The Cog on 2010-09-18
> **CharlesA said:**
> It's fine as long as you don't click on "configure the network automagically" and have UPNP enabled on the router.
Aha! That option had escaped my attention. Maybe because I didn't understand what it meant - I think it could be worded better.

---

### Post by CharlesA on 2010-09-18
> **The Cog said:**
> Aha! That option had escaped my attention. Maybe because I didn't understand what it meant - I think it could be worded better.
Probably could be worded better, but if you mouse-over it, it mentiones UPNP.

---

### Post by cariboo on 2010-09-18
If you don't have UPnP enabled, it isn't even mentioned in the dialog in Maverick .

---

### Post by FuturePilot on 2010-09-18
> **cariboo907 said:**
> If you don't have UPnP enabled, it isn't even mentioned in the dialog in Maverick .

It is. Hover your mouse over the option to read the tooltip.

---

### Post by soulspit on 2010-09-18
> **The Cog said:**
> Try the command:
**grep ssh /var/log/auth.log**
and see if there are any logins you can't explain.
All there is (apart from notices of ssh listening on port X) is this:

```
Sep 15 18:25:21 tensile sudo:     toby : TTY=pts/1 ; PWD=/home/toby ; USER=root ; COMMAND=/usr/bin/apt-get install ssh
Sep 15 18:25:30 tensile useradd[14568]: new user: name=sshd, UID=110, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Sep 15 18:25:31 tensile usermod[14573]: change user 'sshd' password
Sep 15 18:25:31 tensile chage[14578]: changed password expiry for sshd
Sep 15 18:25:31 tensile sshd[14621]: Server listening on 0.0.0.0 port 22.
Sep 15 18:25:31 tensile sshd[14621]: Server listening on :: port 22.
Sep 15 18:55:23 tensile sshd[14965]: Invalid user fran from 192.168.2.3
Sep 15 18:55:23 tensile sshd[14965]: Failed none for invalid user fran from 192.168.2.3 port 33232 ssh2
Sep 15 18:55:27 tensile sshd[14965]: pam_unix(sshd:auth): check pass; user unknown
Sep 15 18:55:27 tensile sshd[14965]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=tensile.local 
Sep 15 18:55:27 tensile sshd[14965]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 15 18:55:27 tensile sshd[14965]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 15 18:55:29 tensile sshd[14965]: Failed password for invalid user fran from 192.168.2.3 port 33232 ssh2
Sep 16 12:22:57 tensile sudo:     toby : TTY=pts/1 ; PWD=/etc/ssh ; USER=root ; COMMAND=/usr/bin/passwd root
Sep 16 12:24:01 tensile sshd[988]: Server listening on 0.0.0.0 port 3922.
Sep 16 12:24:01 tensile sshd[988]: Server listening on :: port 3922.
Sep 16 12:25:15 tensile sshd[988]: Received signal 15; terminating.

```
I think this is all just me installing ssh and testing it out - accidentally tried to log in as the wrong user once, that's the "invalid user fran" part.  I don't understand the fourth to last line - I changed the root password (and ssh port) after this happened, and I think it's that.

> 
P.S.
The other common unwanted access method is VNC, which you can enable from the menu System->Preferences->Remote Desktop. I heard recently that if you check allow other users to access your desktop, it will use UPnP to set up port forwarding through the router to itself so that anyone on the internet can access it. The fact that it does that without warning and that you can't disable the behaviour is a little disturbing to my mind.

I haven't set up VNC at all and UPnP is disabled on my router so I'm safe from this!  That fact is a little worrying though.  Again the conclusion seems to be that what happened wasn't caused by an external event... forever a mystery - but now I know to check this very useful log.

---

### Post by CharlesA on 2010-09-18
Yup, it's a good idea to check auth.log off and on. It looks normal.

---

### Post by soulspit on 2011-09-07
This is a relatively old thread of mine but I have solved it, so I thought I would mention it here in case anyone runs across something similar.

The same thing happened to me a few times and it became clear what was happening. "ssh" wasn't magically appearing in a sticky note widget on my plasma desktop, *the contents of my clipboard *was magically appearing in a sticky note widget on my plasma desktop. Ominously, it happened to be "ssh" the first time, but that was a red herring.

KDE/Plasma automatically sets middle mouse button click on my desktop to paste. I don't have a middle mouse button, but sometimes accidentally hit it because a two-finger press on my touchpad is a middle mouse button. Though I can't get this to work right now, clearly sometimes pasting text on the desktop creates a sticky note with that text. Mystery solved. I very much appreciate everyone's help, however.

EDIT: looking at my first post, I realize I said that "ssh" was not, in fact, in my clipboard. This confuses me, since I thought I'd nailed the thing on its head - what's the chance that there's *two *things causing sticky notes to appear at random on my desktop? It's possible I had some more complicated thing in my clipboard that turned into "sticky note containing text ssh" in the process by which plasma figures out what widget to make from your clipboard contents. Else I was wrong, and "ssh" was in my clipboard. Who knows. I'm satisfied.

---

