---
title: "Playing Halo Combat Evolved on Ubuntu"
date: 2009-11-23
forum: Wine
---

### Post by BMWFan11 on 2009-11-23
I'm trying to play Halo Combat Evolved Demo Version online, and am having trouble downloading Wine.

I read the forums already posted and tried to follow the instructions, but am getting the following error message:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

This is when I entered  *deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" in the *"Third Party Software" tab.

Need HELP!

---

### Post by BMWFan11 on 2009-11-23
why is nobody replying?? 
why does ubuntu suck so much??

---

### Post by hikaricore on 2009-11-23
> **BMWFan11 said:**
> why is nobody replying?? 
why does ubuntu suck so much??

I hope you don't expect an answer now...

---

### Post by BMWFan11 on 2009-11-23
yeah i shouldn't have expected an answer earlier too. 

I bet you too don't know how to fix the problem, just make comments..

funny how ppl overlook the problem sometimes..
 thanks anyways ..you've been a great help!

---

### Post by overdrank on 2009-11-23
> **BMWFan11 said:**
> yeah i shouldn't have expected an answer earlier too. 

I bet you too don't know how to fix the problem, just make comments..

funny how ppl overlook the problem sometimes..
 thanks anyways ..you've been a great help!

Maybe add the key
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
From [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
And please remember the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

---

### Post by jwbrase on 2009-11-23
You shouldn't need to use a third-party repository to get Wine. It's in the main repositories. Try typing "wine" into the search field in Synaptic. That should find it for you.

---

### Post by BMWFan11 on 2009-11-23
Thanks overdrank. I'll try to follow your instructions..
Sorry for the impoliteness earlier. I was just so frustrated!

Thanks jwbrase too..

---

### Post by BMWFan11 on 2009-11-24
Hello everyone,
I successfully installed Halo: Combat Evolved Demo Version on my Ubuntu 9.04 Jaunty Jackalope operating system. I'm currently using a Toshiba Satellite M115 S3094 Laptop. What I was having troubles with, was that when I try to run the game, I can only hear the sounds in the background, but the screen is black. 

I tried several ways including reading dozens and dozens of posts where I'm asked to install patches, and change flags (-vidmode, etc). I tried a lot of different flags, and tried to reinstall Halo on my laptop, as well as Wine. 

But nothing seems to work. The Wine application I'm currently using is Wine 1.1.33. 

Additional Miscellaneous Information:

I currently have these icons on my desktop to use:
a. Halotrialsetup.exe
b. Mfc42.zip (asked to download on a forum).

c. HaloTrial
d. HaloPC107.exe (asked to download patch through a forum).

The forum I used extensively to download and run Halo was this:

[http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)

Need help with this, please. Thanks.

---

### Post by BMWFan11 on 2009-11-24
Hi, I followed all the instructions, and there is a black screen where only the music will play, so in other words, the problem persists..

I have mentioned this problem in greater detaiil in another post. Here's the link:

[http://ubuntuforums.org/showthread.php?p=8378815#post8378815](http://ubuntuforums.org/showthread.php?p=8378815#post8378815)

---

### Post by hikaricore on 2009-11-24
Yea.. there was a reason your original post was moved.
Making a new post in the wrong forum isn't acceptable.

From the sound of it your problem is likely video card/driver related.
More info about your hardware is required.

---

### Post by cariboo on 2009-11-24
Please don't create multiple threads on the same topic. I have merged your two threads.

---

