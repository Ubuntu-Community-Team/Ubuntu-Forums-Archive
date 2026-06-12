---
title: "SSH -&gt; start a gui program on host machine?"
date: 2010-12-10
forum: Server Platforms
---

### Post by pepsifx357 on 2010-12-10
I still haven't got the whole 0:0 display whatever down yet, so I need some help.

When I'm ssh-ing into a machine with my android phone, I would like to start a gui program on that host, from my phone.  Of course running something like Firefox just turns up with a display error, because I'm not trying to forward X.  How would I do this?

---

### Post by arrrghhh on 2010-12-10
You won't be able to with an Android device (to my knowledge, I don't have one).

To forward an X app thru an SSH tunnel, your SSH client needs to support X windows - so either a linux box or windows with xming or cygwin.  I'm sure mac has support for forwarding X apps as well, but again I don't have a mac so I am not sure how that would work ;)

---

### Post by iponeverything on 2010-12-10
on the remote machine, log in via ssh as the user who is currently using the desktop.

```

export DISPLAY=:0.0
xeyes

```

---

### Post by HermanAB on 2010-12-11
$ ssh -C -c blowfish user@serveripaddress "gedit /etc/fstab"

---

### Post by pepsifx357 on 2010-12-11
lol, ok I got three completely different answers.  I'm not forwarding X to my phone.  The second answer looks more like something I'm looking for, however it didn't seem to work for me.  That last one has me confused why would I want to edit fstab? Although I do like the encryption option.  Basically what I'm doing is being lazy and remote controlling my PC using my android from the couch.  Really I'm just playing around with possibilities.  I wanted to start a GUI program on the PC from the phone.

Ok this is wierd, I was going to post the error I get when starting a GUI program, however, it just worked.  I Always get a display error.  I guess problem solved.

I just typed chromium-browser and it popped up on the PC.

---

