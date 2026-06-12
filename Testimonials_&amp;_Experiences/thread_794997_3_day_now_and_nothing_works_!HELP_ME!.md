---
title: "3 day now and nothing works !HELP ME!"
date: 2008-05-15
forum: Testimonials &amp; Experiences
---

### Post by radical3 on 2008-05-15
ok first things first [SIZE="3"]desktop specs[/SIZE]
pentium 4
1gig ram
2 x 80gig hd
audigy 2 sound card "and a built in realtek"
SiS integrated graphics card "6xx" any will and have worked before
zoom wireless g usb wifi adapter model 4410A

[SIZE="3"][COLOR="Blue"]im running ubuntu 8.04[/COLOR][/SIZE] (first time running linux)
[SIZE="3"]
problem number 1--[/SIZE]
sound cards aren't working (of course)

[SIZE="3"]problem number 2-- [/SIZE]
graphics card isn't working ( the sis is 64mb not a lot but in xp i managed to run ages of empires 3 with no issues and a vast number of special desktop effects such as 3d alt tabbing 4 desktops cubes etc all with no problems)
[SIZE="3"]
problem number 3--[/SIZE]
wireless adapter isn't working ( im currently connected directly to my modem via Ethernet) 
[SIZE="3"][COLOR="Red"]
steps ive already taken[/COLOR][/SIZE]
1. i have already installed wine it shows up in applications menu
2. i have installed ndiswrapper (or at least i think i have, because i used the synaptic and there were no errors but i dont know where it is, nor do i know how to access it , nor do i know where to put my wep key)

