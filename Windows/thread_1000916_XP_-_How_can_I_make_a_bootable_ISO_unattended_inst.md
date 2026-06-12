---
title: "XP - How can I make a bootable ISO unattended install disc?"
date: 2008-12-03
forum: Windows
---

### Post by Roasted on 2008-12-03
I'm familiar with nLite, which is great, but I'd like to slipstream programs into the installation too... which nLite can't handle...

I work in a school district, so we have hundreds of computers that often need serviced. We have proper licensing for the volume site so that's not a question at hand.

The issue is I spend so much time installing programs when I could be doing other things.

My goal is this... I'd like a CD or DVD of Windows XP Pro SP3 with a decent amount of drivers to accomodate most of the computers we have here, along with programs such as...

Flash 10
Reader 9
Java 6
Quicktime 7.4
IE 7
Firefox 3.0
Office

And it'd be soooo nice if it was unattended install, with the time zone and default user account already slipstreamed into it.

Is there a free program that does this? I've been googling for about an hour now...

---

### Post by cmay on 2008-12-03
i do not think it is legal to make a custom windows installer. it is what the OEM cd are and they buy a license to do so from microsoft. 
if you used linux then there are program to do so .

---

### Post by Roasted on 2008-12-03
If it would be illegal, why in the world would Norton Ghost exist? It clearly can't be illegal considering how big that program is. The problem is, that program costs money... and uh... yeah.. 

It'd just be nice to pop in a DVD and the thing would just take off and completely install itself from front to back top to bottom left to right.


Question - What if I install Ubuntu on a separate computer, and then hook up the XP HDD in question. Can I use Ubuntu to create a bootable ISO of another HDD?

---

### Post by cmay on 2008-12-03
> If it would be illegal, why in the world would Norton Ghost exist? It clearly can't be illegal considering how big that program isi do not know this program. i left windows around 3 years ago. but i do know that considering the question as i read and understand it you are trying to create some alternative installation procedure than out of the ordinary windows install using a cd mthat is been modified.  and i think its illegal with out a license to do so. all microsoft products has so many restictions of use that the only way you can use it is to use it the one way microsft intend you to do with out breaking any eula .. i would advise to call microsoft your self and ask about it. maybe they can advise you to use a specific procedure or program.

---

### Post by Roasted on 2008-12-03
> **cmay said:**
> i do not know this program. i left windows around 3 years ago. but i do know that considering the question as i read and understand it you are trying to create some alternative installation procedure than out of the ordinary windows install using a cd mthat is been modified.  and i think its illegal with out a license to do so. all microsoft products has so many restictions of use that the only way you can use it is to use it the one way microsft intend you to do with out breaking any eula .. i would advise to call microsoft your self and ask about it. maybe they can advise you to use a specific procedure or program.

Quoted from my first post...

```
I work in a school district, so we have hundreds 
of computers that often need serviced. We have proper 
licensing for the volume site so that's not a question 
at hand.
```

We have licensing.
We have purchased everything we need.
I'm just looking for a more simplified way of servicing hundreds of machines by myself.

---

