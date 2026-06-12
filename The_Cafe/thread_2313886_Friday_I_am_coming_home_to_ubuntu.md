---
title: "Friday I am coming home to ubuntu"
date: 2016-02-16
forum: The Cafe
---

### Post by drascus on 2016-02-16
Hey all,

It's been a while since I have been on here. I switched to chromeOS for a while. But my system76 laptop arrives Friday. I am coming home to Ubuntu as I cannot stand chrome any longer.

---

### Post by TheFu on 2016-02-16
Gotta ask - why not just load Linux onto the chromebook?  I have 2 chromebooks here running Linux. Many reasons for this.  Basically, I got a 3lb ultrabook for $400!

And welcome back.

---

### Post by zircon_34 on 2016-02-16
> **drascus said:**
> Hey all,

It's been a while since I have been on here. I switched to chromeOS for a while. But my system76 laptop arrives Friday. I am coming home to Ubuntu as I cannot stand chrome any longer.

which one from system76 did you get?

---

### Post by drascus on 2016-02-16
I have an ARM chromebook so not really many options. I have been using crouton to tide me over. I got the Lemur from system76 because yeah I like a light weight system. I have been into open source and free software for a long time. I think at some point in my adult life I just got tired of administering systems because I do it for a living. But then that Free Software and Open Source neck beard fellow that sits on my shoulder sometimes started bugging me. I know Ubuntu isn't perfect being a mixture of FLOSS and proprietary software but it's about as far as I can go for my daily driver and keep my sanity. I wish it were different and that I could grow my neck bread long but I have other things to attend to at times other than compiling from source all day.

---

### Post by Linuxratty on 2016-02-25
> **drascus said:**
> Hey all,

It's been a while since I have been on here. I switched to chromeOS for a while. But my system76 laptop arrives Friday. I am coming home to Ubuntu as I cannot stand chrome any longer.
 I've never used it. I'm curious as to why you don't like it.

---

### Post by TheFu on 2016-02-25
> **Linuxratty said:**
> I've never used it. I'm curious as to why you don't like it.

ChromeOS can be fantastic for Grandma and kids and adults who are already inside the google ecosystem.  Automatic updates, all data on google's servers, can be great.  Plus, google has made it possible to edit documents when the internet isn't available.  I have 2 chromebooks - 8 hrs and 11 hrs of battery life are the published numbers.  Generally, I need about 5 hrs a day - which removes the need to take a power cord with me.  These are amazing devices, for cheap, provided you don't mind google "owning" everything you do online - EVERYTHING.  By "owning", I really mean knowing.

These days, it isn't THAT hard to be your own cloud provider.  For most people, they can run everything they need/want on a $50 raspberry pi, but a chromebook won't connect to that easily without someone creating a chrome-plugin (which means google gets to know about it too).

My reasons that ChromeOS isn't for me:
* no skype (or other non-web-based talking apps)
* no NFS client - this is a big deal ; storage access is limited to GVFS (very slow)
* anything that requires a kernel module is a huge hassle, if even possible. ChromeOS mounts the OS as read-only.
* Automatic ChromeOS updates break anything you've done outside the ChromeOS ecosystem, even crouton - it is a reload/refresh, then restore your data from backup (not always needed);  I run as "guest" login and have never connected with a google account. Privacy matters that much to me.
* Sucks you into the google-system for everything - email, bookmarks, surfing, chat, documents.  Did you want to share all of that with google?
* Crouton broke after unwanted, forced, chromeos updates.
* Google Tracking everything [http://www.foxnews.com/tech/2015/12/02/google-accused-invading-student-privacy-via-chromebook-computers.html](http://www.foxnews.com/tech/2015/12/02/google-accused-invading-student-privacy-via-chromebook-computers.html) ; since I run as guest, not all those settings can be disabled and they have to be disabled every reboot.
* poor external USB webcam support - any odd USB device probably won't work.
* Like USB audio microphone support - lsusb sees the microphone, but cannot access it
* Video production impossible - OSB
* complex 2FA for login to ChromeOS 
* "I own the hardware and should be able to run any OS I want" thing. Chromebook makers don't make this as easy as they could. I bricked the first chromebook last fall.  It requires about $80 in equipment to de-brick it - as I understand. Had already replaced the keyboard, then the LCD, so could have bought a refurbished version of that same chromebook.  The new chromebook is 1080p, 2x faster CPU and better battery.

Google's prime business is "ADVERTISING" ... why would you provide access to **all your internet activity** to the largest advertising company in the world? Why?  Think about that for a few minutes. If the data is stored somewhere, it will be free (or taken by a government).

BTW, I'm typing this on a Chromebook right now ... running Ubuntu Server with openbox as the WM. Because it is a laptop, the entire device is encrypted with 2FA required to access.  Do that with ChromeOS.

---

