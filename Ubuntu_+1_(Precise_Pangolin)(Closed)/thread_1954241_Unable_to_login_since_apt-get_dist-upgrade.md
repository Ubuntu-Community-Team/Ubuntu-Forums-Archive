---
title: "Unable to login since apt-get dist-upgrade"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DShad on 2012-04-07
Well I really need your help.

7 days ago I did the usual apt-get dist-upgrade but since then I'm not able to login.  Every time I try to login with my regular user, the screen refreshes and I'm back at login again.  If I attempt a 2nd try, I get a "Connecting..." under my username and nothing more.

The same happens with "Guest" account.

Need to say, it's not a password problem since I can log from the CTRL-ALT-F1 screen.

Tried to CTRL-ALT-F1 and do some more updates but no change.

Tried to dpkg-reconfigure gmd and select either gdm or lightdm but no change.

Tried Unity --reset, no change

Tried to remove (purge) nivida drivers, no change.

Please help!!

---

### Post by rburkartjo on 2012-04-07
try this it worked for me and anyway wont hurt anything. had a similar problem and it was due to a partial upgrade. open up a virtual terminal after you login and run this

sudo rm -rf /var/cache/apt/archives/partial

good luck

---

### Post by cariboo on 2012-04-07
This is kind of drastic, but if your are desperate to get logged in, try removing ~/.config.

---

### Post by DShad on 2012-04-07
> **rburkartjo said:**
> try this it worked for me and anyway wont hurt anything. had a similar problem and it was due to a partial upgrade. open up a virtual terminal after you login and run this

sudo rm -rf /var/cache/apt/archives/partial

good luck

Well no luck.  Problem remains.

I also tried  rm -rf ~/.config and still stuck at login screen.

And YES I am kinda desperate... :(

---

### Post by cariboo on 2012-04-08
Which session are you having a problem with? Have you tried logging into Untiy 2D?

---

### Post by DShad on 2012-04-08
> **cariboo907 said:**
> Which session are you having a problem with? Have you tried logging into Untiy 2D?

Ok this may sound stupid but I don't know how to select Unity2d.  I tried dpkg-reconfigure gdm but I only have lightdm or gdm.

Don't see Unity2d anywhere...

---

### Post by DShad on 2012-04-08
> **DShad said:**
> Ok this may sound stupid but I don't know how to select Unity2d.  I tried dpkg-reconfigure gdm but I only have lightdm or gdm.

Don't see Unity2d anywhere...

Ok so I managed to find the ppa and the install Unity-2d.  I'm now able to login using Unity-2d.  I didn't even had to choose between Unity and Unity-2d.  Could it be because for some reason myregular Unity is broken??

---

### Post by cariboo on 2012-04-08
Click on the cog wheel icon beside your name, on the lightdm login screen.

---

### Post by DShad on 2012-04-08
> **cariboo907 said:**
> Click on the cog wheel icon beside your name, on the lightdm login screen.

Thank you.  Now I can confirm:  Unity-2d is working for me but not Ubuntu (3d). 

I tried WITH and WITHOUT Nvidia drivers.  No difference.

Should I wait and see if future updates will fix the problem?

---

### Post by DShad on 2012-04-08
Ok so here is what I did.

I installed Unity-2d using ppa:unity-team/staging.

Unity-2d was working: good!

Then I tried the default Ubuntu again, and IT WORKS TOO!!

So dunno what was wrong, but now we can put this thread as SOLVED.

---

### Post by cariboo on 2012-04-08
It's great to see your problem is solved.

---

### Post by thelordvimes on 2012-04-08
I think there may be a problem with lightdm, if your in graphics fallback mode. Try sudo apt-get purge lightdm and sudo apt-get install gdm.

Sorry, missed the solved part :P

---

