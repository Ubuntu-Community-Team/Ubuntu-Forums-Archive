---
title: "Ubuntu Desktop Next - black screen with cursor"
date: 2014-10-07
forum: Ubuntu Development Version
---

### Post by IdoSC on 2014-10-07
Hello everyone!

I'm trying to test out the latest available daily build of Ubuntu Desktop Next 14.10 Utopic Unicorn.
I'm running it from a live USB. Unfortunately, upon startup of the LiveUSB trial session, I am greeted by a blank black screen with a cursor. My PC is running with an i5-760 and a GT220. Is there anything I can do to make it work?

Please let me know if any details are missing.
Thanks in advance!

---

### Post by grahammechanical on 2014-10-07
I have Ubuntu Desktop Next installed and I cannot get past the login screen. It is a problem with Nvidia graphic adapters. 

We have to ask, is your problem a standard problem of not being able to run the live session and would it happen if it was 14.04 that was on that USB memory stick? Or, is this special to Ubuntu Desktop Next ISO image?

Do you have hybrid graphics? An internal graphic adapter as well as that GT220? I have an Nvidia GT220. It has been a while since I tested the Desktop Next ISO image. The early ISOs were impossible to install. But after a few weeks progress had been made. I could at less install thing. Now, I update every few days using recovery mode in the hopes that one update will get me past the login screen.

Have you tried the F6 options?

Regards.

---

### Post by IdoSC on 2014-10-07
> **grahammechanical said:**
> I have Ubuntu Desktop Next installed and I cannot get past the login screen. It is a problem with Nvidia graphic adapters. 

We have to ask, is your problem a standard problem of not being able to run the live session and would it happen if it was 14.04 that was on that USB memory stick? Or, is this special to Ubuntu Desktop Next ISO image?

Do you have hybrid graphics? An internal graphic adapter as well as that GT220? I have an Nvidia GT220. It has been a while since I tested the Desktop Next ISO image. The early ISOs were impossible to install. But after a few weeks progress had been made. I could at less install thing. Now, I update every few days using recovery mode in the hopes that one update will get me past the login screen.

Have you tried the F6 options?

Regards.
Hi grahammechanical, thank you for your answer.

On the Live USB I can't even get to the login screen - though could it be because a Live USB operation skips it?

I used the same memory stick today testing out both 14.04 Trusty Tahr LTS and the standard final beta of 14.10 Utopic Unicorn. Both of them worked perfectly, the Desktop Next daily ISO is the only one that has this problem (and I tried to flash it two separate times on the USB).

This is not a laptop, but a desktop PC. My monitor is only connected to the GT 220 DVI socket. On Windows 8 on the same machine, dxdiag only recognizes the GT 220, so I guess it doesn't recognize my onboard graphics.

I will try the options in F6. Anything specific you recommend to try?

Thanks again and sorry for the delay!

EDIT: I tried every option in the special options menu but to no avail. I assume it would be solved if I could install the NVIDIA proprietary driver, but I cannot do that before installing the OS itself...

---

### Post by grahammechanical on 2014-10-07
There are three methods of installing from a live session.

1) We let the live session run until we get to a Try - Install dialog and we select Install
2) We let the live session run until we get to a Try - Install dialog and we select Try and at the desktop we click the install Ubuntu icon.
3) At the first purple screen we press Enter and then select a language and press Enter. We find ourselves at a text mode screen with Try - Install options and we select Install from there.

In the past I have had development ISO images that would only install in 1 or 2 of those three ways and not all three. You are able to get to the text mode screen. Have you tried Installing from there? I have had to do it that way in the past.

Just a thought.

Regards.

---

### Post by jerrylamos on 2014-10-07
Booted the .iso directly from the USB hard drive.

First screen asked me to swipe the screen from the right to unlock.

Hello?  This is a desktop with an external LED monitor, mouse, keyboard.  No touch screen.
Swiping with the cursor did nothing.

Got by that, then got a login screen with user:

ubuntu-desktop-next 
password:

Anyone have any clue what the password is?

On the right half there was a circle saying
no data sources available.

Upper right were a few applets, none of them shutdown or reboot or logout.

Ctrl-AltF2 shutdown now 

worked.

anyone with any pointers to what ubuntu-desktop-next is, what the password is, will it work with a monitor and mouse?

