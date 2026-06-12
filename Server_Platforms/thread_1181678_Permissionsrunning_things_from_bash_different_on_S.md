---
title: "Permissions/running things from bash different on Server 8.10 from Ubuntu?"
date: 2009-06-08
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-06-08
Hi, I recently have been having problems running Twonky Media Server on an Ubuntu Server 8.10 installation. I previously ran Twonky on Intrepid desktop without any issues at all. I think the problem may lie in how Server handles security differently from Ubuntu, but that is just a guess, so hopefully someone can help me.

I explained what was happening in [this post in the General Help forum]("http://ubuntuforums.org/showthread.php?t=1181606"). The main point is that whenever I try to run the twonkymedia .sh file or run the twonkymedia (start) file it tells me that there is "no such file or directory." I changed the permissions to be 777 to ensure there was no permissions problem, and tried using both a fully qualified path (i.e. /home/nixie/.twonkymedia/twonkymedia) and ./twonkymedia, but none of it works, it keeps telling me it does not exist, even though it does.

Is there a difference in security between Ubuntu and Ubuntu Server that would prevent me from running the script and/or startup files from Twonky when I normally would be able to with Ubuntu desktop?

Thanks!

---