### Post by lswest on 2008-12-03
nLite offers to do some of it (never tried it before, except to add SP3 to my XP cd so I didn't have to upgrade everytime, and added drivers for my PC).

[http://www.nliteos.com/](http://www.nliteos.com/)

---

### Post by cmay on 2008-12-03
i do not see that well which also explains the spelling errors i have. 
i cant help as much with the problem as far as windows is concerned but i think when you use redirection from one computer to the ohters you can do this with echo command in the dos terminal. this means you output to the ohter computers what you  are doing in one of them. accordng to my old man pages from dos anyway.  i never tried to install anyting out of the ordinary from withing windows. 

the other question:
 i used iso master in linux to add files to an already existing boot image of a linux live cd so i had my own wall paper. that modifies the cd content and would be illegal even for a licensed computer to do i think., 
> 
Question - What if I install Ubuntu on a separate computer, and then hook up the XP HDD in question. Can I use Ubuntu to create a bootable ISO of another HDD?
there is most certainly ohter programs in linux that can be used to copy content off hdd but the thing is that a windows install copied to anohter comuter wont work since it attaches it self to the proccesor as a way of preventing exactly piracy and that sort. i know since i done something like that. i had a windows xp i could not start so i tranfered the hardisk to anohter computer to start it but it wont since the windows version is already attached to a specific machine. 

try anyway to ask microsoft consumer servise as i am sure they get the question may times.

---

### Post by Roasted on 2008-12-03
This is why I like Ubuntu. Things can be simple and less restrictive. This ungodly headache of trying to manage hundreds of computers myself by doing installations the old fashioned way is laughable at best.

We have a cloning machine, which works wonders, but the trick is you can only clone with identical computers. If a hard drive fails on one computer, that's all I have to work with... is 1 computer. You need 2 (identical) computers/hard drives to clone.

If I can just get XP, SP3, drivers, and several programs loaded onto 1 CD without having to touch a THING during the install, that'd be great. I don't even care how long it takes. If I can pop in an XP CD before I leave and come in in the morning and it says ALL DONE that'd be wooooonderful!

AHHHHHHHHHHHHHHH!!

---

### Post by lswest on 2008-12-03
> **Roasted said:**
> If I can just get XP, SP3, drivers, and several programs loaded onto 1 CD without having to touch a THING during the install, that'd be great. I don't even care how long it takes. If I can pop in an XP CD before I leave and come in in the morning and it says ALL DONE that'd be wooooonderful!

The [nlite program]("http://www.nliteos.com/") will add the XP, SP3 and the drivers on a disc and offers an "unattended" install mode as well.  Check out the link.  Not sure about adding extra programs, should be possible though.  Not sure if you missed my reply the first time around, or just didn't check the program out?  Really, take a look, it should do what you want.

---

### Post by cmay on 2008-12-03
yeah i understand.
as i was saying there is the echo command in the dos shell which should be able to redirect an out put to all the other computers so what you install on one of them is installed on the others. i never done it myself but i once saw in a coffee break a guy setting up printer drivers for the classroom. i think its an more easy option. with out knowing of course.

or try the above link which seems to be a good option.:)

---

### Post by Roasted on 2008-12-03
> **lswest said:**
> The [nlite program]("http://www.nliteos.com/") will add the XP, SP3 and the drivers on a disc and offers an "unattended" install mode as well.  Check out the link.  Not sure about adding extra programs, should be possible though.  Not sure if you missed my reply the first time around, or just didn't check the program out?  Really, take a look, it should do what you want.

I've used nLite heavily. But it doesn't do what I need.

It does Service Packs and drivers. Great.

What about programs? It takes me so long to install IE7, Symantec, etc... if it can be done unattended (or in 1 shot inclusively) I'd be golden.

---

### Post by lswest on 2008-12-04
Maybe you could run a batch file to use the window's version of wget to download and execute the installs automatically?  You'd still need someone to go through the install though.

Just found this: [http://unattended.msfn.org/unattended.xp/](http://unattended.msfn.org/unattended.xp/) I don't know what it's like, never used it before, but it does offer a guide on how to install programs at the same time as XP is being installed.

Good luck, and let us know how you get on.
Lswest

---

### Post by Roasted on 2008-12-04
I started looking into CloneZilla, which looks like a good option. But there's a problem I just realized... some of the computers I deal with don't have DVD drives... some of them have CD drives... soooo that'd be a problem with booting a DVD image...

So I was thinking. I have a little 5 port 10/100 netgear switch here at my desk, which is where I do the installs anyway.

Is there anyway I can use CloneZilla server on a host computer (such as my P4 1gb ram HP desktop that I use for testing purposes anyway) and "push" an ISO image down FROM the HP Test computer down to any computer plugged into the switch?

Is that possible?

---

### Post by rickyjones on 2008-12-04
> **Roasted said:**
> I started looking into CloneZilla, which looks like a good option. But there's a problem I just realized... some of the computers I deal with don't have DVD drives... some of them have CD drives... soooo that'd be a problem with booting a DVD image...

So I was thinking. I have a little 5 port 10/100 netgear switch here at my desk, which is where I do the installs anyway.

Is there anyway I can use CloneZilla server on a host computer (such as my P4 1gb ram HP desktop that I use for testing purposes anyway) and "push" an ISO image down FROM the HP Test computer down to any computer plugged into the switch?

Is that possible?

There are a ton of ways that you can go about doing this. I suggest breaking this down into steps.

1. Install a copy of the OS with drivers for all hardware. Make this unattended.
2. Install various standard applications.

A mix of RIS and scripting will easily take care of this.

Microsoft's RIS service will allow you to essentially clone an already built PC image for re-deployment to other machines via the network.

If a PC cannot use PXE boot for this then you can easily create an unattended CD for the OS and then run a script automatically after the install to install all your applications. 

I hope this helps you out.

-Richard

---

### Post by Roasted on 2008-12-04
Run a script to install applications in XP? Really? How's that work?

Question. Would CloneZilla be able to clone 5 computers that say, are completely different? We have a hard drive cloning machine here... but when I clone an HP D510, Dell Optiplex 740, Optiplex 330, Compaq DC2200, the other computers don't work if the master image was created on the HP D510. The image on the HDD's for the Optiplex's and DC2200 won't work. They'd only work on OTHER D510's.

My plan is to find a method to install a base copy of XP + programs on ANY computer, regardless of whether or not it is a Pentium 3 with 930mhz like some older Dell's we have, or a Dual Core AMD 6000+ with 2gb of RAM and SATA hard drives.

I need something that'll handle this. If CloneZilla is the ticket to cloning many machines that are VERY different hardware wise, then I'm golden with this.

Do you think CloneZilla can do what I need?

---

### Post by rickyjones on 2008-12-04
> **Roasted said:**
> Run a script to install applications in XP? Really? How's that work?

Question. Would CloneZilla be able to clone 5 computers that say, are completely different? We have a hard drive cloning machine here... but when I clone an HP D510, Dell Optiplex 740, Optiplex 330, Compaq DC2200, the other computers don't work if the master image was created on the HP D510. The image on the HDD's for the Optiplex's and DC2200 won't work. They'd only work on OTHER D510's.

My plan is to find a method to install a base copy of XP + programs on ANY computer, regardless of whether or not it is a Pentium 3 with 930mhz like some older Dell's we have, or a Dual Core AMD 6000+ with 2gb of RAM and SATA hard drives.

I need something that'll handle this. If CloneZilla is the ticket to cloning many machines that are VERY different hardware wise, then I'm golden with this.

Do you think CloneZilla can do what I need?

I can't speak about CloneZilla but yes, it is possible to have a base image that will work on all PCs. All you need to do is install all the device drivers for any computer. Will it be a little messy? Yup, but it should work everywhere.

You can script the installation of programs pretty easily. A simple batch script can be created to launch the setup.exe of a program, wait for it to finish, then start another one. You can script the button presses of a program install using third party software - it's done at my workplace so I know it is possible.

-Richard

---

### Post by Roasted on 2008-12-04
Drivers I'm not worried about. I spent a full work day and downloaded all drivers to every computer we have and I have it on an 8gb flash drive I carry with me at all times.

As long as I can get a solid image with everything I need (programs wise) installed in 1 shot without any prompts (time zone, cd key, etc) then I'll be golden...

---

### Post by Roasted on 2008-12-05
I'm in CloneZilla Live right now using the latest stable version. I've ran into a problem. 

I have an 80gb hard drive with XP Pro installed along with all of the applications I need. Time to make an image.

In CloneZilla I get to the prompt where I select my hard drive.

Then, I get an error.

Error! No unmounted devices found! Or some garbage.

I go into command line and manually unmount the drive, but when I go back in the installer I get the same error... Note - It did this on two computers that are completely different, with both computers having XP Pro on it with NTFS file system. 

AHHHHHHHHHHHHHHHHHHHHH

---

### Post by Roasted on 2008-12-05
Is this really a valid option for what I want to do, guys? I can't even get the clonezilla live to work with 1 local machine (and I've tried two computers). I can't imagine trying to get a server running.

Maybe my best option is just to tweak out nlite the best I can and rely on my flash drive with .exe's of the applications we run. I think that'd be a better option I guess. After all, we have a cloning machine for when we buy a mass amount of new computers. And for the random ones that die, instead of carrying 30 images of computers around, I can just have 2 CDs... an nLite'd XP and 2k Pro... then just install drivers afterward.

---

### Post by AlanRogers on 2008-12-05
My first question would be how many different specifications of machine are there?

If it's only a few, and you have all the volume licensing sorted as you say, then build one machine of each specification then, using a LiveCD, copy the hard drive image off onto the network.

On each of the new machines, boot off a LiveCD, then copy the hard drive image done onto the machine. You can then use the LiveCD to resize the partitions if necessary. Boot into Windows and rename the machine.

---

### Post by Roasted on 2008-12-05
Alan -

Thanks for your response. There's quite a few. I manage 3 schools, each has a different set of programs exclusive to that school due to grade level differences. There's also about 4-5 different model computers from each school. We also run a mixture of 2k pro and xp pro.

So take one school for example. 4-5 different types of computers, 2 operating systems. A possible of 10 images there. Plus 1 for teachers, 11, 1 for admin staff, 12... x 3 schools... 36 images?

Wow. That sucks.

Maybe I SHOULD just nlite the crap out of these things?

P.S. - our computers range anywhere from Pentium 3's with 128 ram/20gb HDD (for elementary students) to dual core Dell's running on 250gb hdd's and 2gb of ram.

---

### Post by theozzlives on 2008-12-06
Just a thought, have you looked into Edubuntu? No licensing restrictions there.

---

### Post by Roasted on 2008-12-06
Oh man, I'd absolutely LOVE 'Buntu to get put into our schools.

I've pushed for it, but I haven't been there a long time to really have much weight in decisions like this.

Then again, we have volume licensing for the district... so if we give a trial run to 'Buntu machines (Probably Dell Optiplex's of some sort) and they don't work out, I could just use the cloning machine (since they'd all be identical units) to blast them back to XP...

