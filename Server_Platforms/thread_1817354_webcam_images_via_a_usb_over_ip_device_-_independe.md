---
title: "webcam images via a usb over ip device - independent of any other pc"
date: 2011-08-03
forum: Server Platforms
---

### Post by StevoSn on 2011-08-03
Hey guys!

I don't really know if this is the right place to ask for that, but I am sure starting somewhere will lead to something.. :)

I would like to set up a camera that takes a couple of images of a room every day. I guess the best thing would be, if the camera was connected to a usb over IP device so that the images could be stored somewhere on a file server or similar and to make the acquisition independent of any pc that might be switched of, causing no images to be taken.
So the question is if it is possible to have some kind of small linux running on a usb stick or on the USB over IP device itself that runs a daemon or so that takes the pictures at certain times and saves them somewhere on a server..

Does anybody have an idea where I can start looking and reading?

Thanks for any help!

Cheers!
Stevo
:guitar:

---

### Post by Gyokuro on 2011-08-03
Maybe you can check ZoneMinder: [http://www.zoneminder.com/](http://www.zoneminder.com/)
(check this howto: 
[http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu](http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu))


or Motion: [http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

HTH

---

### Post by ian dobson on 2011-08-03
Hi,

Or maybe an old router with usb port. Just load openwrt, install the correct webcam module and then use Motion to grab pictures.

I've already done something like this with a "dead" siemens se505 router that I picked up for 1Euro, and after hacking the hardware abit, manually loading openwrt I got it up and running.

Maybe go over to [www.openwrt.org](www.openwrt.org) and have a look around.

Regards
Ian Dobson

---

### Post by StevoSn on 2011-08-04
Hey!
Thanks for the links! I'll check them out and see if I can find something. I quite like the router idea.. :o

Cheers!
Stevo

---

