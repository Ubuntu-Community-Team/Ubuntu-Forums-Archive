---
title: "Is it possible I am being hacked?"
date: 2009-02-15
forum: Security
---

### Post by Jimmy9pints on 2009-02-15
If I leave anyone of my 3 Ubuntu computers on over night, quite often the next morning they are super slow - especially with things related to the internet.

This is especially true it seems if I leave the computer downloading a bit torrent (for which I have forwarded a port on the router). 

To give you a typical example I left my wife's 64bit laptop on last night to download a new .iso file using downthemall. This morning, the computer is still on, but both the system and the internet connection (on other computers too) is REALLY slow. On her laptop, the mouse pointer is stuttering across the screen and windows are being grayed out constantly. What's more, the hard drive seems to constantly be accessed.  

Actually, this is the first time I have seen this on her computer, but I often see it on my other two computers.  

James.

---

### Post by x33a on 2009-02-15
check how much data you have downloaded during that duration, and compare it with your total internet usage for that period. if they differ by a huge amount, then someone might be using your internet connection. are you using wireless?

---

### Post by Gramps on 2009-02-15
Check the logs on your router

---

### Post by TuckLive on 2009-02-16
> **Jimmy9pints said:**
> On her laptop, the mouse pointer is stuttering across the screen and windows are being grayed out constantly. What's more, the hard drive seems to constantly be accessed.

Sounds like you just have an application using almost all of your RAM.  Check your Processes under System Status.

---

### Post by donkyhotay on 2009-02-17
Sounds more like a memory leak in your bittorrent client to me. I had this problem quite often with ktorrent before switching to another client a year or so ago. Definitely check your router logs but I'd also check the output of top and see how much RAM your client is using and compare that to how much RAM it uses when it first launches.

---

### Post by Jimmy9pints on 2009-02-17
Cheers everyone. 

I'll try to figure out how to read into my router logs. 

Another (potentially significant) symptom that I saw a couple of times is that when I logged out of my own computer (not my wife's this time) is a box that says that due the policy on this machine I cannot log out when there is more than one user logged in. That's strange, because I only have one user set up. I had to enter a password in order to log out.

---

### Post by styven on 2009-07-03
> **Jimmy9pints said:**
> Cheers everyone. 

I'll try to figure out how to read into my router logs. 

Another (potentially significant) symptom that I saw a couple of times is that when I logged out of my own computer (not my wife's this time) is a box that says that due the policy on this machine I cannot log out when there is more than one user logged in. That's strange, because I only have one user set up. I had to enter a password in order to log out.

I had this issue only recently, any ideas anyone?

---

### Post by Agent ME on 2009-07-03
What's the output of the "top" command while the computer is stuttering?

How much ram and swap space do you have?

What's the output of "free -m" command while the computer is stuttering?

---

### Post by Dave_Connor on 2009-07-03
If your looking for another torrent client then there is rtorrent which is great for use of restoring an rtorrent session in a terminal with ssh.

---

### Post by Himsagar on 2009-07-04
If you are using wifi, first check for the computers connected to it and the amount of data used.
If it is not then change your password to connect the internet, since some one also be using your connection with the password.
I think only these two possibilities exist.

---

### Post by meditatingfrog on 2009-10-01
It is probably unlikely you are being hacked.  You might want to check your syslog in /var/logs to see if there is anything suspicious in there.  Or maybe your authlog.  

Some thoughts on the hacking question, if you have a strong password (8 characters or more with both alpha numeric digits) you shouldn't need to worry.  The other thought I had was that if it was a hack, someone would have had to take over the system, because the system is actually running slow, not your network.  Does the system still run slow when you kill your torrent application (transmission I'm guessing).  Does it run slow if your system is left on and your torrent application isn't running?  

I've had leaving a torrent application downloading slow down the network, but I haven't had it slow down the entire system.  My guess is a problem in the torrent app.  Are you using ndiswrapper?

---

