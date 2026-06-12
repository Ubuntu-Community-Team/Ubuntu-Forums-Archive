---
title: "Wireless Modem Failure"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by lee986321 on 2013-03-23
I can not tell if it is a hardware issue or Software issue.
 I was adding some features to Edubuntu, (Video -Studio to be exact)
When I came across an issue that I thought was only ascociated with Windows 8 ( Complete crash and or Blues screen of death). I was running Ubuntu 12.04 and everything was fine.
I uodated and had difficulty with the repos loading completley, they would stop at 99.
Ah that famous 99 dead stop issue, 
At any rate I I finally plugged it in to the eithernet (crossing fingers that it would work)
And everything loaded fine.,

I realize it is a beta and I realize that it is not perfect. 
I am using an Acer Aspire one Net Book. 
Other then the modem then Netbook is working 10x better then it did with Windows 8 and Ubuntu 12.04.

The problem
Downloading from wireless (in repositories) Downloaded the Edubuntu ISO fine though after fire fox crashed. I used" save as"
and down loaded the iso with out further issues.

Could not down load complete files in the repos.
Could down load smaller items like codecs.
Would dead stop at 99 and then continue to next  and would stop at 99 and then finially ater 4 failures it would say un able to download repositories resulting in a "Broken" for Ubuntu Video add ons , well not sure what else to call it when you add stuff to the Edubuntu.

at any rate, I jsut need to know where I can go to see if it is indeed hardware failure or something else. 
so that I can contribute to the forum or report a possible bug.
I realize that the tech I am using is old, but this is the machine that I try new things one before graduating to the much more important item, my lap top.

---

### Post by grahammechanical on 2013-03-24
It would be useful if you gave us the error messages that you see when you try to do this stuff. What messages do you get when you run ```
sudo apt-get update
```

Two days ago I installed Ubuntu Kylin (Chinese Ubuntu) Raring to a USB stick but the Ubuntu Software Centre in this installation would not install Wine or the Ubuntu Restricted Extras even though I have these two installed on a standard Ubuntu Raring. I guess the Ubuntu Kylin has different repositories to standard Ubuntu.

It is my understanding that Edubuntu uses the same repositories as Ubuntu. So that may not be your problem. It may be that you are trying install an application that has not been packaged for 13.04. It may be that you have PPAs that have not been maintained and that is blocking the updating of the sources list.

It is hard to tell without those error messages.

Regards.

---

