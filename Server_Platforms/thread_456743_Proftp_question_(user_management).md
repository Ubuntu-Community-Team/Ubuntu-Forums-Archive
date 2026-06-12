---
title: "Proftp question (user management)"
date: 2007-05-28
forum: Server Platforms
---

### Post by mortalic on 2007-05-28
Ok, I'm not a linux noob, but I am an ubuntu noob.  I've been using madrake/driva for ages but figured I'd jump on the bandwagon and try ubuntu.  My old mandriva machine did the following:
router/firewall (shorewall)
samba (file and a usb printer)
proftp
vncserver (tight vnc)
ssh server (openssh)

So far in ubuntu I've got file sharing working (haven't even looked into the printer yet, but I will).
vncserver
ssh
router/firewall (firestarter, wow, I've never used a gui firewall before! it's amazing!)

I've set proftp up probably close to a hundred times on mine and other peoples servers in mandriva.  It just works, one or two quick commands or a few mouse clicks and you've got them either jailed to their home dir's or in my case I am the only person that uses mine I have a central repository.  

My question, proftp keeps prompting for a username/password.
I'm assuming mandriva had some kind of auth method already configured that ubuntu doesn't do.  Can someone fill me in?

---

### Post by hawzor on 2007-05-29
Is this version of proftpd substantially newer than the others you have used? There may be new modules and confs that you may not have used before. My 6.06 system stood up in about 20 seconds using apt-get. I highly recommend it. It took about 2 minutes more to configure  /etc/proftpd/modules.conf and /etc/proftpd/proftpd.confthe way I wanted.

Out of curiosity are you running LDAP? (Not that this would affect things, just curious). And are you running with mod_tls engine on?

---

### Post by mortalic on 2007-05-30
Thanks for the reply.

I'm not running ldap, in fact I thought I had the simplest of installs.  I've been trying really hard to do everything from the gui (new for me) as I have a friend trying to get into linux but he's not a computer guy, and I want to be able to show him the gui way to do things.

So I installed proftpd from the synaptics installer.  That's all.  As for newer version, I have to admit I don't remember what versions I was running, as I never checked.

---

### Post by mortalic on 2007-06-06
Just a bump, I removed and reinstalled proftp from apt today.  It does the exact same thing, anyone have any idea?

---

