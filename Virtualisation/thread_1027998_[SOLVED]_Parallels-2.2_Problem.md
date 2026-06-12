---
title: "[SOLVED] Parallels-2.2 Problem"
date: 2009-01-01
forum: Virtualisation
---

### Post by niko123 on 2009-01-01
Hello everyone,

I am using Ubuntu 8.10 and am installing Parallels, the installation went fine, but at the end i was asked to finish configuring parallels with this command.
```
parallels-config
```

After running that command...I go thru the entire agreement process...as soon as i get to the end it prompts me that i ran into this error.

```
Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.
Compilation log is available at /usr/lib/parallels/comp.log.7214.error

```

And whats in that log file is this...
```
cd drivers && make KSRC=/lib/modules/2.6.27-9-generic/build clean && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
make[1]: Leaving directory `/usr/lib/parallels/drivers'
cd wrapper && make clean && cd ..
make[1]: Entering directory `/usr/lib/parallels/wrapper'
rm -f parallels-wrapper
make[1]: Leaving directory `/usr/lib/parallels/wrapper'
cd drivers && make KSRC=/lib/modules/2.6.27-9-generic/build all && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
cd drv_main/ && make KSRC=/lib/modules/2.6.27-9-generic/build && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_main SRCROOT=/usr/lib/parallels/drivers/drv_main modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmmain.o
In file included from /usr/lib/parallels/drivers/drv_main/vmmain.c:29:
/usr/lib/parallels/drivers/drv_main/vmmain.h:193: error: field ‘pmmAccSem’ has incomplete type
/usr/lib/parallels/drivers/drv_main/vmmain.h:206: error: field ‘wsSem’ has incomplete type
In file included from /usr/lib/parallels/drivers/drv_main/vmmain.h:228,
                 from /usr/lib/parallels/drivers/drv_main/vmmain.c:29:
/usr/lib/parallels/drivers/drv_main/mm/mm.h:25:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/lib/parallels/drivers/drv_main/vmmain.h:228,
                 from /usr/lib/parallels/drivers/drv_main/vmmain.c:29:
/usr/lib/parallels/drivers/drv_main/mm/mm.h:99: error: field ‘accSem’ has incomplete type
/usr/lib/parallels/drivers/drv_main/mm/mm.h: In function ‘vmWsetSetup’:
/usr/lib/parallels/drivers/drv_main/mm/mm.h:207: error: implicit declaration of function ‘sema_init’
make[4]: *** [/usr/lib/parallels/drivers/drv_main/vmmain.o] Error 1
make[3]: *** [_module_/usr/lib/parallels/drivers/drv_main] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
make[1]: *** [vmmain] Error 2
make[1]: Leaving directory `/usr/lib/parallels/drivers'
make: *** [build] Error 2
```

Can someone please explain to me what the problem could be...i cant seem to figure it out...

Please and Thank you!

---

### Post by Dedoimedo on 2009-01-02
Do you have the build-essential package installed (gcc, make, kernel source, kernel headers)? If not, install it via synaptic or the command line (sudo apt-get install build-esential), then try again.

Will be installing parallels later today, so we'll see what gives.

Dedoimedo

---

### Post by jrusso2 on 2009-01-02
I don't know why anyone would spend the money for Parallels when there is a really good non = open source version of Virtual box that does more and better at it.

Sorry I am not sure about your problem as I have not used it before but if you can't get it to work try the non open source Virtual Box.

---

### Post by Dedoimedo on 2009-01-02
Parallels are giving free keys for workstation on both windows and linux, so go grabeth one lest they perish.
Dedoimedo

---

### Post by HotShotDJ on 2009-01-02
> **Dedoimedo said:**
> Parallels are giving free keys for workstation on both windows and linux, so go grabeth one lest they perish.
DedoimedoWhat does Parallels have to VirtualBox 2.1 (PUEL) does not have?  I googled "Parallels vs Virtualbox" and could find no reason to to mess with Parallels.

---

### Post by Dedoimedo on 2009-01-02
It's not like someone is going to cut a finger off your hand if you use one, both or neither. FREEDOM of choice ... You can have them all ...
Dedoimedo

---

### Post by HotShotDJ on 2009-01-02
> **Dedoimedo said:**
> It's not like someone is going to cut a finger off your hand if you use one, both or neither.You clearly have never met the manager of my university's ITS department. :lol:

---

### Post by Dedoimedo on 2009-01-02
O-o, one of those, I see!
Well, make sure you run MS VirtualPC then :(
Dedoimedo

---

### Post by niko123 on 2009-01-02
Hi...Thanks for all the replys =]

