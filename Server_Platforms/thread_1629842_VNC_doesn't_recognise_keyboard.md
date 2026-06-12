---
title: "VNC doesn't recognise keyboard??"
date: 2010-11-24
forum: Server Platforms
---

### Post by theDaveTheRave on 2010-11-24
Hi all,

I know that the title sounds wierd, and I have to say that the error I have is very strange.

Here is what I am doing. I've got a 'mostly headless' system I run as a testbed / server / file share (I describe it as mostly headless as I don't find it convenient to plug it into the screen). So I set it up with SSH and VNC.

I can SSH to the box, just fine.
I then start the vnc server with the following
> tightvncserver -nolisten tcp :1

I then open the xVNC4viewer from the menu, and enter in the required details to connect to a 'desktop'

This all works just fine, but I wanted to get the samba shares working for the wife (so she can get to the music on it) - I don't need this as I can just mount the remote directory onto my pc (much easier than samba - but the wife needs her laptop with windoze on it!).

So anyway I opened up gedit with via my VNC connection, and when I tried to enter in the required text I get goobledegook.

I am guessing that the keystrokes are being encrypted on the way over, and aren't being de-crypted when they arrive. Anyone know how I can solve this problem. or where I should start to look.

Also trying to find a solution for this I descovered the
> ssh -X user@remoteHost
so as I can open up gui stuff on the other computer locally, which I will need to try.

For now though I want to understand what I have done wrong with my VNC setup. I have set this sort of VNC over SSH up previously, and it worked like a charm. The only difference here is that I am going over a wireless connection, rather than a hard link into the network.

Any thoughts of things I can test out will be gratefully accepted.

David

ps. I'm logging in to an Gnome desktop on from an LXDE one.

David

---

### Post by endotherm on 2010-11-24
does teh issue occure in apps other than gedit? what kind of Keyboard do you have on the physical machine (us-105?), and what kind of keyboard is set on the remote host in system -> preferences -> keyboard? do the number of keys match? is there a physical keyboard on the server? if not, if you plug one in and reboot, does it resolve your issue?

VNC should not provide any encryption whatsoever, but it does provide some encoding translation. check your encoding types, and see if another is more appropriate.

as for vnc, i would just use freenx instead. much cleaner experience, and better performance and security to boot.

---

### Post by theDaveTheRave on 2010-11-24
Endotherm,

thanks for the quick reply... I hope the following gives you the information you required.

> **endotherm said:**
> does teh issue occure in apps other than gedit? 


It seems to occur everywhere? terminal (tried to apt-get a few extra things), gedit, firefox etc, it doesn't even recognise a carriage return!


> what kind of Keyboard do you have on the physical machine (us-105?),and what kind of keyboard is set on the remote host in system -> preferences -> keyboard? do the number of keys match? is there a physical keyboard on the server? if not, if you plug one in and reboot, does it resolve your issue?[/QUOTE]

Now there is a thought. I am VNC-ing from a laptop (without a number pad) whereas the 'external' keyboard that is plugged into it is a 'standard' 105 key 'english' thing.

> VNC should not provide any encryption whatsoever, but it does provide some encoding translation. check your encoding types,

Err Pardon :???: how do I do this?? 



> as for vnc, i would just use freenx

Fair enough, but I like the 'inconvenience' it means I only do it if I really have to. Also it keeps the 2 year olds from accidentally logging in when they play with the laptop - they have already figured out how to turn it on and off, and love playing with gimp, when they get it turned on!)

>  much cleaner experience, and better performance and security to boot.

I got the impression that as I was starting the VNC server from within the secure shell it was encrypted? or am I wrong? Kind of SSH tunneling, but requiring me to log in before I start the vnc server. Either way mostly I do this only from within the local network, not from the 'wild' side of my router.

Looking into it though, I think that X-forwarding may be a better solution for me, as mostly I only need to install stuff or edit config files, otherwise all I do is read files from the networked shares.

David

---

### Post by endotherm on 2010-11-24
well, vnc does not work directly with SSH, but you can tunnel any kind of traffic over ssh so if you already have a tunnel, then VNC traffic is no differant from any other apps. 

some vnc clients even have a feature to make ssh tunnelling easy:
```
vncview -via user@sshserver vncservername:0
``` will use ssh to tunnel to the ssh server, and then from there, connect to vncservers display 0. 
unless you are envoking vncviewer with the -via switch or you are point it to the local endpoint of a preestablished tunnel, then you are not using any encryption. 

as for encoding, I'm not entirely sure how to do it in ubuntu, but the TightVNC and RealVNC gui applets both have a control that allows you to select options like "Raw" "Hextile" etc. the few references I've seen to it imply that it is chosen dynamically.

---

### Post by theDaveTheRave on 2010-11-24
endotherm


jeepers, that was a quick reply, I just navigated off to do my weekly shop online (I go to collect later tomorrow), and you've already replied :eek:

