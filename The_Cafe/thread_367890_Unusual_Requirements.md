---
title: "Unusual Requirements"
date: 2007-02-22
forum: The Cafe
---

### Post by LostLittleGuy on 2007-02-22
I have what I believe is an unusual set of requirements I'm trying to fill.  I've done some research and I believe what I want to do is _possible_ with Ubuntu, but I can't seem to find any information that gets me quite where I want to go.  Of course, there's a lot of information out there, so if I'm overlooking something, by all means point me in the right direction and I'll try to get out of everyone's hair.

So on to what I'm really trying to do.  I'm trying to set up a computer in a location that makes the persistence of certain peripherals unrealistic.  Specifically, the computer will only have a monitor hooked to it for brief administrative tasks.  So I need to be able to have people login to this machine from remote locations via a network.  The computer may be powered on and off, so I need it to be able to do this without a local user initializing a session.  Local sessions need to be able to control all peripherals and programs on the machine (currently spec'd are a set of speakers, a camera, and a printer, although there may be more in the future).  I need users to be able to login from a variety of operating systems(mostly Windows and Mac, to be honest), either through a publicly available interface program, or through a web browser.  I would very much like for the logged in user to see exactly what the would be seeing if they were in fact looking at a monitor connected to the machine displaying a locally run session.  Further, all user data on the machine MUST be encrypted, and should not be placed anywhere onto the hard drive in an unencrypted state (unencrypted in physical memory is obviously OK).  I do not believe given these requirements WDE would be feasible, but if there is a way, i would love to know.  A secured connection to the clients and the ability to upload and download files are not required, but would be nice benefits.  Because all users would have access to all of the computers resources, I'm thinking there needs to be a restriction at most one users connected at a time, although there might be room to play around here.

As a side note, the system I've been given to test the possibility of setting up this system is a VERY old P3 with 128 Mb of RdRam (so it's not getting any more... no matter how badly it needs it).  If it's absolutely not possible on this machine, I might be able to swing a P4 with up to 2Gb of DDR2 as a test bed, but that's a bigger MIGHT than I'd like to start off with, so IF it's even remotely possible, I would really LIKE to see it done with the older system first.

I thank everyone for their responses, and apologize if what I'm looking to set up is either completely impossible or so unbelievably simple that it's already been done and is well documented somewhere that I've missed entirely.

Regards,

~Dave (The Lost Little Guy):)

---

### Post by Nikron on 2007-02-22
I recently setup a system exactly as described above using SSH and tightvnc..
It was really easy, those are excellent guides.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server)
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

I didn't need to allow only one session, and I can't think of a way to do it off the top of my head.  But I'm sure someone knows how to do it easily.  As a side note:  Do you want GUI on this connection or not?  Terminal is just ssh, graphics would be vnc/freenx.

---

### Post by LostLittleGuy on 2007-02-22
Gui would be preferable.  It's funny how CEO's aren't a big fan of reading ::gasp:: a whole line of information at once.  Of course, I can and will beat him into submission if a GUI isn't possible.

Thank you for all the links!  They look most helpful!  I'm not going to have time to start in on this tonight, but hopefully tomorrow and over the weekend I'll be able to dive into it and let you know how it all works out! Thanks again!

~Dave (The Lost Little Guy)

---