I have tried your suggestions...but i seem to run into the same error. I have ever tried to uninsall ---reinstall. But no luck! Could it not like my kernel version...



 PLEASE let me know what you get when you try installing parallels on your end.

---

### Post by Dedoimedo on 2009-01-02
I got the same errors as you, even though I have kernel source installed. I'll try tweaking this a little, see what happens.
Dedoimedo

---

### Post by bradthewanderer on 2009-01-02
Try Virtualbox.

---

### Post by niko123 on 2009-01-02
LOL thanks but no thanks. I like parallels much better, and since i grabbed one of those free registration code, why not use a "paid" software instead of an freeware. =] but thanks!!


Dedoimedo i have solved the problem... =] If you are getting the same error as me then the problem lies within the directory of the \bin\bash...it seems that it couldnt find it according to the log.

1) So what i did was COMPLETELY remove parallels.
```
sudo dpkg -r Parallels
```

2) Made sure all the repertories are there...
```
sudo apt-get install build-essential libqt3-mt-dev  
```

3)Here is the tricky part...according to the log file
```
cd drivers && make KSRC=/lib/modules/2.6.27-9-generic/build clean && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'

```

/bin/sh is the first error that we run into in which it can seem to find that directory. SO run this command to so it can duplicate directories that is needed

```
sudo mv /bin/sh /bin/sh.old && sudo ln -s /bin/bash /bin/sh
```


4) Getting the rest of the needed files inorder for Parallels to work.
Download this:
[http://www.filesend.net/download.php?f=9fb29bd235deeb28151470fb28c66b9d](http://www.filesend.net/download.php?f=9fb29bd235deeb28151470fb28c66b9d)

And run this command:
```
sudo cp devel.tar.gz /usr/lib/parallels/devel.tar.gz
```

umm...be sure you save the file to your "home" folder...i ran into an issuse when i saved it on my desktop...in which it wouldn't execute correctly.

5) Run the last command...
```
 sudo parallels-config 
```
Go through the agreement process...


Please note i went though and read like 50 different sites on this problem...a little bit of information there and some there...there...and there...untill i solved my problem =]

Hoped this helped you!!

Lisa

---

### Post by niko123 on 2009-01-02
I apologize for the double post but i forgot to mention...That i DO NOT have a filesend account so that file will be up for a limited time. Please let me know if i need to re-upload that file.

---

### Post by Dedoimedo on 2009-01-02
Nice solution, although I don't think I wanna link shell to bash, as I'm using it in quite a few scripts (sh not bash). Too much tweaking for my liking ... without a dire urgency :)

Especially, since I have other virtualization apps running dandily ... Plus, got Parallels running on Windows, so it's not that urgent.

Nevertheless, it's nice to know that you did it!

Dedoimedo

---

### Post by niko123 on 2009-01-02
> **Dedoimedo said:**
> Nice solution, although I don't think I wanna link shell to bash, as I'm using it in quite a few scripts (sh not bash). Too much tweaking for my liking ... without a dire urgency :)

Especially, since I have other virtualization apps running dandily ... Plus, got Parallels running on Windows, so it's not that urgent.

Nevertheless, it's nice to know that you did it!

Dedoimedo

If you do find a solution on your side...Im all ear to see how you solved it. =]

---

### Post by birddog165 on 2009-01-03
So if I were to follow your steps above niko123, would Parallels work for me too? or is there anything else? I want to install Ubuntu and run Vista through parallels.

---

### Post by niko123 on 2009-01-06
> **birddog165 said:**
> So if I were to follow your steps above niko123, would Parallels work for me too? or is there anything else? I want to install Ubuntu and run Vista through parallels.

Sorry for the late comment been so busy at work it isn't even funny...anyways if this solution worked for me, im SURE it will work for you. I haven't had ANY trouble at all, everything has been working GREAT!!! So far i have XP w/sp3 installed...works flawlessly. And i want to test out windows 7...wondering if its a winner or a epic failure....but will see about that.

If you do try my solution and it doesn't work for you, DO let me know and i willing be more than happy to help you.

---

### Post by pandalous on 2009-01-07
Hi. Could you please re upload the files that are needed? Thank you!It'd be really appreciated.

---

### Post by gmatt on 2009-02-20
For those of you still struggling please look at:

[http://ubuntuforums.org/showthread.php?t=1018159](http://ubuntuforums.org/showthread.php?t=1018159)

(note that you need to download certain files to complete the howto successfully, in that thread I have posted an attachment with the two crucial files that might be impossible to get otherwise; I have the sense to avoid rapidshare as it has a tendency to disappear.)

---

