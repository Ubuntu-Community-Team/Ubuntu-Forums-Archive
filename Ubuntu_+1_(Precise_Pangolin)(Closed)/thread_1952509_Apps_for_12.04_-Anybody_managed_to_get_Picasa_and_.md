---
title: "Apps for 12.04 -Anybody managed to get Picasa and Clementine installed"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quarkrad on 2012-04-04
Anybody managed to get Picasa and Clementine (music player) installed on 12.04?

---

### Post by philinux on 2012-04-04
Moved to testing forum.

---

### Post by Perfect Storm on 2012-04-04
You mean by PPA or manual install?
Which error do you get?

---

### Post by Elfy on 2012-04-04
Had clementine installed - you have to change the source list though to reflect oneiric instead of precise if you use a PPA.
I believe it is in the repos.

dev version - Version 1.0.1-341-gb271dc4 works here.

---

### Post by SeijiSensei on 2012-04-04
My copy of clementine came from the repos.  I'm using Kubuntu 12.04b2, and my clementine version is 1.0.1+dfsg-1ubuntu2.

---

### Post by oldos2er on 2012-04-04
I have v1.0.1 of Clementine installed.

---

### Post by cariboo on 2012-04-04
Picasa may not install because of dependencies that are no longer available, or are hard linked that aren't used by Ubuntu. The app installs it's own version of wine, that isn't compatible with Precise, so far.

---

### Post by x-shaney-x on 2012-04-04
I installed Picasa (from installer) into 12.04 via Wine in the repos and it did work to an extent but Google login wouldn't work.

I have had Clementine installed from the repos and it works fine, though the menus aren't integrated into the global menubar like they were in Oneiric.

---

### Post by oldfred on 2012-04-04
I installed wine and then installed the Windows version of Picasa 3.9 currently and it seems to work. 

I have not fully tested it. I do not log into Google so I cannot test that. On my new SSD it found all the photos on my rotating drive very fast.

---

### Post by BigCityCat on 2012-04-04
Just installed Clementine with the software center. It works great.

---

### Post by x-shaney-x on 2012-04-05
> **oldfred said:**
> I installed wine and then installed the Windows version of Picasa 3.9 currently and it seems to work. 

I have not fully tested it. I do not log into Google so I cannot test that. 
I have since read that it is possible to sign in just by having Internet Explorer also installed into Wine because Picasa uses IE's auth process or something.
Unfortunately, when I tried installing IE, Wine told me 64-bit isn't supported for IE.

---

### Post by Quarkrad on 2012-04-07
Thank you all - got it all working.  At first I was using beta 1 - changed to beta 2 and there was no problem.

---

