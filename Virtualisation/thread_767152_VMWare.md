---
title: "VMWare"
date: 2008-04-25
forum: Virtualisation
---

### Post by joeri_83 on 2008-04-25
Hi

This might seem like a stupid question, but I had Windows XP running under VMWare before upgrading to Hardy, and now after the upgrade VMWare doesn't seem to be installed. What's going on?

---

### Post by seamuso on 2008-04-25
Are any of the vmware binaries installed? If they are still on the machine, but just not running, you probably just need to reconfigure vmware again for the new kernel.

sudo vmware-config.pl

If the modules fail to build, you'll need to grab the current any-any patch.

---

### Post by sefs on 2008-04-25
VMware Sever or Vmware Workstation?

And when you say cannot install it do you mean it does not compile against the new hardy kernel?

If so the two problem things are vmmon.tar and vmnet.tar of which they are patches for to get them working especially if you are wireless and need to access the internet from a vm.

When I get home, i'll see if i still have the link that helped me out. 

What you will need to do is get the patches ... follow the directions and then run the vmware installation.

[http://liken.otsoa.net/blog/index.php?entry=entry080301-173023](http://liken.otsoa.net/blog/index.php?entry=entry080301-173023)
This link is for workstation 6.0.3 not sure (doubtful) it will work with the the server version.

What i did was to download the path at the bottom of the page, vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz 
unzip it, get the vmmon.tar and vmnet.net from it copied it to the unziped distribution of 
vmware-distrib/lib/modules/source

and then ran the vmware install.

I came across the patches for the server in my search but i dont seem to see the link around anymore.

---

### Post by unbuntued on 2008-04-25
Check here: [http://communities.vmware.com/docs/DOC-3850](http://communities.vmware.com/docs/DOC-3850)
Solutions for both Vmware Server and Workstation.

Hope it helps.

---

### Post by joeri_83 on 2008-04-25
Guess I expressed myself in an unclear manner, sorry about that. VMServer is what I meant. I had it installed under Gutsy, but if I know type vmware or vm and then tabs, the program does not seem to be installed anymore. Is it lurking somewhere on my harddrive or was it wiped out during the upgrade?

If the latter, are there any binaries I could grab?

---

### Post by sefs on 2008-04-25
Adding to what ubunted said above,

here is another with the patches  you can download for server i believe

[http://communities.vmware.com/thread/121847](http://communities.vmware.com/thread/121847)

---

### Post by Cpudan80 on 2008-04-25
I found this solution in the ubuntu forums -- worked excellent for me:

Kudos to whoever posted it originally -- here's an abridged version:

step 0) sudo apt-get install build-essential
step 1) download newest vmware tar file
step 2) extract it to someplace
step 3) go to [http://groups.google.com/group/vmker...es/files?hl=en](http://groups.google.com/group/vmker...es/files?hl=en) and download patch 116

step 4) extract it someplace (not in your vmware dir)
step 6) Run the patch file (as root)
step 7) This should automatically fire off the regular installer, if it doesn't run that after (as root)

** This is what took me a while to find **
step 8) cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
step 9) cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

---

### Post by joeri_83 on 2008-04-25
I think I will wait until it is more complete. Thanks though!

---

### Post by joeri_83 on 2008-04-25
By the way though, would the upgrade have removed the previously installed Vm Server?

---

### Post by sefs on 2008-04-25
i doubt...it would just prevent it from starting up, so your vm's should still be intact in the vm directory

---

### Post by joeri_83 on 2008-04-25
So where is that directory? (Meaning the one from which I can start vmware.) I can find the files defining the actual VM with Windows XP on it, but I would like to run it too.

Again, thanks!

---

### Post by Cpudan80 on 2008-04-25
VMWare's files are in two locations:

/etc/vmware/
/usr/lib/vmware/

The executable thing is at:

/usr/bin/vmware

The Virtual Machine's HDD is at:

/var/lib/vmware/Virtual Machines/

---

