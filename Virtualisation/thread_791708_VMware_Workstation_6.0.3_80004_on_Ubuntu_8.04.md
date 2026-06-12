---
title: "VMware Workstation 6.0.3 80004 on Ubuntu 8.04"
date: 2008-05-12
forum: Virtualisation
---

### Post by Intangir on 2008-05-12
get VMware-workstation-6.0.3-80004.i386.tar.gz
from [http://www.vmware.com/download/ws](http://www.vmware.com/download/ws) (you will have to make an account)
extract it

get the build-essential package

```
sudo apt-get install build-essential
```

goto the extracted vmware directory and run the install script

the default answers are fine until you get to the part where it asks if you want to configure now, you can try it but for me i got a compiler error.
about "only <linux/bitops.h> can be included directly"
so dont configure yet

follow the instructions here to fix the vmmon compile:
[http://eitchpress.eitchnet.ch/?p=13](http://eitchpress.eitchnet.ch/?p=13)
```
   1.  cd /usr/lib/vmware/modules/source
   2. cp vmmon.tar vmmon.tar.orig
   3. sudo tar xvf vmmon.tar
   4. cd vmmon-only/include/
   5. sudo vi vcpuset.h
   6. change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
   7. rm vmmon.tar
   8. sudo tar cvf vmmon.tar vmmon-only/
   9. sudo rm -rf vmmon-only/
  10. sudo vmware-config.pl

```

the rest of the install should run fine

---

### Post by jcbray on 2008-05-13
As an alternative to editing those files, after running the Workstation install you can run the 'any-any' script as listed in the VMWare sticky. Although that guide refers to VMWare Server, the any-any patch can be applied to make Workstation work aswell.

---

### Post by dandrews on 2008-05-14
Thank you so much for this how to, I was having a load of trouble finding how to fixing the configuration. Workstation works wonderfully now.

---

### Post by carlosavena on 2008-05-22
> **Intangir said:**
> get VMware-workstation-6.0.3-80004.i386.tar.gz
from [http://www.vmware.com/download/ws](http://www.vmware.com/download/ws) (you will have to make an account)
extract it

get the build-essential package

```
sudo apt-get install build-essential
```

goto the extracted vmware directory and run the install script

the default answers are fine until you get to the part where it asks if you want to configure now, you can try it but for me i got a compiler error.
about "only <linux/bitops.h> can be included directly"
so dont configure yet

follow the instructions here to fix the vmmon compile:
[http://eitchpress.eitchnet.ch/?p=13](http://eitchpress.eitchnet.ch/?p=13)
```
   1.  cd /usr/lib/vmware/modules/source
   2. cp vmmon.tar vmmon.tar.orig
   3. sudo tar xvf vmmon.tar
   4. cd vmmon-only/include/
   5. sudo vi vcpuset.h
   6. change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
   7. rm vmmon.tar
   8. sudo tar cvf vmmon.tar vmmon-only/
   9. sudo rm -rf vmmon-only/
  10. sudo vmware-config.pl

```

the rest of the install should run fine

Thanks a lot. It worked great and now I hope I will be able to have wireless on my virtual pc's, which it didn't work when I installed the any-to-any patch. ):P

- Carlos

---

### Post by carlosavena on 2008-05-22
Again I have to say "THANK YOU"=D> =D>. That workaround allows me to configure the wireless adapter into VMware, something that after installing the any-to-any patch I was unable to do.

- Carlos

---

### Post by Skeet on 2008-05-22
Well written. I was gonna write one up tonight, looks like you beat me to it!

:lolflag:

---

### Post by Sollos on 2008-06-02
Uhm! After doing this, I can finish the installation of VMware, but it can't run. The only thing I get is this message: 
> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl
no matter how many time I invoked the vmware-config. Is there anyone face the same problem with me?
Plz help! Thanks!

---

### Post by bmwman on 2008-06-03
They have VMware workstation 6.0.4 already. You can probably use the same serial jey that you have. I just installed without any patches or any tweaks. Give it a try.

---

### Post by buildup on 2008-06-06
Hi,
    Have VM WS b80004 on Kubuntu 8.04 with not (correctly) configured message.  Tried 6.0.04 b93058 with same results. :confused: Compiles nicely, configures nicely, launch workstation and the 'not (correctly) configured' msg comes forth. :confused:   Hacking ain't my thing.  Any thoughts.  I am running on AMD XP2000+ (32bit).   Thanks in advance for any additional help.  :)

---

### Post by me0262 on 2008-06-06
I had this problem on Gentoo as well (about 2 years ago).
There's a file somewhere (I think it's in /etc) called something like "vmware_not_configured". From what I remember VMware checks for this file and if it's found, thinks it's not configured. ](*,) It really should be a switch inside the config file itself.

---

### Post by bmwman on 2008-06-09
> **buildup said:**
> Hi,
    Have VM WS b80004 on Kubuntu 8.04 with not (correctly) configured message.  Tried 6.0.04 b93058 with same results. :confused: Compiles nicely, configures nicely, launch workstation and the 'not (correctly) configured' msg comes forth. :confused:   Hacking ain't my thing.  Any thoughts.  I am running on AMD XP2000+ (32bit).   Thanks in advance for any additional help.  :)

I'm having the same problem. I tried Workstation 6.0.3 and 6.0.4 with the same issue. It installs and complies fine but when try to launch, it's saying that is not configured. So weird. I have 6.0.3 running just fine with 2.6.24.18 kernel on another machine, but I've had it installed for a while now.

---

### Post by Fleuris on 2008-06-11
I'm having a small problem; when I do ```
cp vmmon.tar vmmon.tar.orig
``` I get this error message: > ******@ubuntu-******:/usr/lib/vmware/modules/source$ cp vmmon.tar vmmon.tar.orig
cp: cannot create regular file `vmmon.tar.orig': Permission denied
*******@ubuntu-*******:/usr/lib/vmware/modules/source$  

I have this with all cp commands, so also with other programs.


Can anyone help me out???:(:confused:

P.S. Please excuse my english, I'm not só good at it (yet)

---

### Post by bmwman on 2008-06-11
> **Fleuris said:**
> I'm having a small problem; when I do ```
cp vmmon.tar vmmon.tar.orig
``` I get this error message: 

I have this with all cp commands, so also with other programs.


Can anyone help me out???:(:confused:

P.S. Please excuse my english, I'm not só good at it (yet)

You need to execute as root:

```
sudo cp vmmon.tar vmmon.tar.orig
``` 

BTW after removing VMware and rebooting couple of times I was able to install and it works fine. If you're using VMware workstation 6.0.4 you don't even need to do any patches or changes, it installs right away the way it is.

Now I'm having anothe problem tho: None of my already configured machines work anymore. I get all kinds of errors when I try to open.

---

### Post by Fleuris on 2008-06-12
> **bmwman said:**
> You need to execute as root:

```
sudo cp vmmon.tar vmmon.tar.orig
``` 

BTW after removing VMware and rebooting couple of times I was able to install and it works fine. If you're using VMware workstation 6.0.4 you don't even need to do any patches or changes, it installs right away the way it is.

Now I'm having anothe problem tho: None of my already configured machines work anymore. I get all kinds of errors when I try to open.
I'm sorry, but since I haven't been able to install VMware, I can't help you with that. Can you give me some more info on the problem, maybe I can help after all.

P.S. how do you uninstall VMware?

---

### Post by ttxn on 2008-06-24
do I have to uninstall 6.03 before I install 6.04?

thankx.

---

### Post by Eisenwinter on 2008-06-27
Thank you for this information, I got me the newest VMWare installed.
I never once encountered a compile error though, so I didn't have to start switching lines in the source code, etc - it worked perfectly with default answers on almost all questions.

---

### Post by buivietkhoa1919upg on 2008-06-29
> **Sollos said:**
> Uhm! After doing this, I can finish the installation of VMware, but it can't run. The only thing I get is this message: 

no matter how many time I invoked the vmware-config. Is there anyone face the same problem with me?
Plz help! Thanks!

i had the same pb, after installing vmware server. however, i reinstalled it, taking care of every move and it worked well. you can follow the instruction in this thread, or try this link _http://howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5

---

### Post by panos_tsapralis on 2008-07-02
> **carlosavena said:**
> Again I have to say "THANK YOU"=D> =D>. That workaround allows me to configure the wireless adapter into VMware, something that after installing the any-to-any patch I was unable to do.

- Carlos

I totally agree with everybody else in this thread: this is a very useful post. However, Carlos, what exactly do you mean "configure the wireless adapter into VMWARE"? Did you attach a wireless USB stick to the host and then connected that stick to the guest OS? Did you bridge "vmnet0" to the wireless connection of your host (is this connection named "ath0" in your UBUNTU setup)?

I have been trying to make my virtual guests to connect to the LAN and to the Internet through a bridged wireless connection without any success so far. My setup is: "vmnet0" bridged to "ath0", "vmnet1" -> "host-only" & "vmnet8" -> "NAT" (using Workstation 6.0.4 on an APPLE MacBook Pro). When the "vmware-config.pl" script finishes, it reports that bringing up the VMWARE service "Bridged networking on /dev/vmnet0" failed, it leaves a file named "/etc/vmware/not_configured" (which I have to delete manually in order to make VMWARE Workstation come up correctly). When I start a Microsoft Windows Server 2003 guest in bridged networking mode, I get the message that the LAN connection has limited or no connectivity (and, indeed, I cannot connect to the Internet or to other systems, physical or virtual - trying to repair the LAN connection doesn't do any good).

I need some help on this (my fallback solutions - using a wireless USB stick privately in the guest OS or migrating to VIRTUALBOX - are not so good).

TIA,
Panos.

---

### Post by jerry_gzy on 2008-08-11
Hi, I am thinking of getting VMware,
what is the performance of the guest OS in VMware? 
and how is the virtual graphic card capability in guest OS?
thanks

---

### Post by RealG187 on 2008-08-14
I cannot run vmware-install.pl

> mpg@MIKED5:~$ /home/mpg/Desktop/vmware-distrib/vmware-install.pl 
mpg@MIKED5:~$ sudo /home/mpg/Desktop/vmware-distrib/vmware-install.pl 
mpg@MIKED5:~$ 


It does nothing and I have the option under permissions for running the file as an application!

First I installed Vmware server but it didnt have the shared folder feature which made it useless, then I tried to install workstation from a deb and it F***ed up server, and I think that's why this wont run, how do I remove all of VM Ware from my computer? I ran

```
sudo rm -Rf /etc/vmware/
```

but it still doesnt work.

---

### Post by TpyKv on 2008-08-27
Hi,

Has anyone figured this out yet? and got it working? 

I am stuck and it looks like I have to go back to a dual boot with Vista. Sad Times. Please if anyone knows how to sort this problem of having to run the config script and still getting nowhere, please let me know ASAP!!

---

### Post by bmwman on 2008-08-27
> **TpyKv said:**
> Hi,

Has anyone figured this out yet? and got it working? 

I am stuck and it looks like I have to go back to a dual boot with Vista. Sad Times. Please if anyone knows how to sort this problem of having to run the config script and still getting nowhere, please let me know ASAP!!

Vmware Workstation 6.0.4 works fine and no tweaking is necessary. You need to remove any previous installations including Vmware server if you have it on. Only one can run on your machine, either VMware Server or Workstation.

---

### Post by smartins on 2008-09-10
Hi, 

I am a newbie with Ubantu. Is there are free VMWare Workstation? I see that the one in this link is not free.

---

### Post by bmwman on 2008-09-11
> **smartins said:**
> Hi, 

I am a newbie with Ubantu. Is there are free VMWare Workstation? I see that the one in this link is not free.

You can download Vmware Workstation 6.5beta. I love it, especially the Unity feature in it. It's free since it's beta. Otherwise you need to pay for it. You can use VMware Server which is free but it's not that user friendly, especially for new-to-Ubuntu people :).

---

