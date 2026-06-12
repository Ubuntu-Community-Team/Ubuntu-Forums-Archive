---
title: "Defrag Constantly?"
date: 2008-04-27
forum: Windows
---

### Post by mpgarate on 2008-04-27
Is there an app that will constantly defragment my HD in windows? I thought I heard someone mention something like that recently... but im having trouble googling for it

---

### Post by smoker on 2008-04-27
there's this, but it is a pay for product!
[http://www.oo-software.com/home/en/products/oodefrag/](http://www.oo-software.com/home/en/products/oodefrag/)

---

### Post by LaRoza on 2008-04-27
> **mpgarate said:**
> Is there an app that will constantly defragment my HD in windows? I thought I heard someone mention something like that recently... but im having trouble googling for it

Yes, it is called a better file system ;)

Unfortunately, Windows doesn't support the file systems with this feature.

---

### Post by mpgarate on 2008-04-27
I stumbled upon this today...

[http://www.kessels.com/JkDefrag/index.html](http://www.kessels.com/JkDefrag/index.html)

---

### Post by jbr6700 on 2008-04-27
[]("http://www.diskeeper.com/defrag.asp") [http://www.diskeeper.com/defrag.asp](http://www.diskeeper.com/defrag.asp) These are the same folks who made the defrag utility built into XP, but the pay version works silently in the background automatically. They have a 30 day trial if your interested.

---

### Post by Jiraya on 2008-04-28
Wow. I didn't know about background defragmentation.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Jiraya on 2008-04-28
> **mpgarate said:**
> I stumbled upon this today...

[http://www.kessels.com/JkDefrag/index.html](http://www.kessels.com/JkDefrag/index.html)

This one seems to be the best option, since it's free and open source. I'll test it over this week.

Thanks for the indication.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by TwilightDawn on 2008-04-28
Just FYI: Jkdefrag is not true automatic background defrag; it defrags during screensaver activity, and it also lacks the ability to defrag the MFT.

BTW, there is no use of defragging 'constantly'. What you need is intelligent automatic background defragmentation which defragments only when required, and only using idle resources. This will prevent other apps from slowing down. Auto defrag is super convenient when you have multiple volumes because you don't ever need to worry about defragging those manually or scheduling defrags the old fashioned way.:) Essentially, the user never has to defrag a drive, except for the occasional boot-time defrag in the rare case that the MFT gets fragmented.

BTW, I believe jbr6700's link shows a true automatic defragmenter.

---

### Post by Jiraya on 2008-04-28
> **TwilightDawn said:**
> Just FYI: Jkdefrag is not true automatic background defrag; it defrags during screensaver activity, and it also lacks the ability to defrag the MFT.

BTW, there is no use of defragging 'constantly'. What you need is intelligent automatic background defragmentation which defragments only when required, and only using idle resources. This will prevent other apps from slowing down. Auto defrag is super convenient when you have multiple volumes because you don't ever need to worry about defragging those manually or scheduling defrags the old fashioned way.:) Essentially, the user never has to defrag a drive, except for the occasional boot-time defrag in the rare case that the MFT gets fragmented.

BTW, I believe jbr6700's link shows a true automatic defragmenter.

Actually, JkDefrag DOES have a background defragmentation utility, as you can see at its website:

[QUOTE=http://www.kessels.com/JkDefrag/index.html]
JkDefragCmd.exe
    Commandline version. Specially designed to be run automatically in the background, or from administrator scripts. See the "Commandline" chapter below for a list of commandline options, and the "Frequently Asked Questions" on how to run it automatically with the Windows Scheduler.
[/QUOTE]

---

### Post by gameryoshi600 on 2008-04-29
that will just eat up memory... use [jkdefrag]("http://www.kessels.com/JkDefrag/"). always use it every month

---

### Post by jrusso2 on 2008-04-30
This is the only free true background defrag I have found.

[http://www.iobit.com/iobitsmartdefrag.html](http://www.iobit.com/iobitsmartdefrag.html)

I have played with it a bit seems ok, but it is beta

---

### Post by TwilightDawn on 2008-05-01
> **gameryoshi600 said:**
> that will just eat up memory... use [jkdefrag]("http://www.kessels.com/JkDefrag/"). always use it every month

IIRC, Diskeeper service uses only about 8 MB...it's miniscule.

If defragging Vista, none of the free defraggers come anywhere close to Diskeeper. Defragging Vista with VSS service running, has it's own set of problems, some of which are not easy to circumvent. Only Diskeeper AFAIK, has VSS defrag mode for Vista.

---

### Post by articpenguin on 2008-05-19
I think defragging constantly in the background does more wear and tear to the harddisk than it prevents.

---

### Post by jrusso2 on 2008-05-19
> **articpenguin said:**
> I think defragging constantly in the background does more wear and tear to the harddisk than it prevents.

Actually they don't run all the time, they check every so often and run analyze to see how fragmented the disk is and then run a quick defrag to eliminate the fragmentation.

---

### Post by smoker on 2008-05-19
a badly fragmented disk will wear out quicker, use more energy, and be slower, gathering together bits and pieces of files from all over the drive.

once the major defragging is done, a constant defragger will have very little to do to maintain a drive in order (as jrusso stated above).


Dirms, i think is still free, though i think you have to register, there is also a commandline version available: [http://www.dirms.com/](http://www.dirms.com/)
(i believe 'dirms' stands for 'do it right microsoft!'

---

