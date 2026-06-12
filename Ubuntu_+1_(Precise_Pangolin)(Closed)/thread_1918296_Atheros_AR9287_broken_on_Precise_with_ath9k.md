---
title: "Atheros AR9287 broken on Precise with ath9k"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TBABill on 2012-01-31
Tried the daily build yesterday for Precise since the last one would not even run in the live environment. Ran fine for all hardware, but wireless is broken for the Atheros AR9287. Ath9k was enabled and it saw networks, but it cycled through the "connecting" then it just prompted for the password again over and over.

Same computer works fine for 11.10 and earlier so it's definitely a regression similar to what happened early with 11.10 in development and early release.

Just posting in case anyone else has the same device and wants to try 12.04 while in testing.

---

### Post by ventrical on 2012-01-31
I noticed an off and on bug with most wireless with Precise Alpha.  It will choose a random open connection (and not necessarily that one you put your WEP in for. Simply  right click the connections ICon , disconnect from wrong connection and then re-connect.

  I have an Atheros on an Acer Aspire  3620 .. I'll check it out ..

---

### Post by TBABill on 2012-01-31
Ok, will give it another shot. What I had tried was clicking my connection, entering WEP info, then waited. When it failed more than once I only clicked disconnect, then tried to connect again. Following that I restarted, but followed the same steps. 

May also try to connect to a wrong network with my WEP key, then when it fails try to connect to my network with same key. Worth a shot when it's borked, right? :)

---

### Post by ventrical on 2012-02-01
> **TBABill said:**
> Ok, will give it another shot. What I had tried was clicking my connection, entering WEP info, then waited. When it failed more than once I only clicked disconnect, then tried to connect again. Following that I restarted, but followed the same steps. 

May also try to connect to a wrong network with my WEP key, then when it fails try to connect to my network with same key. Worth a shot when it's borked, right? :)

A few times I just re-enetered my WEP and that worked also. It appeared on a few occasions that the WEP buffer had cleared after an update.

  You should also try to make  a new user account  in User Administration .. just as a back up.

---

### Post by odysseusjak on 2012-02-09
I continue to experience slow through put - so much so that at times it times out and I get a message stating that I need to check my internet connection. This is very frustrating. I don't understand how this works. Are there things that change in the kernel that make the driver not work properly between kernel versions? To me, it seems that if things are working, one would build on top of that. The last couple of releases have been this way concerning ath9k.

---

### Post by ventrical on 2012-02-09
> **odysseusjak said:**
> I continue to experience slow through put - so much so that at times it times out and I get a message stating that I need to check my internet connection. This is very frustrating. I don't understand how this works. Are there things that change in the kernel that make the driver not work properly between kernel versions? To me, it seems that if things are working, one would build on top of that. The last couple of releases have been this way concerning ath9k.

 For the most part these beta/alpha problems are capricious and I had the same discouraging results on my lap-top with Natty beta testing. However, after a while those driver problems were corrected.

   I have had problems with my 64bit AMD Acer Extensa with ATI graphics .. works great with Oneiric.. but not precise .. 32 bit only .. so .. certainly there are a lot of things being sorted out right now .. patience ?? :)

---

### Post by odysseusjak on 2012-02-09
Oh I do understand that part of it. I mean, there's still major work being done. We *are* still in Alpha 2 mode.

It's just the idea about something working flawlessly in one release, but somehow it gets broken in the next release. That's what I don't understand. Like I stated above, it seems that one would take what was working and build on top of that, in my mind anyway. That's why I questioned about the kernel, since I don't have a *clue* as to how the whole thing works.

---

### Post by ventrical on 2012-02-09
Agreed... My Dell OptiGX270 for instance, CCSM , graphics .. all worked great with Oneiric.. anims .. the whole 9 yards... now .. with Precise I cannot even get Brutal Chess to work..

  So there is a verisimilitude that certain  hardware is being obsoleted as the kernel is progressing to release date.. but I cannot authenticate that statement .. I am just making an assumption based on the present data before us .. which is certainly supportive of that.

  But on the other side of the coin it is most likely that I have the wrong video driver .. or that the wrong one was chosen at install (I have to remind myself that this is not Windows XP) :)  .so  more work for the end users..  :)

thanks

---

### Post by odysseusjak on 2012-02-09
Woo Hoo! It seems that the last kernel update that I just downloaded fixed my WLAN issue! How about anyone else?

---

### Post by dianlight on 2012-02-10
Hi,
 just my 2 cents....
On Precise also with the last kernel (  3.2.0-15-generic  x86_64)  on my netbook (Asus U30SD) the ath9k driver not work. ( Scan work but WPA association not,don't know for WEP or free ).
With the prev kernel ( 3.2.0-14-generic  x86_64) the ath9k association with WPA work but is very instable ( disconneccting every 10/15 sec)
With Oniric all work.

Lucio

---

### Post by odysseusjak on 2012-02-10
Okay, so, it's not *quite* right yet. Although it is better, I still get hang ups and sporadic through put every now and then (skipping in video/audio).

---

