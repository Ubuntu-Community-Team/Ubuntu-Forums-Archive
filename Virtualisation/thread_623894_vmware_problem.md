---
title: "vmware problem"
date: 2007-11-26
forum: Virtualisation
---

### Post by shayvasa on 2007-11-26
hey every1. i installed vmware and windows in it but when i try to run windows it gives me an NTLDR is missing error...what can i do?

---

### Post by jcsteele on 2007-11-26
NTLDR is a windows specific error, so you might want to check out [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm) for some hints....

Is there a reason why you need to use VMWare?  QEMU/KQMEU is a wonderful program that I recently have begun to use...there is a guide at [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) however, in order to use NTFS you will need to follow my instructions at [http://ww2.coastal.edu/jcsteele/qemu-ntfs.html](http://ww2.coastal.edu/jcsteele/qemu-ntfs.html)

//jcs

---

### Post by nickpaton on 2007-11-26
I'm not able to give you an answer for this, but I've done a forum search against 'NTLDR' and found many posts relating to this.

Hopefully one of them will have the solution you need.

Good luck and if you are still having problems please get back to us.

Nick

---

### Post by shayvasa on 2007-11-26
sorry man but im a real noob i need really simple instructions...i just dont get what they want me to do in that page u gave me

---

### Post by nickpaton on 2007-11-26
No worries there.

I've not used either program, but like the one JC is suggesting.

To help you out, I'll install Qemu and get back to you with some additional suggestions and how to do the NTFS bug fix etc.

It'll be tomorrow UK time before I can get back to you if you can wait that long.

Nick

---

### Post by shayvasa on 2007-11-26
sure ill w8 thanx

---

### Post by nickpaton on 2007-11-27
Hi Shayvasa

Iv'e installed Qemu on one of the PC's and whilst I've got some of it to work, it's quite complex, and I would need to spend a lot of time getting Windows to fully work on it.
Unfortunately I don't have too much time at the moment to do that, but will see what I can do.
As a matter of interest I did get the same NTLDR message as you did in vmware, and the reason for that was I was not able to fully load XP first time around, and decided to see if it would run.
I then got that error message.
I then did a reinstall of XP and reformatted the partition again and this time XP fully installed.

If you want to have a play with it yourself, there's a typo error in the wiki:

```
$ ls -l /dev/kqemu
```  

should read

```
ls -l /dev/kqemu
``` 

Also it doesn't tell you how to run XP once you've installed it and closed it down!

To do this open a terminal and type

```
qemu windows.img
```

worked for me, but I'm not sure if it's correct!

At present I'm completely lost with connecting via Ubuntu to the Internet, and how to install other XP programs via DVD/ CD drive which shows as being not found even though there's a D drive listed.

If anyone else knows the answer to these questions it would help greatly.

As time allows I'll work on this, but I may give vmware a go to see if it's any easier.

Nick

---

### Post by jcsteele on 2007-11-27
There is no typo in the wiki, the "$" is simple a designation that you should type the command in your terminal....if you open a terminal window you will see the "$" as well.  Throughout the wiki this mark is either included, or not included, depending on who wrote/edited the article...I do agree there should be some uniformity.

What part is confusing you?  To start up qemu with windows run:
    $  usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windows/image

This should take care of your cdrom problem as well....and fix some issues with the mouse, and adjust the memory usage to be "512 Megabytes"..you will want to adjust this depending on how much memory your system has.

And just for fun is a screenshot for you....its Windows XP running.  You will notice I created a "Windows XP" icon in the upper right hand corner...just create a launcher item with the above command (fix it to your needs first) and google for an icon, and your just two clicks away from running windows.

//jcs

---

### Post by nickpaton on 2007-11-27
> **jcsteele said:**
> There is no typo in the wiki, the "$" is simple a designation that you should type the command in your terminal....if you open a terminal window you will see the "$" as well.  Throughout the wiki this mark is either included, or not included, depending on who wrote/edited the article...I do agree there should be some uniformity.

Hi JC and many thanks for the reply.  Am I right in thinking that you wrote Qemu; even if you didn't it's a superb program and many thanks anyway for bringing it to my (and Shayvasa's attention).
Re the typo, my bad for using the wrong word there.  The only reason I mentioned it was for Shay's benefit more since if he isn't too familiar with terminal stuff it could cause a little confusion.  No criticism intended M8.

> **jcsteele said:**
> What part is confusing you?  To start up qemu with windows run:
    $  usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windows/image

This should take care of your cdrom problem as well....and fix some issues with the mouse, and adjust the memory usage to be "512 Megabytes"..you will want to adjust this depending on how much memory your system has.

Yup thanks for that and yes it does sort out the CD drive, USB and does start Windows as well.  What more could one ask for??!!

Just one thing (British pedanticness here LOL), there should be a '/' in front of 'usr' !

Would it be worth adding that to the wiki.  I've never personally gone in and changed one so would prefer yourself as I guess the main author of it to do that.

The major hurdle is Internet access.  I'm looking for something quite straightforward, so User mode networking looks good for me, but there's no real info on how to set it up.  I've done a (brief) search but found nothing and tried setting up the LAN card from within Windows, but realised there was more to it than that.

I have a router with a fixed Internet IP of say 10.11.12.13.  
That is connected to a server which has a fixed IP of say 192.168.1.1.  
This PC with combined Ubu and Windows has a fixed IP of 192 168.2.1

Within Ubu, when connecting to the Internet via  Firefox, Proxy settings are http: 192.168.1.1 (with port 8000).

I don't have access to the server or the router to change settings there.

Which method is the best in my case, considering I still will be using straight Ubuntu, as well as the qemu Windows.

Can you possibly guide me through setting up the network to link across to Ubu with that info?

Many thanks in advance

Nick

---

### Post by shayvasa on 2007-11-27
thanx a lot all...ill try downloading qemu and tell u what happened

---

### Post by shayvasa on 2007-11-27
when i do the usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windows/image
command it says bash: usr/bin/qemu: No such file or directory
what can i do?

---

### Post by nickpaton on 2007-11-27
> **shayvasa said:**
> when i do the usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windows/image
command it says bash: usr/bin/qemu: No such file or directory
what can i do?

I pointed this out to JC as well.

It should be 

```
 /usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windows/image
```

/path/to/your/windows /image is probably going to be something like:

/home/<your-home-folder-name>windows.img

For instance my windows.img file is at /home/nick/windows.img, so insert the correct path at the end of the code above.

If that doesn't run then put sudo in front of it, but I don't think it's needed.

Also I got an error that I didn't have enough memory to run 512Mb, so have to use  386 instead - just to advise you if you get a not-enough-memory message.

A neat trick which JC mentioned is making a desktop shortcut.

To create a desktop launcher, right click on the desktop and select 'Create Launcher'
Type - select Application
Name - whatever you want
Command - insert, but change the paths for yourself

```
/usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 386 /home/nick/windows.img

```

Click on the little icon box at the top left corner and select a suitable icon.  It's also possible to grab one from Google and insert it into the images file

Have you managed to connect to the Internet?

Let us know your progress

Nick

---

### Post by shayvasa on 2007-11-28
i still have this problem: /usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 386 /home/shay/windows/image
You do not have enough space in '/dev/shm' for the 386 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=402m none /dev/shm
Or disable the accelerator module with -no-kqemu

---

### Post by jcsteele on 2007-11-28
You are right on the missing "/" in front of the command...i copied/pasted that from the system and totally goofed on that...sorry, but I am glad you figured it out.

As per networking:

If you setup XP, you should end up with one ethernet interface that has a dynamically assigned IP address....this is all handled by QEMU....the IP on my installation is 10.0.2.15 (of note your ubuntu machine's ip is always 10.0.2.2)  This networking is pretty basic, but will give you basic web browsing, etc. but your going to be running bittorrent or playing any world of warcraft with it....

Getting files back and forth between windows and ubuntu:

First off, we need to setup SMB sharing on your ubuntu machine.  Goto System -> Administration -> Shared Folders, and when it asks you if you would like to install the required software to enable file sharing, tell it yes...it will install everything you need.

Now, goto a folder in your home directory (Places -> Home Folder) and either create a new folder, or use an existing folder.  Right click on the folder and click on "Share Folder".  Make sure it says "Share Through: Windows Network (SMB)" .... for a name just type a one work description like "winshare".

Now, we need to add a user to access that share...from the terminal type:

"smbpasswd -a USERNAME"

It will then ask you for a password, much like adding a regular user to the system.

From here we can change our command to start qemu to something like below (i fixed the missing /):

/usr/bin/qemu -usb -usbdevice tablet -smb /path/to/your/shared/folder -localtime -cdrom /dev/cdrom -m 512 /path/to/your/windoiws/image

Notice the new "-smb" section...this is what enables file sharing.  Now you need to boot up the windows xp installation, and goto "My Computer" from there, on the address bar type in "\\10.0.2.2\" and take note of the direction of the slashes...they are very important.  If it all works, it should ask you for a username and password....type in the user information you used above (when you added the user with the smbpasswd command)...now you should be looking at something like in the screenshot attached.  You should see the folder you told ubuntu to share, and if you right click on that folder and tell it to "Map Network Drive..." you can assign it a drive letter (like X:) in my computer to access it quickly. You will have to enter the username/password each time you turn on/off the xp installation though...

I think thats it, let me know of any questions.

---

### Post by nickpaton on 2007-11-28
@ Shay- I had the same problem.  

You need to change 386 part of

```
/usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 386 /home/shay/windows/image
```

to a lower figure which is accepted by your virtual RAM.   Start at 256 and if OK try taking it up a bit until you get the error message then back up a bit.

I have 1Gb of actual RAM and have managed to push mine up to 480Mb of virtual RAM to give you some idea.  512 was too much.

@JC - Many thanks for all that information.

I reinstalled XP and in fact it's been so long since I have done an install that I'd actually wrongly configured the network settings, so it was finger trouble rather than the program!!

One thing I'm finding (and Shay is having problems with it too) is the lack of virtual memory one can have.  
For me having 1Gb of actual memory and only getting 386Mb is not enough if I wanted to do some video editing in XP (about the only reason now to use it BTW!).
Is there any way of tweaking the software to increase this?

Something else worth mentioning is that installing software seems to take an age and causes the CPU to run at 100%.  It does eventually get there but possibly indicates an area for further examination as to why this is so - I guess a lot of it is the virtual memory issue but not sure.

Networking etc - I'm fortunately set up with samba,so combining it with your information will prove invaluable.

Is any of this information easily available on the Internet, other than the wiki?
<Modified> OK there is good stuff if you Google for it, typically

[http://fabrice.bellard.free.fr/qemu/]("http://fabrice.bellard.free.fr/qemu/")

I feel we're missing a trick here - I'd never heard of Qemu but everyone knows vmware, and I think it's about time Qemu was pushed more.

What about a more comprehensive HOWTO on Ubuntu forums giving some of this extra information?  
I don't feel I have the inside knowledge on the software to be able to support such a HOWTO, but you obviously do.
Do you have time to do one - if not I would be happy to write one for you to then put out in public and support the queries.

Again many thanks for your support and advise M8 - 100% excellent.

Shay let us know how you're getting on - I think you're almost there!

Nick

---

### Post by shayvasa on 2007-11-28
how can i link it to my desktop? im a real noob :D

---

### Post by nickpaton on 2007-11-28
> **shayvasa said:**
> how can i link it to my desktop? im a real noob :D

We were all noobs at one time - confession time - I've been doing this for a good while now and am still one, so don't worry LOL.

Desktop launcher - this can be used for all sorts of programs that you have to normally run from a terminal:

[LIST][*]Within the desktop in a spare space, right click on the desktop and select 'Create Launcher'[/LIST]

[LIST][*]Type - select Application[/LIST]

[LIST][*]Name - whatever you want - eg Windows[/LIST]

[LIST][*]Command - insert the code below, remembering to change the windows.img path and the correct amount of virtual memory for yourself[/LIST]

```
/usr/bin/qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 386 /home/shay/windows/image
```

[LIST][*]Click on the little icon box at the top left corner and select a suitable icon. It's also possible to grab one from Google and insert it into the images file.  I'll come back with a detailed explanation if you need this [/LIST]

I'm also looking at a more comprehensive start up list which will include sound, and will post when working.

Nick

---

### Post by nickpaton on 2007-11-28
Some progress in getting sound, start with full screen and tweaking USB function.

[LIST][*]**Full launcher command Line**[/LIST]

For all this functionality modify your Qemu Windows desktop launcher as follows:

On the launcher icon right click, Properties > Launcher.

Command, change this to read:

```
 /usr/bin/qemu -usb usbdevice tablet -soundhw all -localtime -full-screen -cdrom /dev/cdrom -m 480 /home/nick/windows.img
```

Description of each added invocation:

[LIST][*]**Sound**[/LIST]

```
-soundhw all
```

'-soundhw' is the invocation for loading and using the audio drivers.

'all' offers all the available audio drivers.  This includes a generic driver for Creative Soundblaster cards based on the sb16 but which configured my sb Live! 5.1 OK.

Sound took ages to install and finally hung when it had detected and installed the games port software.  
When Windows was rebooted the sound driver was found to be correctly installed and worked OK.

[LIST][*]**Start with full Screen**[/LIST]

Add the invocation 

```
-full screen
```

Windows will launch as full screen without having to use the Ctrl-Alt-F keys.

[LIST][*]**USB Tweaks**[/LIST]

The invocations within the command launcher are quite configurable.

For instance if you are using a desktop PC and a PS2 mouse, you can removed the 'tablet' invocation from 'usbdevices tablets'. This is only required for laptops with a mouse tablet.

I'm currently working on configuring the correct invocation for a USB flash drive (a corsair flash voyager) but plugging it in causes both Ubuntu and Windows to hang.

[LIST][*]**Other Issues**[/LIST]

Also I've installed Firefox with the major Java & flash drivers, but can't get Alternative Real Player to work when listening to BBC Radio 4, which causes Windows to crash out into Ubuntu which in turn needs to be restarted.  Working on that too.

Also still concerned about the CPU running at 100% for a lot of the time, but noticing that it does eventually drop right down to 10% or so.
Also programs are taking some time to load, but this could be due to the lack of virtual memory.

[LIST][*]**Documentation**[/LIST]

The documentation I'm finding most useful is 

[http://fabrice.bellard.free.fr/qemu/qemu-doc.html]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html")

which goes into the invocations in a lot more detail.

---

### Post by shayvasa on 2007-11-28
i copied the command exactly how u wrote it in the luncher and it didint work

---

### Post by jcsteele on 2007-11-29
> **nickpaton said:**
> 
[LIST][*]**USB Tweaks**[/LIST]

The invocations within the command launcher are quite configurable.

For instance if you are using a desktop PC and a PS2 mouse, you can removed the 'tablet' invocation from 'usbdevices tablets'. This is only required for laptops with a mouse tablet.


This functionality is actually very useful to everyone....you do not need a tablet PC to enjoy its benefits.  Without it, your mouse will be "locked" into the active QEMU window....you can not move it outside without using the input combination "CTRL+ALT+LEFT CLICK" (or something of that sort...I have forgotten exactly off hand) which can get rather annoying real fast....with the tablet functionality the mouse is not locked into the active QEMU window, and is allowed to flow freely between QEMU and your regular desktop session...basically no keyboard interaction needed.

//jcs

---

### Post by jcsteele on 2007-11-29
> **shayvasa said:**
> i copied the command exactly how u wrote it in the luncher and it didint work

You will need to modify the path's to point to your current windows image in YOUR directory structory....

Example:
  Find the image you created when you installed qemu and windows....then simply copy the working directory path into the command.  For my case, it is /home/jcsteele/win32/winxp.img and yours will be something different. (most likely /home/INSERT_YOUR_USERNAME_HERE/ will start it off...the rest depends on where you created the windows image)

//jcs

---

### Post by jcsteele on 2007-11-29
> **nickpaton said:**
> 
One thing I'm finding (and Shay is having problems with it too) is the lack of virtual memory one can have.  
For me having 1Gb of actual memory and only getting 386Mb is not enough if I wanted to do some video editing in XP (about the only reason now to use it BTW!).
Is there any way of tweaking the software to increase this?

Something else worth mentioning is that installing software seems to take an age and causes the CPU to run at 100%.  It does eventually get there but possibly indicates an area for further examination as to why this is so - I guess a lot of it is the virtual memory issue but not sure.

Is any of this information easily available on the Internet, other than the wiki?
<Modified> OK there is good stuff if you Google for it, typically

[http://fabrice.bellard.free.fr/qemu/]("http://fabrice.bellard.free.fr/qemu/")

I feel we're missing a trick here - I'd never heard of Qemu but everyone knows vmware, and I think it's about time Qemu was pushed more.

What about a more comprehensive HOWTO on Ubuntu forums giving some of this extra information?  
I don't feel I have the inside knowledge on the software to be able to support such a HOWTO, but you obviously do.
Do you have time to do one - if not I would be happy to write one for you to then put out in public and support the queries.
Nick

The maximum ammount of virtual memory is probably indeed hard wired into the program somewhere, however I would guess it is done so with reason...for an example:  In your system you have 1GB of memory, however you cannot allocate all of this memory to qemu/windows.....if you did ubuntu would indeed crash, lock up, become uselessly slow, etc. (insert your favorite word for "utter chaos" in there)...you need a moderate percentage value based on your existing physical memory.  With your installation, 386 is apparently that number (i believe mine is around 760 for 2GB of physical memory)...

As per the CPU problem...running QEMU is a very taxing process, not to be done lightly by older computers....your sluggish performance will make things virtually not useful, defeating the purpose of QEMU.  Also, I don't believe QEMU can leverage hosts with multiple CPU's at the current time....a real drawback, but again only an issue on older machines these days.

As per the howto, I was thinking of writing something and putting it on my webpage (i still might), but if you use google, it will return numerous articles, wiki pages, mailing list posts, etc. with alot of questions answered, so right now I dont feel a real need to write such a thing....if anything, I was going to put a post up on [www.ubuntuguide.org](www.ubuntuguide.org) about it, but that will have to wait for the weekend until classes are over for me.

//jcs

---

### Post by nickpaton on 2007-11-29
Yeah it figures regarding the spec of my PC - Athlon XP3200 chip with 1Gb ram.

I think I'll probably leave things as they are at this point, and as time allows to play further with it.

It's a very interesting piece of software which should be more widely known and when you get the hang of it, not so difficult to set up.

Thanks for your help JC.

Shay, I'll keep an eye on this post and offer what help I can.

Nick

---

### Post by shayvasa on 2007-11-29
ok...if i have it in my desktop hot should it be?

---

### Post by nickpaton on 2007-11-29
In post #17 I described how to put it on your desktop.  You use an app called the Desktop launcher.

Is this what you are after?

Also have a look at the more comprehensive startup command which I posted in post #18.
It will cause Windows to be launched full screen and sound to be added.

Are you still having problems with getting the launch command line to work?  If so can you tell me the name of the folder where you have windows.img file?   Mine's in home/nick/windows.img.

Anything else get back to us.

Nick

---

### Post by shayvasa on 2007-11-30
ok heres the problem when u mean windows.img file do u mean the windows installation file? cause i have windows.iso on my dektop...maybe that is y this isnt working

---

### Post by nickpaton on 2007-11-30
Am I right in thinking that you haven't yet managed to even get Windows started, never mind using a desktop shortcut to start it? 

> **shayvasa said:**
> ok heres the problem when u mean windows.img file do u mean the windows installation file? cause i have windows.iso on my dektop...maybe that is y this isnt working

OK, it's not the windows.iso file you're looking for - I guess that's what you used to install Windows in the first place.
The file you're looking for is called windows.img which is the file generated when you install windows qemu.

To find where it is: Places > Search for files.

'Name contains' type - windows.img

'Look in Folder' - should show your home folder name (mines Nick)

Click search now button and hopefully you will see where it is.  Mine is in nick.

If it's on the desktop, it will show the path as shay.Desktop

If it's not there, try changing Look in Folder to Desktop.  I tried doing a search in File system but for some reason it didn't find it.

So from that result you can change the 

```
 /usr/bin/qemu -usb usbdevice tablet -soundhw all -localtime -full-screen -cdrom /dev/cdrom -m 480 /home/nick/windows.img[/CODE

path to wherever the windows.img file is located.

So if it is in your home folder it will be something like:

[CODE] /usr/bin/qemu -usb usbdevice tablet -soundhw all -localtime -full-screen -cdrom /dev/cdrom -m 2856/home/shay/windows.img
```

If it's in a subfolder of home, say temp for arguments sake, then it will read:

```
 /usr/bin/qemu -usb usbdevice tablet -soundhw all -localtime -full-screen -cdrom /dev/cdrom -m 286 /home/shay/temp/windows.img
```

If it's on your desktop then it will read similar to:

```
 /usr/bin/qemu -usb usbdevice tablet -soundhw all -localtime -full-screen -cdrom /dev/cdrom -m 286 /home/shay/Desktop/windows.img
```

Then when you have windows working you can create the launcher using the correct command file from one of the above (with alterations for yourself)

One thing I will say is that it may be that your PC is not powerful enough to run Windows under Qemu.  See the posts between JC Steele and myself above about this.  I personally cannot run it very well coz I have an older PC with an Athlon XP3200 CPU and 1gig of memory.  Just to warn you M8!

Hope that helps

Nick

---

### Post by AndyCooll on 2007-11-30
Usually that message refers to not finding the file required for booting the OS. We used to find that frequently happened when someone had left a floppy disk in the floppy drive, and that was the first boot option.

:cool:

---

### Post by shayvasa on 2007-11-30
it says file not found :(

---

### Post by nickpaton on 2007-11-30
I'm not sure what to suggest - my windows.img installed into my home/nick directory.  Have you tried doing a manual search in yours Places > Home Folder.

Mine's the last entry there.

And if it is there, the path you need to add is shown under 'Location' near the top.

I wasn't given a choice as to where it would be installed, so it seems to go there as a default.

If you cannot find it. I'm not sure what else to suggest.

Nick

---

### Post by shayvasa on 2007-11-30
no there :(

---

### Post by nickpaton on 2007-11-30
Sounds like you haven't actually installed Windows within Qemu.

I'll post tomorrow with some more detailed instructions of how to do it, since if you are not too familiar with Ubuntu, the wiki is maybe not 100% clear for you.

Nick

---

### Post by jcsteele on 2007-11-30
For those interested, I suggest checking out [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) which will help improve your linux command line skills.

I have seen quite a few comments stating that the Wiki article is not detailed enough, or too confusing.  I mention the above URL to check out only because I think its important to stress that you will need to know the basic unix commands (and at least a partial understanding of them) to do anything more complicated than word processing and web browsing in ubuntu...like setting up a machine emulation software to do a very complicated task....I think the wiki article was written in a fashion that seems complicated, etc. simply because its like looking at an algebra book without knowing basic addition/subtraction....as my professor says, its like "trying to identify a cell on a microscope slide without knowing anything about biology" - your not going to get very far without asking the run down of usual questions.  However questions are a good thing, but I just wanted to suggest that to all who think they need it...I am not trying to offend anyone here, I am just trying to say that if you spend some time learning some more unix/linux and ubuntu, and less time getting frustrated because a complicated task isn't working for you, in the end it will be rewarding when you look at the wiki article and say "oh, that makes sense now..."

For the time being, a small guide to get things going...

Make sure we are in the proper home directory
$ cd

Install qemu
$ sudo apt-get install qemu

Create the QEMU image of size 6 Gigabytes
$ qemu-img create -f qcow windows.img 6G

Now put the windows XP cdrom in your drive and boot from it
$ qemu -localtime -cdrom /dev/cdrom -m 128 -boot d windows.img

A window should now pop up that looks like the Windows XP installation...this will probably take at least 1-2 hours to complete (i.e. installing windows) and you will have todo the usual windows installation tasks like set up hard drive partitions, enter your product key, setup the initial user, configure the network settings (leave everything at the default), etc.  

Once its done, and you want to run Windows XP again type:
$ qemu -usb -usbdevice tablet -localtime -cdrom /dev/cdrom -m 128 $HOME/windows.img

The above should work on any newer hardware with no problems...it does not use any KQEMU acceleration (this is cpu dependent) and the memory is at 128megs...so you will need at least 512megs in your system to run the above at the minimum, however I suggest if you make the "-m 128" in each of the commands be something a little bigger if your system has the memory (i.e. if you got a gig of memory, set it to "384" etc.)  Its designed to be failsafe, not run the best.

//jcs

---

### Post by shayvasa on 2007-11-30
ok thanx

---

### Post by dpj23 on 2007-11-30
When your computer starts, the BIOS attempts to find the primary hard drive's active partition to read the first sector for the MBR (Master Boot Record), it uses that info to load the rest of the OS.  For Windows NT4/2k/XP the NTLDR (New Technology Loader) takes it from there.  If you get the "NTLDR is missing, press any key to restart" what's most likely going on is the BIOS either didn't look for the right drive, didn't find the right partition, it wasn't active, didn't find the MBR, or the MBR didn't list NTLDR in the right place,  the location of NTLDR changed, or you are looking at a hardware failure situation

I would delete the the VM machine and re-build a new one...

---

### Post by nickpaton on 2007-12-01
> **dpj23 said:**
> When your computer starts, the BIOS attempts to find the primary hard drive's active partition to read the first sector for the MBR (Master Boot Record), it uses that info to load the rest of the OS.  For Windows NT4/2k/XP the NTLDR (New Technology Loader) takes it from there.  If you get the "NTLDR is missing, press any key to restart" what's most likely going on is the BIOS either didn't look for the right drive, didn't find the right partition, it wasn't active, didn't find the MBR, or the MBR didn't list NTLDR in the right place,  the location of NTLDR changed, or you are looking at a hardware failure situation

I would delete the the VM machine and re-build a new one...

I too had the same error msg when the first install XP via Qemu bombed.
Reinstalling solved the problem.
I also asked someone else who has just installed vmware twice and he's not come across the problem.  
I think he needs to make sure that he has a clean install and if it bombs to reinstall having reformatted the virtual drive.

@JCS - thanks for the great link - I'll certainly be reading it closely!.

I wasn't implying criticism of the wiki, but for instance you will agree that after the Windows install there should be a line to tell you how to run the program - a somewhat major omission!!
This was why I was suggesting a more comprehensive HOWTO which will fill in these holes, together with adding various invocations and their switches.
Really a pulling together of the various bits of information into one place.

I agree with what you're saying though and no offence taken - in fact the more information I personally can have the better - but I do wonder if this is one for people who have been with Linux for a while.

A couple of extra links:

[http://linuxcommand.org/]("http://linuxcommand.org/")

[http://psychocats.net/ubuntu/terminal]("http://psychocats.net/ubuntu/terminal")

and the link at the bottom of that page as well.

@Shay - if you want me to provide more clarity to the wiki for you please get back to me.
JC is right though M8 - we all need to learn more about the basic Linux commands so that we can understand these wiki's more.  
This is typical of how they are written since the authors assume you know the basic commands.
Call it a learning experience if you like and be liberated by gaining more knowledge!

Nick

---

### Post by shayvasa on 2007-12-01
ok thanx a lot all...i think i got it

---

