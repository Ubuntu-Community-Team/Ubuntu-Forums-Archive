---
title: "Using a webcam for a security camera."
date: 2011-07-09
forum: Security
---

### Post by Syndicalist on 2011-07-09
Hello. I am trying to use a webcam as a serious camera for my office. 

Just setting it to record is no big deal. There are a few additional options I need that I do not know how to do.....

1. Viewing the stream remotely from a different computer, either from within the same router network, or via the internet.

2. The ability to stop or set recording from a non-local connection, or at least from another computer on the network....these are not "networked" computers yet, though I want to use Samba or other tools to share folders....High security is not required. If low security makes it easier to control the cameras non-locally, then thats the way to go. Nothing sensitive is on that computer and it wont be used for anything else that is work related.

3. I would like for a duplicate for the stream to download over the internet to a computer at my home, so that even if the computer or the webcam is destroyed, and that hard drive lost, I have all the records downloaded and installed to my home computer.

4....I have also wondered if I could do the same as .3 with an Android phone, but thats a later discussion.


Is this possible? Can anyone help me with this using the simplest method possible?

---

### Post by wacky_sung on 2011-07-09
There are always available webcam in the market with night vision , focus and watch online as well.Not sure if it is gonna work on linux.If you want it, be prepare it may take up lot of disk space if recording has been set.

---

### Post by haqking on 2011-07-09
> **Syndicalist said:**
> Hello. I am trying to use a webcam as a serious camera for my office. 

Just setting it to record is no big deal. There are a few additional options I need that I do not know how to do.....

1. Viewing the stream remotely from a different computer, either from within the same router network, or via the internet.

2. The ability to stop or set recording from a non-local connection, or at least from another computer on the network....these are not "networked" computers yet, though I want to use Samba or other tools to share folders....High security is not required. If low security makes it easier to control the cameras non-locally, then thats the way to go. Nothing sensitive is on that computer and it wont be used for anything else that is work related.

3. I would like for a duplicate for the stream to download over the internet to a computer at my home, so that even if the computer or the webcam is destroyed, and that hard drive lost, I have all the records downloaded and installed to my home computer.

4....I have also wondered if I could do the same as .3 with an Android phone, but thats a later discussion.


Is this possible? Can anyone help me with this using the simplest method possible?


Try Zoneminder

[http://www.zoneminder.com/](http://www.zoneminder.com/)

---

### Post by HermanAB on 2011-07-09
...or 'motion'.

---

### Post by haqking on 2011-07-09
> **HermanAB said:**
> ...or 'motion'.

im pretty sure from what i remember motion wont allow him to do everything he wants to do unless it has been improved.

I know you can do remote monitoring and the like but wasnt sure if you could control it remotely ?

---

### Post by Syndicalist on 2011-07-09
Awesome. Are there any tutorials for this? I have in the past run into some snags just using Samba for sharing Linux to Linux in different distros, when it theoretically should have worked. It was probably my own lack of knowledge, but it had worked previously when using the same distro.....I think one of them had unconventional folder/file system hierarchies. I remember you couldnt log into root using 'su root' only with 'sudo su root'. Relevant?

Anyway, lets assume they are all vanilla Ubuntu or maybe Mint.

Any tutorials for BASIC remote viewing of web cameras? 

Maybe I could combine programs and just make it streaming, uploading it to a server live without it being saved to the database, but recording it live as streaming on the other computer?

Tutorials are needed. Im still getting my feet wet.

---

### Post by conradin on 2011-07-09
webcamd and motion.
sends streams or shots to a server. 
tons of ways to get the job done. I recommend either having motion detection or sending 3 sec bursts to an FTP server like CCTV do in supermarkets. Saving on the computer the cam is attached to is useless in the event someone steals that computer. 

What sort of cam is it?

---

### Post by bichopro on 2011-07-09
Use also have remote administator, SD card and HDD record. You can save the videos on ubuntu one folder and will be save on the cloud. Excuse my bad english

[http://www.dlinkla.com/home/productos/producto.jsp?idp=1106](http://www.dlinkla.com/home/productos/producto.jsp?idp=1106)

---

### Post by Syndicalist on 2011-07-09
Thanks for the suggestions. 

This is a high end logitech pro camera. I forget the model number. It records in resolutions beyond what my fairly advanced hardware can manage.

---

### Post by cariboo on 2011-07-09
I was given a webcam and server comination similar to [this]("http://cgi.ebay.ca/ICAMView-IP-Server-Internet-Network-Camera-Webcam-PTZ-/260799402214?pt=PCA_Video_Conferencing_Webcams&hash=item3cb8db10e6"), except mine doesn't have wireless capabilities. The guy that gave it to me used it to successfully catch a burglar that broke into his house a couple of times. The device has it's own server built in, that can be accessed from any computer on the network

---

### Post by Paradoxfox93 on 2011-07-19
While you're at it a motion sensor and floodlight or whatever depending on how big an area your 'office' is. Wouldn't be too expensive an addition and can be used to obfuscate the presenece of the camera itself.

---

### Post by Cyked on 2011-07-20
How are you doing on this?  I've been running motion *fairly* smoothly at home with a Logitech C500 capturing both vid and pics (saves a pic every second WHEN there is motion detected).

---

### Post by wkulecz on 2011-07-20
Look into Zoneminder, its a bit of work to setup but I've been using it for six months or so.  Been very reliable.  Its webcam support may not be the best, but if your camera installs as a v4l2 device it should work.

I've tried and returned half a dozen commercial stand-alone solutions -- none are versatile enough for our flexible schedules.

It Emails video clips of detected motion to my wife and my work Email address and my gmail account so I can check it anywhere.

---

### Post by Paradoxfox93 on 2011-07-22
incidentally you should have it take pictures at intervals even when it doesn't detect motion.  Motion detector isn't infallable and being able to pinpoint time of occurance for any disturbance a 5 or 10 minute intervalled capture isn't significantly overcautious for the extra 20-50mb/day depending on your camera.

---