Lenovo M58p Intel Core 2 Duo 3 gHz 
VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Thanks.....

googled ubuntu-desktop-next someone wrote push the enter key.  I'll give it a go.

---

### Post by jerrylamos on 2014-10-07
Since I couldn't swipe on a standard LED monitor, I did:

skip this

ubuntu-desktop-next
passwd:

Ctrl-AltF1
passwd ubuntu-deskop-next
whatever1
whatever1

switch back to graphics screen then logged in with the password I just set.

A big whitish screen with a few huge icons.  The hard drive view icon wanted to know if I wanted to format.         !@#$ NO!

browser icon worked.

This is a 1360x768 screen, it showed about 256x768 a long narrow strip on the left.
Couldn't see any way to request desktop view like I can with Nook HD+. 
Every time I pressed 1 ubuntu-desktop-next printed !     On 2 it printed @,    / it printed ?,     ......

Back to utopic:

/var/crash whoopsie 6905045 Oct  7 19:09 _usr_bin_compiz.1000.crash

This is with utopic beta with kernel 3.16.0-21.  
I've even gotten crashes with Kernel 3.17
yes I've entered several launchpad bugs on compiz.  
Seems like I get more bugs with compiz than anything else, starting with Intrepid, and on a variety of pc's.

I have a desktop, a tower, a netbook with external monitor, a notebook with external monitor - compiz loves to crash on one or the other.  
Hope they get somewhere before utopic release.... 
as far as I can tell, ubuntu-desktop-next didn't crash, but of course I haven't found Nautilus or a command line to do ls -l /var/crash

---

### Post by grahammechanical on 2014-10-07
I have just tried the latest ISO image and it goes like this:

first purple screen>black screen + disk activity>grey background>a slight variation of the usual ubuntu default purple background + Welcome dialog with Try - Install.

Try Unbuntu Desktop Next goes to a black screen + disk activity and then no disk activity. Needs Ctrl+Alt+Del to trigger reboot and ejection of the disc.

I already have an Install of Desktop Next and that gives me login screen bounce. So, I see no point in installing this image.

---

### Post by jerrylamos on 2014-10-08
> **grahammechanical said:**
> I have just tried the latest ISO image ....I see no point in installing this image.
Agree, I don't mind booting the .iso from time to time to see any progress.  So long as it doesn't try to format my hard disks!

At this stage the .iso wouldn't do much and certainly didn't support a wide screen monitor.  It's like forcing a "smartphone" image on a much wider function pc.

Times past MIR crashed horribly.  Whatever screen support Next has didn't this time.

---

### Post by grahammechanical on 2014-10-08
I changed my mind and just installed the ISO I downloaded about half a day earlier. It does install. I used the "press enter twice at the purple screen" method.

This time I changed my normal practice of not installing the Nvidia driver. Reboot got as far as the login screen. Then it all I got was a black screen. The hardware cursor made an appearance which indicates MIR is running.

I used recovery mode to update and this time I got beyond the login screen to the phone OS home screen. The password is the user password we put in when doing the normal install.

So, I would say from today onwards the daily ISO image may have something useful if we want to install. But the live session may still be broken.

Now I have two installs of Desktop Next. Both updated. The one on Nouveau gives login screen bounce. The one using Nvidia driver gets to the phone OS. I now have something to play with.

I tried to post from Desktop Next using Browser but it froze the OS just like it does on standard Utopic. <disappointment>

Regards.

---

### Post by grahammechanical on 2014-10-09
I have tested today's image (9th October). The live session loads to the Welcome dialog and the Try Ubuntu button loads to the phone home page. Cannot login. Need a password. Pressing enter does not work neither does typing ubuntu.

The Install Ubuntu does install as a normal install would. The reboot gets to the lightdm login screen. Password accepted. And then on to the phone home login screen. Password accepted.

One bug that really makes it hard to get anywhere on Desktop Next is the fact that Caps Lock does not work and pressing shift even once acts like Caps Locks is on. and there is no way to turn it off. I lose the comma and the full stop which makes it impossible to enter an email address. The numbers keys do not type the numbers but the characters above the numbers. I cannot activate my Ubuntu One sign on. Cannot log in to the forums.

I have yet to find a way to activate the on screen keyboard.

On the other hand Browser is behaving itself. It does re-lay the Forums and uses a blue colour.

Regards.

---

