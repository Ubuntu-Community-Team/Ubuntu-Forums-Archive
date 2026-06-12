---
title: "Using Cheese as security camera"
date: 2011-08-15
forum: The Cafe
---

### Post by kostageas on 2011-08-15
I was at the library today and when I had to run to the restroom, I set up Cheese to take 100 photos, two seconds apart.  I put this in full screen and left it running.  The second time I did this, I come back to find Cheese closed, and none of the photos saved.  I know this isn't normal, because it worked in the first time.  

I'm assuming a person with knowledge of Linux/ubuntu/cheese did this, but I could be wrong.  To be a little bit safer is it possible to have the pictures automatically saved at the moment they were taken (to my dropbox folder, which would automatically sync in the cloud just in case someone decided to snatch my whole laptop)? 

If there's a better idea, please let me know.

---

### Post by szymon_g on 2011-08-15
how someone managed to close that app and delete photos through your locked session?

---

### Post by kostageas on 2011-08-15
I didn't lock it.  I just left it wide open so everyone could see they were being recorded so they wouldn't be tempted...

---

### Post by v1ad on 2011-08-15
The guy that did it is probably laughing his *** off now.

---

### Post by LowSky on 2011-08-15
there is a program called motion

[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)

---

### Post by szymon_g on 2011-08-15
> **kostageas said:**
> I didn't lock it.  I just left it wide open so everyone could see they were being recorded so they wouldn't be tempted...

....

---

### Post by sffvba[e0rt on 2011-08-15
So setting up cheese in this fashion seemed safer and quicker than locking your session... :confused:


404

---

### Post by Thewhistlingwind on 2011-08-15
> **kostageas said:**
> I didn't lock it.  I just left it wide open so everyone could see they were being recorded so they wouldn't be tempted...

There are SO many things wrong with this. To start:

> **not found said:**
> So setting up cheese in this fashion seemed safer and quicker than locking your session... :confused:


404

If you were worried about someone jacking your terminal window (doubt it, but its good habit anyway.) you should have locked screen.

If you were worried about someone taking the laptop itself, I don't see how a recording stored ON the hard drive of the COMPUTER THEY JUST STOLE is going to be at all a deterrent

And lastly, leaving it wide open advertises it's presence, making it more tempting to steal..

---

### Post by cgroza on 2011-08-15
Why don't you put it in your bag and take it with you? It's a lot safer, and maybe this will spare you of the surprise you will get when you will see your that laptop is no longer there.

---

### Post by kostageas on 2011-08-17
> **cgroza said:**
> Why don't you put it in your bag and take it with you? It's a lot safer, and maybe this will spare you of the surprise you will get when you will see your that laptop is no longer there.

Because that takes work to unplug it, put the cords and mouse away, put it away, and take my backpack.  Much easier just to leave it :popcorn:

---

### Post by Paddy Landau on 2011-08-17
> **Thewhistlingwind said:**
> There are SO many things wrong with this...
Also, recording other people without their permission in a public library. Maybe that's why the other person shut it down -- he was offended!

---

### Post by aeiah on 2011-08-17
if someone set up their laptop to record me and then walked off id probably be annoyed enough to do more than just close cheese down and delete the photos.

---

### Post by Inodoro Pereyra on 2011-08-17
> **aeiah said:**
> if someone set up their laptop to record me and then walked off id probably be annoyed enough to do more than just close cheese down and delete the photos.

+1
If someone did that to me, when they came back they would've found a cop right besides the laptop, handcuffs ready.

---

### Post by Eiji Takanaka on 2011-08-17
Here follows a potential security solution for surveillance cameras. Use a linux based box with no external interfaces, essentially if possible a router, with a security camera video feed connected via an ssh tunnel, then an ssh tunnel uplink to a secure server of your choice. Streaming the video and saving it on the remote server. Routinely encrypt the data on the remote server with aes 512 encryption, say every 12 hours. This could be done by executing some sort of shell script located on the remote server. You would need some sort of temporary place to store the stream until the data could be dumped into the encrypted partition, i suppose actually encrypting the partition of the disk housing the 'archives' would be the way forward, dumping the 'live stream' every 6 or 7 hours and decrypting/recrypting as necessary. That way nothing is stored locally, at all, and that which is temporarily unsecure is on a remote server (Proxy-chain optional), which could be based in the country/ or region of your choosing. Actually you could do the decrypt/recrypt process more regularly to prevent local files from being unprotected for substantial periods of time, the lower the temporary 'holding period' the better. 1 minute or less would be most desirable.     With the right tools,knowledge and resources this method could be circumvented, but it would i feel, greatly increase the average level of security for those wishing to protect stuff in general.     That being said a balaclava and a can of spray paint would possibly be the easiest circumvention method ;). But it would prevent local corner shop owners e.t.c by not having their security camera harddrives stored locally.     Fairly simple to pull off as well.

---

### Post by speedwell68 on 2011-08-17
> **Paddy Landau said:**
> Also, recording other people without their permission in a public library. Maybe that's why the other person shut it down -- he was offended!

You don't require anyone's permission to photograph or film them in a public place under UK law.

---

### Post by TriBlox6432 on 2011-08-18
> **speedwell68 said:**
> You don't require anyone's permission to photograph or film them in a public place under UK law.

I'm in the US, and it's even more unrestricted here.  You can do whatever the hell you want, but someone might sock you in the face.  :p

---

