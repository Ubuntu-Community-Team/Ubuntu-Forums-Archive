---
title: "The &quot;NET&quot; in netbook: 200gb of music/movies on my netbook's 8gb hard drive :D"
date: 2009-11-04
forum: The Cafe
---

### Post by earthpigg on 2009-11-04
well, not exactly stored there. but accessed via ssh and sshfs.

i don't know why i didn't think of this earlier.

type "rawr" in a terminal from anywhere my netbook is connected to the net. (add an alias line to .bashrc).

"magically," the netbook and it's 8gb hard drive now has a folder in /home containing 200gb of music and movies. 

(the music and movies are actually on my desktop, which must also be turned on and connected to the net.)


this is not revolutionary at all, and it isn't that hard... but i didn't really think about it before, so maybe i am not the only one who hasn't really put the ***net*** in netbook yet to the greatest extent possible??

the guide i followed: 
[http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)
[http://wiki.archlinux.org/index.php/SSH#Mounting_a_Remote_Filesystem_with_SSHFS](http://wiki.archlinux.org/index.php/SSH#Mounting_a_Remote_Filesystem_with_SSHFS)

(when following Arch Wiki documentation, we ignore all the stuff about Daemons. Ubuntu does that automatically. and we dont 'pacman bla bla', we 'sudo apt-get bla bla'.)


what have you done to put the ***net*** in netbook?

---

### Post by dragos240 on 2009-11-04
> **earthpigg said:**
> well, not exactly stored there. but accessed via ssh and sshfs.

i don't know why i didn't think of this earlier.

type "rawr" in a terminal from anywhere my netbook is connected to the net. (add an alias line to .bashrc).

"magically," the netbook and it's 8gb hard drive now has a folder in /home containing 200gb of music and movies. 

(the music and movies are actually on my desktop, which must also be turned on and connected to the net.)


this is not revolutionary at all, and it isn't that hard... but i didn't really think about it before, so maybe i am not the only one who hasn't really put the ***net*** in netbook yet to the greatest extent possible??

the guide i followed: 
[http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)
[http://wiki.archlinux.org/index.php/SSH#Mounting_a_Remote_Filesystem_with_SSHFS](http://wiki.archlinux.org/index.php/SSH#Mounting_a_Remote_Filesystem_with_SSHFS)

(when following Arch Wiki documentation, we ignore all the stuff about Daemons. Ubuntu does that automatically. and we dont 'pacman bla bla', we 'sudo apt-get bla bla'.)


what have you done to put the ***net*** in netbook?

I connect to the ***net***.

---

### Post by earthpigg on 2009-11-04
> **dragos240 said:**
> I connect to the ***net***.

you clever devil. :lolflag:

net can also stand for networking, not just internet!

---

### Post by dragos240 on 2009-11-04
> **earthpigg said:**
> you clever devil. :lolflag:

net can also stand for networking, not just internet!


Well, most of the time, I connect to the interwebs. And the samba server. So both.

---

### Post by Warpnow on 2009-11-05
Weren't dell minis sold with an online file locker at one point?

The really nice thing would be to use one of these $3 a month unlimited file hosts as a locker...maybe even for multiple people. :D

Then you wouldn't need to put any media on your hard drive, especially if your connection is fast enough to stream movies from the webspace to your computer.

---

### Post by SomeGuyDude on 2009-11-05
> **Warpnow said:**
> Weren't dell minis sold with an online file locker at one point?

The really nice thing would be to use one of these $3 a month unlimited file hosts as a locker...maybe even for multiple people. :D

Then you wouldn't need to put any media on your hard drive, especially if your connection is fast enough to stream movies from the webspace to your computer.

If Verizon would get off it's apple-pancake @sses and put FiOs in my area I'd love to do just that.

---

### Post by earthpigg on 2009-11-05
> Weren't dell minis sold with an online file locker at one point?

i think that required that you use Dell's rediculously horrible version of Ubuntu.

ya know, the one with repositories containing updates that bricked every Dell Mini 9 in early 2009. including mine.

---

### Post by Crunchy the Headcrab on 2009-11-05
> **SomeGuyDude said:**
> If Verizon would get off it's apple-pancake @sses and put FiOs in my area I'd love to do just that.

Haha, I feel the same way.

---

### Post by 00ber n00b on 2009-11-07
sub'd

---

### Post by The Funkbomb on 2009-11-07
I don't know enough about the security risks to even try this.

---

### Post by 3rdalbum on 2009-11-07
I often think "Hey, I should forward the Samba port on my router so I can access my server remotely" and then I think "OMG, someone's gonna get into it and delete all my files!".

I'm especially worried about SSH, as that really does give terminal access; I'd be worried about getting rooted. I'm chicken. But it would be useful to have that sort of pervasive access.

---

### Post by steev182 on 2009-11-07
There's a way of making it so you can only connect using a psk, 2 stage authentication (key and passphrase) should protect you nicely.

---

### Post by pookiebear on 2009-11-07
Or you could ww-DRT your router and set up a VPN with a key and passwords/radius. Then you are a secure as 99.9% of businesses out there.

---

### Post by earthpigg on 2009-11-10
just got back from test running this setup from 5,000 km away.

update time.

streaming music and general system administration was perfect.

streaming movies, however, was not so successful.

some quick imperfect math, in retrospect, tells me why:
assume a 700mb video file that is two hours long.

700,000,000 / 120 / 60 = 97,222. [COLOR="Red"]*****[/COLOR]

the math would be even more disappointing if we used a full DVD-quality video in the >2gb range. [COLOR="Red"]******[/COLOR]

for streaming that video directly, my server's ISP would need to provide greater than roughly 97 kb/s upstream ***sustained*** on the obscure port i happened to choose. which it does not. (observe as i look at AT&T with suspicious eyes regarding traffic throttling on non-"standard" ports.)

if i wanted to watch a movie later in the afternoon, i would have to drag+drop copy it over at lunch time to give it time.

[COLOR="Red"]*****[/COLOR] yes, i know 1mb is not the same as 1,000,000b. for our purposes, it is close enough.

**[COLOR="Red"]**[/COLOR]** legally backed up according to fair use laws, of course, just like the example of the 700mb video above. as i understand it, this would be illegal and/or more difficult to do with BluRay for a variety of [ridiculous]("http://en.wikipedia.org/wiki/Digital_rights_management") [reasons]("http://en.wikipedia.org/wiki/Dmca") that should be discussed in [other threads and/or venues]("http://www.google.com/search?&q=DRM+DMCA+Free+Software").

---

### Post by Warpnow on 2009-11-10
Residential connections tend to have poor upload. That's why I'd use one of the cheap web hosts that has SSH enabled for this task. Also would save you $$$ on hard drives.

---

