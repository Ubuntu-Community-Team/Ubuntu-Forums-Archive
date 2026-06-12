---
title: "wine wont install from .deb package"
date: 2009-03-21
forum: Wine
---

### Post by mjnaik2 on 2009-03-21
im trying to install wine on a spare pc which i recently installed ubuntu, it is not connected to the internet as i need the belkin driver and belkin only makes windows drivers so i thought maybe wine could run it. since that computer isn't connected to the internet, i downloaded a ".deb" file to install from a usb. but it wont install. it gives me an error saying:
Depandancy is not satisfyable binfmt -support

where can i get binfmt -support without using internet from that pc? is there a ".deb" file for binfmt -support? i also have many problems using tarballs so if possible, no tarballs please.

i have done a basic search in google for this file  but i havent found anything

And also, can you tell me another way to get my wireless belkin g to run without the driver?

all help is appreciated

(p.s if it also helps, im running ubuntu 7.10 on the spare machine and if this internet gets working, ill update to 9.04 when it comes out :) )

---

### Post by mjnaik2 on 2009-03-22
its been 12 freakin hours!!!! i was told i would get answers in minutes.... "sigh"...and i actually believed... :-|

---

### Post by NightMKoder on 2009-03-22
[http://packages.ubuntu.com/intrepid/binfmt-support](http://packages.ubuntu.com/intrepid/binfmt-support)

But you can't use wine to install windows drivers.

What you're looking for is ndiswrapper. It lets you run windows wifi drivers on Linux (ONLY WIFI!):

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Look at section 2.2

---

### Post by hikaricore on 2009-03-22
In the future please wait 24-48 hours before bumping your own thread.

Remember the people on this forum are normal folk just like you who volunteer their time to help.

---

### Post by mjnaik2 on 2009-03-22
thanks alot! that really helped. the only problem is, that after installing it, i dont know where the installed file is...strange...

---

### Post by NightMKoder on 2009-03-22
I'm not quite sure what you're expecting... are we even talking about wine or ndiswrapper?

wine lets you RUN windows applications on linux. You won't actually see it until you start some kind of windows application (or wine configuration).

As for ndiswrapper, check section 3.4 on how to install the driver.

---

