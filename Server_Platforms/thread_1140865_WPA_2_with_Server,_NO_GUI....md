---
title: "WPA 2 with Server, NO GUI..."
date: 2009-04-28
forum: Server Platforms
---

### Post by PrpHed on 2009-04-28
Hello everyone!

Just looking for a straight up answer...

Currently have a Budget 1 brand Wireless PCI card with a Realtek 8185 chip.

I am now on week 3 of scouring the forums here and various other places on the net.

I've tried/followed just about every conceivable suggestion, how to, "try this", "do that", that I could find all to no avail.  I've tried the built in RTL8180 drivers which just lock the system solid and don't do much else.  I've compiled the driver from Realtek which appears to be the same driver that ended up in all the recent releases.  Does NOT work.

Currently using ndiswrapper with Windows drivers.  I can connect without issue to an unencrypted router.  Encryption causes problems of every type one can imagine.

The best I can seem to get for an automatic connection is WPA-PSK with AES encryption.

Is this it?!?

Is Ubuntu, and or other Linux dists I've tried ALL broken when it comes to WPA 2 and the Realtek 8185?

Thanks.

---

### Post by PrpHed on 2009-05-06
> **PrpHed said:**
> Hello everyone!

Just looking for a straight up answer...

Currently have a Budget 1 brand Wireless PCI card with a Realtek 8185 chip.

I am now on week 3 of scouring the forums here and various other places on the net.

I've tried/followed just about every conceivable suggestion, how to, "try this", "do that", that I could find all to no avail.  I've tried the built in RTL8180 drivers which just lock the system solid and don't do much else.  I've compiled the driver from Realtek which appears to be the same driver that ended up in all the recent releases.  Does NOT work.

Currently using ndiswrapper with Windows drivers.  I can connect without issue to an unencrypted router.  Encryption causes problems of every type one can imagine.

The best I can seem to get for an automatic connection is WPA-PSK with AES encryption.

Is this it?!?

Is Ubuntu, and or other Linux dists I've tried ALL broken when it comes to WPA 2 and the Realtek 8185?

Thanks.

No replies!  I guess that's my answer... Ubuntu specifically, and Linux for the mostpart IS broken when it comes to the Realtek 8185 Wireless and WPA2.

After all the struggle, reading, searching, attempts at solutions (nearing 4 weeks), I can see why Linux will never be a true option for the average user.

Most would never be able to even get as far as I did because they are simply not tech savvy at all!

As much as I like Linux and can work with it, and make it work, it is beyond most users and XP in contrast generally works, all the time.

The "Linux is the best" "horn blowing" stops here...

---

### Post by windependence on 2009-05-06
Wireless support is horrible in Linux right now but is getting better. It is not the fault of the linux developers as they have their hands tied. Until the hardware manufacturers get out of bed with Mickey$oft and start opening their code or at least providing drivers for their hardware, there is nothing we can do about it. 

What are you doing running wireless on a Server in a production environment anyway? 128 bit WEP isn't good enough for you? Do you realize how long it takes to crack that even if you sitting there the whole time?

-Tim

---

### Post by cariboo on 2009-05-06
A little more info would be helpful, what version are you running, and why not use the driver that is included with the kernel.

This is a server forum, most of us want a fast solid network connection and unfortunately wireless doesn't qualify as either, so it may be hard to get an answer to your question here.

Have you had a look at this [threadt=571188]howto[/thread]?

---

### Post by PrpHed on 2009-05-07
> **windependence said:**
> Wireless support is horrible in Linux right now but is getting better. It is not the fault of the linux developers as they have their hands tied. Until the hardware manufacturers get out of bed with Mickey$oft and start opening their code or at least providing drivers for their hardware, there is nothing we can do about it. 

What are you doing running wireless on a Server in a production environment anyway? 128 bit WEP isn't good enough for you? Do you realize how long it takes to crack that even if you sitting there the whole time?

-Tim

Well, the only 3 reasons for running wireless on a server is one, it's just for my own use in my home office so, it's not overly critical should there be the occasional connection drop via wireless though that doesn't happen in my MS environments as my wireless here happens to work very well...I was hoping for the same in the Linux environment.  Two, due to the layout of my home and home office, there wasn't really a good solution to get cabled where the server lives.  And finally, three, because I can and thought it would be a decent learning exercise to sort out a wireless connection via command line...which I did...as far as it will go. 8)

That said, what I've finally done is setup a bridged WDS setup so the wireless router next to the server that is part of the WDS allows connecting of an ethernet cable so, it's as cabled as it can get.  Because WDS is a broken mess of its own, it only allows WEP at best so I've the wireless in the server connecting without issues to the WEP as well so the connection is backed up so to speak...one way or the other it's connected.

At this point it will suffice.

Thanks.

---

### Post by PrpHed on 2009-05-07
> **windependence said:**
> Wireless support is horrible in Linux right now but is getting better. It is not the fault of the linux developers as they have their hands tied. Until the hardware manufacturers get out of bed with Mickey$oft and start opening their code or at least providing drivers for their hardware, there is nothing we can do about it. 

What are you doing running wireless on a Server in a production environment anyway? 128 bit WEP isn't good enough for you? Do you realize how long it takes to crack that even if you sitting there the whole time?

-Tim

I hear ya on the manufacturer's issues.  That's a whole other "that sucks!" discussion...hehehehe!

It's not that WEP isn't good enough.  I was and am still learning Linux and not only wanted to conquer the WPA 2 connection if possible but was also doing all via command line...no GUI as part of the exercise.  I did get WPA with AES working but just wanted to see if I could get WPA 2 to happen.

See my other post...I did arrive at a solution that will do for now.

Thanks.

---

### Post by windependence on 2009-05-07
Wireless is one of the things I am sorely disappointed about in Linux and even Unix in general. It's not like it's new technology or anything but it just seems still clunky in Linux. Like I said above, I know the reasons for this, but the video cards have the same problem and we seem to have them working pretty well now. If I had time to contribute some code I surely would, but my consulting business keeps me very busy and I'm just making it. I truly wish it were not the case and feel for folks like yourself in situations like yours. Let's hope it gets better. 

There are some chipsets that are better supported than others, in fact there are some that work very well. Maybe you could find one of those cards and try that? Here is some info that may help you:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Good luck!

-Tim

---

