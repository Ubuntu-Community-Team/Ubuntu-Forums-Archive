---
title: "SteamOS: Ext4 or Btrfs?"
date: 2013-09-23
forum: Ubuntu, Linux and OS Chat
---

### Post by King Dude on 2013-09-23
I was basking in the happy news of the SteamOS when I suddenly thought, "What files system should the SteamOS use by default?"

I understand that Btrfs is still technically experimental, but it has become very stable over the past few years of intense development. I personally prefer Btrfs, but what do you guys think?

---

### Post by 3rdalbum on 2013-09-24
I don't think SteamOS will need the btfs features, so they will use Ext.

This is so not a burning question for most people!

---

### Post by philinux on 2013-09-24
News link.

[http://m.bbc.co.uk/news/technology-24207129](http://m.bbc.co.uk/news/technology-24207129)

Very interesting development.

---

### Post by King Dude on 2013-09-24
Btrfs is more optimized for SSDs than Ext4, and SSDs are popular among gamers.

---

### Post by evilsoup on 2013-09-24
According to omgubuntu, SteamOS is going to be based on Ubuntu 12.04, so I would have thought they would use the default filesystem (ext4).

That said, it seems like it will just be another Linux distro (albeit with a TV-centric interface), so it should be possible to set whatever filesystem you want (that Ubuntu 12.04 supports).

---

### Post by King Dude on 2013-09-24
> **evilsoup said:**
> According to omgubuntu, SteamOS is going to be based on Ubuntu 12.04, so I would have thought they would use the default filesystem (ext4).

That said, it seems like it will just be another Linux distro (albeit with a TV-centric interface), so it should be possible to set whatever filesystem you want (that Ubuntu 12.04 supports).
Source?

---

### Post by Lars Noodén on 2013-09-24
> **King Dude said:**
> Source?

"Although not confirmed by Valve, we’ve been told that Steam OS is based on Ubuntu 12.04 LTS."
[http://www.omgubuntu.co.uk/2013/09/valve-announce-steamos](http://www.omgubuntu.co.uk/2013/09/valve-announce-steamos)

---

### Post by y6FgBn)~v on 2013-09-24
> **King Dude said:**
> Source?

[http://www.omgubuntu.co.uk/2013/09/valve-announce-steamos](http://www.omgubuntu.co.uk/2013/09/valve-announce-steamos)

---

### Post by King Dude on 2013-09-24
If it's going to be based on Ubuntu, I guess we can kiss Wayland support goodbye.

---

### Post by Copper Bezel on 2013-09-24
Oh, that makes sense - it means they'll be able to maintain Ubuntu as a platform and not have to write anything twice. If Valve takes the Mir route instead of Wayland, it frankly makes Ubuntu a lot more secure as a platform. (Bit of a slap to everyone else, of course, but that's because it's Mir.)

---

### Post by ssam on 2013-09-24
I think they will be conservative with most things. They want to roll it out to millions of non-techies and not have issues. The only place i imagine them trying to be cutting edge would be bits that they know very well, for example graphics drivers.

Also if they want this to be more appliance than computer, then it may have the main file system read only, and use a separate partition for user data.

---

### Post by King Dude on 2013-09-24
Yeah, I feel bad for Wayland. I wish there was a Wayland/Mir hybrid display server that has dual compatibility. In fact, I heard something like that I while back from one user on here. I'll post what he told me if I can dig it up from the depths of this forum.

> **ssam said:**
> I think they will be conservative with most things. They want to roll it out to millions of non-techies and not have issues. The only place i imagine them trying to be cutting edge would be bits that they know very well, for example graphics drivers.
True. I always find it frustrating knowing how technically impaired the average gamer is :/

I still get messages from random people asking me dumb tech questions such as "Y cant my video drive display my game?" Oy vey.

---

