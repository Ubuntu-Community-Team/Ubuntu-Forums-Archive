---
title: "Xen and convirt: how do I use it?"
date: 2008-10-20
forum: Virtualisation
---

### Post by sci-fi guy on 2008-10-20
I am trying to wrap my head around using Xen and convirt (my only other experiance with VMs is VirtualBox and VMWare).

I am not sure how to create a new VM in convirt. I think I was going the right direction with right-clicking "Desktops" in the side panel and selecting "Add Server", but I got an error (see attached). The [Xen guide]("https://help.ubuntu.com/community/Xen") in the Ubuntu wiki warns that the instructions are for Feisty, and not completely compatible with Gutsy (and I am using Intrepid); so I am not having much luck using that.

---

### Post by eternaluxe on 2008-10-21
Without knowing what you put in for the host name or your overall setup, I'm just taking a shot in the dark.  If you are running Convirt on the same machine as your xen server, then I think you could use the local ip (or the local host name).  Otherwise, use the ip of the managed server.  You could use the host name of the managed server if it is registered in your domain's dns, other wise just add a line to your /etc/hosts file defining it.
ie:
192.168.1.100 managed-server
(or whatever the ip/host name combination is)
-Patrick

---

### Post by sci-fi guy on 2008-10-21
Well, I am running Xen and convirt on the same machine.I set the host name to this machine's name, and I am now getting a "Connection Refused" error (using my login/password for this machine).

---

### Post by eternaluxe on 2008-10-21
The convirt package for intrepid is version 8.2 which supports up to Xen 3.2.  intrepid will install xen 3.1 (which will work) or xen 3.3 (which might not).
which version are you using?  
```
dpkg -l | grep xen
```
should show which xen packages you have installed
If it's 3.3, you may need downgrade xen or upgrade convirt.
If it isn't we'll have to dig deeper.

---

### Post by sci-fi guy on 2008-10-22
It's 3.3.
Why would there be two different versions in the repos?

Hmm. No .debs for convirt. I think I'll go with downgrading xen. Which packages should I remove? I had installed ubuntu-xen-desktop (autoremove should clear out everything it installed, right?)

---

### Post by eternaluxe on 2008-10-22
Okay, here is what I've come up with.  Hold off for the moment on doing anything.
Intrepid uses paramiko 1.7.4 and I haven't seen any patches in the Convirt code for that version of paramiko.  I've left a [note]("http://sourceforge.net/forum/forum.php?thread_id=2416592&forum_id=577781") on the Convirt forum.  We'll see.
We may have to install a lower version of paramiko....
-Patrick

---

### Post by eternaluxe on 2008-10-22
According to the developer, Paramiko 1.7.4 squashed the bugs that necessitated the patches, so that's good.
Let's update convirt instead of downgrading Xen.
I'll paraphrase the instruction from the [convirt wiki]("http://xenman.sourceforge.net/wiki/index.php/Xen_ubuntu")
I list python-xen and python-paramiko in the install in the off chance that by removing convirt you remove them, too.
From the command line:
```
sudo apt-get remove convirt
wget http://superb-east.dl.sourceforge.net/sourceforge/xenman/convirt-0.9.5-1.suse.noarch.rpm
sudo apt-get install alien python-xen-3.3 python-paramiko
sudo alien -d convirt-0.9.5-1.suse.noarch.rpm
sudo dpkg -i convirt_0.9.5-2_all.deb
```
That should do it.
Let me know how it works out for you.
-Patrick

---

### Post by sci-fi guy on 2008-10-22
Eh, still getting "Connection Refused"

Also, no Xen processes are listed as running. When I try to run xend I get

```
$ sudo xend
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xend", line 44, in <module>
    from xen.xend.server import SrvDaemon
  File "/usr/lib/python2.5/site-packages/xen/xend/server/SrvDaemon.py", line 26, in <module>
    import relocate
  File "/usr/lib/python2.5/site-packages/xen/xend/server/relocate.py", line 28, in <module>
    from xen.xend import XendDomain
  File "/usr/lib/python2.5/site-packages/xen/xend/XendDomain.py", line 35, in <module>
    from xen.xend import XendOptions, XendCheckpoint, XendDomainInfo
  File "/usr/lib/python2.5/site-packages/xen/xend/XendCheckpoint.py", line 20, in <module>
    from xen.xend import balloon, sxp, image
  File "/usr/lib/python2.5/site-packages/xen/xend/image.py", line 44, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')

```

---

### Post by eternaluxe on 2008-10-22
Are you booting with a xen kernel?
```
uname -r
```
if you the response ends in -generic you'll need to reboot.
when grub appears press the escape key to get to the grub menu and select one of the xen kernels; they end in -xen.

---

