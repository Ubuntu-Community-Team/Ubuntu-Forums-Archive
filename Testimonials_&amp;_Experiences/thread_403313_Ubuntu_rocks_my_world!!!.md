---
title: "Ubuntu rocks my world!!!"
date: 2007-04-06
forum: Testimonials &amp; Experiences
---

### Post by pneedleman on 2007-04-06
Ive been interested in linux for quite some time and have occasionally tried making the switch from Winblows. I am on a Dell Latitude C840 1.8ghz pentium 4 with a GeForce4 440 go 64mb video card, internal wireless, 512 mb ram and external harddrive.

I started a few years back with RedHat and mandrake and was never able to get all my peripherals  or  all my software working properly and gave up. A few yrs later I tried again with Fedora and mandiva thinking that these update versions of the old OS's i once tried would have the drivers needed to run my hardware. Still after giving it a few weeks I gave up. I cant fully use linux if I cant get my digital camera or printer Installed. I distinctly remember finally getting Java installed after 4-5 hours of google searching!! I mean why should i have to spend 1/2 my day installing basic software. Not to mention the time it took to download the 5 ISO images for the install!!!!!!!

Anyhow, given the recommendation of a coworker a few months ago I decided to give ubuntu a try and I am IN LOVE!!! Everything worked out of the box!!!!!!! Printer, NTFS harddrive, digital camera, sound card, wireless mouse! I was amazed. It has only gotten better and better the more I use it. Installing software is a breeze and it gives you the confidence to try new things and explore.  I installed Apache, PHP and mySQL in no time. Have FTP and SSH servers running as well. I even started writing my own shell script to perform routine tasks such as file backups.  I could not be happier!!!

If you are the fence about switching over from Windows, give it a try. It could not be any easier. I have been windows free for about 4 months!

Some programs I found which are a must:
[LIST]
[*]Automatix2 - for easy installation of common software, codecs, drivers, and much more 
[*]EasyUbuntu - another easy installation of program 
[*]Amarok - best music player ever!
[*]Frostwire - limewire clone
[*]gnomad2 - for Creative mp3 player support. Works great w/ my Vision:M
[*]Thunderbird - mozilla email client
[*]Google Earth
[*]Azureus - bit torrent client 
[/LIST]

I am only having 2 slight issues thus far:
[LIST]
[*]Cannot write to my USB Hard drive. Have searched and still cant not get the darn thing working. 
[*]Embedded WMV movies in Firefox. I am using Totem-xine and some sites they work and others do not. I could of sworn at one time it worked but am not positive. I have tried using mplayer instead but still nothing.
[/LIST]

Overall, I could not be any happier using ubuntu. My system runs great and in most instances programs run better and work easier than when in Windows!!

 Cant wait for the new release of Ubuntu 7.04 to come out later this month!!!

---

### Post by bruenig on 2007-04-06
Try using mozilla-mplayer for the plugin instead of totem-mozilla.

Some of those must have programs are iffy at times, especially automatix, but good to see happy people.

---

### Post by SorenK on 2007-04-06
> **pneedleman said:**
> Cannot write to my USB Hard drive. Have searched and still cant not get the darn thing working.

What file system is it?  Do you have read/write access to NTFS set up?

---

### Post by pneedleman on 2007-04-08
Yes my external hard drive is NTFS. I have been able to get my windows partition writable but that doesn't really help me

---

### Post by sagara on 2007-04-08
I would suggest you read this thread: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+write](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+write)

It helped me set up my NTFS drives for read/write.  Including my external USB drive.
One thing I must mention: after updating **fuse** and installing **ntfs-3g** I had to manually change the properties of my external USB drive to read and write.

I did that by right clicking on my external drive on my desktop>Permissions>Folder Access select **Create and delete files** under the Owner section

Hope this helps

---

### Post by pneedleman on 2007-04-08
i actually just figured out the problem!!! I added a volume label in windows for my drive 'USB-160'. All I had to do was return to windows, delete the label and upon return to ubuntu it worked!!!!!!!!

---

