---
title: "I created my own flavor of ubuntu! ...Now what?"
date: 2009-03-08
forum: The Cafe
---

### Post by CJ Master on 2009-03-08
Hello. :) I've create my own little proof-of-concept distro :) I created it by installing Ubuntu 8.10 within Virtual Box, tinkering with it, then using remastersys to create the iso. Now I got a couple of questions...

How do I get the iso of the Virtual Machine?? I can't burn it to a disk (when I enable the write to DVD setting, the bootup spits up a bunch of errors and it just doesn't work.) and It won't even recognize my flash drive. Oh, and I tried using shared folders but it gives me a "protocol error" when I try to mount it in virtual machine.

And once I get it out... then what? How do I get a license on it? Its 900 megs, so is there any place where I can upload it for free (considering its size.)

Thanks very much. :)

---

### Post by super.rad on 2009-03-08
Out of interest when you say you "tinkered with it" what exactly do you mean?
Why do you want to upload it to the internet, are you planning on trying to start your own distro?

---

### Post by TenPlus1 on 2009-03-08
Set up a shared directory in Virtualbox and copy your .iso to the shared directory in Ubuntu...  Make sure Guest Additions are installed in VirtualBox so that shares work properly...

---

### Post by agim on 2009-03-08
I am also curious. What changes did you make?

---

### Post by CJ Master on 2009-03-08
Thanks TenPlus, but I already said that I couldn't get shared folders working.

Well... it's currently in very early alpha right now, but I am going to create a small speciality distro... Its design philosophy is to make a system in which anybody, no matter what their computing experiance is, even total beginers can use it without any problems. Thats the main philosophy behind it... of course, I'm trying to get it compatable with many other computers, new users generally don't know how to use terminal to start or ect ect...

---

### Post by super.rad on 2009-03-08
So you're trying to make another version of ubuntu? Using ubuntu.
Everyone I've ever introduced Ubuntu to have been able to do everything they usually did on computers straight away.
Sorry if I sound quite negative but in my opinion it would be very hard to make ubuntu any easier than it currently is

---

### Post by Naiki Muliaina on 2009-03-08
So your making a GUI based flavour? Got a website or anything for it? ^^

---

### Post by CJ Master on 2009-03-08
> **super.rad said:**
> So you're trying to make another version of ubuntu? Using ubuntu.
Everyone I've ever introduced Ubuntu to have been able to do everything they usually did on computers straight away.
Sorry if I sound quite negative but in my opinion it would be very hard to make ubuntu any easier than it currently is

I completely understand your opinion. Ubuntu by itself is extremally easy. It's not really meant as a extremely serious distro, basically just a test too see how easy I can get Linux. (Don't deny that Linux is known for needing to be a geek to use it... this project is intended to show the exact opposite, being easier to use then Windows.)

> So your making a GUI based flavour? Got a website or anything for it? ^^ 

Thanks for showing interest, unfortunately I currently do not have a web-site for it. :)

---

### Post by CJ Master on 2009-03-08
Alirght: I found the GPLv3 here:

[http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)

Looks like what I want (although I'm a bad reader of legalbabble...)

Now to find somewhere where I can upload it..

---

### Post by chris4585 on 2009-03-09
try making a torrent?

---

### Post by FuturePilot on 2009-03-09
> **CJ Master said:**
> but I already said that I couldn't get shared folders working.


There's a bug with the shared folders on Linux guests that sometimes shows up. Open the Shared Folder settings and rename your share to something else. Then try and mount it with the new name.

---

### Post by CJ Master on 2009-03-09
**Progress Report:**

This just in: I'm a big fat IDIOT!! It didn't work because I tried to put the 900 gig iso on a CD. D'oh!! Ah, well. At least I figured it out. :D

And to satisfy your curiousity, here's a **alpha** screenshot. (screenshot is large so click on link.) I intend to change it by the time I release it, but I NEED user opinions on how to make it more user friendly.

[http://s146.photobucket.com/albums/r252/CJ_Master/?action=view&current=Screenshot_SL.png](http://s146.photobucket.com/albums/r252/CJ_Master/?action=view&current=Screenshot_SL.png)

One thing that's annoying me is that every time I run remastersys it takes off the FireFox Launcher on Docky, and Internet is obviously a very important part... Plus, LiveCD shows the color of the wallpaper, but not the top-right logo. :o Not major, but I'd like to get it fixed.

Other then that, progress going smoother, still have no idea in heck how I'm going to upload it. :D

---

### Post by Bart_D on 2009-03-09
Looks good....

But you'll have to upload it for people to get a feel for it.....

---

### Post by Mehall on 2009-03-09
RE: Using GPLv3

Since it's a modification of Ubuntu, you need to use the License Ubuntu itself uses.

EDIT: looks like Dream Linux.

---

### Post by CJ Master on 2009-03-09
Haha, Yea I relised that right after I posted. :P So I recon thats the one I'm gonna use. :P

Hmm... Now that you mention it, It does! I always thought that dream linux looks cool, so this is a nice little realisation for me. :)

---

