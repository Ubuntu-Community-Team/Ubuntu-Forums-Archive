---
title: "install problems with wine and/or World of Warcraft"
date: 2009-09-30
forum: Wine
---

### Post by alving on 2009-09-30
hi all

im completely baffled here.
i have an older toshiba laptop, 1.3Ghz, 256Meg ram, 40Gig HD and trident cyberblade video.
i have just installed ubuntu 9.04 and wine 1.1.29.
i went into my account on WOW website and downloaded the game installer.
when it finished, i ran it. about 6 hours later i went to bed and progress indicator was about 45%.
when i woke in the morning it was at 62% and computer was locked up.

i have checked numerous forums and cant find out where the temp install files would have been saved.
there is no warcraft directory any where on the computer.
before install i had approx 18Gig free space. after restart in morning i had about 4.1Gig.
i have already deleted a bunch of temp files from different cache folders, but,
i still only come up with about  8.6Gig.
when i run the installer it tells me i need at least 15Gig.

can some-one please tell me where these files might be?

i have emptied the trash bin for both myself and root.

any help will be greatly appreciated.

thanks
alving

---

### Post by alving on 2009-10-05
can any one tell me a website to find more info?
i have no idea what happened with the install.

it seems to me, my only other choice is to reformat and reinstall OS and Wine and hope it works then.

---

### Post by asdfoo on 2009-10-05
> **alving said:**
> can any one tell me a website to find more info?
i have no idea what happened with the install.

it seems to me, my only other choice is to reformat and reinstall OS and Wine and hope it works then.


99% of the time data created by programs run in wine, will be in /home/alving/.wine/drive_c somewhere

If you want to start fresh then delete your .wine directory.

---

### Post by hikaricore on 2009-10-05
99.9% would be more accurate.
The only reason data would ever be outside this is due to user interaction.

---

### Post by alving on 2009-10-05
hi again

i just deleted the .wine directory.
went emptied the trash bin, and i still only brought me up to 9.6Gig free space.
game installer tells me that i need at least 15Gig of free space for download and install.

is there any other place the files would have been saved?

when i did the install, i ran it with all the defaults.
it was installing the game to c:\Program Files\WorldofWarcraft.

would i be better off to reformat, reinstall OS, then wine, then game?
and then install the couple other packages that i have?

thanks
alving

---

### Post by YokoZar on 2009-10-06
The files were in ~/.wine somewhere, and you already deleted them.  Is it possible something else on your system was taking up space after you started the install?  That could explain why it failed -- running out.

Some possibilities: update-manager downloading packages (sudo apt-get clean to remove the old ones), a torrent you had forgotten about, etc.  Also be sure to empty the trash.

---

### Post by alving on 2009-10-06
i just ran the above command:

allyn@laptop:~$ sudo apt-get clean
[sudo] password for allyn: 
E: Archive directory /var/cache/apt/archives/partial is missing.
E: Unable to read /var/cache/apt/archives/partial/ - opendir (2 No such file or directory)


do you have any more suggestions?

is there a/any command(s) that will tell me where the temp download files would have been put?

i do not have the CD&#347; for the game any more, i have to download/install full game from WoW website.

i dont know anything about torrents, so i dont think i am using any. unless they are started automatically.
the trash is emptied almost as soon as i put something into it.

---

### Post by hikaricore on 2009-10-06
Err... if you downloaded the game installer to your desktop or something, there's a good chance THAT is taking up the space you seem to be missing.
Last I checked the base WoW installer was several gigs in size.

---

### Post by alving on 2009-10-07
the downloader that i have saved on my desktop is only 1.6Meg.

can you tell me where the OS would save temp internet files?
where it would download the install files before they were run.


should i reformat and try again?

---

### Post by hikaricore on 2009-10-07
The OS doesn't control where the installer downloads to.  It would either download to your desktop or the wine folder.
Worst case and I don't imagine it would happen, it would download to somewhere else in your home folder? (not likely)

Open a terminal and tell me the output of these commands.

> du -hs ~/.wine
du -hs ~

---

