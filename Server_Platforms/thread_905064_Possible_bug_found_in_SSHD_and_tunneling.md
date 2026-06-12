---
title: "Possible bug found in SSHD and tunneling"
date: 2008-08-29
forum: Server Platforms
---

### Post by Sp00nMan on 2008-08-29
Greetings all,

I've run into a very strange phenomenom that I'm hoping someone can help me with.  I've debugged it from all angles and everything points back to ubuntu and sshd (or a library it depends on).  Here's the scenario:

At my office, I am sshing to my home machine using putty and setting up a dynamic socks proxy on port 8080.  When I point my firefox 3 (or firefox 2, or ie 7, I tried them all) to the localhost:8080 and surf the web (specifically lifehacker.com due to it's massive number of external links), the web pages renders through once.  Then if I do a shift-refresh, it starts to load again, then hangs.  My putty ssh session is hung also.  I can however fire up a second putty session into my home machine and it responds fine.  My home linux machine can also still go out on the internet, surf from the console (vnc) etc just fine.

So.. after trying out all the browsers, I thought, well, maybe it's my router.. (whr-g125 running dd-wrt 2.4sp1).  So .. I made my router itself open via ssh to the internet, and tunneled (ssh'd) in directly to my router.  The socks proxy using Firefox worked just fine, refreshing over and over without incident.

So now I thought "It must be the sshd on ubuntu".  So I downloaded the latest Openssh Portable 5.1p1 and compiled it from source.  Fired up a new putty session to tunnel, refreshed the browser, same hang.. browser quits pulling up website, putty session hung.

So finally, I fired up a brand new Fedora 9 instance in my ubuntu server (using vbox), told my router to redirect to it's sshd, and connected from my work machine directly to Fedora 9 VM.  Lo and behold, it worked just fine refreshing lifehacker.com over and over.

So .. the $64,000 question is what library or networking code does ssh compile against that could be causing the ssh channels via socks to not free up (or get overloaded)?  I have attached a snipped of the sshd running in debug mode to glean some insight (the final entry is the last time returned before hang).  The only difference I can see from the ubuntu sshd logs vs the fedora sshd logs is fedora seems to instantly free up the 'nchannels' as soon as the browser has finished loading the page.  I did not see that same behavior from the ubuntu sshd dump (stuck upwards of 33 nchannels).

Thanks in advance, and if you have read this far, you are a rockstar! :guitar:

---

### Post by Sp00nMan on 2008-08-30
Here is a link I found on the net with a similiar issue. I too get a list below right before it hangs.  It just spits out these lines and hangs forever.

[http://osdir.com/ml/network.openssh.general/2006-11/msg00047.html](http://osdir.com/ml/network.openssh.general/2006-11/msg00047.html)

debug1: server_request_direct_tcpip: originator 0.0.0.0 port 0, target safebrowsing.clients.google.com port 80
debug2: fd 40 setting O_NONBLOCK
debug2: fd 40 setting TCP_NODELAY
debug3: fd 40 is O_NONBLOCK
debug3: fd 40 is O_NONBLOCK
debug1: channel 30: new [direct-tcpip]
debug1: server_input_channel_open: confirm direct-tcpip
debug3: channel 30: waiting for connection
debug1: channel 30: connected
debug2: channel 30: read<=0 rfd 40 len 0
debug2: channel 30: read failed
debug2: channel 30: close_read
debug2: channel 30: input open -> drain
debug2: channel 2: ibuf empty
debug2: channel 2: send eof
debug2: channel 2: input drain -> closed
debug2: channel 3: ibuf empty
debug2: channel 3: send eof
debug2: channel 3: input drain -> closed
debug2: channel 4: ibuf empty
debug2: channel 4: send eof
debug2: channel 4: input drain -> closed
debug2: channel 6: ibuf empty
debug2: channel 6: send eof
debug2: channel 6: input drain -> closed
debug2: channel 8: ibuf empty
debug2: channel 8: send eof
debug2: channel 8: input drain -> closed
debug2: channel 9: ibuf empty
debug2: channel 9: send eof
debug2: channel 9: input drain -> closed
debug2: channel 13: ibuf empty
debug2: channel 13: send eof
debug2: channel 13: input drain -> closed
debug2: channel 14: ibuf empty
debug2: channel 14: send eof
debug2: channel 14: input drain -> closed
debug2: channel 17: ibuf empty
debug2: channel 17: send eof
debug2: channel 17: input drain -> closed
debug2: channel 19: ibuf empty
debug2: channel 19: send eof
debug2: channel 19: input drain -> closed
debug2: channel 21: ibuf empty
debug2: channel 21: send eof
debug2: channel 21: input drain -> closed
debug2: channel 26: ibuf empty
debug2: channel 26: send eof
debug2: channel 26: input drain -> closed
debug2: channel 29: ibuf empty
debug2: channel 29: send eof
debug2: channel 29: input drain -> closed
debug2: channel 30: ibuf empty
debug2: channel 30: send eof
debug2: channel 30: input drain -> closed

---

### Post by windependence on 2008-08-30
You're doing a tunnel over the internet (variable quality connection) and your going out through various devices, and back in via a consumer quality router. Then, you're browsing GUI stuff. Don't expect this to be a perfect connection because it isn't. It will get you by at best. If the quality of your pipe (the internet) goes down, you're hosed. It's not like being hard wired unfortunately. It's a great tool and you can do a lot with it, but mostly I restrict my use to ssh connections via console for this reason.

-Tim

---

