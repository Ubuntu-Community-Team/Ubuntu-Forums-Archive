---
title: "Ubuntu Server's Remote Desktop to work like in Windows Server 2008"
date: 2013-07-18
forum: Server Platforms
---

### Post by lucaslittermentz on 2013-07-18
Hello all.

I'm trying for the past two weeks to make a Ubuntu Server 12.04 LTS work like Windows Server works (in terms of Remote Destop).
So, what I need to do is the following:

 1. Users can connect from any computer, be it Windows, Linux (Ubuntu) or Mac.
 2. Users have only one session, and they always log on to that one session.
 3. Some folders on the computer should be available only to certain users.

I've managed to complete the first objective, but only on one user (three others were created using Ajenti's users module, and they all did not work) and every remote login was a new session.

Please consider me as a total newbie on this subject.

---

### Post by CharlesA on 2013-07-18
I haven't used a *nix box like that, but have you looked into the LTSP?
[http://www.ltsp.org/](http://www.ltsp.org/)

I'm not sure if that fits your needs, but it might be worth checking out.

---

### Post by lucaslittermentz on 2013-07-18
I did look into that, but I still have lots of questions about it and nobody seems to have an answer...

So, does anyone know if it fits my needs?

I need it to work exactly like Windows Server 2008's Remote Desktop, which allows me to connect to multiple accounts at a time (different computers) and enter the same session I was connected before.

I have tried setting up xrdp and x11rdp but it just didn't work the way I wanted. It connects like heaven, so smooth and all but to a different session.

---

### Post by CharlesA on 2013-07-18
Stupid question, but why not just use Server 2008, instead of trying to make a different OS act like Server 2008?

Other than not actually having Server 2008, of course.

---

### Post by lucaslittermentz on 2013-07-18
I actually did try Server 2008, but the free trial is going to expire in 7 days.
Also, it is going to be too expensive for the company I work for to handle the costs (18 users, 18 licenses, a lot of money), so we've decided to go the hard, free way (Linux based server).
Ubuntu was the chosen distro because it's very user friendly and we have some workers that don't have experience with computers, so user friendly is good.

Anyway, solutions that may help are always welcome.

---

### Post by CharlesA on 2013-07-18
> **lucaslittermentz said:**
> I actually did try Server 2008, but the free trial is going to expire in 7 days.
Also, it is going to be too expensive for the company I work for to handle the costs (18 users, 18 licenses, a lot of money), so we've decided to go the hard, free way (Linux based server).
Ubuntu was the chosen distro because it's very user friendly and we have some workers that don't have experience with computers, so user friendly is good.

Anyway, solutions that may help are always welcome.

Makes sense. I've been in that boat before, but the company I work for has access to MSDN stuff.

Hopefully someone will be able to help you - are you able to set up a test machine to try it out and see what happens?

---

### Post by lucaslittermentz on 2013-07-18
I can only use a VM right now, it's running Ubuntu Server 12.04 LTS 32bits.

---

### Post by CharlesA on 2013-07-18
> **lucaslittermentz said:**
> I can only use a VM right now, it's running Ubuntu Server 12.04 LTS 32bits.

That should be fine. You just need something you can mess with without worrying about it blowing up in your face.

---

### Post by lucaslittermentz on 2013-07-18
Alright.

Should I try LTSP right away or are there other options?

---

### Post by steeldriver on 2013-07-18
We 'kind of' do that with tightvncserver on an Ubuntu box at my work - the "users have only one session" isn't enforced but in practice we each choose a display number (port number) and stick to it (otherwise tightvncserver just allocates the next available display) - once a session is started by user A on display :n then A can connect to that session from anywhere on VNC port 5900 + n

That's the 101 - we actually make it a bit more complicated by enforcing SSH tunneling - some clients e.g. Remmina can handle that under the hood, I use TightVNC viewer on Windows and that currently requires a separate PuTTY session to create the tunnel. I have no experience of VNC clients on MAC.

[LIST=1]
[*]Windows and Linux have several good VNC clients each - MAC I'm not so sure but probably 
[*]You could permanently allocate a display # to each user and have a wrapper script that started the VNC server on that user's allocated display - it wouldn't prevent a savvy user from starting a session on a different display though (if that's important - there are probably ways to do it) 
[*]comes for free with *nix, really just a matter of setting up appropriate groups and group memberships 
[/LIST]

---

### Post by stupidscript on 2013-07-18
Grab an Edubuntu disc and run it as a LiveDVD on the machine you want to use as your server.

Once it's loaded up, you can use Applications => Other => LTSP Live to run a test of LTSP. ([http://edubuntu.org/documentation/ltsp-live](http://edubuntu.org/documentation/ltsp-live))

See how you like it.

Unsupported NIC issues were our original problem children, but once we started using machines with supported cards, everything worked great.

We really like LTSP. In our office, each user logs in and gets their own session. There are powerful file/directory/desktop sharing tools and excellent admin tools.

Use "SeamlessRDP" from Cendio to run Windows apps (hosted on a Windows terminal server box with proper licensing, of course.)

---

