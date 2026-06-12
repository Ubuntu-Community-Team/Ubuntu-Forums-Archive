---
title: "Choosing laptop for Linux audio"
date: 2009-06-26
forum: Ubuntu Studio
---

### Post by ENatanael on 2009-06-26
I will soon buy a new computer, most likely a laptop, to replace my old one. As I'm a musician, I would like to play around with some sound recording/processing stuff as well as software synths and such. Apart from that the computer is going to be used for some minor gaming, surfing, writing sheet music, listening to music etc.
What I wonder is what I should think about when choosing a laptop for Linux audio processing. I've heard that an external hard drive is better than a large internal one, and I suppose that I should get an external sound card too? 
Are there any compatibility issues concerning sound cards and Linux that I should consider? 
Is a lot of RAM important, or a dual core processor? 
Is there any special brand I should avoid or favor? 
And I suppose Ubuntu Studio would be good?

---

### Post by trulan on 2009-06-27
Dual Core is good for audio processing.  As far as external cards go, I am currently fighting with a Dell laptop to get firewire audio working (using a Presonus Firepod, works great on my desktop).  There would have to be something better.  So at the moment I can't recommend a Dell, but I'm just biased.

The firepod (or FP10) is a great interface if you want to record eight simultaneous tracks.  If you don't need that many tracks, there are a lot of good USB sound cards out there.  Of course, if you have plenty of money to spend, there are devices that will do a lot more than the firepod.

And as a general rule, a laptop will be a bit trickier to set up than a desktop.

Ubuntu Studio is good, I also hear good stuff about 64studio (fewer frills, better reliability).  I have yet to try it though.

---

### Post by igorzwx on 2009-06-28
Try the true OSS on your old box.

Howto is here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Fantastic performance!

You do not need to be a sound master to understand the difference.

---

### Post by ENatanael on 2009-06-28
> **igorzwx said:**
> Try the true OSS on your old box.

Howto is here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Fantastic performance!

You do not need to be a sound master to understand the difference.

That's some quite interesting information. Will OSS 4 work with Ardour, JACK and Rosegarden? (Maybe a stupid question, but I'm new to Linux audio)

However, not buying a new computer is not an option.

[QUOTE=trulan]Dual Core is good for audio processing. As far as external cards go, I am currently fighting with a Dell laptop to get firewire audio working (using a Presonus Firepod, works great on my desktop). There would have to be something better. So at the moment I can't recommend a Dell, but I'm just biased.

The firepod (or FP10) is a great interface if you want to record eight simultaneous tracks. If you don't need that many tracks, there are a lot of good USB sound cards out there. Of course, if you have plenty of money to spend, there are devices that will do a lot more than the firepod.

And as a general rule, a laptop will be a bit trickier to set up than a desktop.

Ubuntu Studio is good, I also hear good stuff about 64studio (fewer frills, better reliability).  I have yet to try it though.[/QUOTE]

That's too bad your Dell isn't working as it should. Dell was kind of my first choice... Dual Core it is. Eight simultaneous tracks feels like the maximum I could use, but maybe 4 or 5 would be sufficient. But Firewire is the way to go when recording sound?

---

### Post by igorzwx on 2009-06-28
Will OSS 4 work with Ardour, JACK and Rosegarden?

See:
[http://www.4front-tech.com/forum/index.php](http://www.4front-tech.com/forum/index.php)
[http://www.4front-tech.com/forum/viewforum.php?f=3&sid=b290041a32b3ef11b710479687fd2185](http://www.4front-tech.com/forum/viewforum.php?f=3&sid=b290041a32b3ef11b710479687fd2185)

---

### Post by markbuntu on 2009-06-30
There are some guys selling preconfigured linux audio production laptops. I wish I could remember their name......

---

### Post by trulan on 2009-07-02
FWIW, I have the Dell working now.  I am using Ubuntu Studio Hardy, and had to fiddle a bit to get Jack and ffado (the firewire driver) up to date.  Jaunty, unfortunately, was a no-go on the Dell.  So my attitude towards Dell has improved dramatically in the past two days.

This machine has a built-in firewire port (Ricoh chipset, supposed to be one of the worst) and it is now working like a charm.  If you want more than four channels I would recommend going with firewire.  I have no complaints with the firepod (now that Windows XP Media Center is in my rearview mirror) but there are a lot of good devices out there and ffado supports most of them.

---

### Post by Bartender on 2009-07-05
Make sure to get a laptop with eSATA port if you're going to run an external HDD for real-time editing

---

### Post by ENatanael on 2009-07-14
Thank you for your advices! I have now ordered a Dell Studio 1555.

---

