---
title: "What is your experience with Noveau?"
date: 2011-08-27
forum: The Cafe
---

### Post by lovinglinux on 2011-08-27
I was experiencing bad performance with the latest nvidia driver from x-swat ppa on Kubuntu 11.04 with KDE 4.7 and nvidia 7300GT card. For instance, when scrolling a couple of web sites on Firefox while watching a video on smplayer, the video would stutter momentarily.

So I decided to give Noveau a try. I am impressed. Not only the video doesn't stutter anymore, but also a particular web site that was really slow on Firefox, is scrolling very smoothly now.

I haven't tested any games or HD videos yet.

I would like to know what is your experience with Noveau?

---

### Post by lovinglinux on 2011-08-27
Looks like my nvidia card is running at 90ºC instead of 65ºC.

Can I trust the noveau sensor? The card heat-sink doesn't appear to be that hot.

---

### Post by ilovelinux33467 on 2011-08-27
Fedora 15 is the first release of Fedora that I haven't bothered installing the NVIDIA closed source driver as I find the Nouveau one now works perfectly for me (KDE Desktop Effects, Nexuiz, etc...). My card is NVIDIA GTX 260.

---

### Post by lovinglinux on 2011-08-27
> **ilovelinux33467 said:**
> Fedora 15 is the first release of Fedora that I haven't bothered installing the NVIDIA closed source driver as I find the Nouveau one now works perfectly for me (KDE Desktop Effects, Nexuiz, etc...). My card is NVIDIA GTX 260.

What about the temp?

---

### Post by el_koraco on 2011-08-27
> **lovinglinux said:**
> 
Can I trust the noveau sensor? The card heat-sink doesn't appear to be that hot.

Yes, you get about a 10-15 percent increase in temperature with open source drivers with ATI and Nvidia. I'd be using radeon if it wasn't turning my laptop into an oven.

---

### Post by ilovelinux33467 on 2011-08-27
> **lovinglinux said:**
> What about the temp?

The card itself never really feels hot. For some reason I can't seem to get a reading using sensors.
```

[andrew@localhost]~% sensors
nouveau-pci-0100
Adapter: PCI adapter
temp1:         +0.0°C  (high = +100.0°C, crit = +110.0°C)

```

---

### Post by lovinglinux on 2011-08-27
> **el_koraco said:**
> Yes, you get about a 10-15 percent increase in temperature with open source drivers with ATI and Nvidia. I'd be using radeon if it wasn't turning my laptop into an oven.

Just installed nvidia proprietary driver and I am back to slow performance. I just don't feel comfortable running my card at 90ºC. :evil:

I guess I will have to wait for Ubuntu 11.10 to see if things get better.

---

### Post by wojox on 2011-08-27
I found for 11.04 the 173.xx.xx ran better than the 280.xx.xx or nouveau.

---

### Post by lovinglinux on 2011-08-28
> **wojox said:**
> I found for 11.04 the 173.xx.xx ran better than the 280.xx.xx or nouveau.

WOW! Huge difference. I wouldn't expect the old 173 to be better than the new and shiny 280 and noveau. 

Thanks a lot for the tip. 

:KS:KS:KS:KS:KS

---

### Post by el_koraco on 2011-08-28
> **lovinglinux said:**
> I guess I will have to wait for Ubuntu 11.10 to see if things get better.

Nah, AMD is publishing specs for years now, and radeon is nowhere near with regard to PM. It does have downclocking options for the card (not enabled by default, I have no idea why), but it just doesn't match fglrx performance. I'd guess we'll have to give it a year or two.

---

### Post by 3rdalbum on 2011-08-28
Nouveau works pretty well for my GTX260. I can run Unity 3D on it. I'd still be using Nouveau if I didn't like watching videos - the Nvidia driver does video decode acceleration.

---

### Post by kaldor on 2011-08-28
If not for the heat problems, Nouveau would be running on my laptop instead of the NVIDIA blob.

My experience = fried eggs.

---

### Post by Oxwivi on 2011-08-29
Things are looking up: [http://www.phoronix.com/scan.php?page=news_item&px=OTg0OA](http://www.phoronix.com/scan.php?page=news_item&px=OTg0OA)

That's about fan control code being published. There's a snippet in the end saying there's some power management announcement in the making. It will be worth using X-Swat PPA in the near-future. :)

---

### Post by beew on 2011-08-30
In my experience the pros and cons of nouveau are

pros: 

1.FLOSS

2.Can be used in a portable installation. I have a Natty installed on an  external drive and I can plug it in any computer and use it (well most  of the time)

3.It integrates better with the rest of the system, when it works it is really smooth (no problem running 3d Unity) It is certainly smoother than the Nvidia blobs when entering and exiting full screen on Umplayer (with Nvidia there is a momentary lag and a strange green flash during this transition to and from full screen for smplayer and umplayer)

4.Performance is actually quite good for videos and such. I can watch  1080p with my dual core machine with 3G of ram (not really top of the  line) with mplayer2 and VLC (not as good as MPlayer2, but mostly ok) I can even  watch 3D movies with bino.

Cons: 

1.No vdpau, so it is a lot more taxing on cpu when viewing hd movies I can  watch 1080P movies on my dual core machine with nouveau but difference  is it uses ~80% cpu instead of 8% with the Nvidia blobs (that is  probably the reason for heat reported by some here, though I have not experienced overheating on my Natty install with the nouveau driver even when watching hd movies)

2.Tearing and artefacts for videos and compiz (when rotate the cube e.g, I  have the cube enabled in Unity), though it is not very serious.

3.Lower OpenGL support (In my machine the Nvidia card supports OpenGL version 3.3 but Nouveau only supports version 2.1)

4.Doesn't work for most (I suppose) games, yofrankie doesn't even load  after the game starts (probably something to do with OpenGL support)

I am actually using noveau from the xorg-edgers ppa, the Ubuntu official  version actually performs a lot more poorly (e.g it only supports  OpenGL 1.7 on my machine and the screen freezes quite a bit.

On my main machine I use the Nvidia blob (Maverick) I also have another  Natty using the Nvidia driver for testing, I use Nvidia 280.xx (the  latest stable) in Maverick and 285.03 (latest beta) in Natty, both work  very well, I have not experienced the problems described by Lovinglinux. 

P.S. I found this new ppa it kind of sounds interesting and supposed to  provide even more cutting edge open source graphic drivers than  xorg-edgers with better support for OpenGL and games, but I have not  been able to get it to work (made a fresh install, update with the ppa  and it wouldn't boot into gui) The curious and brave may want to  experiment with it.

[https://launchpad.net/~oibaf/+archive/graphics-drivers]("https://launchpad.net/%7Eoibaf/+archive/graphics-drivers")

---

### Post by jis on 2011-08-30
I see excessive Xorg activity in some tasks:
[http://askubuntu.com/questions/59222/why-does-xorg-take-all-available-cpu-power-when-i-run-update-manager](http://askubuntu.com/questions/59222/why-does-xorg-take-all-available-cpu-power-when-i-run-update-manager)
On the other hand, I can play some 720p HD videos with the driver by the old hardware, not by Adobe Flash player, though.

---

