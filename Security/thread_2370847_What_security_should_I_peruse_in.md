---
title: "What security should I peruse in?"
date: 2017-09-08
forum: Security
---

### Post by 1jarwolf on 2017-09-08
I am relatively new to Linux in general. I have mostly used Windows all my life however I sold my gaming laptop and my Windows machine crashed, I got another copy of Windows 10 from a non trusting community and it was really slow from the get-go. God knows if there was a RAT or a rootkit installed beforehand. 

   Anyhow... I wanted to ask what security measures I should take for my Ubuntu MATE OS in which is running on a raspberry pi 3. I wanted to try to install a IDS (Intrusion detection system?) called SNORT. I learned minor stuff about this last year in my cyber security class but I wish they would teach me about Linux.... there is way too much stuff to configure and or install so I wish to come back to this community and ask if there is anything I can install such as antivirus or anti malware or IDS/IPS programs/software I can get to help my linux system be more secure. I have heard Linux is a lot more secure than Windows and Mac. Anything with an IP or that connects to something else in any way, shape or form can be messed with or hacked into. 

P>S: I also have a small camera attached to a ribbon that can be inserted into my pi. Is there a way I can EASILY install a program to let's say, motion detect my room for when I am at work? I heard something about motion eye but I've tried that a while ago and well....I didn't get so far.

Additional question: What is the most secure browser that I should use that has cookies, java and whatnot disabled by default. I am thinking *White Hat Security* as they have a browser called _***Aviator***_. Any other suggestions?

---

### Post by Bucky Ball on 2017-09-08
> **1jarwolf said:**
> P>S: I also have a small camera attached to a ribbon that can be inserted into my pi. Is there a way I can EASILY install a program to let's say, motion detect my room for when I am at work? I heard something about motion eye but I've tried that a while ago and well....I didn't get so far.

Can't help with your security questions, but can help by bumping the thread to mention that you will probably have better success solving your camera issues by editing that stuff out of this thread and posting it in a new one. Won't get much attention nuzzled in here unrelated and one question per thread a general policy on UForums. ;)

Good luck with it and enjoy Ubuntu and the RPi.

---

### Post by Habitual on 2017-09-08
[Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812")
and possibly also [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

Found this Keeper today!
```
apt install harden-doc
```
Browser File menu > Open File > /usr/share/doc/harden-doc/html/securing-debian-howto/index.en.html

YMMV for Pi environs.

---

### Post by HermanAB on 2017-09-09
On Win10, you can start with a program called Shutup10.  There are several similar things.

On Linux, you don't need special security software.  A default install is secure.  Simply stop any insecure services - or better - don't install random junk that you know nothing about in the first place.

For camera - try two programs called motion and zoneminder.

---

### Post by 1jarwolf on 2017-09-10
@HermanAB, How do I use the zoneminder after installing it? I do know I have to have the camera correctly attached to my raspberry pi in which I do. I wanted to ask on here however, I am also searching Youtube videos as well for instructions on how to use it after installment.

---

