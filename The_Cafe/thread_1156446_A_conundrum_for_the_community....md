---
title: "A conundrum for the community..."
date: 2009-05-11
forum: The Cafe
---

### Post by Arbiter on 2009-05-11
Hello all, I've come looking for an answer to a question posed to me - if possible I'd like to know if there is some kind of open source (or even closed source) program that could achieve this.

I'm a mid level IT admin who has been asked to find a way to wipe 100 or more computer's hard drives via network simultaneously with a minimum of interaction.  The way my supervisor wants it is to "be able to push a button on the server and overnight all the machines on the network have their hard drives wiped."

I'd like to know if there's a way to "push" a drive wipe command out to machines on a network, or if something like this must be done individually on each machine by setting up some kind of PXE boot or some such.

Inversely, I'd like to know if there's a way to image a computer's hard disk with a new image in a similar manner.  My supervisor has lead me to believe that there is some technology out there that will accomplish this.

So, any such animal out there?


Thanks in advance,

Arbiter

---

### Post by will1911a1 on 2009-05-11
I was prepared to say that I've never seen or heard of such a program, but then I found this:

[http://www.cyberscrub.com/topics/clean_disks_with_hard_drive_eraser.php](http://www.cyberscrub.com/topics/clean_disks_with_hard_drive_eraser.php)

Dunno if it's legit or not though.

---

### Post by wannadumpwindows on 2009-05-11
I'm not sure about wiping the drives, but there's a pretty nice program for reinstalling them all. It's called Clonezilla.

Have a look here:
[http://www.clonezilla.org/]("http://www.clonezilla.org/")

---

### Post by t0p on 2009-05-11
Check out [this page]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html").

---

### Post by Firestem4 on 2009-05-11
Thats a very interesting task you have. I'd be very interested to hear what you come up with to accomplish this.

---

### Post by starcannon on 2009-05-11
I'm wondering if you couldn't just ssh into every computer on your network, and then use dd to wipe the drives. I think this should be possible using a fairly easy to create bash script. One could even log into only computers of a given address range or of a particular subnet, etc.

I wish I had time to setup a testbed to try it out, sounds like a fun and interesting project.

P.S. I think I read somewhere once that dban can do this task, but I'd have to go googling to remember for sure.
P.S.S. As mentioned earlier, Clonezilla for imaging, you can even restore the same image to every computer on a network; my cousin just set a similar situation up for just that purpose, so I know its doable.

---

### Post by Arbiter on 2009-05-11
I've looked at a few of those solutions mentioned above already - but to do a network clone/drive wipe it requires all machines boot to a PXE environment, which is something that requires setup and doesn't want to do.

I've been wrestling with clonezilla for a while with imaging and its been a bit of a bear.

To do a wipe using a BASH script, that'd be the simplest maneuver, except that none of the machines are Linux machines, they're all Windows boxes.

My supervisor keeps telling me that at a company he worked for, machines on the Windows network there could be reimaged without any techs having to go to the machines physically.  I have yet to hear of such a thing.  There's the possibility that he doesn't know what he's talking about - I'm just trying to get down the bottom of this and see if what he's saying is plausible...not looking good though :(

---

### Post by starcannon on 2009-05-11
[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)
[http://sysadmin.wikia.com/wiki/Clonezilla](http://sysadmin.wikia.com/wiki/Clonezilla)

Are 2 places to start reading; theres gonna be a bit of research time invested in your project, once you have something going though, it should make your wipe/restore a breeze.

---

### Post by Arbiter on 2009-05-11
Well, this kind of proves me right then - you need to have each machine you want to wipe boot over a network and start into the wiping process through a network boot or through a bootdisk.

I still don't know how someone would image PC over a network without any physical interaction - which is one of the bigger questions.

---

### Post by I-75 on 2009-05-11
It might be less of a hassle to just burn 100 CD copies of D-Ban's Nuke and Boot and then on each computer insert the disk, select your preferred method of wipe ( DOD option is good) and the HD is wiped clean. 100 blank CDs can be had for less than $20, Nuke and Boot is free from Source Forge and you can get a team of 5 people to do 20 computers each which should not take all that long. 

[http://sourceforge.net/projects/dban/](http://sourceforge.net/projects/dban/)

---

### Post by Bölvaður on 2009-05-11
it depends upon the computers you are going to be accessing.

if they all have ssh then  you can just make a script to log into each client on a new gnome terminal or something (so you have the terminal window you begin with to execute the initial command and 100 new terminal windows will appear each logged into each computer via ssh)

and then # rm -fr / && shutdown -now

that should take about 1 minute :)

---

### Post by thisllub on 2009-05-11
Must be a lot of unlicensed software there.
You realise that even if you erase everything on a disk the police can still read it.
They pull the platters out and read the residual magnetic residue between the tracks.

---

### Post by Arbiter on 2009-05-12
@I-75

Yeah, I know - that's what I've been trying to tell them.  The process is just quicker to do by hand than to have to set up some huge infrastructure.  In the time it takes to do all the set up, most of the wipes would be done already.

And the struggle between technicians and management continues...:-P

---

### Post by Arbiter on 2009-05-12
> **thisllub said:**
> Must be a lot of unlicensed software there.
You realise that even if you erase everything on a disk the police can still read it.
They pull the platters out and read the residual magnetic residue between the tracks.


Actually quite the opposite, we have a lot of sensitive information - we're an asset disposition company.  We deal with banks and large corporations with technological end-of-life solutions.  We're just trying to find a solution to do large jobs quicker. 

And a recent study by the Center for Magnetic Research (I think that's the name of the place anyway) concluded that any hard drive over 15GB can be unrecoverable after a single zeroing out of the drive (one pass zeros) because of the high magnetic density of modern hard disks it makes it nigh impossible to recover the data even after one overwrite.

---

### Post by fatality_uk on 2009-05-12
> **thisllub said:**
> Must be a lot of unlicensed software there.
You realise that even if you erase everything on a disk the police can still read it.
They pull the platters out and read the residual magnetic residue between the tracks.

As the saying goes "don't believe the hype!"

Overwriting a hard drive in the correct manner, Blancco style, and the Police won't be able to see what was on previously.

---

### Post by Skripka on 2009-05-12
I have to admit I was curious about why someone would want a failsafe like this....it is the perfect setup for a cover-up in the event of legal action to destroy evidence.

---

### Post by Arbiter on 2009-05-12
> **Skripka said:**
> I have to admit I was curious about why someone would want a failsafe like this....it is the perfect setup for a cover-up in the event of legal action to destroy evidence.

Looking back on my original post, yeah, I see how you could come to that conclusion.  It did kind of seem like a shady request lol

---

### Post by koenn on 2009-05-12
> **Arbiter said:**
> Looking back on my original post, yeah, I see how you could come to that conclusion.  It did kind of seem like a shady request lol

it's a pretty valid request.
If you're a sysadmin looking to decommission a couple of hunders/thousands of PC's, you'll probably want to wipe the disks to prevent sensitive data that ends op on the hard disk (temp files, cached credentials,  ...) before they the end up some place (junk yard, refurbishing, 2nd hand sales, ...) where someone might have a go at recovering them.

DBAN is excellent to do this manually, for a few computers, but if you regularly need to wipe large numbers of PC's, you'd want something like what your sysadmin requested.

something like "EBAN" [http://www1.techwayservices.com/about-eban/](http://www1.techwayservices.com/about-eban/) - enterprise grade DBAN.

---

### Post by freebeer on 2009-05-12
> **Arbiter said:**
> they're all Windows boxes.


Oh.  In that case, just open them up to the internet and let the malware take care of it for you.  :D

(I know, not terribly helpful, but I couldn't resist.)

---

### Post by swoll1980 on 2009-05-12
Would it be possable to remaster a tool like parted magic to run a script at start up? Then you could make a virtual disk of it on the server,and have the machines boot into that, but you would have to find an easy way to get all the computers to boot into it, on demand.

---

### Post by koenn on 2009-05-13
> **Arbiter said:**
> Well, this kind of proves me right then - you need to have each machine you want to wipe boot over a network and start into the wiping process through a network boot or through a bootdisk.

I still don't know how someone would image PC over a network without any physical interaction - which is one of the bigger questions.

a pxe netboot capable PC will usually try to boot from the network if it doesn't find an other bootable medium, so you if you render the hard disk unbootable, it would fallback to network boot automatically. You can then boot a DBAN image (eg EBAN), or any other installer, or clonizilla server, etc.

Windows has quite an arsenal of remote administration tools : you can drop startup / shutdown scripts on target PC's, you can remotely setup scheduled tasks, remote registry editing, remote installation of software, etc, so plenty of avenues to get something to execute without fysically being at the machine. 

The remaining question is then : what could you have them execute that renders their hard disk unbootable (withe the MBR ?) so they'd network boot when they restart, and wipe themselves out.


You should also look up Windows Remote installation services - it might be what your admin is hinting at ?

---

### Post by Arbiter on 2009-05-14
> **koenn said:**
> a pxe netboot capable PC will usually try to boot from the network if it doesn't find an other bootable medium, so you if you render the hard disk unbootable, it would fallback to network boot automatically. You can then boot a DBAN image (eg EBAN), or any other installer, or clonizilla server, etc.

Windows has quite an arsenal of remote administration tools : you can drop startup / shutdown scripts on target PC's, you can remotely setup scheduled tasks, remote registry editing, remote installation of software, etc, so plenty of avenues to get something to execute without fysically being at the machine. 

The remaining question is then : what could you have them execute that renders their hard disk unbootable (withe the MBR ?) so they'd network boot when they restart, and wipe themselves out.


You should also look up Windows Remote installation services - it might be what your admin is hinting at ?

Hmm...hadn't thought about that - I'll have to look into that - much appreciated :-D

And now part 2 to the conundrum - does anyone know if its possible to read a hard drive to see what is written to it bit for bit?  We want to be able to tell a customer if a drive has had all zeros written to it or random numbers or something.  Is there an app that does that?

---

### Post by MaxIBoy on 2009-05-14
"dd" is installed on any complete Unix-like system. You can also get it on Windows. It is designed for copying binary data from one source to another. For example, you could read some blocks off /dev/sda and write it to a file, or you could read a file and write it to /dev/dsp (hit the mute button first.)

A word of warning-- "dd" has earned the nickname "data destroyer," be careful with it.

---

