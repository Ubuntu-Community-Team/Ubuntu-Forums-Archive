---
title: "Ubuntu one activity monitor"
date: 2010-09-25
forum: Ubuntu One (CLOSED)
---

### Post by Zakhafr on 2010-09-25
Has anyone developped a small program or script to monitor Ubuntu One activity?

I'm planning to do so with a script, and then make it available (GPL), but it might already exist.
If so, why reinvent the wheel, I'd like to use the already existing stuff and/or contribute.

Many thanks.

---

### Post by Zakhafr on 2010-09-25
Ok, so I already did a small (and quite ugly, too quickly written!) script that works fine to monitor uploads.

It gives:
- U1 main status
- Count of files to upload, and Bytes to upload
- Current files being uploaded
- Refresh automatically

It is still a bit buggy as it trashes corrupted output on download.

I'll make it available if it can be useful for anybody.

---

### Post by duanedesign on 2010-09-26
Some of the U1 developers created a program called [Magicicada]("https://launchpad.net/magicicada"). It is a GUI for the syncdaemon. You can add the PPA with:

```
sudo add-apt-repository ppa:chicharreros/ppa
```

then install with

```
sudo apt-get update; sudo apt-get install magicicada
```

Another good tool is u1sdtool. You can get all its commands by running:

```
man u1sdtool
```

I use these commands a lot to monitor progress:

```
u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

---

### Post by Zakhafr on 2010-09-27
Many thanks for your answer duanedesign.

I'll try Magicicada

As for u1sdtool, I know of it because it what my script is using :)

I'm still wondering about u1sync (another u1 client). It works for path "outside" you Ubuntu One local path, but as soon as you upload stuff through u1sync, they are downloaded back to your Ubuntu One, and so all get mixed and creates a big mess...

If someone could clarify the use of u1sync: upload + download, through some basic examples it would be very nice!

---

### Post by duanedesign on 2010-09-28
u1sync is mainly used for testing. From what all the developers have told me, they do not recommend using u1sync.

If you do develop a script or application there is a [page on the wiki]("https://wiki.ubuntu.com/UbuntuOne/ThirdPartyProjects") for Ubuntu One related projects you should add your project too.

~duanedesign

---

### Post by Zakhafr on 2010-09-28
Thank you for your clarifications about u1sync duanedesign.

It's really very helpful!

As for monitoring what the Chicharreros done already has a much better look than my ugly script, although there are still missing functions such as :
- current download progression on single files (you have it with --current-transfers)
- overall download progression for the upload (you can stat the files to upload)
- assuming it will be a front-end to u1sdtool, we could get a way to put in front one of the content operation such as what you can do with --reschedule-next

I assume this is a beta and a work in progress, and it's already very nice and helpful as it is now.


I'm doing something else with U1. I'm using it as a temporary storage to transfer big amounts of data between my PC and my mother's PC.

For my mother, there will be user-friendly automatic download, adding 2 things to what U1 already does magically!

-1) a nice notification to tell my mother "Automatic download / The video of last holidays with the family / Overall size 1.200MB / Resuming at 57%"

-2) when she switches off her PC, get an option to wait for the end of the download then automatically switch off, or switch off immediately as the transfer will resume next time she power on.


1) is already done and working.
It's quite easy, you just define a file that holds the description of the download. Let's say it is called :
Bigdata_Shared_From_Zakhar/description
-a) search content for such a file, and schedule it first
-b) wait for download of this file to be done
[skip a & b if file already there from last download]
-c) display the message in the file


For 2, the most difficult part was to figure out how to "hook" the shutdown dialog. Then it's just a test and some zenity code (yet to be done)


Of course, you would have noticed U1 do not have the resume function and I have it. Well, in fact I don't, but my script that prepares the download splits the file in small chunks so that it looks like resuming if chunks are reasonably small (I'm using 5M).
Once all the chunks has been received, you just need a cat to reassemble the initial file.
All that is done automatically by the background download script.
(And much more because I added md5 and some par2 just in case... and put the chunks through encfs, although I trust people at U1, they don't need to see my holiday videos [-X )


So that's why I needed a monitor tool, it's for debugging purpose, and I'm glad you pointed me at magicicada.


Of course if some are interested by functions similar to what I did, I'll be glad to share... but I tend to think it's quite specific.

---

### Post by duanedesign on 2010-09-29
The great thing about open source you can take the magicicada project and add/remove to suit your need. :)

If you need any help the U1 devs hang out on irc.freenode.net #ubuntuone They are very friendly and helpful

---

### Post by Zakhafr on 2010-09-29
Thanks duanedesign for the IRC channel address.

I just have to figure how to set it up, as the last time I used IRC it was... well, for sure on the previous millenium!..

At the time I was using something like Windows 3 :eek:

But rest assure that the French Ubuntu community is very active, and they have all the needed documentation for setting up an IRC. I'll have a look at that on ubuntu-fr.org

---

### Post by Zakhafr on 2010-10-05
And thanks Duanedesign, I'm marking this thread as "Solved" as magicicada is a good tool for what I need to do.

Now let see what improvements they manage to insert in Maverick for Ubuntu One. :)

---

