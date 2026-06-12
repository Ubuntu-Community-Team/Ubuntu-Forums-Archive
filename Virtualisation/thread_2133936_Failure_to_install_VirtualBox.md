---
title: "Failure to install VirtualBox"
date: 2013-04-09
forum: Virtualisation
---

### Post by ToraxOutlaw on 2013-04-09
After many hours of googling, installs, uninstalls and raging, I still have failed to install VirtualBox despite many suggestions and solutions. I still keep getting the same error repeatedly. It still keeps telling me that I don't have Linux Kernel Headers but according to Synaptic I have the latest version of Linux Kernel and I keep getting the same error log.

---

### Post by koecse on 2013-04-09
hi

Did you try this tutorial?
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-12.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-12.04-server)

cheerio

---

### Post by QIII on 2013-04-09
Hello!

You didn't specify your Linux version, but judging from the description of your problem I suspect you are running 12.10.

If so, then

```
sudo apt-get install linux-headers-generic
```

will get you the headers you are looking for.

Also, it is worth it to make sure you have the build-essential package

```
sudo apt-get install build-essential
```

Best wishes!


QIII

---

### Post by ToraxOutlaw on 2013-04-09
@koesce
That tutorial doesn't help me at all.

@QIII
Those command just tell me that I have the latest version.

---

### Post by ibjsb4 on 2013-04-09
What about dkms?

```
sudo apt-get install dkms
```

Did you install from the vBox site or the software center?

A bit more detail of what you have done/tried would be helpful :)

---

### Post by ToraxOutlaw on 2013-04-09
DKMS is the newest version. I tried the software centre version and the virtualbox.org version. Any other suggestions that I could try?

---

### Post by ToraxOutlaw on 2013-04-09
It says 3.4.0 when I use the command 'uname -r' and I have the latest linux-generic-headers which are 3.5. Are the errors I'm that I'm getting in relation to the fact that in my src folder there isn't a 3.4.0 labeled directory?

---

### Post by ibjsb4 on 2013-04-09
Yep, thats the problem.  Kernel and header need to be the same version.

---

### Post by ToraxOutlaw on 2013-04-09
So how do I fix this? Any suggestions for that?

Edit: After a yet again another quick google, after the revelation of my posts, I came across the answer and a download. Here's the link if anyone else has this issue (the solution is in post #4).
[http://ubuntuforums.org/showthread.php?t=2128334](http://ubuntuforums.org/showthread.php?t=2128334)

---

### Post by ibjsb4 on 2013-04-09
Congratulations :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ToraxOutlaw on 2013-04-09
How do I fix the no audio issue in VirtualBox. I have an Acer C7 and I can't seem to get the audio to work.

---

### Post by ibjsb4 on 2013-04-09
> **ToraxOutlaw said:**
> How do I fix the no audio issue in VirtualBox. I have an Acer C7 and I can't seem to get the audio to work.

Machine>Settings ?

[ATTACH=CONFIG]241169[/ATTACH]

[http://www.virtualbox.org/manual/ch03.html#settings-audio](http://www.virtualbox.org/manual/ch03.html#settings-audio)

---

