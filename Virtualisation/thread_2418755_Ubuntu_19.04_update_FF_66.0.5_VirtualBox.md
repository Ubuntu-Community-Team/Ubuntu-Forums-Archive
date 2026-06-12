---
title: "Ubuntu 19.04 update FF 66.0.5 VirtualBox"
date: 2019-05-10
forum: Virtualisation
---

### Post by moahiah51n32 on 2019-05-10
Hello forum community,
I'm a newbie and just started with Ubuntu 19.04 running in VirtualBox.

My problem is I upgraded FF 66.0.3 to FF 66.0.4 but I cannot update FF to the latest version which is 66.0.5.
What in the world am I doing wrong? Need help with the command prompt in Terminal.
This was my last command and everything worked like a charm to upgrade FF to 66.0.4.
Whats the trick to go to FF 66.0.5? My command is below:

> sudo apt update && sudo apt dist-upgrade

Cheers,
moahiah51n32 :)

---

### Post by wildmanne39 on 2019-05-10
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by QIII on 2019-05-10
With Ubuntu, package versions of software are fixed at the time of each Ubuntu release and don't get version updates -- only security updates.

FF is an unusual package.  All FF updates are considered security updates, so unlike most packages, new versions FF are made available in the repos across the supported releases of Ubuntu.  

However, it does take some time to package and test a new software release, so such updates are not often available immediately when the vendor releases them.

66.0.5 was released by Mozilla on May 7, 2019.  Here in the US, where FF is developed, it is May 10.  Give it a few more days before you panic.

---

### Post by moahiah51n32 on 2019-05-10
Thank you very much [**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533"). I told you I was newbie.. LOL
I missed that sub forum, my bad.):P

> **QIII said:**
> With Ubuntu, package versions of software are fixed at the time of each Ubuntu release and don't get version updates -- only security updates.

FF is an unusual package.  All FF updates are considered security updates, so unlike most packages, new versions FF are made available in the repos across the supported releases of Ubuntu.  

However, it does take some time to package and test a new software release, so such updates are not often available immediately when the vendor releases them.

66.0.5 was released by Mozilla on May 7, 2019.  Here in the US, where FF is developed, it is May 10.  Give it a few more days before you panic.

Oh okie dokie so my command was right then. That's great news for a newbie like me and I thank very much for the very prompt and quick reply.

Many thanks to you QIII. I will sit back and eat some :popcorn: now.

Cheers,
moahiah51n32

---

### Post by VMC on 2019-05-10
Or you could download the zip file and replace "/usr/lib/firefox" with 66.0.5. Then link to the new firefox:
[https://www.techspot.com/downloads/19-mozilla-firefox.html](https://www.techspot.com/downloads/19-mozilla-firefox.html)

---

### Post by QIII on 2019-05-10
It should be noted, however, that doing it that way -- which will work -- may cause problems with the normal update process later.  You might be left having to do the update manually each time from there on out.

My opinion and recommendation for a new user:  Let the update come through the normal repo updates to avoid difficulties.

---

### Post by VMC on 2019-05-11
Right after I posted, then I remember he did mention he was new user. 

For the OP, is there a reason you need to use the latest issue of Firefox?
Some were reporting the uBlock wasn't working or was blocked. I have 66.0.4 and uBlock works fine.

---

### Post by moahiah51n32 on 2019-05-11
Well well, now I know why there's no update yet because I'm running Firefox and not Firefox Quantum. Did a little checking behind the scenes in Software and seen what I had.
Everything makes since now and I'm sorry if I through off anyone that was trying to help me but I know exactly what to do if I want to change to Quantum which has the version I was looking for the fixes the Master Password issue.

I have to admit I'm loving **[COLOR=#B22222]Ubuntu[/COLOR]** bundles... :guitar:

> **VMC said:**
> Right after I posted, then I remember he did mention he was new user. 

For the OP, is there a reason you need to use the latest issue of Firefox?
Some were reporting the uBlock wasn't working or was blocked. I have 66.0.4 and uBlock works fine.
Yes, VMC I'm also running uBlock in advanced mode and everything works very well here. Advanced mode gives you so many more options that you can save for any url.
Ohhhhhh yeah!! :biggrin:

---

### Post by moahiah51n32 on 2019-05-11
Well I was wrong I'm running Quantum version 66.0.4 and Ublock is working fine.
So I will wait until they release the new version of FF.

---

### Post by moahiah51n32 on 2019-05-12
> **VMC said:**
> Right after I posted, then I remember he did mention he was new user. 

For the OP, is there a reason you need to use the latest issue of Firefox?
Some were reporting the uBlock wasn't working or was blocked. I have 66.0.4 and uBlock works fine.

Yes, VMC you would not have any issues with FF 66.0.4 which fixed the certificate but if you had Master Password enabled then there would still be a problem. FF 66.0.5 fixes that issue. Also for anyone that is interested you can google uBlock and run in advanced mode which I highly recommend. You will find it on YouTube.

---

### Post by moahiah51n32 on 2019-05-13
Cool Beans just got the FF 66.0.5 update, :guitar:

---

### Post by oldfred on 2019-05-13
Removed screen shot per user request. User can do it, in advanced mode and paperclip icon. Click on x on attached screen shot.

Please do not attach screen shots of terminal output, but just copy & paste terminal output. Then it also can be user edited.

Also please do not PM moderators or admins. the report issue icon is for any issue, not just spam, so just report post and explain issue.

---

### Post by moahiah51n32 on 2019-05-13
> **oldfred said:**
> Removed screen shot per user request. User can do it, in advanced mode and paperclip icon. Click on x on attached screen shot.

Please do not attach screen shots of terminal output, but just copy & paste terminal output. Then it also can be user edited.

Also please do not PM moderators or admins. the report issue icon is for any issue, not just spam, so just report post and explain issue.
I'm very sorry. I went into advanced mode but the edit screen was so small I couldn't see what I was doing.:(
All is understood now. I apologize.

---

