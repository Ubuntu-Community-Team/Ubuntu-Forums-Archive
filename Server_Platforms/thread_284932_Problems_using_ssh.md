---
title: "Problems using ssh"
date: 2006-10-26
forum: Server Platforms
---

### Post by bush doctor on 2006-10-26
Hey

Installing a linux server for the first time but am having problems ssh'ing into the server (openssh client & server installed). I can see the server from my windows pc and using Putty can input the username. When it asks for my password however, I just get 'access denied'. Are there any settings on ssh_config or sshd_config that I have to input (i.e. not as default) or anything else which could be blocking me?

Any help appreciated.
:confused:

---

### Post by Iowan on 2006-10-26
What name are you using to log in?  IIRC, the default config blocks root user login.

---

### Post by bush doctor on 2006-10-26
I'm using the account I setup when first installed. However I just  added a new user and tried that without success.
:-k

---

### Post by Iowan on 2006-10-26
I won't be near my server for another 6 hours (and it's not online), so I can't check my setup, and I can't remember some of the details... 
Check the config (that'd be the server) for limits set by subnet, host, or user.  I've put a fresh install of Dapper back on my workstation, and the client worked without a hitch - but I remember having problems setting up the server.
I gotta admit - I haven't used PuTTY enough to be familiar with it (as mentioned, the SSH client on the Ubuntu workstation works fine).  Where did you enter the username  - under category: Connection>Data? What did you set for SSH Authentication?

---

### Post by bush doctor on 2006-10-26
I just enter the username when prompted as it attempts to connect to the server. I haven't setup any authentication on the server side so leave this blank in putty.

I'll keep trying - thanks for your help all the same.

---

### Post by fatbastard spice on 2006-10-27
Sounds like it might be trying a key based authentication. Have a look at your Auth options under Connection > SSH in the PuTTY configuration section to see if it's trying a keyboard interactive login. You can also configure the SSH server to deny keyboard authentication, but unless something's changed from my last install, that'd be a pretty deliberate action that i'm sure you'd have remembered.

---

### Post by Iowan on 2006-10-27
Last night I downloaded a copy of Putty onto one of my network's XP stations, entered the username into Connection>Data>Login details (auto-login username), and the server name in Session>Hostname... and it connected (after asking for password. 
I think PuTTY defaults to **Attempt "keyboard-interactive" auth (SSH-2)**.  If you disabled it, turn that option back on and see if you can connect.
Passwordless SSH (using keys)is convenient - there are How-To's around here - if I find one, I'll post it for you.

---

### Post by bush doctor on 2006-10-27
Got it working - took a while for the penny to drop! 

Didn't realise that Caps Lock is working as Shift, so my password (with numbers) was being rejected when using Caps from the windows machine.

<hangs head in shame>

Cheers for the help

---

