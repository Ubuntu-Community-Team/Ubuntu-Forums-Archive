---
title: "Can't install iTunes using Wine"
date: 2011-05-22
forum: Wine
---

### Post by p1ngp0ng123 on 2011-05-22
When I tried to install iTunes through Wine, I got this:


The file '/home/name/Downloads/iTunes64Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.



...and I downloaded off of Apple's site. I have an iPod Nano 5th Gen.

---

### Post by quarkhirad on 2011-05-22
I have a  120 GB video ipod.  I was  also  not  successful  installing itunes thats  when i  realized  that if you are wanting to sync songs from  say  your  pen  drive  or  comp onto  your ipod you can use GTKpod it works very well.Though playing music from your ipod is not that good i prefer rhythmbox for that.

for sync of movies i think it should work but  i  have  not   tried  it.

---

### Post by philinux on 2011-05-22
Moved to the Wine forum.

---

### Post by maxmiaggi on 2011-05-23
copy the installer to anywhere in your home directory. now right click it, go to properties and then to the permissions tab. There check the allow executing file as program. and then it works!

in ubuntu, every file that runs must be executable as program. ubuntu demands it... ;)

---

### Post by bobwyajnr on 2011-05-23
> **p1ngp0ng123 said:**
> 
The file '/home/name/Downloads/iTunes64Setup.exe' ...

The 64-bit build of Wine is still experimental - all regular users (like you!!) are using a 32-built of Wine. You want the 32-bit build of iTunes (_even if you are using a 64-bit OS_).

There is loads of [waffle]("http://www.jonathanmoeller.com/screed/?p=1647") out on the net about installing iTunes. From what I have seen the iTunes 10 series is a non-starter. I haven't tried it recently though I must admit... :-)

Sadly we are waiting for USB device (pass-through) support to integrated into Wine ([due in the Wine 1.4.xx series stable branch]("http://wiki.winehq.org/WineReleaseCriteria")). Would love that for my iPod touch 3G because the Linux FOSS equivalents are still a long way from being fast/stable-enough and at the stage of having a UI from the 1980's.:)

Bob

---