### Post by joeri_83 on 2008-04-25
Thanks! The files in /etc/vmware/ are there (and I know where I've kept the VM HDDs) but the other two are not there. 

What's the best way to get it up and running again.

---

### Post by mpp on 2008-04-26
It looks like vmware-server is not (yet) available in the partner repositories for hardy :(

[http://archive.canonical.com/ubuntu/pool/partner/v/vmware-server/](http://archive.canonical.com/ubuntu/pool/partner/v/vmware-server/)

I wonder if/when it will be?  I remember for the gutsy upgrade it was yonks before it was available.  I hope it doesn't take so long this time.

have fun()
mike

---

### Post by Syspeg on 2008-04-26
I followed this and it worked for me. You saved the day. :)

---

### Post by joeri_83 on 2008-04-26
So I would have to download the tar and then follow the steps outline earlier?

---

### Post by Cpudan80 on 2008-04-26
Yes -- just download the new tar from VMWare and follow my steps from earlier. If it gives you an error about not being able to install, delete the old vmware install directories (don't delete the actual VMs!) then retry.

Dan

---

### Post by joeri_83 on 2008-04-26
Thanks! I will give this a try.

---

### Post by joeri_83 on 2008-04-26
When I'm trying to run runme.pl in the patch it tells me this:

> Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware-server/modules/source/vmmon.tar.

Execution aborted.

What is wrong?

---

### Post by joeri_83 on 2008-04-26
Missed one line:
> 
Updating /usr/bin/vmware-config.pl ... corrupted
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware-server/modules/source/vmmon.tar.

---

### Post by Jerrac on 2008-04-26
> **Cpudan80 said:**
> I found this solution in the ubuntu forums -- worked excellent for me:

Kudos to whoever posted it originally -- here's an abridged version:

step 0) sudo apt-get install build-essential
step 1) download newest vmware tar file
step 2) extract it to someplace
step 3) go to [http://groups.google.com/group/vmker...es/files?hl=en](http://groups.google.com/group/vmker...es/files?hl=en) and download patch 116

step 4) extract it someplace (not in your vmware dir)
step 6) Run the patch file (as root)
step 7) This should automatically fire off the regular installer, if it doesn't run that after (as root)

** This is what took me a while to find **
step 8) cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
step 9) cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

Hey, I went to try the patch, but the link doesn't work. Could you post it again?

---

### Post by doctah on 2008-04-26
Download it from [http://vmware.com/download/server/](http://vmware.com/download/server/)
Patches: [http://groups.google.com/group/vmkernelnewbies/files?hl=en](http://groups.google.com/group/vmkernelnewbies/files?hl=en)

Install guide:
[http://ubuntuforums.org/showpost.php?p=4357442&postcount=10](http://ubuntuforums.org/showpost.php?p=4357442&postcount=10)

For what it's worth, I installed VMWare Server Beta 2 under Hardy w/o issue.  No any-any patches...bridging with wireless worked "out of the box".  VMWare seems to be going in a different direction as far as a Console application...some hate it...I think 1 or 2 people like it :)

...but the fact it compiled and worked without much googling or "sed" commands rocks.

---

### Post by Jerrac on 2008-04-26
Thanks for the links. I'll try the beta. :D

---

### Post by joeri_83 on 2008-04-26
thanks doctah

---

### Post by wkoorts on 2008-04-27
Thanks for this thread guys, but I'm having similar problems and am still a little confused.  My VMWare Workstation installed fine on Hardy with the any-any-116 patch and everything seems to be working fine except that I can't access the internet from my virtual machines (they can ping the host box and vice versa).  One is Gutsy Server and the other Win XP.

Does this mean that I need that wireless bridge patch also and then re-install?  I'm using bridged mode networking and a wireless ethernet adapter.

Regards,
Wayne

---

### Post by Jerrac on 2008-05-02
Well, I tried the beta version, and it didn't work right... running vmware from the commandline just opened up a browser to 127.0.0.1(I think that was it). Which didn't load anything.

So I used the any-any-wireless patch, and the config would not build the vmnet module.

Any suggestions? I'll do some more research later when I have more time.

---

### Post by DapperDanMan on 2008-05-03
I have this problem every time I upgrade to a new version (kernel). I have to search the web for a VMserver fix because a new kernel breaks it. I have to have vmserver to connect to my work PC (unless someone can tell me how to get a Linux Cisco client to work :oops:). Anyway, I upgraded yesterday and found the following this morning. VMserver is running once again.

[http://www.bauer-power.net/2008/04/i...buntu-804.html](http://www.bauer-power.net/2008/04/i...buntu-804.html)

---

### Post by Jerrac on 2008-05-03
Hmm.. thanks for the reply. But the link didn't work. The forums apparently decided that sticking "..." in the middle of the link was a good thing... Second link in the topic that has done that. heh.

---

### Post by Jerrac on 2008-05-03
I think I found the link you posted...
[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)

And also this:
[http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu.html](http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu.html)

Followed the instructions for installing the stable version of vmware-server, but the config script still ends when it can't compile the vmnet module.

Here is what it outputs:
> 
Building the vmnet module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config7/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config7/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config7/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config7/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config7/vmnet-only/bridge.o
/tmp/vmware-config7/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config7/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmnet-only'
Unable to build the vmnet module.


This is after the patch is installed.

I also copied those two libraries mentioned in the link.

---

### Post by digitalbenji on 2008-05-04
I'm getting the exact same error, it can't compile the vmnet.tar module.  Does anyone know a solution to this?  I hope so :)

---

### Post by digitalbenji on 2008-05-06
bump.  vmware works, but I can't get the wireless bridge to function.  I even modified the bridge.c file and changed line 35 to #if instead of #ifdef.  It compiles, but the brigde doesn't function.  Does it work for anyone?

---

### Post by digitalbenji on 2008-06-06
ok, so vmware 1.0.6 is out.  it does install in hardy, but for me i needed to do this after installation
```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```
in order to get it to start.  it runs alright, but i'm testing now, and it doesn't seem like the wireless bridge is working.

---

