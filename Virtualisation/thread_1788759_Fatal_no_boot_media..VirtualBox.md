---
title: "Fatal no boot media..VirtualBox"
date: 2011-06-23
forum: Virtualisation
---

### Post by Ginzell on 2011-06-23
Hi all,
I'm sorry to post yet another VB Fatal: Could not read from the boot medium; system halted! error, but I've looked and looked for an answer and have not been able to come up with anything that works.

Downloaded VB from VirtualBox.org- installed fine, when I go to install guest OS WinME from CD installation, I get the above error.
It is mounted as far as I can tell, unless something is missing.  See screenshot please. I also disabled the USB in case there was a conflict, but it didn't help.

Ubuntu 11.04
Current version of VB
Any help much appreciated.

---

### Post by varunendra on 2011-06-25
You haven't created a virtual hard disk. So your virtual machine is a machine without a hard disk, hence the error.

To add one, goto the same "storage" settings as in your first snap, then right-click "IDE Controller" icon and select "Add Hard disk". Then follow the steps to create a new disk or add an existing one.

---

### Post by Ginzell on 2011-06-25
My apologies, I did (do) have the virtual hard disk, I was trying different things and when I took that screenshot I hadn't put it back in. 
 
I still cannot make this work.  I've even been able to boot to my Ubuntu disk to add it as a guest OS so I know the CD/DVD is working.  I also can boot to the Windows disk outside of the VB, so I am not sure why I cannot boot to it within the VB.  I've been searching this answer out for days now and I'm so aggravated that I cannot get this going.  

Thank you for any help,:confused:

---

### Post by varunendra on 2011-06-25
Quick suggestions:

[LIST=1]
[*]Try adding hard disk as IDE Primary Master and CD/DVD drive as IDE Secondary Master,
[*]Try creating iso of the CD and mounting it in VBox.
[/LIST]
Can you post the entire content of the configuration file of your virtual machine? I hope that may tell more than screen shots.

---

### Post by Ginzell on 2011-06-25
Ok, I've switched machines so here's what I have now. (it's all the same as the other one, cept this VB is SUN and the other one is OSE- just in case you was wondering about the diff SS's)  

Did suggestion num 1. No joy. As for suggestion 2, I've seen lots of responses from people with this same problem that say they've done that and it didn't work, and since it's such a pain to do, I've not attempted it because frankly I can't understand why it wouldn't just boot from a bootable disk since it's supposed to be able to..if that makes sense.. I guess I was just trying all other options before I went through the trouble to burn ISO.  At any rate, I'd be willing to try anything if all else fails.  

You said post my conf file for the VM..where can I get that?  

Thanks so much for trying to help me.

---

### Post by varunendra on 2011-06-25
The first suggestion was based on my experience with some physical machines with ancient hardware/BIOS (BIOS went crazy whenever two particular drives were connected to same IDE port).

The second one was a wild guess assuming there may be some communication error while virtualizing the physical drive.

The configuration file is located in the same place where you've created the virtual machine with extension name ".vbox"(should be **WinME.vbox** in your case).

I've never had an original WinME boot disk. I created one myself by creating a DOS bootable CD and placing dump of installation files of different versions on it (WinME, 98SE etc.). So basically I used to boot into DOS with CD support and invoked the setup from there. It still works everywhere including VBox. However, on VBox I've tried its iso only, not a physical disc.

So how does your CD's booting goes (on physical machine)?


**EDIT:** I can't handle so many thanks, especially when nothing is proving helpful!! ;)
So let's just talk without inclusion of thanks and sorrows. :)

**EDIT2:** I just realized the default path to configuration file in ubuntu is:** /home/<your username>/.VirtualBox/Machines/<your virtual machine name>/<your virtual machine name>.xml**.
i.e., it will be an xml file (same in windows, only extension name differs).

---

### Post by Ginzell on 2011-06-25
I'm having trouble finding this config file.  I looked for vbox and for the XML and can't find either named what you're calling it.  I don't even have a .VirtualBox/Machines folder.. 

You ask me how my CD's booting goes on physical machine?  I'm kinda confused by that question - are you asking if I can boot at all?  

As for the inclusion of the "Thanks" - that has been a long on going "issue" here in my household, from my son saying Thank you to everything and anything and it just falling out of his mouth as easy as "Hey", to his Girlfriend not even knowing how to say Thank you for ANYTHING - so begins the cycle of how much THANKS should one get/give.. My Thanks to you was well deserved in my opinion because it's been almost 2 days with no reply at all to my original post. And even if you think it's not helpful, it is because that's the game - troubleshooting - narrowing down - learning what the solution it is or is not. Process of elimination. So there you have it, my reasoning behind the Thanks.  