3. i used wine to install my SiS intergrated graphics driver (exe) (by moving it into the mock c drive and double clikcing it)and it actually worked with no errors, or so i thought because im unable to find out that its wroking and desktop effects (appearances) wont enable](*,). ( i haven't rebooted)

4 i used wine to try and install my audigy drivers , didnt work
-------------------------------------------------------------------
[COLOR="SandyBrown"]Error Code:	-5011 : 0x80020005
Error Information:
>SetupDLL\SetupDLL.cpp (548 )
pAPP:Creative Sound Blaster Audigy, Audigy 2 series and Audigy 4 series Driver
PVENDOR:Creative Technology Ltd.
PGUID:AAF283AE-985D-4B8A-AFEC-A742D5A797E9
$9.1.0.429[/COLOR]
------------------------------------------------------------------------

5. ive been back and forth over the internet and the ubuntu help docs, i cannot figure out what to do. ive managed to find out that every where i go my hardware (usb wifi, SiS, audigy) are listed as WORKING:-k.



[SIZE="4"][COLOR="DarkRed"]if you choose to help me[/COLOR][/SIZE]
1. PLEASE PLEASE do not for 1 second think i know what im doing or i know how to navigate properly or anything like that , example, 

-----do not say something like, *oh just open up xx[COLOR="Magenta"]Z[/COLOR] and run xx[COLOR="DarkGreen"]E[/COLOR] then your done*------
-----say something like ,* go to xxx>xxy>xx[COLOR="Magenta"]Z[/COLOR]> and run xx[COLOR="DarkGreen"]E[/COLOR]*-----

2. please do not link me to a site which you know i wont understand.

3.  PLEASE, PLEASE do not give me half a solution. example -----*telling me to go and download something , then not telling me how to implement/use/install/activate it or how exactly its going to help*------

4. in windows im not too bad i can fix most of my own problems without any real assistance, so using windows "like" kind of programs like a command line/terminal im not afraid of doing.

5. lastly please dont make a one line reply. its been 3 days CLEARLY i cant figure it out myself and i need real assistance:confused:. 


[SIZE="4"][COLOR="Red"]thank you in advance[/COLOR][/SIZE]

---

### Post by radical3 on 2008-05-18
okay its been five days now , thanks everybody for all your [SIZE="5"]imaginary [/SIZE]help . 


ive taken the action of uninstalling ubuntu and reinstalling xp and guess what everything works in xp, so dont bother helping anymore ive [SIZE="5"]helped myself[/SIZE]. maybe if i use enough bad language i might get the MOD's attention and someone will at least read this thread if not reply. 

<snip>
why dosent my ipod work?
how do i install directX?
why dosent Ctrl+Alt+Del work
how do i install MSN messenger?
when i double click my xxx.tar.gz/bz why dosent it install?
why isnt my wifi working
etc etc

dont get me wrong i see what linux is TRYING to do , i mean everybody must be sick and tired of "windows xp professional spyware" and those backdoors in the os which have been sold off to the likes of the nsa and such, who have access to everyones computer. maybe linux will get better someday, but until then i will simply see every distro as a beta of what might be coming.
in other words i'll come back when you or someone else has fixed it.


i dont get it man
mozilla firefox=open source = easy to use and understand, owns all.
7zip = open source= easy to use and understand, owns all.
nvu = open source = easy to use and understand, owns all.
etc...etc.. the list goes on 

ubuntu = open source = :-#

---

### Post by paintba||er on 2008-05-18
Perhaps you should give this a read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by desheikh on 2008-05-18
Hi radical3,

Ignoring your rant, the first thing I want to remind you is that Linux is not windows. And since Ubuntu is free you cant expect instant help the moment you have a problem. Im not telling you off, its just one of the things you need to accept. If you really need some direct Linux support you can pay for Xandros/Mandriva or one of the many distros which sell the OS with direct support. Its the same with Windows too, If you get a "free" copy i doubt you can call up Microsoft when you have a problem. Except of of course its not illegal in this case :P

In my experience, especially with ubuntu, Iv received help on issues within minutes of submitting a problem. You need to understand the different culture and work with it. The people posting here do so voluntarily and had your post been differently phrased Im sure you would have had enough responses. 

As for the problems you have been having:
You cant install windows drivers via WINE in linux and expect them to work. For windows applications what you do get is alternative applications which will perform the same task for you eg 

Microsoft Word => OpenOffice
MSN Messenger => Pidgin IM
IE => Firefox

And if you dont like pidgin there are a lot of other linux clients you can choose from.. aMSN/Kopete/Kmess and theres no need to hunt down and download the exe file and run through long setup routines, all you need to do is Administration -> Synaptic Package Manager and select the softwares you want to install/uninstall.

WINE can come in when theres a particular windows only software that you NEED to run eg AOE.

For your audigy problem.. Double click the audigy volume control and 
do File -> Change Device (select your Audigy card)
Then in edit -> preferences select the surround sound track to be visible. Make sure this, PCM, and master are all turned up.

Your graphics drivers are already installed 
In Synaptic Package Manager you should see this package
xserver-xorg-video-sis

I dont think thats enough to run Special Effect on btw, you try to enable them to make sure.

Wireless
Unfortunately there are no linux drivers for your wireless card. This is a problem with linux that cant be helped. You have to make sure you buy linux friendly hardware, its easier than jumping through loopholes. You can make your card work by using ndiswrapper. download the drivers from the zoom website. You need this file "wlanuig.inf"

open up the terminal, browse to where the file is and type in
ndiswrapper -i wlanuig.inf

and then 
sudo modprobe ndiswrapper

done

Linux is not perfect, just like every other operating system. You just need to choose what works best for you. 

Ali

---

### Post by vvvladut on 2008-05-18
> **paintba||er said:**
> Perhaps you should give this a read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Perhaps someone should have just answered him after his first post.

---

### Post by Kokopelli on 2008-05-18
I am sorry your first experience in Linux (through Ubuntu) did not turn out all that well.  Linux requires some patience and work to get going sometimes.  Given your rant in the second post I think it safe to assume you will not be back but I would like to make a few comments for others who come across this thread:

1) Even as a newbie the Linux community expects a certain level of self reliance and ability to experiment.  For "How to" kinds of articles it is possible to write it such that a user does not need to understand the commands (though some including myself add explanations to each command).  For diagnosis of problems though, blind command typing is somewhat less effective. > PLEASE PLEASE do not for 1 second think i know what im doing or i know how to navigate properly or anything like that  means to me you expect to have everything handed to you.  This makes the challenging task of debugging install problems tedious and far less likely to be fruitful. > 2. please do not link me to a site which you know i wont understand.

3. PLEASE, PLEASE do not give me half a solution. example -----telling me to go and download something , then not telling me how to implement/use/install/activate it or how exactly its going to help------ tells me not only do you expect to get spoon fed the solutions but you also are not willing to do any research of your own to meet the volunteers half way.  Honestly even if I had seen the thread before today this would have prevented me from offering much help. A computer can be used without needing to understand it; OS X and XP are very good at that and Linux is getting there.  However debugging problems on Linux requires the willingness to tinker and learn on your own. The lack of this willingness changes the rewarding experience of trying to help others into something unpleasant.  People rarely volunteer for the unpleasant duties.