But, nonetheless, I think I'm sticking to nLite. I made two copies last night. One XP Pro, one 2K Pro, the two OS's I use a lot at work.

The 2K Pro CD works flawlessly and goes right to the login screen after install.

The XP Pro CD works good too, however at the end of the XP install there's a few steps I can't skip with nLite... such as "would you like to register with Microsoft now?" and the fact I have to add a user... which I hate cause I simply delete all users except administrator once I log in. (We have no need for local users cause we set these computers up on a domain).

---

### Post by rickyjones on 2008-12-07
> **Roasted said:**
> Oh man, I'd absolutely LOVE 'Buntu to get put into our schools.

I've pushed for it, but I haven't been there a long time to really have much weight in decisions like this.

Then again, we have volume licensing for the district... so if we give a trial run to 'Buntu machines (Probably Dell Optiplex's of some sort) and they don't work out, I could just use the cloning machine (since they'd all be identical units) to blast them back to XP...

But, nonetheless, I think I'm sticking to nLite. I made two copies last night. One XP Pro, one 2K Pro, the two OS's I use a lot at work.

The 2K Pro CD works flawlessly and goes right to the login screen after install.

The XP Pro CD works good too, however at the end of the XP install there's a few steps I can't skip with nLite... such as "would you like to register with Microsoft now?" and the fact I have to add a user... which I hate cause I simply delete all users except administrator once I log in. (We have no need for local users cause we set these computers up on a domain).

I used nLite on my latest CD and one of the unattended options is to automatically login once as Administrator. This skips the screen asking you to add a user - it might skip the registration step, I can't recall.

-Richard

---

### Post by nnamdi on 2008-12-07
hello have you heard of arconis it could help you in achiving that just check it out

[www.acronis.com](www.acronis.com)

---

### Post by Roasted on 2008-12-07
> **rickyjones said:**
> I used nLite on my latest CD and one of the unattended options is to automatically login once as Administrator. This skips the screen asking you to add a user - it might skip the registration step, I can't recall.

-Richard

Wow, thanks for that tip. I'll give it a shot! I wonder though... if you would reboot after the initial login, would it just stay at the login screen, requiring the administrator password?

I'll give it a shot right now...

---

### Post by rickyjones on 2008-12-08
> **Roasted said:**
> Wow, thanks for that tip. I'll give it a shot! I wonder though... if you would reboot after the initial login, would it just stay at the login screen, requiring the administrator password?

I'll give it a shot right now...

Yes. It will go to the login screen asking for the administrator password.

-Richard

---

