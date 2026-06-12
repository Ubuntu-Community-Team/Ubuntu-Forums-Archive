---
title: "Has anyone got Camfrog working in Wine yet?"
date: 2009-04-25
forum: Wine
---

### Post by mingtien on 2009-04-25
Yes, that old chestnut again :)

I've looked in the database, and there are a few people who seem to have camfrog working on Hardy Heron, but there is no indication of what they did to get it working.  Various Internet searches have revealed one person who said it worked, and another who 'isn't telling.' 

Has anyone gotten this to work, and if so, could you please let us know how you managed it?

Thanks ever so much!

---

### Post by asdfoo on 2009-04-26
> **mingtien said:**
> Yes, that old chestnut again :)

I've looked in the database, and there are a few people who seem to have camfrog working on Hardy Heron, but there is no indication of what they did to get it working.  Various Internet searches have revealed one person who said it worked, and another who 'isn't telling.' 

Has anyone gotten this to work, and if so, could you please let us know how you managed it?

Thanks ever so much!

Why don't you tell us what goes wrong when you try it... and which Wine version you are using.

---

### Post by mingtien on 2009-04-26
Yes, of course (my brain must have been switched off!):

Wine version is 1.0.1, and I've tried all of the emulations (Vista, XP, 2000, etc.).

The behaviour is the same all the other posts that Google finds (most are fairly old): Installation works fine, as does applying for an account.  After starting.  You can see a list of available rooms, but if you try to enter one, Camfrog crashes (window vanishes).

The only suspicious line in the logs: if I tail -f /var/log/messages, I get the following as soon as camfrog is opened (buriram is the hostname):

Apr 26 16:27:14 buriram kernel: [ 9047.811638] Too big adjustment 32
Apr 26 16:27:14 buriram kernel: [ 9047.859560] Too big adjustment 32


Anyone's shared experience of how they got camfrog running would be most appreciated.  Clues on where to look would also be very well-received :)

---

### Post by asdfoo on 2009-04-26
> **mingtien said:**
> Yes, of course (my brain must have been switched off!):

Wine version is 1.0.1, and I've tried all of the emulations (Vista, XP, 2000, etc.).

The behaviour is the same all the other posts that Google finds (most are fairly old): Installation works fine, as does applying for an account.  After starting.  You can see a list of available rooms, but if you try to enter one, Camfrog crashes (window vanishes).

The only suspicious line in the logs: if I tail -f /var/log/messages, I get the following as soon as camfrog is opened (buriram is the hostname):

Apr 26 16:27:14 buriram kernel: [ 9047.811638] Too big adjustment 32
Apr 26 16:27:14 buriram kernel: [ 9047.859560] Too big adjustment 32


Anyone's shared experience of how they got camfrog running would be most appreciated.  Clues on where to look would also be very well-received :)

I'm not sure what the state of support for webcams and the like is... but you could try using a newer release of Wine, 1.0.1 was released 6+ months ago, visit [http://winehq.org/download](http://winehq.org/download) to find a newer testing release.

---

### Post by mingtien on 2009-04-27
Hmm... I should not have assumed that just because Jaunty is new, it would have the latest Wine.  I downloaded 1.1.20, and Gecko today.

Camfrog behaviour is roughly the same, except that one gets an error dialogue box after the crash.  I'm hoping to find some workaround before being forced by my better half to put Windows back on the other partition... 

(I roasted the Windows partition to install Jaunty, and am currently keeping Intrepid during the testing period.  I would prefer to keep that other partition as a testing partition, rather than waste it on Windows)

---

### Post by lappo on 2010-03-16
Hi , 

Yes i get work camfrog on wine i use ubuntu 9.10 , but without any webcam support  and no accessibility to the room ....only private message to other user. But in virtual machine work fine , i found a micro xp edition is perfert ( microxp 0.82) combination..

---

### Post by christa40 on 2010-07-06
i have camfrog working too in wine. i downloaded the latest version of camfrog . when ubuntu suggested the program to open it with i choose......use other program. search for wine in the list . wine will unpack and install it. i think i have wine for starters. i can enter chatrooms en i have cam aswel. but i can not open other cams because when i do i get an report and the program shuts down. btw i use ubuntu

---

