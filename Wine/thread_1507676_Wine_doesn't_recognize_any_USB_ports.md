---
title: "Wine doesn't recognize any USB ports"
date: 2010-06-11
forum: Wine
---

### Post by Gwilki on 2010-06-11
I have a gateway laptop with ubuntu 10.04 installed but in wine none of the USB ports are recognized. Any ideas?? I've scoured the Internet but haven't found anything related to the subject

---

### Post by hikaricore on 2010-06-11
You should probably mention what program you're trying to use... if it's itunes or something you're SOL.

---

### Post by Gwilki on 2010-06-12
Haha ya got me lol but I'm trying to have it see any USB port/USB stick at all. I have iTunes 9.1.1 installed and it functions perfectly but I don't know how to make the USB ports visible to wine. I can connect my iPod to my laptop and right click on the icon and tell it to run with iTunes but iTunes only imports all the music without showing the iPod in iTunes. I also tried to have wine recognize any USB stick but nothing happened. I've scoured the forums and google to find anyone that has had any luck but I cant find anything relative to my situation.

---

### Post by hikaricore on 2010-06-13
There should be no problem with usb support in wine, however I think you may be expecting things to happen that won't without your intervention.
For wine to be able to "see" things like flash drives and such you'll have to map a virtual drive to their mount point at the very least.
And since wine can only access things that are accessable via linux, anything that you can't access outside of it (without serious tinkering) such as the iphone won't work at all.

---

### Post by Gwilki on 2010-06-13
ok thanks for your help :D i'll mess around with it some more but i'll probably have to keep windows :( i kinda messed up some of the files so its not working now but ill fix that. hopefully something will come through with wine caus that will help me get rid of windows!!

---

### Post by edounn on 2011-02-10
Hey, I was having this discussion over at macrumors...  it's probably better suited for over here.  we have some grumpy faces over there.  :-)

I was thinking about how possible it would be to duplicate itunes.  with say, Rythem Box

**copied from macrumors 
[http://forums.macrumors.com/showthread.php?t=1092182&highlight=](http://forums.macrumors.com/showthread.php?t=1092182&highlight=)

i really meant duplicate, sort of like rythem box did, but with all the functions as itunes.

The only thing really missing is the store (hopefully just replacing store URL's etc), more specifically, being able to backup, and sync apps, calander, email, application document sharing. Music and video sync is really covered. I was thinking about it a little more, and it seems like it would be possible, but probably only with a jailbroken phone. Apt-get backup script through a music manager probably wouldn't be too bad, for sycning apps. Installing IPA's through a music manager seems possible if the connection was done thru, ssh over USB, and a script, similar to the instalous install script.

---