So, Are you saying that my way of Starting vnc isn't secure? or is it the same as putting the whole command onto a single line such as....

```
ssh -f -L 5901:localhost:5901 user@remoteHost tightvncserver -nolisten tcp :1
```

or something similar?

Sorry I suddenly feel like I'm becoming confused by the whole thing!

Oh and I checked the settings in my viewer.

I'm using realVNC viewer, and encoding is set to 'auto, with option ZRLE being highlighted, and options of RAW or Hextile available.

Should I change the encoding to see if makes any difference?

Should I try another viewer? if so what would you recomend?

Or should I simply head over to freeNX (as it seems to be 'the same difference' as a VNC).

Thanks for your input.....


David

ps, this answer took a long time as I got caught up reading stuff about mysql / postgres (part of my line of work), this was after doing a search for the comparison of NX to VNC - this is why I hate / love the internet.
David

---

### Post by endotherm on 2010-11-25
well, first off, I really like freenx, so I'd say give it a try.

as for vnc, all I'm saying, is that if you have not specifically put ssh in the mix, it isn;t part of the equation. I've never seen a vnc server instance started this way, but there are lots of things Ive never seen. Ive done this a few times in a few configurations, but am by no means an expert. 

I generally set up ssh, and then install whatever service I want to access through it. thats all the relationship between the two required server-side. then on the client, I map the tunnel to the server, and from there access the service using localhost or 127.0.0.1 for addressing. 

as for encoding, yes, expirement. I've also found that all viewers are not created equal. x4vncviewer seems to be the fastest but has really annoying scroll bars if the server res is higher than the local res. vinagre is smooth, but slow to scroll. tight and real seem about the same, but I'll admit, its been a long time since I had to rely on vnc.

---

### Post by theDaveTheRave on 2010-11-25
endotherm,

Thanks again for the reply.

regarding my method of starting the VNC server.

___ as a side note _____
I remember setting this up for where I used to work, and I'm sure there was a config file somewhere - in it I forced the connections to only be possible from within the local network. Which meant that whoever was logging on was on the same side of the firewall, and had to be somewhere in the office!

At that time I set it up to work like this as all my less tech savy colleagues had an issue with the command line - so when they logged in (via putty) then had to enter some 'strange looking command' they immediately got confused, and came running for help, which meant I could keep tabs on what people were up to, and could guarantee that no-one was messing up the config of the server!

I will admit this seemed a bit 'heavy handed' but I had created very easy help intstructions, and all the info for them was readily available on our local wiki - and across the file shares - not that anyone every seemed to look at them!
___ok back to it... ____

regarding starting VNC like this, do you know where I can go to find out if this is secure or not - or have a link to a 'guru' thread on the forums?

I'm going to look myself, but I thought I would ask just in case you are aware of who the 'main man' is on the forums for this stuff.

thanks again.

David


Edit 1: I've installed FreeNX, everything went just fine. I've tested and it works and accepts the keyboard input. I also get the impression it is a bit quicker, and even the screen auto-resizes (I'm using the no-mahcine NX-client).
All is happy camping, now I can get to work on the samba shares, and remove the old VNC stuff.

Edit 2: I've managed to get X11Forwarding to work as well now. I didn't realise that there was a /etc/ssh/ssh_config on my laptop that needed a line to be edited.

I just changed the line
```
X11Forwarding no
```

to

[HTML]X11Forwarding yes[/HTML]

Now I can keep an eye on the xsensors on my box, without running a GUI - so it is quieter, and cooler without the extra kick it gets from running all the graphics.

I'm off for some lunch.. :popcorn:

ps, I'm marking this thread as solved. Thanks to the following pages.
[x11-connection-rejected-because-of-wrong-authentication]("http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/")
Of course thanks to endotherm
the [FreeNX]("https://help.ubuntu.com/community/FreeNX") page on the wiki.

---

### Post by endotherm on 2010-11-26
glad you got everything worked out. I've never forwarded X, but I hear a lot of people swear by it. 

in terms of judging the strength of your security, I guess I would test to ensure that ssh was absolutely required to access the vnc service. that was my only concern. since you appear to start vnc as the endpoint for a tunnel, that may take care of everything. sorry if I alarmed you.

in terms of hardening SSH itself, here is a guru for ya: [http://bodhizazen.net/Tutorials/ssh_security/](http://bodhizazen.net/Tutorials/ssh_security/) .

---

### Post by theDaveTheRave on 2010-11-26
should have guessed it would be Bodhizazen :popcorn:


The things with my method of connecting, is that until I have SSH'd to the box, the vnc server isn't running.

In a way I liken it to forwarding the varions X stuff. This opens in a window on my terminal, and is secure. So from there I make the assumption that so would vnc be secure.

I'll head over to the Bodhizazen thread and see what advice he has.... although I must admit I think that X forwarding (as it is working) is the way to go, and if required I'll use FreeNX for a full gui connection.

David.

---

