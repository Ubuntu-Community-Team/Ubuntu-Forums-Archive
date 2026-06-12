---
title: "Clearing all user history of all kinds"
date: 2009-06-11
forum: Security
---

### Post by Linuxnewbz on 2009-06-11
Is there a way in Ubuntu to clear all history of all kinds? What type of logs does Ubuntu keep? Everything that you type? Every program that you have opened?

What is the best way to clear everything so that the system basically appears as if no one has ever opened a program, opened a folder, file, clicked on anything, browsed the web, etc...? (besides the obvious joke of a new installation, lol)

I have used Windows for a long time and am absolutely loving Ubuntu!

But, I am not as familiar with the way Linux does things. I had several programs in windows that would clear basically everything in one click, java history, files, folders, movie player history, everything. Does something like that exist for Ubuntu, or in Ubuntu itself?

---

### Post by cariboo on 2009-06-11
Linux starts writing logs the second you touch the power button. Depending on how many users your computer has there will be logs in various places. If you use firefox, the cache is located in ~/.mozilla. There will be the same directory in each users home directory. 

Temp file end up in /tmp, but that is cleared on each shutdown automatically. 

The majority of the logs are in /var/logs. If you have log rotate installed, some logs are rotated daily and others weekly. It is ok to remove archived logs, but removing current logs could cause problems.

---

### Post by bodhi.zazen on 2009-06-11
Not that I know of.

I suggest if you need a "clean" system that you run a live CD.

---

### Post by moe19790 on 2009-06-11
> **bodhi.zazen said:**
> Not that I know of.

I suggest if you need a "clean" system that you run a live CD.


this isn`t the best news for today :(

---

### Post by tubbygweilo on 2009-06-11
As previously suggested a LiveCD but with data that is required between LiveCD sessions stored on the machine and truecrypt encrypted, that way data exists but can not be examined unless the user has the required pass phrase. Possibly paranoid but possible.

---

### Post by doas777 on 2009-06-11
I don;'t know about resetting to factory, but i would love an app or script like CCleaner for windows. deletes cache and temporary files from the OS and many common apps like firefox.

---

### Post by bodhi.zazen on 2009-06-11
> **moe19790 said:**
> this isn`t the best news for today :(

> **doas777 said:**
> I don;'t know about resetting to factory, but i would love an app or script like CCleaner for windows. deletes cache and temporary files from the OS and many common apps like firefox.

Mind you this is somewhat of a different question. The OP is asking about logs and well the whole tamale.

bleachbit :

Try [http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html#more-803](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html#more-803)

---

### Post by doas777 on 2009-06-11
> **bodhi.zazen said:**
> Mind you this is somewhat of a different question. The OP is asking about logs and well the whole tamale.

bleachbit :

Try [http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html#more-803](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html#more-803)



in terms of the ops quandry, perhaps a default image is a good way to get the performance of a hardware install (with drivers even), and a clean fresh system every day. the only problem is it would take a few minutes to restore it daily, for a minimum build. with a pxe server, it could be automated, but that takes some infrastructure. 


many thanks bodhi, that looks very promising. 

cheers

---

### Post by cdenley on 2009-06-12
As long as you don't write too many large files, you can mount the root filesystem with aufs. All write operations will be done in memory, but you still boot and run software off the hard drive. When you reboot, everything gets rolled back. You get the benefits of a livecd without the decreased performance.

[http://ubuntuforums.org/showpost.php?p=5720661&postcount=5](http://ubuntuforums.org/showpost.php?p=5720661&postcount=5)

Also, anything stored by applications you run, not services, should be stored in your home directory. You can simply make your home directory non-persistent, then updating your system would be easier. Of course your system logs would still be stored, but that shouldn't contain anything sensitive.

[http://ubuntuforums.org/showpost.php?p=6598376&postcount=5](http://ubuntuforums.org/showpost.php?p=6598376&postcount=5)

---

### Post by zuerston on 2009-06-13
**Here is what I did to ****fix the problem.**
First go into administration menu, click "services"  and **disable** "computer **activity logger**",,
**next** fire up **Synaptic** and install **"BleachBit"**

**AFTER ITS INSTALLED,**
 go in **Aplications-** **system tools** ,,run **BleachBit **as **(Root**), (has 2 choices)
now check **ALL** boxes when it comes up and **run it! ** I did so and absolutely nothing broke and computer rebooted fine.All programs worked including **Googlearth** and **Virtualbox** nothing broken.
My computer is so much** faster** now after running it. and lots more secure.
I took almost** 20 minutes **running to finish its job it also writes zero's after cleaning up the mess.
I would compare it with Eastek Eraser in Windows.

It deleted hundreds of pieces of junk and trash!! I was sure it deleted my entire system but nope all fine here!
Great stuff!:KS

---

### Post by cariboo on 2009-06-13
But what about clearing the logs in /var/log? Does the program do that like the op was asking?

---

### Post by zuerston on 2009-06-14
YUP all fixed up.

---

### Post by Linuxnewbz on 2009-06-15
Thank you for all of the replies. 

So, in Ubuntu, if I were to download a file, Unzip it, extract it, open it, and then a few days later delete the .zip file, and the other file, and restart my computer, is there any trace that that file ever existed on my computer?

---

### Post by cdenley on 2009-06-15
> **Linuxnewbz said:**
> Thank you for all of the replies. 

So, in Ubuntu, if I were to download a file, Unzip it, extract it, open it, and then a few days later delete the .zip file, and the other file, and restart my computer, is there any trace that that file ever existed on my computer?

Deleted files exist until overwritten. The meta-data is overwritten with zeros, so any data about the file is gone, but it would be inefficient to overwrite an entire file to delete it. If BleachBit fills all unallocated space on the filesystem with zeros (I'm not familiar with it), then you're probably safe after running it.
```

sudo apt-get install secure-delete
man sfill
man srm

```

---

