---
title: "cannot install Citadel groupware"
date: 2008-04-05
forum: Server Platforms
---

### Post by TuckLive on 2008-04-05
When I try to install Citadel my server hangs on > sudo apt-get update  It will stop at 27%.  Then I tried > sudo wget -q -o - [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sh and I get nothing.

I checked my network settings and all is good.  I pinged the address my server was trying to update from and that worked so I have no idea what my problem could be.  Any help?

---

### Post by wthanna on 2008-04-05
I personally would recommend going here:

[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Follow the instructions for the Debian / Ubuntu install instead of using Easy Install.  Then your Citadel system will update just like the rest of your system when you apt-get, or aptitude, or use synaptic.  It works great.  Also, I would recommend you visit their support forum at:

[https://uncensored.citadel.org/](https://uncensored.citadel.org/)

There you will find the developers with knowledge of the inner workings of Citadel.  I have been using it for several months, and think you will be pleased with its performance and versatility.

---

### Post by TuckLive on 2008-04-05
Thanks, I'll give that a try.  Any reason as to why my server will not update though when I use sudo apt-get update?  It will start, but then it stops at 27% everytime.

---

### Post by wthanna on 2008-04-05
I'm not sure why your update is hanging.  If it is hanging while trying to access the Citadel repo, you may want to ask that over at their support site.  They have always been quite helpful.

---

### Post by mmichalik on 2008-04-05
I have previewed both Citadel and Zimbra as groupware solutions for our clients and have found Zimbra to be much more robust and modern.

If you can't get Citadel to install, I would suggest giving Zimbra a try.  It's very nice.

---

### Post by TuckLive on 2008-04-05
Found out eBox was causing my update to hang.  I did a fresh install and   tried the easy install again with success.  This is for home use so I didn't need anything fancy.

---

