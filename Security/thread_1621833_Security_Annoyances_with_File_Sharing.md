---
title: "Security Annoyances with File Sharing"
date: 2010-11-14
forum: Security
---

### Post by PerryCS on 2010-11-14
Hey there,

I am pretty frustrated with Ubuntu security partially because I don't know exactly how to fix things in it like I do windows and you can't always use GUI with Ubuntu which is quite annoying.

Basically.. I created a samba share.  When I copy files from my Windows machine TO the Samba share the permissions are always screwed up.  I can watch the videos but I can't delete them.  I have to go into Nautalis? via F2, sudo something and change permissions everytime I copy something into the shared folder.  To me, this is stupid.

Another issue... I added a 2nd hard drive to my Ubuntu machine, shared the entire drive.  Once again.. when I copy files to the share I can only read them.. I have to keep stealing ownership so to speak over the files.

Now, when I want to CUT and PASTE from my Drive "C" Ubuntu to my Drive "D" I dont have access.   Ugh... why can't there just be a way to make all files accessable.

Why should I have to pop into a different program to regain permissions everytime.

When I create a folder it should STAY that way.  Anything I copy into it.. its MINE....  Just because I copy from another machine onto THIS machine, I am still the creator of that folder.  I SHOULD have access to EVERYTHING in it.

Ugh... Im so fed up with security in Windows (huge joke) and now this annoyance.   Windows XP and previous was easy.  Vista, 7 suck huge..... well... you know...   and now I'm finding annoyances with Ubuntu.


Sorry to sound annoyed but all this security is really annoying me.  I want a "GOD" mode.  If I want to delete the entire Windows folder while windows is running... let me!   If I want to delete the entire Ubuntu drive while its running.. let me!  At least give me the option of turning it on.

So... please explain to me how to fix this please?

Either show me a way to make my current login as powerful as root (sudo?) everytime or show me a way please to make a folder and ALL its contents always accessable to me regardless who stuck the files into the folder I created in Ubuntu :(

How I miss the good ole days. I hate everything about all the new OS's.

It wouldn't be so bad if I could just right click and "GIVE ME ALL PERMISSIONS" on a folder but instead it says.. "You don't have access to change the permissions" even though "I" created the folder.   I did pop into SUDO and change the permissions for the folder and its contents everytime I dump something into it.

Thank you for your help.  Sorry to be so grumpy about it... it's just getting more annoying as time goes on using anything.  UAC in Windows, security, crap and more crap.  More hastle, less functionality.

---

### Post by brian_p on 2010-11-14
> **PerryCS said:**
> Hey there,

Who? Me?

> Sorry to sound annoyed but all this security is really annoying me.  I want a "GOD" mode.  If I want to delete the entire Windows folder while windows is running... let me!   If I want to delete the entire Ubuntu drive while its running.. let me!  At least give me the option of turning it on.

So... please explain to me how to fix this please?

I'd tell you how to become and remain root but then nobody on this forum would speak to me. Not that they do that anyway! Even mentioning searching G---l- might get me black looks.

You remind me of a friend of mine. Every time a fuse blew in his house he wanted to reconstruct the national grid.

---

### Post by cariboo on 2010-11-14
Although it isn't very advisable, you can set the permissions of the mount points to 777, to give everyone read/write access to your files. eg:

```
 sudo chmod -R 777 /media/disk
```

Remember you weren't born knowing how to use Windows, it took time to learn the OS, why should Ubuntu or any other Linux variant be any different.

---

### Post by CharlesA on 2010-11-14
How did you set up Samba?

It shouldn't be doing that.

---

### Post by Citizen_Kane01 on 2011-02-14
Simple file sharing over a home network, in my opinion, is the glass jaw of Linux usability. It should be the simplest thing to set up and use, however it is not.

Over the last 3 years of Linux use it is the one item where I consistently get stuck. I am no Guru, but have definitely passed the Newbie status. It always kinda works, but runs into some sort of trouble.

The best I have got it is to skip the "out of the box" setup and go straight to assigning fixed IP adresses to my home computers on the wireless router.

I then map these manually as Windows shares in Nautilus. This enables me to at least reliably see and connect to my shares, except for a ext4 partition set up from install (separate from /) to store data on my media machine. Something in Fstab wont allow samba to mount!

Permissions!!! - Don't get me started. When I copy a file, I get read only access to it from the machine it is copied to. (user- nobody, group nobody) and no amount of tampering with samba.cfg seems to want to change that.

I have searched relentlessly on Google for a simple guide aimed at a general user setting up shares at home, but always seem to run into advanced configuration networking guides which need a degree to understand.

Anyway - this looked like a good thread for a little rant, so rant over.

I still love you Linux and Ubuntu.

---

### Post by sydbat on 2011-02-14
> **Citizen_Kane01 said:**
> Simple file sharing over a home network, in my opinion, is the glass jaw of Linux usability. It should be the simplest thing to set up and use, however it is not.Not really a Linux problem, though. If Microsoft did not make life extremely difficult for people NOT using Windows, the set up would be straight forward, point and click...which it is between Linux boxen...and with OSX.

---

### Post by CharlesA on 2011-02-14
> **sydbat said:**
> Not really a Linux problem, though. If Microsoft did not make life extremely difficult for people NOT using Windows, the set up would be straight forward, point and click...which it is between Linux boxen...and with OSX.

Gogo NFS! ;)

---

### Post by HermanAB on 2011-02-15
Howdy,

The root of the problem is that Windows and Linux handle Users and Groups differently. Since you got it mostly working, you already had a major accomplishment.  The remaining little tweaks are simple to do and I think that all you need to do is open up the Linux access permissions - set it to 777:
$ sudo chmod -R 777 /home/sambashare

and one day once you have the sambashare user group under control, you can restrict it a bit to 775.

Here is a little guide that may help as well:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