Ok so back to it, booting into DOS and invoking the setup there..that's a good thought, but I still would need CD support..unless..I did the ISO.  Darn.  I think I'm really fighting doing that.

---

### Post by varunendra on 2011-06-25
Hmm.. sounds pretty reasonable now, no objection to thanks from now on.. :)

As for ability to boot from CD, you mentioned that you managed it, although with an ubuntu CD:
> **Ginzell said:**
> ....
I've even been able to boot to my Ubuntu disk to add it as a guest OS so I know the CD/DVD is working.
....

The ~/.VirtualBox/Machines... location is default for ubuntu. To see any directory or file whose name starts with a dot (.), you must enable 'Show hidden files' in nautilus (or just press "ctrl+h") as they are hidden by default. Although I presume you already knew that.

Try this in terminal:
```
gedit ~/.VirtualBox/Machines/WinME/WinME.xml
```this should open the file in gedit if it exists.

You may use following command to find its location (assuming its name contains WinME):
```
ls -Ra ~/ | grep WinME
```It will search your entire home directory to see if any file/folder exists with 'WinMW' in its name.
Another way to find the location would be to create a new machine and at the step where virtual box asks to select location for virtual disk, click on "browse" button. It should open the browser in the default location where your WinME machine is already located. (you can obviously cancel the machine creation process then).

When I asked 'how booting goes' I meant - does it boot into DOS shell, or some GUI over DOS shell, or in win nt mode (like XP)? Because if it boots into DOS and immediately tries to invoke some app (setup.exe??) from CD, then the CD driver included in DOS mode must support your virtual CD drive and virtual IDE adapter. Else the booting would complete, but it will halt on the step of invoking the desired application because it won't be able to read CD contents (out of boot area) due to unsupported driver.

As another wild guess, have you tried changing IDE type under "storage" settings?


**PS:** As a side note, my DOS CD with ME setup boots fine on VBox. CD was made bootable using bootable floppy image created within an ME system (EBD- Emergency Boot Disk).
My virtual IDE controller type is "PIIX4".

---

### Post by Ginzell on 2011-06-25
The first command I ran returned an empty file.  The second command returned the actual program, and vbox-prev which I opened and it contained a bunch of stuff that looked like IPs and HTML.. 

As for the IDE type, no, I haven't changed it, what would I change to?  

And the boot issue, I'm not sure what it booted into, my husband gave the disc to me and said "it boots". I'm assuming it booted as it would to start installing.  I guess I could try it now but I'm delirious at this point, I haven't slept all night.  
I had figured I'd end up having to try the ISO thing, but I had a hard time doing it when I made this ISO for Ubuntu so I don't have a clue what I did.  At any rate, it would probably be a different process creating an ISO from the Windows install CD. I started looking for that info, but like I said, I'm tired, my brain is on overload and I think it's shutting down. 
I'll be back on later but right now time for bed.

---

### Post by varunendra on 2011-06-25
Good Night! (if it is still night there at all! :))

When you get back to it again:-

Enter this command into a terminal:
```
gedit ~/"VirtualBox VMs"/WinME/WinME.vbox
```This will open the file we need (not blank this time). Just copy-paste its contents in your next post. (wrapping the pasted content in html tags (<>) would be a good idea).

Alternatively, you can just attach the file itself in your next post.


I'm now confused about two things, please confirm these-

[LIST=1]
[*]Did you use an iso image or a physical CD to install ubuntu in Virtual Box?
[*]Have you checked yourself the WinME CD that it works on physical computer?
[/LIST]
> **Ginzell said:**
> ....
I also can boot to the Windows disk outside of the VB, so I am not sure why I cannot boot to it within the VB.
....
 
It maybe that you got a working CD but now it is corrupt due to scratches or whatever. So if you haven't tested it yourself, do it now!

There is no point in creating iso from a corrupt CD, so first make sure the CD is ok. And by the way, creating iso image shouldn't be a problem. Just insert the CD in drive, open brasero > choose "Disc Copy" > Select Write to: Image File > click properties > change Disc-image-type from 'toc' to 'iso' > close > click "create image" .... done!

As for IDE controller type, my VBox version (4.0.4) has three options: PIIX3, PIIX4 and ICH6. Try all of them one by one (whatever option you have).

