---
title: "I'v done something wrong"
date: 2009-04-05
forum: Server Platforms
---

### Post by Lori700698 on 2009-04-05
Webmin and Citadel/webcit are apparently very closely tied together, I found out the hard way today when I deleted a citadel user which deleted the same user off webmin (which was my main log in) I fixed that but now webmin boots me off after less than 15 mins, I used to be able to stay logged in all day with no issues. And Citadel is acting up so bad with logging me out I can't even change rooms.  I'm still very new to this so I don't know were to look for these settings, can somebody please point me in the right direction.  Everything was working fine until I went to the new stable version of Citadel yesterday, the pkg'ed one that I used from apt-get last week was no problem at all.  I could kick myself for thinking I needed the newer one.  I need to fix the time out thing, I will remove all of Citadel (if I can find it) and be happy with the apt-get version!

Thanks for helping!
Lori

---

### Post by jamesrfla on 2009-04-06
Very odd what happened to you. I have Citadel mail server running with webmin and they don't seem to be interfering in any way. Try adding a new user on the server or just remove webmin and reinstall it.

---

### Post by Lori700698 on 2009-04-06
Well I've come to a couple of conclusions and narrowed my issues down to two possible culprits.

1. I know my lori ID was deleted from webmin when I deleted that ID out of Citadel. (had a back up webmin log in so I was good there)

2. Webmin seems ok now it's not booting me off so uninstalling Citadel/Webcit and re-installing helped (not sure why)

3. Citadel boots me out and then won't let me log back in without a reboot.  It's either the Funambol push causing the issue or the pop to get my outside mail from comcast.  It goes haywire when I get a new message and needs rebooted. 

If anybody knows of any known issues and fixes I'm all ears, in the mean time I'm going to test Citadel with each of these issues individually and see if I can pinpoint the problem and get it fixed.

Thanks All
Lori

---

### Post by hyper_ch on 2009-04-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

