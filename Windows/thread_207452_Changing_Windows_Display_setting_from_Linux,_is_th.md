---
title: "Changing Windows Display setting from Linux, is this possible?"
date: 2006-07-01
forum: Windows
---

### Post by Dewmeister on 2006-07-01
Hi, this is what I want to do:

I want to boot a linux live CD on a computer, and from there, mount my windows partition, and find the system file that stores display settings(screen resolution to be specific), and manually change the file so that when I boot windows, It will take on that resolution.

Basically, I guess I'm asking what system file stores that information for windows, and if it can be edited in this way from linux

I know this sounds kind of weird, but my work computer is locked at 800x600 and I feel like I am going to die of some kind of 'bad resolution' disease. I don't really know what that would be, but I'm sure it is fatal.

Thanks for reading!
~Ryan

---

### Post by adwait on 2006-07-01
If Windows is stuck on 800 x 600, if you force it to increase the resolution it will give you wierd results. You need to install the correct graphic drivers whcih will allow you to change the resolution from the Display Settings.

---

### Post by thingy on 2006-07-02
Hi Dew,

I suggest that instead of trying to figure out how to change the display settings yourself, you let a program do it.

Here's a free one:

[http://www.softpedia.com/get/System/OS-Enhancements/Resolution-Changer.shtml](http://www.softpedia.com/get/System/OS-Enhancements/Resolution-Changer.shtml)

Basically, add a shortcut to a batchfile in your Programs\Startup menu and in the batch file call this resolution changing util with params set to what res/depth you want. Now in linux, you simply need to mount the NTFS partition, and modify the batch file to choose a different res when you want to boot into windows with a different res.

regards

jin

---

