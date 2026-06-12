---
title: "Wireless camera that does not require a smart phone"
date: 2022-12-07
forum: The Cafe
---

### Post by raleigh3 on 2022-12-07
I am looking for a wireless camera that does NOT require a smart phone and that can broadcast it's signal to a desktop computer.

I thought of using a desk cam, but would need a very long cable for use outdoors. (I could make the camera water-proof)

What do you think?

---

### Post by grahammechanical on 2022-12-07
I assume that you have already done what I have just been doing - searching the web. :)

 I find that the cameras are not cheap; they save to cloud storage that requires a paid for subscription. I did find one that with the addition of a module will save to a USB stick that can then be plugged into a computer. This is an extra expense and a complicated way of doing things when all you want is a straight forward connection by WiFi to transfer the images in a format that can be read by a Linux application.

I am not recommending this device. A smartphone my still be required.

[https://www.amazon.com/Blink-Outdoor-Wireless-Security-Camera/dp/B086DKSYTS?ref_=ast_sto_dp&th=1&psc=1](https://www.amazon.com/Blink-Outdoor-Wireless-Security-Camera/dp/B086DKSYTS?ref_=ast_sto_dp&th=1&psc=1)

> Store video clips and photos in the cloud with  the Blink Subscription Plan and save events locally to the Blink Sync  Module 2 via a USB flash drive (sold separately).  

> Save motion clips and photos from up to 10 Blink cameras connected to  the Blink Sync Module 2 locally in your home and view them through the  Blink app or the computer by plugging in a USB flash drive (sold  separately) for no additional fee. Learn more [here]("https://www.amazon.com/dp/B084RQ6MHJ").

Regards

---

### Post by zebra2 on 2022-12-08
I just use the cheapest IP cam with WIFI that I can fine (about $40) connected to the cheapest router that I can find, connected to the cheapest 10 inch tablet that I can find. I remove all apps from the tablet except google play and my Ipcam app.  Been using this for years now.  

Don't know how to get video on a linux pc though.

---

### Post by grahammechanical on 2022-12-08
another idea has entered my head.

An Internet of Things (IOT) device such as a Raspberry Pi + camera + Ubuntu Core. Here are some links.

[https://projects.raspberrypi.org/en/projects/getting-started-with-picamera](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera)

[https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core](https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core)

Ubuntu core is a secure OS. I would be more trusting of Ubuntu Core than I would the proprietary OS in a commercially available security CCTV camera. 

Regards

---

### Post by TheFu on 2022-12-08
So, my LUG has looked into this for years.
Different people needed different solutions, so we all ended up with different answers.

One guy needed to watch a few properties that he owns. He visits one monthly and the other just a few times yearly. Both were remote and didn't have internet connectivity, so most of his effort was in finding a router with cellular data that worked from each location.  He also wanted a central web interface that could be used by any modern browser to view live or saved video.  I think he spent just under $300 for the router/modem and IP-cam setup.  He went with more expensive outdoor cameras to deal with sub-freezing, snow, ice for one place and 120°F temperatures in the other location. 

Anther guy was given a few Raspberry Pi computers to monitor a group rental homes and decided to make that his base.  He bought a HAT with a 1080p pi-cam and built some custom scripts along with normal pi software to capture 30 seconds of video whenever their was motion detected.  The property owner wanted the cameras watching the houses, but didn't want them dependent on the power or internet provided by the house.  So, a battery system was created to last a few months and cellular data was used. I'm a little vague on the details. The setup included a cloud VPS with a login to view the streams from all 5-10 homes on a single page.  This was custom. The owner didn't want to use a 3rd party service.  The server was pulling the streams from each r-pi.  Each r-pi had a public internet address.  That was 3-5 yrs ago.  If I were doing it today, I'd setup a wireguard peer-to-peer VPN for all the devices.  2 of the r-pi system disappeared, BTW.  Seems the renters weren't happy.

Then there was me.  My need was very specific.  Cheap webcam to figure out which critters were in the attic so I could clear them out.  $22 and I got the highest rated, cheapo, cam made in China.  It phones home constantly and doesn't work when the internet is down.  Also, it only works using their phone app ... so more tracking.  I didn't do my research. I'd never heard of a wifi-cam that only worked with a phone app, no way to use a web browers or even VLC to grab the stream directly.  Sigh.  I'm stupid - AND I'm the product being sold.  OTOH, the night vision did capture this: 

[https://ubuntuforums.org/attachment.php?attachmentid=289300&d=1634496585](https://ubuntuforums.org/attachment.php?attachmentid=289300&d=1634496585)

Well, I can't see the Adv Reply buttons to add the photo in my album, so I'll try adding the code above.  The photo was from over a year ago. That's larger than a house cat.  He looked surprised and guilty.

---

### Post by #&amp;thj^% on 2022-12-08
> **TheFu said:**
> 

[https://ubuntuforums.org/attachment.php?attachmentid=289300&d=1634496585](https://ubuntuforums.org/attachment.php?attachmentid=289300&d=1634496585)

Well, I can't see the Adv Reply buttons to add the photo in my album, so I'll try adding the code above.  The photo was from over a year ago. That's larger than a house cat.  He looked surprised and guilty.

I get them here as well, I actually had one brush my leg in his escape route.

---

### Post by raleigh3 on 2022-12-08
Thanks, it has a monthly fee.

---

### Post by raleigh3 on 2022-12-08
I found this, but I am not sure if this is what cable I would need.

[https://tripplite.eaton.com/usb-c-active-extension-cable-usb-c-usb-a-10m-32-ft~U33010M1](https://tripplite.eaton.com/usb-c-active-extension-cable-usb-c-usb-a-10m-32-ft~U33010M1)

I have a usb 3.0 port on the front of my desktop and one in the back.

My plan would be to run the cable across the ceiling from my webcam to the front window.

I do not care how "tacky" it looks. :-)

I would aim the webcam from inside and avoid issues of weather, even though I have a covered porch.

---

### Post by TheFu on 2022-12-08
USB-over-ethernet is a thing if you'd like smaller cables and farther distances.  Think it works 100m. 

I've seen USB-over-ethernet that doesn't have any distance limitations too, but the bandwidth suffers. It is meant for keyboard and mice, not video. Mainly used for remote KVMs and suffering through doing remote installs over the painfully slow connection.

---

