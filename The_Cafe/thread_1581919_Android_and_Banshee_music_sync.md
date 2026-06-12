---
title: "Android and Banshee music sync"
date: 2010-09-25
forum: The Cafe
---

### Post by donniezazen on 2010-09-25
Have you guys had problem syncing music using Banshee. I have observed that Banshee either fails to transfer all the song or the music player in Android (DoubleTwist) fails to recognize the songs. My SD card has all the songs but they are just not recognized. I don't have to use sync feature but it's just easy to manage playlist and count.

It is sad that Android a linux build doesn't really play as nice with Linux Distro as iPhone with Mac.

Thanks.

PS:-
Fresh Rom on Evo 4G
Ubuntu Maverick on Dell 6400/E1505
DoubleTwist Music Player on Phone.
Banshee 1.7.6 on my Ubuntu Box.

---

### Post by gnomeuser on 2010-09-25
First it would be very helpful if you could try this with the new 1.8.0 release which we will be unleashing on the 29th of September. This is because we changed the hardware support entirely moving from HAL to udev, additionally we have solved a number of important issues surrounding synchronization and worked around a really nasty bug in one of the libraries we use which turned out to be the reason for a lot of our unexplained freezes.

Provided we still don't work for you please do follow the instructions on [www.banshee.fm/file-bugs](www.banshee.fm/file-bugs) and tell us, we will be happy to work on the issue. If you need help obtaining the required information you can stop by #banshee on irc.gimp.net and ask for help (please stick around a while, it can take a while for people to get back to you). I am dnielsen in that channel.

If you want early access to this code, please try the banshee daily ppa. The code is in late stages of development currently but even as a day to day Banshee experience it is very solid through out the cycle.

*edit*

(I should have been clearer, we fixed a lot of these bugs after 1.7.6, in fact some only just yesterday so please do upgrade, I promise it is a far more pleasing experience than 1.7.6 despite the short time in between the two releases)

---

### Post by donniezazen on 2010-09-26
There seems to be over 100% CPU usage problem with latest banshee. It seems to work without most of the plugins.

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/396268](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/396268)

I have added banshee daily ppa but i still have 1.7.6 and other thing unlike stable Banshee, the ppa banshee is just dumping all the files in my sdcard. They are not put in a music folder.

Thanks let me try to sync my EVO 4G.

---

### Post by gnomeuser on 2010-09-26
If you want your bug fixed, please do follow the instructions I gave above. The Banshee developers simply cannot keep an eye on every single distribution bugtracker, we center our workflow around the GNOME bugtracker and if it is not in there, it is likely we are unaware of it.

As for the 100% CPU load, the bugreport you linked mention a hodgepodge of Banshee versions which makes it very hard to track the specific issue down. There might be several bugs, some are likely to be SQLite related, some the ndesk-dbus and gio-sharp bugs which are respectively worked around and fixed upstream currently. (the gio-sharp fix really needs to go into Maverick, or every gio-sharp using app will leak memory).

If you want to narrow down the problem try using the --debug-sql parameter and look for long queries (above say.. 100ms). If you find that this reveals clearly repeated bad behavior please do file a bug (or file one anyways, we will do our finest to narrow down the issue by asking for feedback as required).

---

