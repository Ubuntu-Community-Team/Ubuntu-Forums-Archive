---
title: "LimeWire installation in Ubuntu 5.04"
date: 2005-09-12
forum: The Cafe
---

### Post by mchatel on 2005-09-12
Hey everyone.
I was reading the forum, and noticed a lot of threads about LimeWire installation under Ubuntu.

I thought I would just mention my experience, and how I installed LimeWire.  I didn't have many issues, and did not have to follow all the steps listed in the Unoffical Unbuntu Guide ([www.ubuntuguide.org)](www.ubuntuguide.org)).  

All I did was...

Used Synaptic Package Manager, to get the J2SE Runtime Environment (JRE) package.  This is *one* of the *two* steps I did follow from the guide, but that was it.

After that was installed, I simply downloaded the LimeWire RPM from the LimeWire site.  I then followed the steps from the Ubuntu Guide, specific to converting an RPM file to a DEB package.  Once I did that, I then installed that package according to the guide.

When the package was installed, everything was ready to run for LimeWire.  The Gnome menu even had the menu item for me already.

Was this a fluke, being so easy?  I see that a lot of other people had to follow more complicated steps, and have had trouble with LimeWire, but mine is working fine.

Running it this way, installing the converted .DEB package, allowed me to install LimeWire as an app, not specific to my /home directory or my own user.  I like having it installed this way.

I will say again...  I am loving Ubuntu.  I am impressed with this distribution.

---

### Post by Steve Smith on 2005-09-22
Amazing, just did it the way you did it and worked for me too  Thanks :)

---

### Post by poofyhairguy on 2005-09-22
[QUOTE=mchatel]
Was this a fluke, being so easy?  [/QUOTE]

Alien is hit or miss. Sometimes it works well. Other times it doesn't.

---

### Post by xequence on 2005-09-22
For some reason, JRE doesent show up for me in synaptic :/

I need something like limewire to download one song at a time if I dont feel like getting a whole album off bittorent.

I had it working before I reformatted my ubuntu...

---

### Post by Steve Smith on 2005-09-22
[QUOTE=xequence]For some reason, JRE doesent show up for me in synaptic :/

I need something like limewire to download one song at a time if I dont feel like getting a whole album off bittorent.

I had it working before I reformatted my ubuntu...[/QUOTE]
 I think it was taken our for legal reasons or something.

Take a deep breath, then go here:
[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

Ignore the whole "Changes to java-package files" section if you're on Hoary.
I had trouble finding the Java download from the link it gives: once you follow the link, click the red & white "J2EE download the SDK picture", then choose "J2SE 5.0" under separate bundles.

---

### Post by benplaut on 2005-09-22
i used the .tar.gz... it's easy to "java -jar limewire,jar" to get the program to run  :wink:

---

### Post by Steve Smith on 2005-09-24
[QUOTE=benplaut]i used the .tar.gz... it's easy to "java -jar limewire,jar" to get the program to run  :wink:[/QUOTE]
bo-boom-chhhh

---

### Post by bjweeks on 2005-09-24
[QUOTE=xequence]For some reason, JRE doesent show up for me in synaptic :/

I need something like limewire to download one song at a time if I dont feel like getting a whole album off bittorent.

I had it working before I reformatted my ubuntu...[/QUOTE]
Or you could buy the songs.

---

### Post by benplaut on 2005-09-24
[QUOTE=Steve Smith]bo-boom-chhhh[/QUOTE]

um... ?

---

### Post by majikstreet on 2005-09-24
[QUOTE=bjweeks]Or you could buy the songs.[/QUOTE]
 Are you serious? No-one buys songs! Weirdo..

---

### Post by benplaut on 2005-09-24
[QUOTE=majikstreet]Are you serious? No-one buys songs! Weirdo..[/QUOTE]

i don't even *listen* to songs  :roll:

---

