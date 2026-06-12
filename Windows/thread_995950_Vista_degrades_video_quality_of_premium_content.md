---
title: "Vista degrades video quality of premium content?"
date: 2008-11-28
forum: Windows
---

### Post by sdowney717 on 2008-11-28
13. Vista Content protection only helps Big Media: A computer scientist in New Zealand found that Vista intentionally degrades the picture quality of premium content when played on most computer monitors. Microsoft wants you to see that content on TV or bigger, pricier displays.

[http://www.magicjacksupport.com/13-reasons-why-i-will-stay-away-from-vista-a-long-as-i-can-t2284.html?highlight=linux](http://www.magicjacksupport.com/13-reasons-why-i-will-stay-away-from-vista-a-long-as-i-can-t2284.html?highlight=linux)

So is this truly real?

---

### Post by oldos2er on 2008-11-28
What is "premium content"?

---

### Post by Yownanymous on 2008-11-28
Wouldn't surprise me. Micro$oft are evil and, at risk of being infracted, I'm beginning to think that they might well be the Nazis of computing.
----------------
Now playing: [Pink Floyd - Echoes](http://www.foxytunes.com/artist/pink+floyd/track/echoes)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by L815 on 2008-11-28
This either doesn't affect me, or is just an outrageous claim. I've played HD videos which would most likely fit under "premium content *w/e that is*" and the quality is in no way degraded.

Or (after not reading the article) is this just affecting users who use WMP?


This would make sense if you were on a laptop using the battery.

---

### Post by zmjjmz on 2008-11-30
> **L815 said:**
> This either doesn't affect me, or is just an outrageous claim. I've played HD videos which would most likely fit under "premium content *w/e that is*" and the quality is in no way degraded.

Or (after not reading the article) is this just affecting users who use WMP?


This would make sense if you were on a laptop using the battery.

Probably a WMP thing, I imagine other players have something to bypass it.
It is true though, there have been more than one accounts of this happening (it happens with the latest MacBooks too)

---

### Post by L815 on 2008-11-30
That's horrible news :/ One of the reasons I play with Windows more often is because of the poor intel video drivers (video tearing :/) for Linux.

---

### Post by K.Mandla on 2008-11-30
Moved to Windows discussions.

---

### Post by doas777 on 2008-11-30
yes it is real. the things you should look up are HDCP, Protected Media Path, and SecurePath. they are new gen anti piracy technologies designed to make sure that you can't capture digital HD content (720p and higher) either in software, or with external hardware.

Theres an old adage. "if you can see it, you can pirate it". that is because monitors are dumb devices, and just take analog input and reproduce it. that means that the stream coming out of your vidcard is susceptible to analog capture, by any device placed inline. 

HDCP relies on intelligent monitors (your new HDMI connectable TV for instance) to be able to decrypt HDCP content, so that everything is encrypted until the exact second that your TV draws the output, meaning that unless you hack your TV, there is no point that you can access the stream while it is unencrypted.

Securepath and Protected media path, are technologies in your OS (possibly aided by your motherboard) that keep the signal encrypted as it passes throught your PC hardware and the kernel. it listens for any sign of a driver or other piece of software from intercepting the stream. this is part of the reason for the signed driver model. 

so to sum up, if you play premium content (HD video) on your HDDVD player, and all your drivers are signed, and you use an HDCP compliant vid card/mobo, and you have an HDMI TV, with no analog or DVI connections anywhere, then you can play protected content, as long as a twitch on the system bus doesn't activate a downgrade via PMP. 

if you have 1 unsigned driver, or a peice of somewhat unstable software, or a process debugger, or have any analog/old digital connections, then you get downgraded to 480p (DVD quality).

I'm also told that Vista refuses to copy files that contain HD content. can't attest to that just yet, but it might explain why it takes so long to copy files.

[http://www.eff.org/deeplinks/2005/07/protected-media-path-component-revocation-windows-driver-lockdown](http://www.eff.org/deeplinks/2005/07/protected-media-path-component-revocation-windows-driver-lockdown)

[http://www.microsoft.com/whdc/device/media/output_protect.mspx](http://www.microsoft.com/whdc/device/media/output_protect.mspx)

[http://msdn.microsoft.com/en-us/library/aa376846(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa376846(VS.85).aspx)


have fun

---

### Post by Betsybuntu on 2008-11-30
> **doas777 said:**
> yes it is real. the things you should look up are HDCP, Protected Media Path, and SecurePath. they are new gen anti piracy technologies designed to make sure that you can't capture digital HD content (720p and higher) either in software, or with external hardware...

Good Post, doas777. This is hardly news as HDCP has been circulating for some time, lol @ this "scientist in New Zealand." Looks like he was out of the loop. Another lol @ Yownanymous, too.

---

