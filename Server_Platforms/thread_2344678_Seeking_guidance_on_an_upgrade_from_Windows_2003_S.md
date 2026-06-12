---
title: "Seeking guidance on an upgrade from Windows 2003 Server to Ubuntu 16.04.1"
date: 2016-11-27
forum: Server Platforms
---

### Post by nick003 on 2016-11-27
About Me:  While I do have some experience with various distributions of LINUX, I still see myself as a beginner.  Once upon a time, there was DOS. And, I was fluent in the OS and the commands one could issue to achieve your goals. Oh, how I long for the days of "format c: /s". LOL  But, in the name of progress things became increasingly complicated. I believe Windows came on the scene because of this; it allowed the less technical minded to do more advanced things with a few button clicks without knowing what was going on behind those clicks.

I currently own a Dell Poweredge 1800 which operates Windows 2003 server. I'd like to upgrade to a more current operating system, and it seems like this is the perfect opportunity to switch over to Ubuntu.  I completed an Ubuntu 16.04.1 installation and all hardware is recognized and functioning. But my skill level is not allowing me to accomplish certain tasks. Primarily, RAID configuration.

As a Windows 2003 Server, I have 6 1TB drives which are connected to an Adaptec Serial ATA II RAID 2820SA controller. The drives are configured as mirrors, giving me 3 mirrored 1 TB volumes. I would like to configure those 6 1 TB drives as 3 1 TB mirrored volumes in Ubuntu.

Can someone direct me to literature which provides instruction on how this is done in Ubuntu?

Thank you.
Nick

---

### Post by timfinley on 2016-11-27
I've never done a RAID setup. But I will say that if you are not familiar with BASH, you will have a bit of an uphill climb. Here's a great place to start: [http://ryanstutorials.net/linuxtutorial/](http://ryanstutorials.net/linuxtutorial/)

Here's a guide that might help you with your RAID setup: 
[URL="http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html"]
http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html[/URL]

There are tons more resources out there. You can also look at videos on YouTube or similar websites. 

Good Luck!

---

### Post by cariboo on 2016-11-28
You should find better help here.

---

### Post by darkod on 2016-11-28
The SW raid link suggested is basically that, a SW raid solution with mdadm standard in linux. But branded servers with "built-in" raid cards usually do HW raid even before the OS takes over, so the OS should basically see separate 3x 1TB disks that your raid adapter is presenting to it.

That means if you did the raid in the raid adapter, which it looks you did, that's it. The Ubuntu Server OS will never see 6x 1TB disks, it will see 3x 1TB instead.

Now it depends how you want to use that space... Join it into one big 3TB space?

There are a number of ways to check disks in the command line, for example:
```
sudo parted -l (small L)
```

That should show you all disks present...

---

### Post by nick003 on 2016-11-29
> **darkod said:**
> The SW raid link suggested is basically that, a SW raid solution with mdadm standard in linux. But branded servers with "built-in" raid cards usually do HW raid even before the OS takes over, so the OS should basically see separate 3x 1TB disks that your raid adapter is presenting to it.

That means if you did the raid in the raid adapter, which it looks you did, that's it. The Ubuntu Server OS will never see 6x 1TB disks, it will see 3x 1TB instead.

Now it depends how you want to use that space... Join it into one big 3TB space?

There are a number of ways to check disks in the command line, for example:
```
sudo parted -l (small L)
```

That should show you all disks present...

That is correct; the system was set up as a HW RAID prior to the Ubuntu (16.04.1) install. Once the install was complete, it DID show the 3 mirrored drives. But, after some updates, they disappeared. I've even tried reversing the updates and did a fresh install to no avail. I suppose the real question is why have the mirrors disappeared?

---

### Post by nick003 on 2016-11-29
What I do notice is that when booting, I am getting the following message:

"AAC: host adapter dead -1"

This message will repeat several times and then he boot up will continue.

---

### Post by darkod on 2016-11-29
That doesn't sound good, although I have to say I have never heard of such a message before. But the words "host adapter" and "dead" in the same sentence definitely don't sound good.

Are you sure your raid card hasn't died?

This is why most linux server admins prefer mdadm SW raid. No dependance on raid cards, and you can even move the disks to completely different machine and the raid will assemble if the disks are good. 

With HW raid cards you are very lucky if you manage to re-assemble your arrays when your card dies even if you buy the identical model.

Try going into the raid bios/setup and check out if it looks normal (it lets you in, the arrays are there, etc).

---

### Post by nick003 on 2016-11-29
Yes; the HW raid is fine. It worked perfectly in Win Server 2003

---

### Post by nick003 on 2016-11-29
I noticed something when I ran dmesg:

```
[  393.396309] aacraid 0000:02:05.0: PCI IRQ 37 -> rerouted to legacy IRQ 17
[  393.396331] aacraid: probe of 0000:02:05.0 failed with error -110
```

It sees the raid card, but why would the interrupt be rerouted and might that be the reason why I'm not seeing the drives?

---

