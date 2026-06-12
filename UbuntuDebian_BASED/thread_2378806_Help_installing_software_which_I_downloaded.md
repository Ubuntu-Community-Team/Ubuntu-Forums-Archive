---
title: "Help installing software which I downloaded"
date: 2017-11-27
forum: Ubuntu/Debian BASED
---

### Post by scollar on 2017-11-27
Hello and thanks in advance for helping me leave Windows behind ......

Relatively new to ubuntu one stepping stone I'm having a hard time grasping is software installation. Most of the time I have installed software via terminal 'sudo apt-get install' and I get this simple concept and the necessity of repositories so on and so forth. But I cannot seem to get the hang of installing software CLI with software which I have downloaded ...

Currently trying to install linux-wbfs-manager-0.1.12 I have downloaded the file 'tar.gz' which is compressed how the heck do I install?

---

### Post by Dennis N on 2017-11-27
Could you use the one in the Ubuntu repository?

package name: **qwbfsmanager**

---

### Post by howefield on 2017-11-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by yancek on 2017-11-27
You should be able to simply right click on the tar.gz file and select an option to 'extract' or 'extract here' and another folder with the same name (minus the tar.gz) should be created.  Look in that folder for a README or install file which should have instructions.  That's the standard.

---

### Post by scollar on 2017-11-27
I've tried that not happy with the program

The README has no installation information

Here is the README file 
```



This is yet another graphic WBFS manager for Linux.


It uses libwbfs from Kwiirk and caristat available at


  [http://github.com/kwiirk/wbfs/tree/master](http://github.com/kwiirk/wbfs/tree/master)




=== WARNINGS ===


This might eat all your partitions. I offer no warranty
whatsoever. Use at your own risk.




=== USAGE ===


You must have access to your raw block devices. On most systems, this
means having to run the program as root (or manually changing device
permissions). You may use "sudo"; for example, in Ubuntu you might run
the program as:


  sudo ./wbfs_gtk


When running the program, the first thing you want to do is open your
WBFS partition (or you might want to format one if you don't have it,
see below). In the upper left corner of the screen, select the device
for your USB hard disk or pendrive and click the green arrow beside it
to load it.


(If it shows an error about "bad magic", most likely the device you
selected doesn't contain a WBFS partition.)


The program lists devices /dev/hd* and /dev/sd*, excluding the devices
it thinks are mounted (according to /proc/mounts). You may choose do
list the mounted devices as well by de-selecting the menu "Tools ->
Ignore mounted devices".


The left pane shows information about the loaded WBFS partition (the
list of discs and the space usage). The right pane shows your
filesystem (so you can select ISO files to add).


The available operations are:


  - To add an ISO file, go to the directory that contains the ISO and
    select file and click "Add ISO" (or simply double-click the file).


  - To extract a disc from the WBFS to an ISO file, select it and click
    "Extract ISO". The ISO file will be written to the directory selected
    in the right panel.


  - To remove a disc from the WBFS, select it and click "Remove Disc".


  - To format a WBFS partition, select the device and click the menu
    "Tools -> Initialize WBFS partition".


Any comments or suggestions, drop me a line at
[email]ricardo.massaro@gmail.com[/email].

```

---

### Post by scollar on 2017-11-27
Figured it out ...... Almost like a portable ..... Just ran it from folder it extracted to.

Thank you for your Help 

Please close thread

---

### Post by vasa1 on 2017-11-27
We don't close threads unless something goes wrong or the thread is very old.

[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