### Post by alving on 2009-10-07
allyn@laptop:~$ du -hs ~/.wine
du: cannot access `/home/allyn/.wine': No such file or directory
allyn@laptop:~$ du -hs ~
93M    /home/allyn
allyn@laptop:~$

---

### Post by hikaricore on 2009-10-07
Well nothing in your home directory is taking up any space.
You could have an oversized log file somewhere or something.

> sudo du -hs /*
df -h

The 2nd one will take awhile.
If you happen to have any large files anywhere such as your /tmp you'll be able to see.
At the very least you'll be able to better understand what's taking up space and where.

Almost forgot, is yours the ONLY user account on this system?

---

### Post by alving on 2009-10-08
ok, here we go.....


yes, mine is the only account


allyn@laptop:~$ sudo du -hs /*
[sudo] password for allyn: 
6.1M    /bin
13M    /boot
0    /cdrom
224K    /dev
13M    /etc
du: cannot access `/home/allyn/.gvfs': Permission denied
94M    /home
0    /initrd.img
127M    /lib
16K    /lost+found
8.0K    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/24356/task/24356/fd/3': No such file or directory
du: cannot access `/proc/24356/task/24356/fdinfo/3': No such file or directory
du: cannot access `/proc/24356/fd/3': No such file or directory
du: cannot access `/proc/24356/fdinfo/3': No such file or directory
0    /proc
14G    /root
7.3M    /sbin
4.0K    /selinux
4.0K    /srv
0    /sys
112K    /tmp
2.0G    /usr
205M    /var
0    /vmlinuz
allyn@laptop:~$ 

allyn@laptop:~$ df -h
Filesystem                         Size    Used   Avail   Use%   Mounted on
/dev/sda1                              27G    16G     9.6G    63%      /
tmpfs                                        115M      0         115M     0%       /lib/init/rw
varrun                                    115M  216K   115M     1%       /var/run
varlock                                   115M  0        115M     0%       /var/lock
udev                                          115M  148K   115M     1%       /dev
tmpfs                                        115M   76K     115M     1%       /dev/shm
lrm                                              115M   2.2M    113M     2%      /lib/modules/2.6.28-15-generic/volatile
/home/allyn/.Private    27G     16G      9.6G    63%    /home/allyn
allyn@laptop:~$

---

### Post by hikaricore on 2009-10-08
You ran something with sudo possibly WINE.

Notice how your /root partition is using 14Gb of space.
Don't run WINE with sudo.  :p

> sudo du -hs /root/.wine

If this shows that the majority of the data is actually here then run use:

> sudo rm -R /root/.wine

Then you should have your drive space back.

I have to say tho for installing and updating WoW you REALLY REALLY need a bigger hard drive.
27Gb is not enough for all the unpacking and repacking it does on updates and installations.
This is assuming you're using both expansions.

---

### Post by alving on 2009-10-08
AWESOME BUD. THANKS A MILLION.
/root/.wine=13Gig

back up to 22.4Gig free space.

i am trying to run the original WoW for now. want to make sure it works properly before i upgrade.

now i will try to install game again.
with any luck it will work this time.

again, thank you very much

---

### Post by alving on 2009-10-16
hi again

i have a new problem now.

i got the original version of the game installed, all patches have been downloaded and installed.
when i first started the game it took me a whole night (about 6 hours) just to load the game and create a new toon.
when i try to play i get about 1 frame per 10 seconds.

i have tried adding the lines suggested here:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
with no luck.

does any one know where else i can find more info on how to speed up the game?

---

### Post by hikaricore on 2009-10-16
> **alving said:**
> 
i have an older toshiba laptop, 1.3Ghz, 256Meg ram, 40Gig HD and **trident cyberblade video**.

I doubt WoW will even run on that in Windows.
Sorry I didn't notice your hardware before.

You can run WoW on a lot of hardware but there is a rational limit.
You're far far far below that limit I'm afraid.

---

### Post by alving on 2009-10-16
what do you think my chances are if i can find/install the max 1G ram the laptop can use?

would i be better off to get a new computer?

---

### Post by hikaricore on 2009-10-17
Your video card is going to be the limitation.
No amount of ram in the world will help you.

You may be able to run some games with that system in ***dows but I can almost assure you it will never happen on Linux from what I've seen.

I could be wrong but I don't think this is the case.

---

### Post by alving on 2009-10-17
ok thanks for all your help.

i will try to get it running on my other machine.
AMD 1400+ (1.1Ghz)
i have 768Meg SDRAM installed now, or i have a 512Meg DDR. machine will take both
i will have to buy new video card for it, it has a built-in Intel i815.

i did have the game running on that machine in WinXP.

it was rather slow there as well. at least i could get 5-6FPS.
but maybe with a new video card and more DDR instead of SDRAM it will run better.

the minimum system requirements for the BC expansion are only:
P3 - 800, 512Meg, and a half decent video card.

recommended system requirements are:
P3 - 1.7, 1Gig, 64Meg video

---

