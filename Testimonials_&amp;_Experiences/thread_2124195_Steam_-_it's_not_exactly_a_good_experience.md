---
title: "Steam - it's not exactly a good experience?"
date: 2013-03-10
forum: Testimonials &amp; Experiences
---

### Post by 3rdalbum on 2013-03-10
So far I'm not especially liking Steam for Ubuntu. It's not a very "Ubuntu-like" experience.

I downloaded the Steam client today. The first thing it wanted to do was "update" - actually, it looks like it was downloading the real client. 165 megabytes! For a digital shop! Craziness, pure craziness. There are games on Steam that are smaller than the Steam client!

After it finished downloading, I tried to launch it and log in, only for it to tell me that Steam requires a later version of the Nvidia driver than what I was using (the one available from day-one of Ubuntu 12.04). Once again, this is a digital download store, requiring a particular graphics driver version? Insane!

As I'm running 12.04, the version of the Nvidia driver that Steam requires is higher than what is available from the Additional Drivers program. I'd have to find and install a PPA or manually install the Nvidia driver and keep reinstalling it whenever there's a kernel update. This seems like a curious and unacceptable oversight considering the partnership between Valve and Canonical. You'd think either Valve would make sure Steam could work with the 12.04 driver, or that Canonical would package the later Nvidia driver as a backport for 12.04.

I'll update this post when I have Steam finally running.

---

### Post by mastablasta on 2013-03-11
what happens if you use opensource drivers? you can't run steam, but can run the games? this is strange. why would graphics card drivers really matter in a store?

---

### Post by 3rdalbum on 2013-03-11
> **mastablasta said:**
> what happens if you use opensource drivers? you can't run steam, but can run the games? this is strange. why would graphics card drivers really matter in a store?

I don't know why they matter, but Steam works fine on Nouveau. I found this out because the PPA stuffed up my graphics, and now it's fallen back to the open-source driver.

Downloading the manual Nvidia driver now.

Jolly poor show, that you have to do so much mucking around just to run Steam on 12.04 - a supported platform!

---

### Post by samsom63 on 2013-03-11
> **3rdalbum said:**
> So far I'm not especially liking Steam for Ubuntu. It's not a very "Ubuntu-like" experience.

I downloaded the Steam client today. The first thing it wanted to do was "update" - actually, it looks like it was downloading the real client. 165 megabytes! For a digital shop! Craziness, pure craziness. There are games on Steam that are smaller than the Steam client!

After it finished downloading, I tried to launch it and log in, only for it to tell me that Steam requires a later version of the Nvidia driver than what I was using (the one available from day-one of Ubuntu 12.04). Once again, this is a digital download store, requiring a particular graphics driver version? Insane!

As I'm running 12.04, the version of the Nvidia driver that Steam requires is higher than what is available from the Additional Drivers program. I'd have to find and install a PPA or manually install the Nvidia driver and keep reinstalling it whenever there's a kernel update. This seems like a curious and unacceptable oversight considering the partnership between Valve and Canonical. You'd think either Valve would make sure Steam could work with the 12.04 driver, or that Canonical would package the later Nvidia driver as a backport for 12.04.

I'll update this post when I have Steam finally running.

i don't know for Nvidia, but I have the open source drivers for my ATI card and Steam never complained about it, let alone asked for me to install new ones.

---

### Post by mastablasta on 2013-03-12
> **samsom63 said:**
> i don't know for Nvidia, but I have the open source drivers for my ATI card and Steam never complained about it, let alone asked for me to install new ones.

yah, Nouveau are ndvidia opensoruce drivers. but opensource driver (also for AMD) do not use full potential of graphcis card. and with games you need as much as you can get from a GPU. furthermore new cards need proprietary drivers to even work propperly. which means this could potentially be a big issue.

---

### Post by samsom63 on 2013-03-12
> **mastablasta said:**
> yah, Nouveau are ndvidia opensoruce drivers. but opensource driver (also for AMD) do not use full potential of graphcis card. and with games you need as much as you can get from a GPU. furthermore new cards need proprietary drivers to even work propperly. which means this could potentially be a big issue.

I agree that it could be a problem. I was merely noting that the OP's issue with Nvidia does not happen for me with ATI. The legacy proprietary drivers for my graphic card (Radeon 4500) are not supported with the latest xserver and kernel, so I stick with the open source drivers. It is actually ok for playing not too graphically demanding games (Bastion runs at a correct FPS as well).

---

### Post by 3rdalbum on 2013-03-12
> **samsom63 said:**
> I agree that it could be a problem. I was merely noting that the OP's issue with Nvidia does not happen for me with ATI. The legacy proprietary drivers for my graphic card (Radeon 4500) are not supported with the latest xserver and kernel, so I stick with the open source drivers. It is actually ok for playing not too graphically demanding games (Bastion runs at a correct FPS as well).

Note, if I use the default Nouveau driver I can run Steam. There's even some measure of 3D support for running Unity, although I've never tried games on it. Steam doesn't mind if you barely have any 3D support, just as long as you're not using an old driver!

I finally got the Nvidia driver installed - took long enough to figure out how to blacklist Nouveau these days, it's not as simple as it used to be - and now Steam runs happily. I can browse all the games that I could ever want, except that most of the games displayed are only on Windows and Mac. Oh; there's a little tab for Linux. It's quite a visually noisy user interface, I didn't see it before.

With all that hassle over, so far Steam work as I'd expect. I haven't bought any games, only claimed an Indie Bundle one, which promptly downloaded. Steam appears to work, although I'm still not sure where all those 165 megabytes went, or why exactly it needs a specific driver version just for the store.

I definitely think Steam's repository should have up-to-date graphics drivers for easy installation, or Steam should work with all proprietary graphics drivers from the Additional Drivers program on all supported versions of Ubuntu.

---

### Post by Sesshomurai on 2013-03-18
This is really sad. Why doesn't steam provide the option to install its driver dependencies? It's kind of the whole point of Steam that you don't have to hunt around and install crap yourself.
Gonna need lots of improvement before its successful.

---

