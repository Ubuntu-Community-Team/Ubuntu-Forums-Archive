---
title: "fresh install firefox won't connect to internet"
date: 2009-04-25
forum: Ubuntuzilla
---

### Post by swatsbiz on 2009-04-25
Hi have just completed a fresh install of Jaunty 64bit Desktop edition and went straight for the ubuntuzilla install - after installing I could not connect to anywebsites with it (page load error)  I did an uninstall of ubuntuzilla to see if that would correct the problem, but no joy.

(update - I just realised that I have only uninstalled ubuntuzilla not firefox, I uninstalled ubuntuzill-firefox and have firefox working again - any ideas why ubuntuzilla wasn't working or should I try reinstalling it later?)

Is there a simple setting that I have missed?

David

---

### Post by nanotube on 2009-04-25
Hi,

Well, I haven't come across anything like this before, so not sure what could be going on...

try installing again with ubuntuzilla, run firefox, see if it works, if it doesn't work, close firefox completely, then open a terminal and run "firefox.ubuntu" (that's where ubuntuzilla sticks default repository-version of firefox), and see if it works.

if it does keep working with firefox.ubuntu, but not with just firefox, i would venture to guess (and a guess it is) that it may have something to do with some 64bit libraries on jaunty...

also, try running just "firefox" from a terminal (when ubuntuzilla's version is installed), try going to some websites, and see if any useful error messages show up in the terminal...

---

### Post by honeywine on 2009-05-14
Hi.

Try switching **network.dns.disableIPv6** option to **true** in your *about:config*. That's what solved similar problem of mine.

---

### Post by shoeheight on 2009-05-30
This seems to be an issue with a number of installs, 

[http://ubuntuforums.org/showthread.php?t=1167706](http://ubuntuforums.org/showthread.php?t=1167706)

Thanks, I'll try your fix too.

---

### Post by shoeheight on 2009-05-30
Changing ivp6 fixed it, thanks.

If anyone else has this problem type "about:config" into the firefox browser. 

Then use the filter (on the top of the screen) for ipv6.

The first value is "network.dns.disableIPv6" double click on "false" to change it to "true".  (this disables IPv6 support in Firefox.)

This fixed it for me...I hope it does for you.

---

### Post by beartham on 2009-05-30
Hey,

That worked for me, and for SeaMonkey too.:p

Thanks guys.

---

### Post by nanotube on 2009-06-01
> **honeywine said:**
> Hi.

Try switching **network.dns.disableIPv6** option to **true** in your *about:config*. That's what solved similar problem of mine.

thanks for the tip, honeywine. seems like that's the ticket! :)

---

### Post by alliance1975 on 2009-07-07
I just experienced the same problem and the recommended solution also solved it. My question would be why? If knowledge of ubuntu ranges from sublime to ridiculous then I am right next to ridiculous. Basically I'd like to know if a problem was created by the config change.

---

### Post by Jimleko211 on 2009-07-13
THanks a lot, it solved my problem.  Firefox 3.5 is soo much better than 3.

---

### Post by gnoob on 2009-07-16
This worked for me too (64bit jaunty, FFv3.5). Not that IPv6 is necessary right now but i'd rather not disable the next generation standards. They'll probably fix it in karmic, but i would like to know why this happens.

---

### Post by d0b33 on 2009-07-17
Thanks honeywine, just downloaded the latest firefox but not connecting to the net was confusing me but that fixed it though.

---

### Post by bluenix on 2009-07-28
dear honeywine, that absolutely worked, thanks!

---

### Post by w33d3d on 2009-07-29
Thank you this also fixed my problem

---

### Post by beadrifle on 2009-09-30
[FONT=Courier New]Disabling the IPv6 option worked for me too. Thanks a bunch.
[/FONT]

---

### Post by grkor on 2009-10-01
Below is brilliant!  :-)    / I tried it and it DID WORK  like a charm ! Now Firefox 3.5 runs like a fast race car ! :-)  / Gregory


Changing ivp6 fixed it, thanks.

If anyone else has this problem type "about:config" into the firefox browser. 

Then use the filter (on the top of the screen) for ipv6.

The first value is "network.dns.disableIPv6" double click on "false" to change it to "true". (this disables IPv6 support in Firefox.)

This fixed it for me...I hope it does for you.

---

### Post by Algus on 2009-10-13
> **honeywine said:**
> Hi.

Try switching **network.dns.disableIPv6** option to **true** in your *about:config*. That's what solved similar problem of mine.

Hey everyone.  Just chipping in that I just now used the script and had the EXACT SAME PROBLEM as described in the OP.  However, I did what honeywine suggested and it worked immediately.  

Just wanted to throw in that this worked for me for anyone else having issues.  

Also thanks to honeywine for posting; all the way back in May and still very useful!

---

### Post by honeywine on 2009-10-19
I'm glad that helped. :)

---

### Post by virgil_machine on 2009-11-02
Setting the disable ipv6 to true Worked for me, too. 

I am running jaunty with several vms under virtualbox 3.0.8. The problem was on the host.

I checked a karmic 64-bit vm and the value was "false".  Everything works fine in the vm, so something may have been fixed.  It sure seems like a bug.  I set the vm to true also, just for grins, ands there's no difference.

I have not tried upgrading a jaunty vm to 3.5.4 to see if I get the same problem.

---

### Post by tons-of-funs on 2009-11-17
ok im having the same problem, the only thing is when i disabled the ipv6 it didnt do anything, i still can not connect to the internet, ubuntu says im connected to my wireless but i cant connect to anything, my update manager cant connect either

---

### Post by nanotube on 2009-11-17
> **tons-of-funs said:**
> ok im having the same problem, the only thing is when i disabled the ipv6 it didnt do anything, i still can not connect to the internet, ubuntu says im connected to my wireless but i cant connect to anything, my update manager cant connect either

if other applications can't connect, then the problem is not with firefox, but with your network connection. try pinging google, maybe, to see if you've got net.
```
ping google.com
```

---

