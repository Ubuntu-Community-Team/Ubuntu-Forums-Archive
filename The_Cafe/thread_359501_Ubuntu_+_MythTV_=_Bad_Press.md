---
title: "Ubuntu + MythTV = Bad Press"
date: 2007-02-12
forum: The Cafe
---

### Post by Titus A Duxass on 2007-02-12
It appears that the combination of Ubuntu with MythTV is not going down well on the MythTV forum.

One member of that community is, and quite rightly so, getting a bit pissed at all the Ubuntu, MythTV database problems that are appearing on the MythTV forum.

When you compare this forum with the other you can see what happens, users first register their problems here and then after receiving no satisfactory guidance they move over to the MythTV forum.

It would seem that Ubuntu Edgy and MythTV are not a good combination or maybe there is room for improvement in the How-To documents.

I personally have not experienced these problems, many others have.  Running a search for MythTV shows quite a few database or backend related issues. 

How many others have experienced or are still experiencing database or backend problems?

Is there really a problem or is it down to inexperienced users attempting something that is not easy?

---

### Post by wjston on 2007-02-12
I have been running mythtv on ubuntu edgy for about three months now and I can say I have had no more problems with this combination than with MythDora (a mythtv + fedora core5 combination). 

I have two systems, and I have had instances where commercial flagging has stopped working on both and the culprit was indeed MYSQL database related, but I think it was due to deleting files out of MythTV and while I was in ubuntu. This corrupts the database but can be fixed by going into MYSQl and repairing the database. I know there are ways to set up a cron job so this is done automatically, but I haven't tried this to date. 

I can say I am very happy with my system running edgy and mythtv and would not hesitate to use this combination again. I know I have done extensive "Google" searching on many issues I needed help with, but many answers are there if one wants to take some time to fine them. I think many problems are a combination hardware/user_experience related. I think the biggest set back I had was permissions related to get my system up and running. Once I figured that out, everything else seemed to work the same as my MythDora system.

---

### Post by Unisted on 2007-02-12
When I first setup Mythtv I had no end of problems with MySql and could not find any satisfactory answers.

However, since then (2/3 weeks ago) the Community Documents have been updated and there are a number of threads informing users what to do in event of this happening.

As Titus A Duxass says the answers are out there but it's having the patience to find them (and the one b***** thing that needs fixing!) before it works.

Of course now I've moved onto LIRC and getting MAME to work but that's another question!

---

### Post by MetalMusicAddict on 2007-02-12
As I understand it MythTV is getting more love for Feisty. So hopefully some issues sort themselves out.

Also users might have more issues when using Ubuntu because from what Ive seen most of the guides/info is from a Fedora POV.

For those of you who actually want to help with MythTV on Ubuntu [HERES]("https://wiki.ubuntu.com/MythTVTeam") a link to its team and [HERES]("https://launchpad.net/products?text=mythtv") a link to the products in Launchpad. Get involved. ;)

---

### Post by basketcase on 2007-02-12
My personal experience, in the dozen times I've tried to setup Myth over the last year or so, I was only successful this last weekend on 6.06 following [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) and the wiki.  

I think the documentation specific to Ubuntu needs more work, as it has you go from one page, to another page, to another page, back to the original page.  It needs to be more fluid.  

The wiki also has you create your user account, and then add yourself to the MythTV group, I couldn't get this to work.  I had to create a user called Mythtv and log in as that user and do everything in that user.  In the end, it doesn't really matter.

But the box has been up for 3 days w/o a single problem, I just need to work out the details for LIRC and getting channels changed on my STB.

---

### Post by Titus A Duxass on 2007-02-13
> The wiki also has you create your user account, and then add yourself to the MythTV group, I couldn't get this to work. I had to create a user called Mythtv and log in as that user - This and the automatic password generation appear to be the main problems.

>  HERES a link to the products in Launchpad.  - That appears to be an empty page or whatever it's supposed to be. I cannot make any sense of the launchpad thing, what is it supposed to do?

---

### Post by basketcase on 2007-02-13
> **Titus A Duxass said:**
> - This and the automatic password generation appear to be the main problems.

Yeah, I'm uncertain how it works behind the scenes, but setting up a mythtv user in MySQL seems to not work, but it's an easy fix.

---

### Post by bpmorris on 2007-02-13
I have just started using ubuntu/linux for the first time over the last 2 months and have just attempted to install MythTv with my Avermedia DVB-t 777 PCI card. The experience I have had has been worse then getting the nvidia drivers working. However in saying that with persistence I did eventually get it all going, I am hoping that that will be the case with the TV card. I have managed to get over the first hurdle of getting the mysql database working and now am focusing on getting the card detected. I got the distinct impression that my database issue was caused by mysql installing by default with no password for the 'root' account. Don’t ask me the commands I used to change it now as I tried everything but eventually I was able to set a non blank password and test it by logging into mysql in the terminal window. Once I had done that I then set the same password in the mythtv setup program I was then able to start everything with out errors about connecting to the 'backend database'. It seems a real shame the %95 effort has been put into packaging this application but the final essential %5 to polish it is missing and giving more and more users a bad experience. Unless you really like playing with your pc and problem solving this will deffinatly put of new and less technical people. Either way I am currently enjoying the chalenge and loving learning a new OS.  Definatly a change from support ten's of thousands of windows boxes....

---

### Post by majoridiot on 2007-02-14
i will agree that mythtv on edgy can be contentious.  i run my backend on edgy and my frontend
on dapper and have more problems with the backend- although not many and all related
to installation and not operation.

in my experience, many things, not just mythtv, have issues with edgy.  i gave edgy a shot on
my main box and went back to dapper out of frustration. dapper seems to be much more stable
on my systems out-of-the-box, as it were.  i stck with edgy on the backend as the packages 
were only available for edgy at the time.  installation at the time went 90% without error, 
which i was very pleased with--  my first installation from source took weeks to get running.

since then, our wiki pages have vastly improved.  from the comparisons i have done, i think
our documentation is far superior to most, if not all distros- including the ubuntu docs on the 
mythtv-home wiki.  yes, our wiki needs work- constant work, in fact, but nobody is being 
paid for this, so patience is a must.  

i reinstalled my systems a few days ago and even thought i *probably* could have done it 
unaided, i followed our guides just to check their accuracy.  i was very happy that the only 
issue i had was in getting and registering the gpg key for the repo-- easily solved by 
splitting up the compund command line into 2 lines.

IMO, as i've posted in other threads like this, is that problems are caused by immediate
frustration and the tendency to jump to another guide to fix what our guide is failing on, 
which compunds the problem.

i **LOVE** mythtv and **LOVE** ubuntu-- and dare anyone to try and take them away from me! :D

thanks for the link to the mythtvteam... i didn't know we had one.  now that i do, i'll see if
i can maybe help out with our guide documentation.

---

### Post by barney_1 on 2007-02-14
I had some problems when I tried to set things up on Dapper.  With Edgy I had no problem using the community guide [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

I think the biggest problem with usability is that mySQL is a damn comfusing program to work with.  I had trouble figuring out that it blocks requests from LAN ip addresses (for my various frontends) unless you specifically tell it to listen to the 192.168.*.* subnet.

Anyway.  I've extremely happy with the install and the stability (uptime for my backend is about two months at this point).

---

