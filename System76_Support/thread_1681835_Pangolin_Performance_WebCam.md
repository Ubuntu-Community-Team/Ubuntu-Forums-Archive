---
title: "Pangolin Performance WebCam"
date: 2011-02-04
forum: System76 Support
---

### Post by McTwitch on 2011-02-04
I bought the Pangolin Performance laptop right around Christmas time. It came preinstalled with 10.10, so I overwrote that with 10.04. Everything seems to be working rather well. The only problem that I have encountered is that the webcam won't work online, for Skype or Emesene. I don't have any programs that deal with the webcam, and I'm not sure if I installed any software that deals with it, either.

In short, how do I make it work?

---

### Post by Derath on 2011-02-05
Did you use the System76 Driver installation? There's a couple packages in that utility that installs the drivers for the webcam. The first thing I would do is download, install the utility, and then use the "Install Drivers" which should take care of you.

Hope this helps.

---

### Post by smarmytime on 2011-02-05
Curious - why did you downgrade Ubuntu?

---

### Post by McTwitch on 2011-02-05
> Did you use the System76 Driver installation? There's a couple packages  in that utility that installs the drivers for the webcam. The first  thing I would do is download, install the utility, and then use the  "Install Drivers" which should take care of you.

Hope this helps. 	

I'll get right on this, and get back with results...eventually.

>  		Curious - why did you downgrade Ubuntu? 	

10.04 is the first installation I had, back when I was booting off of a 320 Gig Portable Harddrive. It's what I was raised on. I prefer it over 10.10.

---

### Post by hasenj on 2011-02-07
I had the same problem .. it turned out it was disabled by default, you have to enable it with one of the function keys (in my case, Fn-F10).

---

### Post by McTwitch on 2011-02-07
Right, I feel like an idiot. I haven't been able to find the utility, but with my luck it's because I'm not looking in anywhere near the right places. I've tried keyboard shortcuts, including the fn+ the functions keys. Nothing. Any other ideas/where I should look to find the utility?

---

### Post by Derath on 2011-02-08
Here's the info for the driver utility:

[http://knowledge76.com/index.php/System76_Driver]("http://knowledge76.com/index.php/System76_Driver")

At the bottom of the page is a link for the repository, you can add that, or just click the link, find the 2.5.9 driver, download and install...

---

### Post by pafufta503 on 2011-02-09
> **hasenj said:**
> I had the same problem .. it turned out it was disabled by default, you have to enable it with one of the function keys (in my case, Fn-F10).lol!  I was having problems getting any programs to acknowledge my webcam.  Programs would say "cannot access webcam" I thought the drivers were corrupted, that something bad had happened.  Turns out it was a very simple fix indeed!  Next time I'll make sure there's not a magic button to fix my problems first.  : ) thanks

---

### Post by McTwitch on 2011-02-12
> Here's the info for the driver utility:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

At the bottom of the page is a link for the repository, you can add  that, or just click the link, find the 2.5.9 driver, download and  install... 	

Well, I did this, had the System 76 install the drivers, rebooted the system, and still nothing. When I try to access a program, it tells me that there is no webcam.

---

### Post by McTwitch on 2011-08-30
Right, I managed to get it to work. For the record, this is how:

I used Derath's idea, and installed the repositories, using the commands in this post: 
> Originally Posted by crichell  
For good measure run the following two commands in your terminal to add the System76 repository and System76 repository signing key:```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
``````
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