### Post by sci-fi guy on 2008-10-22
Hmmm. For some reason I am on -server, and don't have a -xen installed at all. In fact, I don't see any -xen kernels in the repos. There is, however, a -virtual.

---

### Post by eternaluxe on 2008-10-23
have you installed ubuntu-xen-desktop or ubuntu-xen-server?

---

### Post by sci-fi guy on 2008-10-23
> **eternaluxe said:**
> have you installed ubuntu-xen-desktop or ubuntu-xen-server?

I had installed ubuntu-xen-server, then -desktop later hoping to get a GUI manager. Now -desktop isn't installed because upgrading convirt had removed -desktop (which had depended on it)

---

### Post by eternaluxe on 2008-10-23
Reinstall -desktop and give it a go.

---

### Post by sci-fi guy on 2008-10-24
Still on linux-server. ubuntu-xen-desktop lists it as a dependancy. And I still can't find any linux-xen kernels in the repos, just linux-virtual. Should I try that? ubuntu-xen-desktop's description says that it is safe to uninstall because none of the xen packages depend on it (I guess it is a meta-meta-package).

---

### Post by eternaluxe on 2008-10-24
Wierd.  The kernel provided by the [meta package]("http://packages.ubuntu.com/intrepid/ubuntu-xen-desktop") for intrepid is the standard server kernel, not the xen.  If you check the [package for hardy]("http://packages.ubuntu.com/hardy/ubuntu-xen-desktop"), it has a xen kernel as the 4th depend.  

I did find a xen kernel for intrepid [here]("https://launchpad.net/ubuntu/intrepid/i386/linux-xen/2.6.24.16.18").

you can down load it and install it with dpkg.

---

### Post by sci-fi guy on 2008-10-24
Well, I use x86-64 so I went and got the right package. 2.6.24? I suppose that's why it isn't in the repos at this time?

Anyways, the xen kernel isn't working (unless it is *supposed* to show a completely blank screen).

---

### Post by eternaluxe on 2008-10-27
You _should_ be able to run a 32-bit kernel on a 64-bit machine, it just wouldn't be optimized for 64-bit architecure.  That being said, I don;t have a 64-bit machine to test on, so I cannot confirm.
Did you download and install the intrepid xen kernel I pointed out?

---

### Post by sci-fi guy on 2008-10-27
Whew. I was afraid I had scared you off.

> **eternaluxe said:**
> You _should_ be able to run a 32-bit kernel on a 64-bit machine, it just wouldn't be optimized for 64-bit architecture.  
True, 32-bit OSs work on 64-bit CPUs (It is getting hard to find a 32-bit CPU nowadays, but Windows is still mostly 32-bit), but I don't think they can run 64-bit programs (which is all I have installed)

> Did you download and install the intrepid xen kernel I pointed out?
I installed [this one]("https://launchpad.net/ubuntu/intrepid/amd64/linux-xen/2.6.24.16.18"); and half a dozen dependencies. Not being able to use the repos makes me appreciate them much more.

---

### Post by sci-fi guy on 2008-10-29
OK, I think I found the problem: My processor, a [Core 2 Duo T5300]("http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#.22Merom-2M.22_.28standard-voltage.2C_65_nm.29"), does not support virtualization. (although VirtualBox works for some reason)

---

### Post by eternaluxe on 2008-10-30
VT is not necessary for Xen, though it helps alot.
I set up a machine (32-bit) in your configuration and have gotten the same results.
After some research, [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/68440") is what I found.
We could be out of luck.  Looks like a bug in either the kernel or the intel drivers and it doesn't look fixed. 
Are you using on-board intel graphics? or do you have a grahpics card?  If you are using on-board intel chipset, that could be the issue.  I'm going to install a graphics card and see what happens.

[edit]
I lied.  I'm still using hardy, not intrepid.  Found [this]("http://ubuntuforums.org/showpost.php?p=5992466&postcount=6") about intrepid and Xen.>  Re: Xen in 8.10
The normal kernels support Xen domU functionality. We do not and will not have a dom0 kernel in 8.10.
__________________
William Grant
Ubuntu Developer 
Looks like you'll have to try your hand at KVM? or downgrade to Hardy.  Sorry about that.
-Patrick

---

### Post by eternaluxe on 2008-10-30
Works with a graphics card.
```
dpkg-reconfigure -phigh xorg-xserver
```
seems to do the trick.  Now... about that 32-bit issue...

---

### Post by sci-fi guy on 2008-11-03
> **eternaluxe said:**
> Works with a graphics card.
```
dpkg-reconfigure -phigh xorg-xserver
```
seems to do the trick.  Now... about that 32-bit issue...

Are you doing this in Hardy? In Intrepid the package is named xserver-xorg.

---

