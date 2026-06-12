---
title: "My sound problems. (Not Drivers)"
date: 2008-03-04
forum: System76 Support
---

### Post by Royal_Pwner on 2008-03-04
I had a wrong alsa version. Thanks everyone.

---

### Post by superprash2003 on 2008-03-05
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by thomasaaron on 2008-03-05
Royal_Pwner,

It's always a good idea to say which computer model you have. It enables us to do in-house testing if necessary. All System76 models do not have the same options in the sound control GUI or the same ALSA version installed. You should also say if you are using Ubuntu or Kubuntu.

So, to get started:
1. Run your system76 driver and reboot. Did that help?
2. Double-click your speaker icon. In the resulting window, go to Edit > Prefs. Select all checkboxes. Do you now see speakers, mics, etc...?

---

### Post by Royal_Pwner on 2008-03-05
I'm using a serp3. I've run the system76 driver and rebooted, but still nothing.
The speakers and headphones aren't even detected in alsa or oss, so I can't select them.

Do you think that they aren't connected somehow so it's a hardware problem?

---

### Post by thomasaaron on 2008-03-05
If your speakers EVER worked, there is almost no chance that they are now disconnected. I would say that there is a very good chance that there is a configuration issue here.

You didn't say if you tried this:
> 2. Double-click your speaker icon. In the resulting window, go to Edit > Prefs. Select all checkboxes. Do you now see speakers, mics, etc...?

If not, please try it.

You also did not answer this:
> You should also say if you are using Ubuntu or Kubuntu.
Are you using Ubuntu?

Is there a speaker icon in the upper right of your screen? If so, double click it. In the resulting window, please take screenshots of each of the tabs, so we can have a look at your settings. (Applications > Accessories > Take Screenshots).

Also, please post the output of this command:
```
cat /proc/asound/version
```

Please answer all questions thoroughly. Otherwise it is very difficult to analytically approach the problem.

---

### Post by Royal_Pwner on 2008-03-05
It worked at one point when I got the computer, it worked on 8.04 alpha, but it doesn't now.
I use ubuntu.
I've got an FL90.

output of that command:
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Mar  4 2008 for kernel 2.6.22-14-generic (SMP).

---

### Post by thomasaaron on 2008-03-05
OK. Well, you have the wrong ALSA version installed. It should have:
ALSA 1.0.15rc3 

Try running the **system76 driver** one more time. Run the "Restore" function just for good measure. You will then need to** reboot** your computer. If sound does not work after rebooting, please send me an email at (support(at)system76(dot)com), and I will provide you with instructions for removing the current version of ALSA and getting the new one in place.

---

### Post by Royal_Pwner on 2008-03-05
I did that. Still nothing.

---