But the very first step for you is to verify that the CD works and is not corrupt!

---

### Post by Ginzell on 2011-06-25
Ok before we go any further, I'm looking at this WinME disc.  First off it's an upgrade (I do have the req'd software for it) but I'm thinking these are maybe not bootable, don't we just stick them in when in Windows and they start up and do their thing? I also have Windows 2000 full version - but it's not booting just from a restart - what can I do now? Yeah, I didn't test myself, and it didn't occur to me off hand.  I've got tons of recovery discs for PC's and laptops I've bought over the years.Wonder if one of those would help me boot.  I used to do this years ago, I'd reformat entire HDs and install the OS's, I'm trying to remember - something about FDISK -FORMAT-Partions..ugh..having to get the CD working then I could just install from there.. dang, it's been a while. 

To answer real quick one of your questions- I downloaded the Ubuntu ISO when I was in Windows and burned it to disc and that was what I was booting off of to install Ubuntu.  The reason I had problems to begin with on that was because I didn't know there was a difference between burning and copying image files and I used the wrong CD/DVD type etc.  My burn prog in Windows didn't have the option to burn ISO..on and on..:D

So I'll wait for you to tell me something on the above before I go any further because I'm guessing that's the problem.
On a side note, I LOVE LINUX/Ubuntu!! I'm new to all this but it has opened a whole new world for me.

---

### Post by varunendra on 2011-06-26
I am not familiar with Windows ME (or previous versions') upgrade disks, so can't say if it contains all the files required for installation. If you are not sure either, you can post the files-list with file-sizes which I can compare with my installation files. Commandline is your friend to generate such a list. Besides, the CD must be bootable with CD drive support.

Assuming that the installation files "are complete", but the disc is not bootable, we can try workarounds, some of which are guaranteed to work but it depends upon how much you are willing to go 'non-standard' methods.

One such simple (but non-standard) way to do so would be to :

[LIST]
[*]download a DOS - bootable floppy image from [here]("http://www.allbootdisks.com/downloads/Disks/Windows_ME_Boot_Disk_Download50/Diskette%20Images/WindowsME.img"),
[*]boot VBox using that floppy image, create two partitions using fdisk (C: being large, D being slightly above the size of installation files),
[*]format both C: and D: (after a reboot),
[*]Now boot from your ubuntu iso, insert WinME CD, and copy the contents to virtual D: drive. *[For this you'll need to add two CD drives to the IDE controller - one using ubuntu iso and the other your physical drive.]*
[*]Reboot with the floppy image, go to D: drive, invoke "setup.exe".
[*]The rest depends on whether the installation files are complete or not!
[/LIST]
One critical issue I noticed with these DOS bootable floppies was that they often hung if you chose to boot with CD ROM support. This required me to proceed me with "shift+F8" (stepwise booting), and dropping some certain drivers. But that shouldn't be an issue since we are not using its CD support in above steps (we used ubuntu iso to copy WinME cd contents). So just choose to boot without CD ROM support.

If this seems too troublesome to do, we can think of other ways if you are willing to try, only it may stretch this thread to a few more pages I'm afraid :). Besides, if you can find any Win95/98 or ME recovery disc among your 'tons-of-recovery-discs', it'd be quite trivial to proceed with them.

My apologies in advance if I confused you.


**EDIT:** Some useful bootable floppy/cd images: [http://www.allbootdisks.com/download/me.html](http://www.allbootdisks.com/download/me.html) (also the source of above floppy image link)

---

### Post by Ginzell on 2011-06-26
I don't mind going through things to try to get to the end I'm seeking.  I always hope for the easiest way of course.  I'm wondering now, this suggestion about the DOS boot and fdisking, I'm guessing since I'm going to be inside the virtualbox, nothing I do inside there can harm my outside OS, correct?  

About the recovery discs, what I have are the discs that ship with PC's or laptops, and I read somewhere that someone was trying to use hers and it didn't work.  Although, I could try it myself.  I'm not sure why it wouldn't work if I'm using the exact disc that shipped with this laptop, but having said that, I have no idea how that is handled within Ubuntu on VB.  

On the commandline for the list of ME install files, what is the command to get that list?  At least I can see if these are complete.

---

### Post by varunendra on 2011-06-26
> **Ginzell said:**
> ..since I'm going to be inside the virtualbox, nothing I do inside there can harm my outside OS, correct? Correct.

> **Ginzell said:**
>  I'm not sure why it wouldn't work if I'm using the exact disc that shipped with this laptop..must work on the laptop itself, but may not work with any virtual machine inside it.. because if it is not an automated installation disc, instead- an image of installed OS, then the device drivers and corresponding settings won't match any other hardware - virtual or physical, causing a failed recovery/installation effort.

> **Ginzell said:**
>  On the commandline for the list of ME install files, what is the command to get that list?  At least I can see if these are complete.
For windows/DOS, open command prompt, go into the folder where the files are, then-
```
dir /a /s > D:\list.txt
```
where D:\list.txt is an example path/filename which you can change as required.

For ubuntu, open terminal, go into the folder, then-
```
ls -la > ~/Desktop/list.txt
```
which will create list.txt file on your desktop. [it is small "L" in the command, not capital "i"]

---

### Post by Ginzell on 2011-06-26
Oh yeah, I forgot about the hardware etc. for the recovery disc.  Makes perfect sense.  

Ok, I am trying to make the list, I'm doing it from inside Ubuntu, so I navigate in File Manager to check the disc in the CDROM to make sure it's there and it is, but when I go into Terminal to make the list I can't get into the media folder.  It's saying it doesn't exist. Am I typing it wrong - "cd ~/media"  ? But while I was in File manager I see a few files and then several folders - is that what's going to show up in the list?  Because I'm thinking that won't list all the files then without going to each folder..? I also tried "cd ~/media/Windows Me

I have to thank you again, because I am learning a lot through this process and waking my brain up- doing lots of remembering.  :D
I downloaded the Windows ME boot from your link, it's an .img file - how do I use it to boot? I did look at the help section on that site, but I must be missing it.

EDIT: Found the media folder..no ~ needed ha!  
EDIT2: OK I made the list but it has nothing but this in it : 
total 9
drwxr-xr-x  3 root root 4096 2011-06-26 03:35 .
drwxr-xr-x 22 root root 4096 2011-06-13 18:25 ..
dr-x------  1 liz  liz   570 2000-06-08 12:00 Windows Me

What am I doing wrong? Oh and that's not what's on the disc either.  I've got several folders and a few txt files, the autorun and the setup.exe

---

### Post by varunendra on 2011-06-26
Remove ~ from your command. It stands for "<current user's home>", while 'media' directory is located in root ('/'), not your home folder. To see full path to your CD, use **mount** command. It will show all mounts, with the cdrom mount at the bottom (something like- "/dev/sr0 on **/media/<the label of your WinME cd>**"

So the correct command to get into the installation folder would be something like-
```
cd /media/<remaining path to the installation folder>
```

The source having several files is okay, but most of the 'several folders' may be useless for us. For our particular method- we need only core installation files which should be placed together in any one folder. Its size should be around 154 MB, give or take a few MBs. It maybe named "W9XFLAT", but I'm not sure.

But anyway, you can also just add 'R' to ls parameters to get a recursive list (files/subdirectories within directory/subdirectories):
```
ls -laR > ~/Desktop/list.txt
```

As for using floppy image, you need to have a virtual floppy drive added into VirtualBox. If it's not already there, goto 'storage' settings > add a 'floppy controller' > add a floppy drive (choose to leave it empty).
Then in floppy drive's option, choose to add a floppy image > browse to downloaded image > load it and boot virtual machine (make sure 'floppy' is included in 'System' > Boot Order')

---

### Post by varunendra on 2011-06-26
> **Ginzell said:**
> 
EDIT2: OK I made the list but it has nothing but this in it : 
total 9
drwxr-xr-x  3 root root 4096 2011-06-26 03:35 .
drwxr-xr-x 22 root root 4096 2011-06-13 18:25 ..
dr-x------  1 liz  liz   570 2000-06-08 12:00 **Windows Me**


OK, the final command that "should" generate required list:
```
ls -laR /media/Win*/ ~/Desktop/list.txt
```(make sure to delete the previous "list.txt" file before trying above command).

_A Side Note_: Actually, the "Windows ME" is your CD's name. The files should be within it. You just listed the '/media/' folder, not the win folder in it.


EDIT: If, in the above command, **Win*** doesn't work, replace it with **"Windows ME"** (WITH quotes, since it contains a blank space).

---

### Post by Ginzell on 2011-06-26
Finally got that file.  I can't upload it here it's exceeds the limit for that type of file on upload.  Do I paste it then?  I wanted to make sure before I did.

---

### Post by Ginzell on 2011-06-26
OK also, I went ahead and started the process of FDISK'ng etc.  Was able to boot to floppy..yay...
*Created 2 Partitions - C, D
*Formatted both
*Wanted so bad to boot with CD support, froze up like you said. 
*Now am trying to boot to my Ubuntu ISO- it will pop up the first purple screen then it freezes black with a "_" at the top of the screen.  I even tried to boot to the CDROM with Ubuntu on it, still froze.  So I went into the Ubuntu VM that I was going to create at one time( but only had gotten as far as trying it at the time.)  But anyway I wanted to make sure the ISO was working and it was -booted fine.  I noticed some differences like it has a SATA  and a VDI - is that something I will need to make on the ME one too?  
Anyway that's as far as I can get. 
I'm starting to get sleepy - I spent another night awake.  It's actually 8 AM so I should be getting up instead of going to sleep but I am a night person I guess.

---

### Post by varunendra on 2011-06-26
> **Ginzell said:**
> Finally got that file.  I can't upload it here it's exceeds the limit for that type of file on upload.  Do I paste it then?  I wanted to make sure before I did.
If you can find the folder with the core installation files, folder size being around 154 MB, then the list won't be much long to exceed size limits. Pasting contents is also an option, only make sure to wrap the pasted list in [ code].... [ /code] tags (# icon on top of post editor box).


> **Ginzell said:**
> ....
*Wanted so bad to boot with CD support, froze up like you said. 
*Now am trying to boot to my Ubuntu ISO- it will pop up the first purple screen then it freezes black with a "_" at the top of the screen.
Sorry, my fault, I forgot to consider the memory limit. Just temporary increase the memory (RAM) for the WinME machine to what you've set for the ubuntu machine, then retry ubuntu iso. After the ubuntu iso has done its job, you can reset it to current limit.

You may also boot with CD support, just press "shift+F8" at the WinME boot menu, then drop following drivers (press Esc to drop):

[LIST]
[*]DEVICE=ASPI2DOS.sys
[*]DEVICE=ASPI8DOS.sys
[*]DEVICE=ASPICD.sys
[*](press enter for the rest)
[/LIST]
> **Ginzell said:**
> I noticed some differences like it has a SATA  and a VDI - is that something I will need to make on the ME one too? I guess no. Increasing RAM limit should be all you need.

> **Ginzell said:**
> 
I'm starting to get sleepy - I spent another night awake.  It's actually 8 AM so I should be getting up instead of going to sleep but I am a night person I guess.
sorry for that too :). Actually I fell too sleepy to keep up after my last post, have just returned after a nap (lucky me!). It's 8:27 pm here now! But I have no particular schedule to sleep or wake up! It keeps changing :D...


**PS:** I see that you just "Spilled the Beans".. Congrats! (although we are gaining experience more in WinME and VBox rather than ubuntu itself so far.... But hopefully, the experience in everything goes side-by-side!).

---

### Post by Ginzell on 2011-06-26
Yeah, I noticed I had jumped up to "Spilled the beans"!  I feel like I'm fitting in just great! :)
I have no sleeping pattern either, I just kind of fall asleep with the laptop on my lap.  OR with my iPhone in my hand.  It's a great source of entertainment for my husband to catch a picture of me and then laugh at them with my kids.  What a great guy! :)

So for the last hour I've been finally getting to what I've been trying to do for days!! I got WINME Installed!!!!! 
I can't believe it!!! I used the shift f8 and dropped the drivers like you said and just booted to the ME disc. I had fun trying to figure out which letter my CDRom was because I had added several drives through the process - ended up being G.  
I would never had been able to do this without your help,  I haven't seen this kind of detail for this issue in any of the threads I searched.  You went above and beyond - THANK YOU!!  
I'm thinking I might try to do a YouTube video on this process. 
YAYAYAYYAAYYA Marking solved!

---

### Post by varunendra on 2011-06-26
It's 7:34 am here and I'm up.... to be greeted with a thanks via PM,  and then this over-generous post of yours! Again - "lucky me!!". :) Thanks to you for starting my day in so pleasant mode!

> **Ginzell said:**
> I'm thinking I might try to do a YouTube video on this process.
- A very good idea indeed.


**_PS_:**
Now that it has been established that your installation files on that disc are complete, you may wish to try to make that CD bootable with the help of the downloaded floppy image. If you do, you can use apps like Nero/K3B or any similar one having the capability to create a bootable cd with a boot image. Or you may simply use **mkisofs** command to achieve that, just google for that. This will create an iso or cd that will boot just like the floppy did, and will contain all the files that are on your current CD. Just FYI!

---

