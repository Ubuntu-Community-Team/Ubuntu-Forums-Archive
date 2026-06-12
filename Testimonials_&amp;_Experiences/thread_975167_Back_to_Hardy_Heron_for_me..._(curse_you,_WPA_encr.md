---
title: "Back to Hardy Heron for me... (curse you, WPA encryption bug!)"
date: 2008-11-08
forum: Testimonials &amp; Experiences
---

### Post by hurtstotalktoyou on 2008-11-08
I installed Intrepid Ibex yesterday.  I liked the new "compact" file view.  But I'm going to have to get by without it, though, because the new version 8.10 doesn't support my WPA router.

Why?  I have no idea.  In version 8.04 and 8.04.1, I would ALT-F2 > "network-admin" and enable my wireless router connection from there.  It had a gui where I'd just select "WPA" from a drop-down menu and then type in my network name and password.  It had to be re-configured every time I rebooted, and then it took up to five attempts before it would actually connect, but at least I could always get it to work.

Yesterday I performed a fresh install of 8.10.  After installing my ndisgtk driver, I went to do what I did in 8.04.x:  ALT-F2 > "network-admin".  But, much to my dismay, I got an error message.  It turns out that there is no "network-admin" in 8.10!

No problem, though, right?  I'll just install it from Synaptic.  I found something called network-admin-gnome, and installed it.  Now when I go to ALT-F2 > "network-admin", the familiar gui pops up.  But wait!  When I go to select "WPA" from the drop-down menu, I find that it has disappeared from the network-admin in 8.04.x.  Now all I get are options for WEP, which is not what my wireless router uses.

So I spend the bulk of last night trying to figure out a workaround, to no avail.  What a waste of time...

This is a major problem with Ubuntu, in my opinion.  The internet is an extremely important part of the home computing experience.  Pretty much everyone depends on the internet in some way or another, and so it seems to me that internet hardware compatibility would be a paramount concern for developers.

My last upgrade experience was problematic, too.  Ubuntu 8.04 did not support any of my CRT monitors out of the box, and I spent several days (and a lot of wasted time) trying to figure out a solution.

I can't imagine what kind of terrible time newbies are having.  I hope they have better luck than I did.

I'm beginning to think that a 6-month upgrade cycle is a bad idea.  I may be sticking with 8.04.1 even after version 9 is released.

---

### Post by nickdbliss on 2008-11-08
well i agree with you. Six months are not enough, they should make it 8 or 10.

---

### Post by iponeverything on 2008-11-08
Just use /etc/network/interfaces instead.

---

### Post by hurtstotalktoyou on 2008-11-08
> **iponeverything said:**
> Just use /etc/network/interfaces instead.

Isn't that for the wifi driver?  The driver worked fine with ndisgtk.  It was connecting to a router with WPA encryption that was impossible, a problem with network-admin-gnome.

Besides, I did try setting up the driver manually with madwifi.  I followed some command-line instructions, but they didn't work for me.  Oh, well.

---

