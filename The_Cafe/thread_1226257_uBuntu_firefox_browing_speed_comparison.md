---
title: "uBuntu firefox browing speed comparison"
date: 2009-07-29
forum: The Cafe
---

### Post by legendbb on 2009-07-29
New to uBuntu,
 
ran speedtest.net, the result is hard to accept, firefox under uBuntu is nothing to catch up any other speeds under other OS.
 
Please comment (see attachment):
 
 
 
Thanks in advance.

uBuntu 9.04 installed by WUBI
Tested machine: X61 = Thinkpad x61 tablet, Core2Duo 1.6G, 4G Ram
                HP = HP minibook 1G Ram

---

### Post by khelben1979 on 2009-07-29
You haven't specified which version of Ubuntu you're using.

---

### Post by Copernicus1234 on 2009-07-29
Seems your computer doesnt like Ubuntu. Or something. Never seen worse results.

Good thing this is not representative of the general population. I have max speed in Ubuntu, just like in any other OS. The browser or OS doesnt impact download speeds.

---

### Post by madjr on 2009-07-29
> **Copernicus1234 said:**
> Seems your computer doesnt like Ubuntu. Or something. Never seen worse results.

Good thing this is not representative of the general population. I have max speed in Ubuntu, just like in any other OS. The browser or OS doesnt impact download speeds.

same

full speed :)

---

### Post by legendbb on 2009-07-29
Two computers did the test:
Lenovo Thinkpad X61 Tablet, Core2Duo 1.6GHz 4GRam
HP minibook N270

LAN connection in U of Waterloo, Canada

---

### Post by jomiolto on 2009-07-29
Have you tried downloading some large file (like Ubuntu ISO) and seeing if the same difference applies to that? speedtest.net uses Flash, so it might be possible that Flash is too slow under Linux to give reliable results.

That's pretty much the only thing I can think of, since my Internet connection has always been equally fast (or slow, since I'm on 1Mbps ADSL) on Windows and Linux.

---

### Post by MaxIBoy on 2009-07-29
[IMG]http://www.speedtest.net/result/528079290.png[/IMG]
[img]http://www.speedtest.net/result/528081908.png[/img]

I think it's a crock. I've **never** had anything go that fast.

---

### Post by legendbb on 2009-07-29
I don't concern about the speed itself (it's from university LAN). Just the differences between I could not understand.

Recent test did on thinkpad x61, under vista

---

### Post by .Maleficus. on 2009-07-29
> **MaxIBoy said:**
> [IMG]http://www.speedtest.net/result/528079290.png[/IMG]
[img]http://www.speedtest.net/result/528081908.png[/img]

I think it's a crock. I've **never** had anything go that fast.
You are aware that those results are in M**b**ps, right?  And not M**B**ps (the difference being megabits vs. megabytes)?  Divide that number by 8 and you'll have an idea of what your download actually is.

---

### Post by gletob on 2009-07-29
I have heard multiple times that comcast has issues with IPv6 (note: this has nothing to do with the issue with IPv6 from a few years ago)

Many have said to run this
```
echo 'blacklist ipv6' | sudo tee -a '/etc/modprobe.d/blacklist.local' >/dev/null
```

Then reboot your system and see if the speed improves.

This blacklist IPv6 from being used on you computer.  

[COLOR=Red]NOTE: This is only necesary for those with an internet connection provided by comcast cable.[/COLOR]

---

### Post by HappinessNow on 2009-07-29
My > browing Speed is fine, now if I can just figure out how to lick my eye brows I would be truly more reptilian-like.

---

### Post by windows-killer on 2009-07-29
Try installing ubuntu natevily on your machine. WUBI is too slow compared to the actual install. 

Good luck

---

### Post by MaxIBoy on 2009-07-29
> **.Maleficus. said:**
> You are aware that those results are in M**b**ps, right?  And not M**B**ps (the difference being megabits vs. megabytes)?  Divide that number by 8 and you'll have an idea of what your download actually is.Yeah, I'm very much aware of that. 15/8 is 1.875 Mib/s. I have never gotten above 800 Kib/s (at 3 AM when no one else is on,) usually closer to 400 or 500.

---

### Post by .Maleficus. on 2009-07-29
> **MaxIBoy said:**
> Yeah, I'm very much aware of that. 15/8 is 1.875 Mib/s. I have never gotten above 800 Kib/s (at 3 AM when no one else is on,) usually closer to 400 or 500.
Just making sure ;).  Sorry to hear that though; I'm usually at 1.25 - 1.3MB/s on my 10Mbps line so Speedtest is probably pretty accurate.

---

### Post by MaxIBoy on 2009-07-29
Might be something to do with that test server being only 50 miles from where I live. The other server I tested with was closer to the truth, sort of.

---

### Post by EM man on 2009-07-29
> **legendbb said:**
> New to uBuntu,
 
ran speedtest.net, the result is hard to accept, firefox under uBuntu is nothing to catch up any other speeds under other OS.
 
Please comment (see attachment):
 
 
 
Thanks in advance.

uBuntu 9.04 installed by WUBI
Tested machine: X61 = Thinkpad x61 tablet, Core2Duo 1.6G, 4G Ram
                HP = HP minibook 1G Ram

Even if this data isn't a fluke, the ridiculous time required for Windows to start, for applications to load in Windows, and the frequency of crashes in Windows, more than cancels that out.

---

### Post by .Maleficus. on 2009-07-29
> **EM man said:**
> Even if this data isn't a fluke, the ridiculous time required for Windows to start, for applications to load in Windows, and the frequency of crashes in Windows, more than cancels that out.
Sounds like you have just had a bad experience because my Windows 7 install has done none of that and is just as quick as a vanilla Ubuntu install.

---

### Post by EM man on 2009-07-29
> **.Maleficus. said:**
> Sounds like you have just had a bad experience because my Windows 7 install has done none of that and is just as quick as a vanilla Ubuntu install.

I was referring to every version of Windows that I have ever used.  I have not used Windows 7.  Is it radically different than the other versions?  :confused:

---

### Post by gletob on 2009-07-29
> **EM man said:**
> Even if this data isn't a fluke, the ridiculous time required for Windows to start, for applications to load in Windows, and the frequency of crashes in Windows, more than cancels that out.

Compare this to downloading a huge torrent file (let's say a 700 MB movie) I'm sure an extra 200-300 KB/s of speed will more than make up for a slow startup.

---

