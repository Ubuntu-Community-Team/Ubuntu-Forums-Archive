---
title: "Ubuntu GNOME &quot;Gnome3-next PPA&quot;"
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-09-10
This is fairly important so I'll post the full content of the message I received here:

> Since there were a few pieces of gnome 3.8 that didnt make it into Saucy, for the 13.10 cycle gnome3 PPA will reserved for 3.8 components
only. As such we have created a new Gnome3-next PPA, this will contain the GNOME 3.10 bits that we consider stable. Gnome3-staging will continue
on as usual holding the 3.10 bits that arent entirely ready just yet. Right now its a little empty, however it will start to fill up over the
next week or two!

It is important to note, that if you are using gnome3-staging PPA, then you must add gnome3-next PPA as this will contain required dependencies
for the staging ppa.

So we now have three PPA's to take into consideration!

Edit; link added:

[https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000669.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000669.html)

---

### Post by Stinger on 2013-09-10
Makes good sense to have this ppa since the GNOME3 ppa still is going to be used for GNOME 3.8, but also harder to maintain.
Seems that Tim is now pulling the heavy load on UbuntuGNOME.
Almost all Saucy packages in the ppa's has been uploaded by Tim with a few from Rico also.
It's a pity that Ubuntu GNOME can't use the current GNOME 3.10 for their release, I think to many resources are used to maintain and debug two GNOME versions instead of just the current.

---

### Post by SurfaceUnits on 2013-09-16
The current state of the repo is whack. It will uninstall gnome and other stuff.

--The Iceweasel

---

### Post by zika on 2013-09-17
> **SurfaceUnits said:**
> The current state of the repo is whack. It will uninstall gnome and other stuff.

--The Iceweasel
That is the beauty of testing...
Just read [http://ubuntuforums.org/showthread.php?t=2097359&p=12791170#post12791170](http://ubuntuforums.org/showthread.php?t=2097359&p=12791170#post12791170) ...

---

### Post by kansasnoob on 2013-09-19
Tim sent an important message at the mailing list:

> Hi All,

The gnome3-next PPA is now ready for standalone use. Right now you will find the release candidate of gnome-shell 3.10, but more will be added in the coming weeks.

If you are using gnome3-staging PPA you ****must** also add gnome3-next PPA**, since it will provide required dependencies which I will be deleting from staging very soon!

Tim


[https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000742.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000742.html)

---

### Post by zika on 2013-09-19
Who is responsible for gnome-control-center-unity... ;P ?
It's been (a)waiting for ages...

Update&#8321;: No, it is not true... Trouble was with rolling (devel) repositories...
[http://ubuntuforums.org/showthread.php?t=2174436&p=12794015#post12794015](http://ubuntuforums.org/showthread.php?t=2174436&p=12794015#post12794015)

---

### Post by amjjawad on 2013-09-20
Much easier and better for everyone either to subscribe to the mailing list or join the social media channels:

[https://wiki.ubuntu.com/UbuntuGNOME/ContactUs](https://wiki.ubuntu.com/UbuntuGNOME/ContactUs)

All updates, news, etc can be found there. 

I make sure to update all the channels whenever there is something important but thanks for sharing this here anyway :)

P.S.
Now, even the website is being updated ;)

---

