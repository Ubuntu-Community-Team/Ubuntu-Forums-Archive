---
title: "Music app not detecting SD card content after Phone Update:OTA-7"
date: 2015-10-20
forum: Ubuntu Phone and Tablet
---

### Post by tafari2 on 2015-10-20
After the most recent update my SD card content is no longer detected by the Music app, able to browse the media fine using File Manager app as previously, Has anyone else experienced this?

actually to be more accurate it appears the device is connected and detected fine but possibly my content has been wiped since the music app no longer detects my media... will double check if my data is still present

---

### Post by sudodus on 2015-10-20
Welcome to the Ubuntu Forums :-)

Where is the card no longer detected? In the phone or in Ubuntu or both?

If Ubuntu, which version of Ubuntu? Please post the output of the following command, when the card is connected in the computer:

```
sudo lsblk -fm
```

(Enter the password when you are prompted for it. There is no echo to the terminal window, but you use your usual user password anyway.)

---

### Post by coffeecat on 2015-10-20
No problem here with my BQ Aquaris E5 with yesterday's OTA update, but I do have one suggestion. Test the Micro-SD card in another device. It could have failed co-incidentally at the time of the upgrade. A couple of weeks ago I was experiencing odd glitches with the Music app and the camera, and wondered if I had encountered a bug. It turned out that the micro-SD card had failed, and my glitches were cured by putting a new one in.

The faulty card was only a couple of months old and of a reputable make. They do fail, and sometimes quickly.

---

### Post by tafari2 on 2015-10-20
Thanks all, used the file manager app and noticed all data still present so will investigate further why my music app is not currently able to scan the device...

Hi, forgot to reply directly to your post but posted an update on this issue, i think the more accurate heading for this forum would be Music app not detecting SD card content post update... that's currently the stage i'm at which isn't a major problem right now but potentially a bigger problem if more people experience it. I just happened to notice since using the music player is one of the main uses for my smartphone.

---

### Post by sudodus on 2015-10-20
If you edit the first post in this thread (Edit Post), and select **Go Advanced** (the big red button), I think you can edit the title :-)

That will change the title of the thread, the first post and all posts that are created after that. Come back if you cannot edit it, and I can edit it for you.

---

### Post by Cortbssguitar on 2015-10-22
I'm also infected by this bug. I can't listen to any song since the OTA7 upgrade :/
The SD card is ok, and I can access any file with the file-manager.

---

### Post by howefield on 2015-10-22
Stupid question, but have you checked the scope sources to make sure "*Display results from My Music*" is still selected ?

---

### Post by tafari2 on 2015-10-22
Would altering the scope sources be applicable when we are using the Music core app? However i no longer see that option listed in my scope sources...

btw the PhoenixPlayer app picks up my music from the SD card fine so definitely an issue with the Music app on the latest OS version...

---

### Post by howefield on 2015-10-22
> **tafari2 said:**
> Would altering the scope sources be applicable when we are using the Music core app? However i no longer see that option listed in my scope sources...

Not necessarily but interesting that it isn't available as an option.

> btw the PhoenixPlayer app picks up my music from the SD card fine so definitely an issue with the Music app on the latest OS version...

I suggest filing a bug, (if this [bug]("https://bugs.launchpad.net/music-app/+bug/1505807") sounds similar, mark it as affects me too, if not start a new one..

---

### Post by tafari2 on 2015-10-22
Thanks for the bug page link, i will raise a new one since that bug is slightly different (referring to Music in local folder) rather than SD card.

---

### Post by tafari2 on 2015-10-22
For anyone wishing to track the latest updates on the bug here's the link [https://bugs.launchpad.net/music-app/+bug/1508873](https://bugs.launchpad.net/music-app/+bug/1508873)

---

### Post by toinelorieau on 2015-10-22
Hi everyone!!!

I'm experiencing exactly the same problem as described: the Music app can't find the music contained in my 16Gb SD Card since the last OTA-7 update, whereas all my pictures and videos are "viewed" in my photo library app...
I've checked the SD Card and it works perfectly.
I'll try the PhoenixPlayer app meanwhile the bug is fixed, but I'm really looking forward to use again the cool Music core app!!!!!!

Antoine

---

### Post by howefield on 2015-10-22
> **toinelorieau said:**
> I'm experiencing exactly the same problem as described: the Music app can't find the music contained in my 16Gb SD Card since the last OTA-7 update...

Please mark the bug report that tafari2 kindly created as affecting you as well.

---

### Post by toinelorieau on 2015-10-22
Just did it.
:wink:

---

### Post by tafari2 on 2015-11-19
Latest OTA-8 update has resolved this problem, thanks all!

---

