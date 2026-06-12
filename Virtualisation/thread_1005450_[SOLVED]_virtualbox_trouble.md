---
title: "[SOLVED] virtualbox trouble"
date: 2008-12-08
forum: Virtualisation
---

### Post by 2handband on 2008-12-08
I set up a virtual machine for Windows Vista as per the instructions I found online and when I try to run it I get the following output:


"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic.."

I already installed virtualbox-ose-modules-generic. But it keeps giving me this output. What am I doing wrong?

---

### Post by roadmouse on 2008-12-08
I have the same problem. VirtualBox used to work before.
Also got the required kernel drivers installed, but no luck...

Any suggestions are welcome :)

---

### Post by Locke_99GS on 2008-12-08
Make sure you have the *virtualbox-ose-source* and *dkms* packages installed.

---

### Post by howefield on 2008-12-08
If you open a terminal and type

```
uname -r
```

The modules you install need to correspond with the output of the above command.

---

### Post by p_quarles on 2008-12-08
> **howefield said:**
> If you open a terminal and type

```
uname -r
```

The modules you install need to correspond with the output of the above command.
Which can be done more easily by running:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

---

### Post by 2handband on 2008-12-08
the response to that command was: 2.6.24-22-generic

there isn't a module in the package manager for that kernel. where can i get one?

---

### Post by frodon on 2008-12-08
yep, same here.

i think there's a delay currently between the new kernel and the corresponding virtualbox kernel modules. It seems that the new kernel modules for virtualbox have not reached the repositories yet.
So for this issue all we need is to wait for these kernel modules to hit the repositories.

---

### Post by p_quarles on 2008-12-08
> **frodon said:**
> yep, same here.

i think there's a delay currently between the new kernel and the corresponding virtualbox kernel modules. It seems that the new kernel modules for virtualbox have not reached the repositories yet.
So for this issue all we need is to wait for these kernel modules to hit the repositories.
I find it easier to use Sun's repository. For 8.10, you would add the following source to /etc/apt/sources.list:
```
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```
And yes, Ubuntu packages are in the debian directory on Sun's servers, not a typo.

---

### Post by 2handband on 2008-12-08
I tried that command (amending intrepid to hardy) and it insists that deb isn't a command. I'm probably doing something wrong... I'm pretty lame when it comes to command line.

---

### Post by p_quarles on 2008-12-08
> **2handband said:**
> I tried that command (amending intrepid to hardy) and it insists that deb isn't a command. I'm probably doing something wrong... I'm pretty lame when it comes to command line.
It's not a command, you need to add that to the file I mentioned.

---

### Post by Locke_99GS on 2008-12-08
Use:

```

sudo nano /etc/apt/sources.list

```

and add the deb line p_quarles mentioned earlier to the bottom of that file:

[quote=p_quarles]
```

deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

```
[/quote]

Use Ctrl+O to save the file in nano. 

You'll next need to add Sun's key to authenticate; this can be done with this one-liner:

```

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

Then all thats left to do is refresh your lists:

```

sudo apt-get update

```



Though, *dkms* should keep everything in line for you.

---

### Post by 2handband on 2008-12-08
I ran that and got the following output. I'm a little confused; I thought i just ran apt-get update.



"W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: You may want to run apt-get update to correct these problems"

---

### Post by Locke_99GS on 2008-12-08
I see. Try this, then update again:

```

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

This will download sun's key and add it for you. I'll edit my previous post to reflect this.

---

### Post by 2handband on 2008-12-08
The good news is that it now does the updates without any error messages. The bad news is that I still get that same error message when I try to run Virtualbox.

---

### Post by Locke_99GS on 2008-12-08
I wish I could be of more help. Virtualbox works fine for me - I've never really had any issues with it.

I am using kernel 2.6.27-10 and Virtualbox 2.0.4 OSE from the repo's.

---

### Post by p_quarles on 2008-12-08
> **2handband said:**
> The good news is that it now does the updates without any error messages. The bad news is that I still get that same error message when I try to run Virtualbox.
Try:
```
sudo /etc/init.d/vboxdrv start
```

---

### Post by 2handband on 2008-12-08
I tried that command and got this:

"gene@gene-laptop:~$ sudo /etc/init.d/vboxdrv start
[sudo] password for gene: 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found."

Thanks for sticking with me here everyone... this is the best online community I've ever come across! Assuming I can't get this damn thing working what's another virtual machine I can try?

---

### Post by Locke_99GS on 2008-12-08
If you're using an older version of vbox (1.6 or whatever) try this:

```

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv restart 

```

What version os VirtualBox are you using, and do you have dkms installed?

---

### Post by 2handband on 2008-12-08
Ok, fixed. First I uninstalled the outdated version of virtualbox on my machine. I then installed virtualbox 2.0. I then followed the instructions from the following website:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Works great! Thanks to everybody... you guys seriously rock.:guitar:

---

### Post by John Jason Jordan on 2008-12-08
I have been using Virtualbox for a long time. The only problems I have had is when there is a kernel upgrade I have to go into Synaptic and install the new virtualbox-ose headers.

Today I upgraded my laptop from Hardy to Intrepid and now Virtualbox won't start. According to Synaptic I have version 2.0.4-dfsg-0ubuntu. I also have virtualbox-ose-guest-utils and virtualbox-ose-source, same versions. I had the guest utilities installed previously but I noticed that they were not installed after the upgrade to Intrepid.

From the command line I get:

jjj@Devil7:~$ virtualbox
VirtualBox: supR3HardenedVerifyDir: Cannot trust the directory "/usr/lib/virtualbox": not owned by root (st_uid=1000)

Does anyone know what is going on and how to fix it?

---

### Post by loveandequality on 2008-12-08
please i need help really i mean im going to rip my fongers alredy. here is what i get i try several post and ideas nothing works i got 8.4. i want my USB to work


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}


im new to linux so im dum.

---

### Post by p_quarles on 2008-12-08
The last two posts are problems that are completely unrelated to the problem addressed in this thread. Please start threads of your own.

---

