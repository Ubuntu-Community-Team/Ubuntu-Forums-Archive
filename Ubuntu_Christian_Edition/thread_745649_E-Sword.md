---
title: "E-Sword"
date: 2008-04-04
forum: Ubuntu Christian Edition
---

### Post by retiree on 2008-04-04
I am running AMD dual core processor, and Ubuntux64 bit OS.I downloaded E-sword and run under wine.When E-sword starts up to main screen there is no Bible to open. I understand KJV with Strong's is default Bible, but nothing shows. I also tried to download more Bibles but the same thing happens.What have I done wrong? I am a new user of Ubuntu of about a week,so I am really green right now. Any help would be greatly appreciated. Thanks in advance

---

### Post by david_kt on 2008-04-04
E-sword need some tweaking to run in wine. Please follow below instruction:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

DK

---

### Post by pastormick on 2008-04-04
If you ever have a chance, try giving jSword - [http://www.crosswire.org/jsword/](http://www.crosswire.org/jsword/) - a try. It's a Sword version from the Crosswire Project written in java. There's no actual 'installation'; it'll run on just about any platform that runs java, and is compatible between, say, Ububtu and XP, so if you're writing notes, you can work on either.

Also, just two files (program and texts) - I just made a link in the office menu with Alacarte and was good to go...

Mick

---

### Post by retiree on 2008-04-05
I know am doing something wrong but I don't know what it is.I downloaded it twice two different ways and still no results.What do you mean there is no installation? J-sword that is.
I also am still trying to get E-sword to install with no results. Like I said I'm one week into Linux and green as they come, but I am loving it,especially Swiftweasel , lighting quick on the web compared to windows.

---

### Post by david_kt on 2008-04-06
> **retiree said:**
> 
I also am still trying to get E-sword to install with no results.
Which way did you try to get e-sword? Have you tried the manual method I give before?

DK

---

### Post by retiree on 2008-04-06
I am running Ubuntu (Gutsy)x64, does it make a difference in Ubuntu CE?
It actually installed and runs under wine ,but the Bibles still don't show up.I have read some more forums on some of your replies to others, and I am beginning to pick up some of the ways to navigate around. When I type in terminal according to your instructions,and it tells me no such directory then I get lost as what to do.It's frustrating but I am not one to give up. I will figure it out. All of the mistakes is a learning process that will pay of eventually.I was familiar with the old dos ways.Where can I get a list of all the commands in Linux? I'm sorry to be a bother to you,as I know you must grow weary of trying to answer the same questions all the time. I do appreciate your time and effort.   Thanks, Clayton

---

### Post by Eutaw on 2008-04-06
Clayton,
I found it helped to cut and paste instead of type the commands. Lessens the risk of the "fat-finger". I'm also learning the command stuff. If you google "linux commands" you should find several sites that list and define the commands.
As far as the Bibles and commentaries etc, I had to download them to desktop individually, and then install them. I think if you review the steps again, you'll see it. It took me a few times reading through to catch it.
Happy installing.
Rick

---

### Post by david_kt on 2008-04-06
> **retiree said:**
> When I type in terminal according to your instructions,and it tells me no such directory then I get lost as what to do.It's frustrating but I am not one to give up. 

It could be used on Gutsy, even Hardy. And also it could be used on puppy, Mepis, bassically all distro running linux. Could you follow it step by step, and inform me in detail on which step you have problem, and I will try to make it clear. And I will also edit the instruction based on your feedback so that later on other people will be able to follow it easily.

DK

---

### Post by Eutaw on 2008-04-06
> **david_kt said:**
> It could be used on Gutsy, even Hardy. And also it could be used on puppy, Mepis, bassically all distro running linux. Could you follow it step by step, and inform me in detail on which step you have problem, and I will try to make it clear. And I will also edit the instruction based on your feedback so that later on other people will be able to follow it easily.

DK

David, I don't know about the rest, but I found your instructions clear - after I studied them awhile. It was me, not you. I had to get familiar with the process and terminology. There's always a learning curve.

---

### Post by retiree on 2008-04-07
Eureka!!!!! It WORKS
Thanks David and Eutaw
After I got the two DLL's that needed to be edited to native (windows) things begin to change. The Bible then worked but did not run properly,giving me a module msls31.dll not found. I had previously checked the folder for all of the Dll's and they were there, but still the error. Then I checked the virtual system32 folder and it was not there, so I copied it to folder and Viola !! it started working perfectly. Learning curves are like life's curves, you will learn one way or the other.
Hey Guys, I really do appreciate your time and effort in helping others as well as me.Clayton

---

### Post by retiree on 2008-04-07
Hey Pastormick
I will download and take a look at J-Sword. I have looked at the various screen shots and they look interesting.Thanks for the link to it. Clayton

---

### Post by rcdeacon on 2008-04-11
Pastormick, I downloaded j-sword 1.0.7 but could not get it to install. I am relatively new at the Linux thing. I do have e-sword up and running and I do run virtualbox so I can use Logos but I cannot get jsword to run. Not sure what I am doing wrong.

---

### Post by retiree on 2008-04-11
Good Morning Deacon
I am having the same problem with J-Sword. I tried Pastor Mick's instructions and I am still at a loss as how to get it running. I have been reading several forums related to this type file (tarball), and I have upgraded repositories and I can't find it to load it under Sypaptic package manager, which I understand is the easy way to load it. Let me know if you have any success. I am determined to get it running. Regards, Claytonhttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

### Post by rcdeacon on 2008-04-11
Retiree, do you know the repo information? I would like to give synaptic a try.

---

### Post by retiree on 2008-04-11
i have not been able to find it in any repos. I have downloaded RPM and trying to load it with that.

---