2) Except for wireless drivers using ndiswrapper you can not use windows drivers to run hardware on a Linux box

3) On the audigy problem the first link from a google of "audigy 2 hardy" points to this: [https://answers.launchpad.net/ubuntu/+question/30828](https://answers.launchpad.net/ubuntu/+question/30828)  Did you try this?  Something else? Nothing? It helps if you provide something to go on.

4) On your graphics problem there was not any information as to what was wrong.  No video?  Wrong resolution?  No 3d acceleration? What?  When reporting problems a simple "Doesn't work" is far more likely to be ignored than "My resolution on video is wrong.  I have tried x, y, and z and it is still broken."  since the former gives someone willing to help nothing to go on.

5) An lscpi ("lspci > ~/hardware.txt" to send the results to a text file) is usually better than vague models on the hardware.  By knowing more precisely what is being used it is easier to do googles and find others who might have had similar problems.

6) Childish rants like your second post are not helpful and at best will build animosity.  Try and reflect upon some task to which you have gained proficiency.  Do you spend your free time teaching others this task?  If so, how would you feel if everyone that came along said "teach me" and showed nothing but belligerence.  Your cussing and berating may have made you feel better for a moment, but it was not constructive or even fair.  Try to stay civil and treat others with the respect you would expect to be treated.  It might or might not yield results but in the end reflects better of you in either case.

I wish you the best of luck in the future and hope one day you try Linux again.   It is not for everybody but it can be a rewarding experience.

---

### Post by Kokopelli on 2008-05-18
> **vvvladut said:**
> Perhaps someone should have just answered him after his first post.

His first post did not give enough information to lead to an answer.  It also showed an unwillingness to enter dialog to reach one.  "Volunteers" is a key concept here.  We are in it for fun.

---

### Post by forestpixie on 2008-05-18
It certainly might have better if the OP had posted in Absolute Beginners rather than here.

---

### Post by karellen on 2008-05-18
> **radical3 said:**
> okay its been five days now , thanks everybody for all your [SIZE="5"]imaginary [/SIZE]help . 


ive taken the action of uninstalling ubuntu and reinstalling xp and guess what everything works in xp, so dont bother helping anymore ive [SIZE="5"]helped myself[/SIZE]. maybe if i use enough bad language i might get the MOD's attention and someone will at least read this thread if not reply. 

<snip>
why dosent my ipod work?
how do i install directX?
why dosent Ctrl+Alt+Del work
how do i install MSN messenger?
when i double click my xxx.tar.gz/bz why dosent it install?
why isnt my wifi working
etc etc

dont get me wrong i see what linux is TRYING to do , i mean everybody must be sick and tired of "windows xp professional spyware" and those backdoors in the os which have been sold off to the likes of the nsa and such, who have access to everyones computer. maybe linux will get better someday, but until then i will simply see every distro as a beta of what might be coming.
in other words i'll come back when you or someone else has fixed it.


i dont get it man
mozilla firefox=open source = easy to use and understand, owns all.
7zip = open source= easy to use and understand, owns all.
nvu = open source = easy to use and understand, owns all.
etc...etc.. the list goes on 

ubuntu = open source = :-#

is this for real? what do you want? a free version of Windows? than maybe this is not the right place for you to look for answers ;)

---

### Post by vvvladut on 2008-05-19
> **Kokopelli said:**
> His first post did not give enough information to lead to an answer.  It also showed an unwillingness to enter dialog to reach one.  "Volunteers" is a key concept here.  We are in it for fun.

Of course, and everyone on this forum is free to reply to what posts they feel like replying. I agree the tone of his first post was childish and perhaps there was not much fun in replying to that and having to squeeze information from him on what his problems actually were.

That said, I have to admit I understand his frustration perfectly. I too have felt it on quite a number of times, the only difference probably is that I have been fortunate enough to find a few people who have been more than kind and helpful  to me, this is why I'm still on this forum. But I still have a few posts left unanswered to this day, or with just a few irrelevant replies. I have never cursed and never will, or even expressed my frustration too loudly, but only I know how close I've been. 

I don't think there wasn't enough information to give a reply. I think anyone with little Linux knowledge could have at least told him that it was useless trying to install Windows drivers in Wine. Even I know that. And posting on a help forum means that there is an inherent willingness to enter a dialogue, I don't think he was posting just to see his own words on a web page. 

