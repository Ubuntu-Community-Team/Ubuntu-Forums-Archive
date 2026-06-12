---
title: "Daru2 - Status on various components?"
date: 2007-11-30
forum: System76 Support
---

### Post by imhavoc on 2007-11-30
I was wondering about the status of the some of the Daru2 components (as far as drivers are concerned).

 - HDMI port
 - card reader
 - battery/power status monitoring

Thanks!

---

### Post by agisfox on 2007-11-30
Card reader works with the SD card I tried it with.

---

### Post by palintheus on 2007-11-30
My card reader also works with SD cards.

Also any update on the fingerprint reader, or has that pushed to the backburner ;)

---

### Post by thomasaaron on 2007-11-30
The fingerprint reader is still being worked on. It is proving a bit tricky.

---

### Post by imhavoc on 2007-11-30
Is there something I have to install or run to activate the card reader?

When I insert an SD card, nothing happens.

(sorry about the double-post. I was having internet problems right then.)

also, I should have listed fingerprint reader in the original post. Thanks for hitting that one, palintheus.

---

### Post by palintheus on 2007-11-30
No, you shouldn't have to install anything. It was one of the first things I tested when I first installed Gutsy and it worked. 

No problem on the fingerprint reader, it is one of the things I am really looking forward to!

---

### Post by imhavoc on 2007-11-30
okay, so why isn't anything happening?

I've got Kubuntu 7.10 installed. I'm stumped.

In years past, I fiddled with Linux to get things to work. I've gotten spoiled in the last couple of months.

---

### Post by palintheus on 2007-11-30
Hmm had this feeling before, ](*,) but Im not sure where to start with Kubuntu or even if it would be any different than Ubuntu.

---

### Post by imhavoc on 2007-11-30
shouldn't be substantially different. Kubuntu is just Ubuntu wrapped in KDE.

Unless there's a Gnome app doing something that's not getting done in KDE?

---

### Post by palintheus on 2007-11-30
Ive seen cases where that is the case...

do you see any changes in your syslog when you insert the card?

---

### Post by imhavoc on 2007-12-02
i checked with another card, and it works great. I'm going to assume something strange is going on with the first card I tested it with... go figure.

---

### Post by imhavoc on 2007-12-02
Oh, yeah, the web cam..... I've never been able to get it to work. Cheese and ... another app I tried turned on the "on" indicator LED, but I've never managed to actually get anything out of the silly thing.

Just wondering.

Looking forward to the new, improved and pruned driver!

---

### Post by palintheus on 2007-12-02
Does cheese say it can't find a webcam? If so, hit the 'P2' button and restart the program, mine works with cheese

---

### Post by gamx on 2007-12-02
The cam so far works only with Ekiga. With Cheese (and I guess other programs that use gstreamer) it crashes. I have also tried to make it work with Skype 2 and no luck so far.
With respect to gstreamer. I type gstreamer-properties, click on the video tab and push the p2 button so that the cam is activated. When I push the button test on the Default Input with v4l2 as a plugin the program crashes and I get the message 

:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by palintheus on 2007-12-02
hmm, haven't rant into that issue. I just installed cheese from the repos and it worked :???:

---

### Post by gamx on 2007-12-02
I have fixed it!!!! It was a matter of changing the Default Output to X Window System...
Thanks again

---

### Post by palintheus on 2007-12-02
\o/ , always nice when its something easy, just hate it when the solution is obscure or you think you've tried everything

---

### Post by saxamo on 2007-12-04
An additional note for the darter camera. It works flawlessly with the latest version of skype (video support :) )

---

### Post by pavel_987 on 2007-12-05
Concerning the card reader: I'm not an expert on this by my hypothesis is that it only works with certain cards. Glancing over these forums I see that quite a few people were able to get the card reader working, but there are cases of the opposite as well.

Quite a while ago I purchased a Canon camera. The 32mb SD card that came with the camera is detected just fine and works well. The 1GB Kingston Card I bought for the camera isn't detected at all. (nothing in dmesg too)

Your comments appreciated :)

---

### Post by thomasaaron on 2007-12-05
At System 76, we've found that cards formatted with Palm devices often don't work. Ubuntu only recognizes certain formats.

---

### Post by pavel_987 on 2007-12-05
Doesn't it have to do more with the kernel driver? If ubuntu can't recognize the format, won't it still show up in dmesg?

Both cards are formatted with the same digital camera. One card shows up and mountable. The other doesn't show up, not in dmesg, not in gparted.

---

### Post by thomasaaron on 2007-12-06
Are you sure they are FORMATTED with the same camera? Or have they just been USED with the same camera?

The camera might recognize different formats as well, one of which is a format not recognized by Ubuntu.

If both work in the camera and only one works with the computer, there is probably some formatting issue.

---

### Post by pavel_987 on 2007-12-06
Yes, both SD cards have been formatted with the camera. Both regular and the "low level format" option. This is the kingston memory that I have: [http://www.amazon.com/Kingston-1GB-SecureDigital-SD-Package/dp/B00070QI1I](http://www.amazon.com/Kingston-1GB-SecureDigital-SD-Package/dp/B00070QI1I)

Please correct me if I'm wrong, but even if the format isn't recognized, shouldn't the card at least detected? Isn't "format" just a file system type? Wouldn't it be detected as "unrecognized format" in that case?

---

### Post by thomasaaron on 2007-12-06
I'm not sure if it would be detected or not. I would think so, but I do not have one with me today to test with.

I'll bring one in tomorrow and have a look.

---

