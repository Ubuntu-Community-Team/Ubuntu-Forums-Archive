---
title: "Sims 3 won't install?"
date: 2009-06-21
forum: Wine
---

### Post by YakoiB on 2009-06-21
Hi everyone.  I am fairly new to Ubuntu and am having a bit of trouble with the installation of my newest game!  My friend made me an ISO of his game so that I can see if I can get it working on Ubuntu before I go and spend the 60 bucks for the game.  

ISO is fine, but wine doesn't see the mounted image?  Will only let me open through WinAce, which is a worthless program imo.  

Any help would be great!

Oh and I read that running the install through Playonlinux would work, but I am a scripting tard and have no clue what the sudo blah blah blah means.  That is what I have my husband for, but I am determined to at least TRY to install this on my own. 


Again any help would be great!

Thanks!

---

### Post by YakoiB on 2009-06-21
5.6 gigs.  Highest DVD I have is 4.7 >.<  Thought of that already.

---

### Post by YakoiB on 2009-06-21
Okay. I am dling Gmount now, I was using Archive Manager....hopefully this will do better =D


*Crosses fingers*

---

### Post by YakoiB on 2009-06-21
*Sigh*  Got this :

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by YakoiB on 2009-06-21
LOL Give me a little credit.  I am far from a ISO tard, just suck at scripting.  :P

Where do I need to mount the image to?  I tried a new folder on my desktop and a folder in Wine I named TS3?

Neither of those worked with Gmount so what would you suggest?

---

### Post by YakoiB on 2009-06-21
Yeah I found it....got the error I posted right before your last post....

I think I have been defeated and should wait for my husband to get outta bed....lol

---

### Post by YakoiB on 2009-06-21
lol No worries.  My husband has become an all knowing Ubuntu God in the passed 6 months...I will leave it to him.  Thanks for your help!!! *hugs*

---

### Post by flixgallardo on 2009-06-21
Have you tried extracting the iso and running the installation with Croosover Games? :confused:

---

### Post by YakoiB on 2009-06-21
yup tried that too.  My husband is working on it now....lol he is so gonna hate me by the end of this I have a feeling >.<

---

### Post by YakoiB on 2009-06-21
Ok so we tried to install the ISO on a PC instead of my poopy laptop, and the ISO mounting programs that we have tried say that it isn't an ISO...Any thoughts?

---

### Post by cutterjohn on 2009-06-21
Also if you try to install with wine 1.1.22(IIRC) OR 1.1.23 installs are broken, but 1.1.24 is out now and supposedly fixes that problem.  (Along with a bunch of ATI specific problems which makes me happier...)

Is it a .mdf or something disguised as a .iso?  (Propietary compressed disk image formats used by various Windows virtual drive drivers...  IIRC Daemon Tools can handle most of them...)

o.w. I suggest re-obtaining an image of the disk, and keep in mind the above about broken installs under the last few wine versions, but should be fixed for 1.1.24, so update if you're not using the default 1.01 stable version of wine.

---

### Post by YakoiB on 2009-06-21
Figured out what it was!!!! The ISO was made in a CDISO instead of DVDISO so none of the iso readers we tried worked.  Eventually my husband was able to puzzle it out and get something to work with our original mounting program.  Now all we have to do is figure out why wine isn't showing the files we installed from the iso...

I suppose if it isn't one thing it is another....lol

Thanks guys!!!

~Y:KS

---

### Post by opt1k on 2009-07-11
also anyone who cant get an iso to work
$ sudo apt-get install mdf2iso nrg2iso ccd2iso

then try every single one with your iso
ie.
mdf2iso foo.iso bar.iso
nrg2iso foo.iso bar.iso
ccd2iso foo.iso bar.iso

until one of them works ;)

---

### Post by ackanao on 2009-07-11
You don't need to convert .mdf or .nrg images to .iso, you can mount them directly by using mount command:

[https://help.ubuntu.com/community/MountIso?highlight=%28CategoryCleanup%29]("https://help.ubuntu.com/community/MountIso?highlight=%28CategoryCleanup%29")

---

### Post by Samsinsane on 2009-07-12
Hey, not sure if you are still having issues or not but with World of Warcraft, it is suggested to copy all the files off the cds to install it faster. You could apply the same technique to the Sims 3 and take all the data off the ISO into a folder in your home folder or desktop and run the setup.exe file. Just a thought might not work, let me know how it goes if you try it though.

Regards,
Samsinsane

---

