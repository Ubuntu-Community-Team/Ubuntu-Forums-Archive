---
title: "Wireless in Starling (jaunty)"
date: 2009-06-30
forum: System76 Support
---

### Post by Ruthless on 2009-06-30
Hello, 

I opened up my brand new Starling netbook (with Jaunty) last night and, after twiddling around for a  bit, I found that I couldn't connect to the internet via wireless. Here is what happens:

I go to the Network Manager icon in the system tray and click the radio button next to the wireless network I desire (mmmk). The icon switches and it begins to try to connect. After several seconds, a notification appears informing me that I have been disconnected (without ever truly connecting!). 

So. Here's what I did next. 

I went to the terminal and entered the following:

```
netbook:~$ sudo iwconfig wlan0

            \wlan0         IEEE 802.11bg    ESSID: " "
```

Okay. Then I enter this.

```
netbook:~$ sudo iwconfig wlan0 essid mmk
```

I try the first response again and receive this as an answer

```
netbook:~$ sudo iwconfig wlan0

             \wlan0         IEEE 802.11bg    ESSID: "mmmk"
```

So, of course, I try to connect to the internet again. No go. Same thing happens again. 


I've already gone into my user account and set permissions so that this user can connect via wireless. I'm quite confused and would appreciate any help. Thank you all!

---

### Post by thomasaaron on 2009-06-30
How far are you from your access point? What happens if you get closer to the AP?

---

### Post by Georgesl on 2009-06-30
I am having a similar problem and I think that it relates to the computer being too picky about signal strength.

If I am right next to the wireless AP and the signal strength bar is maxed out my Starling will connect fine.  However, if I am a short distance (~15 feet) away it will list the AP, show a strong (75%+ of maximum) signal strength bar, but will not connect.  If I connect near the AP and then move away the connection is lost.

I have experienced this in two different public (unsecured) locations and at my own secured AP at home.  At both of the public locations (a college and a restaurant) people around me were connecting with no problems.  They had similar signal strength indications to mine.  At my home location my Dell laptop running XP will connect successfully at locations where my Starling will not, again with similar signal strength indications.
 
It seems to me that the Starling is being overly picky about the quality of the signal with which it will initiate or maintain a connection.  If the connection isn't 100% it flat doesn't connect.  Considering that this same problem has been mentioned on other hardware than the Starling it might well be a fault in the way that Jaunty deals with wireless connections.

This does not seem to be a unique problem to Ruthless and myself.  I've read similar symptoms in other posts here.  I hope that a fix will be found soon, because this problem renders my Starling pretty much useless for the purpose for which it is intended, mobile computing.

---

### Post by Ruthless on 2009-07-01
I'm not sure how far I'm from the AP at home (we steal it from the neighbors) but at work I can be sitting next to the AP and still not connect. 

Also, I'm using my Dell with Vista right now and using wireless just fine. I'm posting to [another thread]("http://ubuntuforums.org/showthread.php?p=7546822#post7546822") to see if they can help us.

---

### Post by Ruthless on 2009-07-01
It doesn't seem to matter where the AP is. I've been sitting next to one (with 100% signal) and still unable to connect. Regardless, it seems to me that I shouldn't have to worry about how weak the signal is .. as long as I can connect, shouldn't I be able to?


What about doing something with this:

```
iwconfig wlan0 sens ##
```
.... where ## stands for a numeric value

---

### Post by thomasaaron on 2009-07-01
Hi, Ruth.

I see you've sent me an email on this. I've responded to it, but didn't realize it was you. Most of my questions are answered above. Give me a call at support tomorrow.

---

### Post by Ruthless on 2009-07-01
Thanks!

---

### Post by Georgesl on 2009-07-01
Since my problem is weak wireless, not lack of wireless, I'll start a new thread.

---

### Post by Ruthless on 2009-07-05
I ended up finding a wireless connection that was at a steady 100%. I was able to connect for a few mintues and, when I did, I did two things immediately. I upgraded my system76 driver and I installed a new network manager (wicd). 

So far so good. If I have more problems, I'll probably post back here.

Thanks so  much for all the help. You guys are amazing.

---

### Post by zoso1969 on 2009-07-10
I am having the same problem with my Starling. It will connect to my router but will not transfer data when the signal strength is below 100%. I have updated my system 76 driver and installed wicd but I am still having this problem. Any suggestions?

Thanks

---

### Post by thomasaaron on 2009-07-10
How far are you from your access point? Does it transfer data if you are closer?

---

### Post by zoso1969 on 2009-07-10
I am about 30ft away from my access point. I noticed when I am downloading if the signal strength drops below 100% I will not have any data transfering. When I get closer and have a steady 100% signal stength I do not have this problem.

---

### Post by thomasaaron on 2009-07-10
See...

[http://ubuntuforums.org/showthread.php?t=1208842](http://ubuntuforums.org/showthread.php?t=1208842)

---