I'm not saying I'm any better than you, after all I didn't even see this post until the second reply was in there. But it doesn't matter now, does it? Your reply is very nicely written, your tone is calm and asertive, and you have even explained what "An lspci"
is (of course, you didn't mention that that had to be pasted into a terminal, but hey, what do I know, perhaps there is no fun in detailing that). But it doesn't matter now because it's too late and Ubuntu has one less user. Does it matter that this user was behaving like a spoiled child? Because most of them are, and will be. 

Now we're turning this into a debate: you might have been wrong, or who knows, I might be wrong. But it doesn't even matter anymore.

---

### Post by Thanh-BKK on 2008-05-19
Hello :)

While i can't be of any help, unfortunately, i have a few points to make.

SiS: It sucks. Plain and simple. I have a second computer with such a graphic card (onboard as well) and it can NOT enable any desktop effects, doesn't even run Google Earth. Yes, it's a 64 MB too. If SiS doesn't release source code then the Linux/driver developers can't code proper drivers for it. As long as SiS feeds only Microsoft with the details, well - only Windows will run great on such graphic card.

Wine: It can be used to run PROGRAMS, many of them in fact, but NOT drivers. A program is launched the moment you need it - while a driver needs to load at boot. A driver is part of the main system, not sub-part of an application (which Wine essentially is - an application that "emulates" a Windows-environment to run some software in it).

Sound: If you have an on-board AND a PCI sound card, disable one. I guess your PCI (Audigy) is the better one of them so disable the on-board one - can be done thru the BIOS, you may need to look  in your mainboard's manual as this is different for every mainboard model, but ANYTHING onboard can be disabled. If you don't disable one of the two, chances are neither will work - how would Linux chose for you which one you prefer? No, that's your job :)

3 Days: An experience i made myself. Please remember - you did not pay a penny for Linux, so please don't expect the manufacturer's hotline to be available for you. There is no "manufacturer", but a huge group of enthusiasts coding the system that hums in your machine (or stutters now, but will get humming soon, i promise!) and they do so because they like it - nobody pays them to do so. Also nobody pays anyone here to support others, people do it with the Linux spirit of wanting to be helpful. I, too, have been stuck on basic questions - graphic card issues (yes, with both an SiS (!!) and an Nvidia) and assorted others, however i found out that by simply googling the issues i found pretty much all answers needed, and most Google hits brought me right back to this site :) Most issues have been dealt with before. Other questions, even difficult ones, have been answered here, and believe me - i was like you, kind of scared of the command line (telling myself "i'm not" but i AM scared of messing things up!)but you know what?

I switched to Ubuntu "cold turkey" little over two weeks ago, i.e. "Windows out - Ubuntu in" and got pretty much everything to work, even using command lines - and did NOT break my system. I even got my system tweaked and customized in a way that it even blows Windows Vista, which i used before, out of the water and to the moon. You know what? I even got my internal MODEM to work - a thing that is normally "Windows only", yes, Linux CAN do it..... if the user has a little patience and will to learn.

I, too, have used Windows since 1997 or so, had a few (bad!) experiences with Linux before, but now - i won't go back. And guess what? I also didn't learn Windows in three days....... so how would i expect it from Linux?

Riding a motorbike is different from driving a car, altough both are fun and get you there. 

Best regards.....

Thanh

---

### Post by ukripper on 2008-05-19
Could someone please point OP to official guide of ubuntu Hardy!

I think it is common sense, before you cook something new you read instructions and so is true when changing OS.

Read ubuntu guide!!


Below is official guide.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by forestpixie on 2008-05-19
What has to be remembered is that the original post was made in Desktop Effects not Absolute Beginners or General Help - I only stumbled on it by accident.

If a thread gets put somewhere like that and if it's then not seen by people who can actually answer - you could get a 3 day wait or more.

These are the only 2 posts the OP has made - he didn't try and help his own cause, just blasted lines of abuse at all who read it.

---

### Post by 3rdalbum on 2008-05-20
Linux does not need people like him.

---

### Post by vvvladut on 2008-05-20
> **3rdalbum said:**
> Linux does not need people like him.

I personally think Linux needs each and every single person Linux can get. 

If good ol' Mr. Gates thought the same about all the radical 3's of the world, he wouldn't have billions of dollars now to spend on charity. And I bet Mr. Shuttleworth would agree with that.

---

