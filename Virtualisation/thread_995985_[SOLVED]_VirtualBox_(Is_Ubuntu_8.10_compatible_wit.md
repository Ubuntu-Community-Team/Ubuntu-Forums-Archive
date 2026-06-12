---
title: "[SOLVED] VirtualBox (Is Ubuntu 8.10 compatible with anything?)"
date: 2008-11-28
forum: Virtualisation
---

### Post by PCessna on 2008-11-28
Could not find VirtualBox installation. Please reinstall.

here's what I followed
sudo apt-get install virtualbox-ose virtualbox-ose-modules-`uname -r`

Nope can't do that
sudo apt-get install virtualbox-ose 

Try to launch it?

Nope.

Try to launch in terminal

Could not find VirtualBox installation. Please reinstall.

Can I please follow some method to downgrade to 8.04?

**[SIZE="7"]EDIT SOLVED:[/SIZE]**

(what else did I do to make it more clear)

I completely removed OSE, get that junk out, and i installed VirtualBox 1.6, You can find it on Sun's site, I'm terribly sorry I don't have a link now.

I then got the Vir Machine up and going with a fresh install of whatever OS, (Windows XP Pro in my case) I installed additions, closed everything up, and went into terminal to assure the process was terminated

```
killall VirtualBox
```

That's it! Then perform the proper command which I also dont have at this second, man im horrible, to get shared folder configured, closed terminal once you see it was performed ONLY with no errors, and open up virtual box, virtual boxify.. I mean.. uhh.. er.. Power the Virtual Machine up.. and share like a big man. 

-PCessna

---

### Post by evildragon2 on 2008-11-28
I have virtual box working in mine with no problems (using ubuntu 8.10 intrepid. 
I installed by Synaptic and the package is called virtualbox-ose. 
It is located in Accessories

---

### Post by PCessna on 2008-11-28
> **evildragon2 said:**
> I have virtual box working in mine with no problems (using ubuntu 8.10 intrepid. 
I installed by Synaptic and the package is called virtualbox-ose. 
It is located in Accessories

That was not very usual. I would not like to know you're up and running fine when I cannot solve my own problem.

---

### Post by pumkinut on 2008-11-28
I have VirtualBox with a Windows XP guest OS working just fine with 8.10, and the whole things is running on a USB-connected external HDD to boot.  Although, I forewent the OSE install and went with the closed source version from Sun, as I needed USB support to work well.  You could try an apt-get remove and then try to reinstall.  Are you sure all of your repositories are working correctly and updated.

And your second post was a little out of line.  You asked, in your thread topic, if 8.10 and VirtualBox are compatible; evildragon2 replied that his/hers was working just fine.  So, question answered.

---

### Post by PCessna on 2008-11-28
I am sorry. I was mad and replyed incorrectly. Let me start fresh here.

I found a wonderful user's solution to get it installed, now this error with shared folders:

```
paul@paul-desktop:~$ VBoxManage sharedfolder add "XPMCE" -name "paul" -hostpath /home/paul/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.6.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath), fWritable) at line 7320!
[!] Primary RC  = NS_ERROR_FAILURE (0x80004005) - Operation failed
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_FAILURE (0x80004005) - Operation failed
[!] Text        = Shared folder named 'paul' already exists
[!] Component   = Machine, Interface: IMachine, {f95c0793-7737-49a1-85d9-6da81097173b}
[!] Callee      = IMachine, {f95c0793-7737-49a1-85d9-6da81097173b}
paul@paul-desktop:~$ 

THEN I GOT THIS RIGHT NOW: 

paul@paul-desktop:~$ VBoxManage sharedfolder add "XPMCE" -name "paul" -hostpath /home/paul/VirtualBoxShare/
VirtualBox Command Line Management Interface Version 1.6.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling aVirtualBox->OpenSession(aSession, uuid) at line 7315!
[!] Primary RC  = E_ACCESSDENIED (0x80070005) - Access denied
[!] Full error info present: true , basic error info present: true 
[!] Result Code = E_ACCESSDENIED (0x80070005) - Access denied
[!] Text        = A session for the machine 'XPMCE' is currently open (or being closed)
[!] Component   = Machine, Interface: IMachine, {f95c0793-7737-49a1-85d9-6da81097173b}
[!] Callee      = IVirtualBox, {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}
paul@paul-desktop:~$

```

---

### Post by Tom--d on 2008-11-28
Go into synpatic Manager, Install VirtualBox OSE. Virtualbox guess additions. Virtualbox modules.

Then when finished, go to Users and groups and go to manage groups and go to vboxusers and tick your name.

---

### Post by PCessna on 2008-11-28
> **Tom--d said:**
> Go into synpatic Manager, Install VirtualBox OSE. Virtualbox guess additions. Virtualbox modules.

Then when finished, go to Users and groups and go to manage groups and go to vboxusers and tick your name.

How does that deal with my current problem, You need to read the posts above!

---

### Post by howefield on 2008-11-28
Calm down, it is easily fixed, but you can't expect much help when you snap at any and all respondents.

---

### Post by PCessna on 2008-11-28
> **howefield said:**
> Calm down, it is easily fixed, but you can't expect much help when you snap at any and all respondents.
This is a perfect example of a post that gets me angry

The positive part:
"Calm down,***_ it is easily fixed_***"

The spam and useless part the ruiens the whole post part:
" but you can't expect much help when you snap at any and all respondents."

-PCessna

---

### Post by PCessna on 2008-11-28
Bump

---

### Post by PCessna on 2008-11-28
> **pcessna said:**
> bumpbump!!!

---

### Post by bodhi.zazen on 2008-11-28
It would help if you steped back for a minute and took a deep breath.

First to answer your question "VirtualBox (Is Ubuntu 8.10 compatible with anything?)" 

- Yes. Virtualbox , both OSE and PULE editions work on Ubuntu 8.10 as both a guest and host.

After reading your post, it appears you are having a problem with shared folders. The problem is shared folders do not work in the OSE, you need to install the PUEL edition.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Which you get from here :

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

IMO if you had asked "help with shared folders" you would have gotten an answer much more quickly.

If you do not wish to use the PUEL edition, then set up a network share, either samba or ssh (sshfs), or FTP, or http, or what you wish.

---

### Post by PCessna on 2008-11-28
It worked, and no I never had OE, I had the one you said to install. I just had to terminate the process ^^

---

### Post by bodhi.zazen on 2008-11-28
> **PCessna said:**
> It worked, and no I never had OE, I had the one you said to install. I just had to terminate the process ^^

Well, now you are just being difficult (or you do not know what "ose" means or you did not give sufficient information, hard to know what).

from your first post :

> here's what I followed
sudo apt-get install virtualbox-ose virtualbox-ose-modules-`uname -r`That ^^ is the OSE (virtualbox-**ose** virtualbox-**ose**-modules).

At any rate, if it is working, please mark this thread as solved and in  the future:

1. Please try to be more specific and use better titles in your post.

2. Please do not bump your own posts so often (it is considered rude and we are all volunteers here).

---

### Post by Megatrom on 2008-11-28
I am a complete noob and am mostly confused by all of the "ose" "sudo app etc.." stuff, but I suggest you install a fresh 8.04, thats what i did when i was having problems with 8.10 and getting frustrated :-)

---

### Post by bodhi.zazen on 2008-11-28
> **Megatrom said:**
> I am a complete noob and am mostly confused by all of the "ose" "sudo app etc.." stuff, but I suggest you install a fresh 8.04, thats what i did when i was having problems with 8.10 and getting frustrated :-)

:lolflag: Re-installing is common, it is called learning. I had to set a rule on problem solving ...

I can re-install in say 20 min or less, and all my data is backed up so ...

If a system critical problem (like say X) is broken, and it takes longer then 40 min to fix, I re-install.

Without that rule I was spending too much time "learning" and I found it is easier to learn from a working system then a broken one.

Well let me also say, welcome to Ubuntu. It is hard to learn a new OS, but we are here to help. If you have questions feel free to ask. In terms of Virtualbox:

OSE = Open Source Edition, ie installing from the Ubutnu Repositories or compiling from source code.

PUEL = Personal Use Evaluation Liscense. The details are in the link I posted earlier.

---

### Post by jmrjmrjmr on 2008-11-28
I work for a large movie theater and I have received hundreds of complaints that most of the large budget movies are being filmed to dark. Even in the theater you have to strain your eyes through half of the movie. You may notice the greenish tint also. I was told by a film rep that they do this for several reasons, none of which are to make copying easier. So don;t feel bad.

---

### Post by jackm on 2008-11-28
Hi all,
> **Tom--d said:**
> Go into synpatic Manager, Install VirtualBox OSE. Virtualbox guess additions. Virtualbox modules
There isn't **Virtualbox modules** !

---

### Post by Megatrom on 2008-11-28
> **bodhi.zazen said:**
> :lolflag: Re-installing is common, it is called learning. I had to set a rule on problem solving ...

I can re-install in say 20 min or less, and all my data is backed up so ...

If a system critical problem (like say X) is broken, and it takes longer then 40 min to fix, I re-install.

Without that rule I was spending too much time "learning" and I found it is easier to learn from a working system then a broken one.

Well let me also say, welcome to Ubuntu. It is hard to learn a new OS, but we are here to help. If you have questions feel free to ask. In terms of Virtualbox:

OSE = Open Source Edition, ie installing from the Ubutnu Repositories or compiling from source code.

PUEL = Personal Use Evaluation Liscense. The details are in the link I posted earlier.

thank you, and i cud use some help in understanding how to enter those commands in that other thread------>[http://ubuntuforums.org/showthread.php?t=770716&page=4]("http://ubuntuforums.org/showthread.php?t=770716&page=4")

---

### Post by PCessna on 2008-11-29
> **bodhi.zazen said:**
> It would help if you steped back for a minute and took a deep breath.

First to answer your question "VirtualBox (Is Ubuntu 8.10 compatible with anything?)" 

- Yes. Virtualbox , both OSE and PULE editions work on Ubuntu 8.10 as both a guest and host.

After reading your post, it appears you are having a problem with shared folders. The problem is shared folders do not work in the OSE, you need to install the PUEL edition.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Which you get from here :

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

IMO if you had asked "help with shared folders" you would have gotten an answer much more quickly.

If you do not wish to use the PUEL edition, then set up a network share, either samba or ssh (sshfs), or FTP, or http, or what you wish.

Please refer to my edit on my first post, it hopefully clears things up.

---

### Post by jalirious on 2008-12-04
Hm. I just wanted to mention here that it makes me sad that in order to have usb capabilities on virtualbox you must use the (latest) PUEL version.

I specifically decided to use virtualbox rather than VMWare as I had heard it was under the GPL. I ended up installing vb 2.0 on my intrepid (works fine), but the stupid PUEL deal did take the shine off it.

:mad:

---

### Post by bodhi.zazen on 2008-12-04
> **jalirious said:**
> Hm. I just wanted to mention here that it makes me sad that in order to have usb capabilities on virtualbox you must use the (latest) PUEL version.

I specifically decided to use virtualbox rather than VMWare as I had heard it was under the GPL. I ended up installing vb 2.0 on my intrepid (works fine), but the stupid PUEL deal did take the shine off it.

:mad:

+10

If you wish, and have the hardware, try KVM. KVM is opensource.

I agree most people talk about Virtualbox as "opensource", but the OSE is a gateway to the PUEL and then a product, same as VMWare (IMO, don't take it the wrong way (not trying to start a flame war), but VMWare Server is compiled not distributed as a binary).

---

