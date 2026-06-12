---
title: "How to VMWare Server 1.0.7 with Ubuntu 8.10"
date: 2008-11-01
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-11-01
[CENTER][FONT=Times New Roman][SIZE=6]Install VMWare 1.0.7 in Ubuntu 8.10[/SIZE][/FONT][/CENTER]
[FONT=Times New Roman]
[CENTER][[IMG]http://tbn0.google.com/images?q=tbn:SalBlZhJj2MeFM:http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg[/IMG]]("http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg")
<click image for larger view>[/CENTER]

[SIZE=4]Introduction[/SIZE]

Well, just to clarify, installation of VMWare is dependent on the version of your Linux kernel, not so much the version of Ubuntu (although obviously there is a relationship between the two).

I would also like to thank all the people who offered solutions to problems, in particular [Kang]("https://bugs.launchpad.net/%7Edump-tzib") and [nthrbldyblg]("http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html").

**[SIZE=2][COLOR=navy]This how-to works for server 1.0.7 / workstation 5.5.x and both 32 and 64 bit hosts.[/COLOR][/SIZE]**

Lets do it :)

[LIST=1]
[*]Prep ~ Install the needed tools.
```
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
```***64 bit users only***
In addition install ia32-libs (ia32-libs is in universe so you may need to enable the repository) :
```
sudo apt-get install ia32-libs
```_Note_: Some users reported the need to install additional dependencies :
```
sudo apt-get install libxtst6 libxt6 libxrender1
```[COLOR=blue]~ Thanks SirMADOG and whitegourd[/COLOR]
[*]Download vmware server (be sure to obtain a serial number) Place in an installation directory ( I use ~/src/VMWare).

```
mkdir -p ~/src/VMWare #Download VMWare files here
```
[LIST]
[*]VMWare server : [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
[*]VMWare serial number : [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
[/LIST]
 
[*]Extract and run the VMWare Server installer.
```
cd ~/src/VMWare
tar xzf VMware-server-1.0.7-108231.tar.gz

cd ~/src/VMWare/vmware-server-distrib 
sudo ./vmware-install.pl
```Stop the installer (answer "no") when it asks if you wish to run "vmware-config.pl". If you continue with the installation at this point it will do not harm, it will just terminate with an error (see next step).

[COLOR=blue]~ Thanks mandavi and GuruX[/COLOR]
[*]Install and run the patch from Kang. See [This (Launchpad) bug report]("https://bugs.launchpad.net/ubuntu/+bug/263837").

Download the patch from here : [vmware-update-2.6.27-5.5.7-2.tar.gz]("http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627")

[COLOR=blue]Thank you [/COLOR][Kang]("https://bugs.launchpad.net/%7Edump-tzib").

Again, save it in ~/src/VMWare

Extract the patch ("update")
```
tar xzf vmware-update-2.6.27-5.5.7-2.tar.gz
```
[*]Install the patch (which will install VMWare server as well).

```
cd vmware-update
sudo ./run-me
```This will patch vmware and start the installer. Unless you know what you are doing, select the defaults and ***Enter your serial # during the installation.***.

That is it.
[/LIST]

Well, almost ...

There is an issue with the keyboard as well. See [this blog]("http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html") for details (and the solution).

[COLOR=blue]Thanks nthrbldyblg[/COLOR].

Basically, using any editor (gedit), put this into ~/.vmware/config :

_Note_: For some reason it is confusing people (my mistake :rolleyes:), the file "~/.vmware/config" does not exist by default, you need to create it.

Using any editor **make a file** ~/.vmware/config
[INDENT]The directory ~/.vmware *should* exist, but the "config" file does not.[/INDENT]Add the following text (from the VMWare forums): 

```
xkeymap.nokeycodeMap = TRUE 
```

[COLOR="DarkRed"]**WARNING**: The [FONT="Courier New"]'xkeymap.nokeycodeMap = true'[/FONT] configuration breaks the Unity feature on VMWare Workstation! Use the alternate solution below.[/COLOR]

[INDENT]Old solution (I left this in the event the "new" configuration does not work, **you do not need to do this if the above solution works**).[INDENT]```
xkeymap.keycode.108 = 0x138 # Alt_R
 xkeymap.keycode.106 = 0x135 # KP_Divide
 xkeymap.keycode.104 = 0x11c # KP_Enter
 xkeymap.keycode.111 = 0x148 # Up
 xkeymap.keycode.116 = 0x150 # Down
 xkeymap.keycode.113 = 0x14b # Left
 xkeymap.keycode.114 = 0x14d # Right
 xkeymap.keycode.105 = 0x11d # Control_R
 xkeymap.keycode.118 = 0x152 # Insert
 xkeymap.keycode.119 = 0x153 # Delete
 xkeymap.keycode.110 = 0x147 # Home
 xkeymap.keycode.115 = 0x14f # End
 xkeymap.keycode.112 = 0x149 # Prior
 xkeymap.keycode.117 = 0x151 # Next
 xkeymap.keycode.78 = 0x46 # Scroll_Lock
 xkeymap.keycode.127 = 0x100 # Pause
 xkeymap.keycode.133 = 0x15b # Meta_L
 xkeymap.keycode.134 = 0x15c # Meta_R
 xkeymap.keycode.135 = 0x15d # Menu
```[Thanks nthrbldyblg]("http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html")[/INDENT][/INDENT][/FONT]

---

### Post by fjgaude on 2008-11-01
Thanks for the quick fix.

Just a note: .vmware folder doesn't have a file named **config** in it so we have to create one for the keystroke data. Works great, but I did have to add this line to the /etc/fstab file to get VMware to show my USBs:

```
usbfs   /proc/bus/usb   usbfs   auto   0   0
```

I can't say if it is necessary in all cases, but it has been for mine.

---

### Post by bodhi.zazen on 2008-11-01
> **fjgaude said:**
> Thanks for the quick fix.

Just a note: .vmware folder doesn't have a file named **config** in it so we have to create one for the keystroke data. Works great, but I did have to add this line to the /etc/fstab file to get VMware to show my USBs:

```
usbfs   /proc/bus/usb   usbfs   auto   0   0
```I can't say if it is necessary in all cases, but it has been for mine.

As usual, thank you once again figaude.

---

### Post by mandavi on 2008-11-01
If you get an error message saying:

```
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.
```

start to install the unpachted VMWare untill you get an error message and run the update after that. Only than it worked for me.

---

### Post by GuruX on 2008-11-02
> **mandavi said:**
> If you get an error message saying:

```
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.
```

start to install the unpachted VMWare untill you get an error message and run the update after that. Only than it worked for me.

I had kind of the same problem. The trick is to first run the vmware-install.pl. But do NOT let it invoke the vmware-config.pl for you. Choose no and instead run the runme.pl from the vmware-update patch.

---

### Post by bodhi.zazen on 2008-11-02
> **mandavi said:**
> If you get an error message saying:

```
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.
```

start to install the unpachted VMWare untill you get an error message and run the update after that. Only than it worked for me.

> **GuruX said:**
> I had kind of the same problem. The trick is to first run the vmware-install.pl. But do NOT let it invoke the vmware-config.pl for you. Choose no and instead run the runme.pl from the vmware-update patch.

Thank you both as well, I updated the how-to ;)

---

### Post by SirMADOG on 2008-11-03
Yeah I ran this and it never accepts any of the serials I have from VMware. 

I love this error message:

The process exited with an error:
/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libXtst.so.6: cannot open shared object file: No such file or directory End of error message. 


After some Googledrudging I got this guide:
[http://www.rasyid.net/2008/07/09/usrlibvmwarebinvmware-vmx-error-while-loading-shared-libraries/](http://www.rasyid.net/2008/07/09/usrlibvmwarebinvmware-vmx-error-while-loading-shared-libraries/)

so I ran: **apt-get install libxtst6**

Still won't let me put in a valid serial

---

### Post by whitegourd on 2008-11-05
I had to install additional items as well as the patch to get vmware server to work on 8.10

apt-get install build-essential linux-headers-`uname -r` xinetd libxtst6 libxt6 libxrender1

---

### Post by carpe diem on 2008-11-06
when trying to install the patch i get this

theninja@ninja:~$ tar xzf vmware-update-2.6.27-5.5.7-2.tar.gz
tar: vmware-update-2.6.27-5.5.7-2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
theninja@ninja:~$

---

### Post by bodhi.zazen on 2008-11-06
> **SirMADOG said:**
> Yeah I ran this and it never accepts any of the serials I have from VMware. 

I love this error message:

The process exited with an error:
/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libXtst.so.6: cannot open shared object file: No such file or directory End of error message. 


After some Googledrudging I got this guide:
[http://www.rasyid.net/2008/07/09/usrlibvmwarebinvmware-vmx-error-while-loading-shared-libraries/](http://www.rasyid.net/2008/07/09/usrlibvmwarebinvmware-vmx-error-while-loading-shared-libraries/)

so I ran: **apt-get install libxtst6**

Still won't let me put in a valid serial
> **whitegourd said:**
> I had to install additional items as well as the patch to get vmware server to work on 8.10

apt-get install build-essential linux-headers-`uname -r` xinetd libxtst6 libxt6 libxrender1

Thanks you two, I added that information in.

> **carpe diem said:**
> when trying to install the patch i get this

theninja@ninja:~$ tar xzf vmware-update-2.6.27-5.5.7-2.tar.gz
tar: vmware-update-2.6.27-5.5.7-2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
theninja@ninja:~$

My guess is a corrupt down load, try downloading the patch again ;)

---

### Post by RandyRandola on 2008-11-07
Hello:

I really appreciate the amount of work everyone does to get this stuff running. 

Mine was running fine till I played and it broke so bad I had to start over. So here I am, all fresh and sparkly and VMware does not install. Even though it had run for me for the past 6 months. *sigh*

A couple of notes: 
Step 5: Install the patch (which will install VMWare server as well).
cd vmware-update
sudo ./run-me
Should be 
cd vmware-update-2.6.27-5.5.7-2
sudo ./runme.pl

Neither here nor there, but it makes it easier. 

But this is where I now am ...
Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:29: error: linux/semaphore.h: No such file or directory
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:333:
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h: In function ‘LinuxDriverLockedNoPage’:
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h:283: warning: return makes integer from pointer without a cast
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h:287: warning: return makes integer from pointer without a cast
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h:292: warning: return makes integer from pointer without a cast
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h:299: warning: return makes integer from pointer without a cast
/tmp/vmware-config0/vmmon-only/linux/driver_compat.h:303: warning: return makes integer from pointer without a cast
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

What the heck am I doing wrong?

Thanking everyone in advance to get this going. 

Randy

---

### Post by le_vainqueur on 2008-11-08
> Basically, using any editor (gedit), put this into ~/.vmware/config :

Neither this file nor folder existed, so I created both of them and pasted the given text into the new config file.  There is still no response for my keyboard in vmware, however.

---

### Post by bodhi.zazen on 2008-11-08
> **le_vainqueur said:**
> Neither this file nor folder existed, so I created both of them and pasted the given text into the new config file.  There is still no response for my keyboard in vmware, however.

This seems to be confusing people, sorry about that. I added a comment on my first post.

If the directory ~/.vmware did not exist I suspect a typo.

The file ~/.vmware/config must be created by you.

If it does not work, what type of keyboard are you using ? You may need to map your keys manually :(

---

### Post by carpe diem on 2008-11-09
same error :(

update-i tried unpacking it outside the terminal and running the runme file...and got this...

theninja@ninja:~$ sudo '/home/theninja/src/VMWare/vmware-update/runme.pl' 
sudo: unable to resolve host ninja
Updating /usr/bin/vmware-config.pl ... now patched
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware/modules/source/vmmon.tar.

Execution aborted.

---

### Post by le_vainqueur on 2008-11-10
> **bodhi.zazen said:**
> 
If the directory ~/.vmware did not exist I suspect a typo.

I did have to create this directory manually.  Was it supposed to have been created during the installation?

> **bodhi.zazen said:**
> 
If it does not work, what type of keyboard are you using ? You may need to map your keys manually :(

It's a Gateway RT3602.  I've never had problems with compatibility in the past, so hopefully it doesn't come to that.

---

### Post by phalbert on 2008-11-20
Does anyone know if this procedure works  with VMware Server 1.08?

---

### Post by le_vainqueur on 2008-11-21
> **le_vainqueur said:**
> I did have to create this directory manually.  Was it supposed to have been created during the installation?



It's a Gateway RT3602.  I've never had problems with compatibility in the past, so hopefully it doesn't come to that.

***bump***

---

### Post by bodhi.zazen on 2008-11-21
> **le_vainqueur said:**
> ***bump***

What is the question ? For me the directory was automatically created.

Keep in mind ~ is short hand for /home/username 

(just in case).

---

### Post by bodhi.zazen on 2008-11-21
> **phalbert said:**
> Does anyone know if this procedure works  with VMware Server 1.08?

Yes, it does. I updated this post.

---

### Post by CloudFX on 2008-11-22
Hi,

Thanks a lot for this.  Just pointing out that in the section for dependencies which may need to be installed, you put in 'sudo apt-get libxtst6 libxt6 libxrender1', with the 'install' part.

---

### Post by bodhi.zazen on 2008-11-22
> **CloudFX said:**
> Hi,

Thanks a lot for this.  Just pointing out that in the section for dependencies which may need to be installed, you put in 'sudo apt-get libxtst6 libxt6 libxrender1', with the 'install' part.

:lolflag: Thanks.

---

### Post by le_vainqueur on 2008-11-23
> **bodhi.zazen said:**
> What is the question ? For me the directory was automatically created.

Keep in mind ~ is short hand for /home/username 

(just in case).

Sorry for the ambiguity.  My problem is with the keyboard.  It still does not work in vmware.  I tried both of the options you listed for the ~/.vmware/config file.  In the guide you say that the ~/.vmware directory should exist, but it did not for me.  I had to create both the folder and the config file.  Could this be part of the problem?

---

### Post by bodhi.zazen on 2008-11-23
> **le_vainqueur said:**
> Sorry for the ambiguity.  My problem is with the keyboard.  It still does not work in vmware.  I tried both of the options you listed for the ~/.vmware/config file.  In the guide you say that the ~/.vmware directory should exist, but it did not for me.  I had to create both the folder and the config file.  Could this be part of the problem?

Ah, I am not sure, but I do not see how that would be a problem. Are you running vmware or logging in as root ?

---

### Post by le_vainqueur on 2008-11-23
> **bodhi.zazen said:**
> Ah, I am not sure, but I do not see how that would be a problem. Are you running vmware or logging in as root ?

Ahhhh...now I see what I was doing wrong.  Thanks for enlightening me.  I run vmware as root because my vm uses physical partitions which requires root access to the drives. So, now I have added the config file to the root .vmware folder instead.  Everything is working beautifully!

Since we're on this subject...is it okay for me to be running vmware as root?  I have always done this, but I don't remember checking to see if it was okay... 8-[

---

### Post by bodhi.zazen on 2008-11-23
It is "OK", but most prefer to run as a user if possible.

What I do is chown/chmod the device. Say you are booting /dev/sda1

```
sudo chown root.user /dev/sda1
sudo chmod 770 /dev/sda1
```

user = your user

This chown/chmod is not permanent and will be re-set after a re-boot.

You should be able to run vmware & boot the physical device as a user.

---

### Post by carpe diem on 2008-11-24
when trying to extract the update i get this...

theninja@ninja:~$ tar xzf vmware-update-2.6.27-5.5.7-2.tar.gz
tar: vmware-update-2.6.27-5.5.7-2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
theninja@ninja:~$ 

and if i extract it outside the terminal and and try to run it i get this...

theninja@ninja:~$ sudo '/home/theninja/Desktop/vmware-update-2.6.27-5.5.7-2/runme.pl' 
sudo: unable to resolve host ninja
Updating /usr/bin/vmware-config.pl ... already patched
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware/modules/source/vmmon.tar.

Execution aborted.

theninja@ninja:~$ 
:(

---

### Post by carpe diem on 2008-12-13
help please :confused:

---

### Post by xrvjorn on 2008-12-19
> **CloudFX said:**
> Hi,

Thanks a lot for this.  Just pointing out that in the section for dependencies which may need to be installed, you put in 'sudo apt-get libxtst6 libxt6 libxrender1', with the 'install' part.

Make that '**sudo apt-get install libxrender1 libxt6 libxtst6 libx11-6 libice-dev libsm-dev**', and it will work on a clean Ubuntu Server with nothing else installed.

---

### Post by jonta on 2009-04-18
here is a brief explanation when attempting to use vmware under 9.04 Release Candidate amd64

Starting with trying to follow the instructions here in the thread:

```
jonta@xeon:~/installation/vmware-server-distrib/vmware-update-2.6.27-5.5.7-2$ sudo ./runme.pl
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.

```

Well since you need to run the ./vmware-install.pl all the way to the "do you want to run wmware-config.pl before applying to patch i guess this is normal.
So i begin with running ./vmware-install.pl using the default on all options, no problems here

```
Before running VMware Server for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this
program to invoke the command for you now? [yes] no
```

Now i patch it with vmware-update-2.6.27-5.5.7-2
```
jonta@xeon:~/installation/vmware-server-distrib/vmware-update-2.6.27-5.5.7-2$ sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it
for your running kernel by invoking the following command:
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for
you now? [no] yes
```
Ok works a bit better.

```
None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

```
I have previosly apt-get the header file for my kernel:

```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-11-generic/build/include]
```

It compiles with alot of warnings as usual for example:
```
/tmp/vmware-config0/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
```
but in the end
```
The module loads perfectly in the running kernel.
```
then it builds the network drier, also with a i bit of errors but in the end:
```
The module loads perfectly in the running kernel.
```

```
The configuration of VMware Server 1.0.9 build-156507 for Linux for this
running kernel completed successfully.
```

Perfect, that worked without problems, now to the problems then.
I want to connect to my vmware server with vmware-console now from another machine, a windows XP machine as i always have:
Hmm "Login (username/password) incorrect
```
jonta@xeon:~$ cat /var/log/auth.log
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM unable to dlopen(/usr/lib/vmware/lib/libpam.so.0/security/pam_unix2.so)
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM [error: /usr/lib/vmware/lib/libpam.so.0/security/pam_unix2.so: cannot open shared object file: No such file or directory]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM adding faulty module: /usr/lib/vmware/lib/libpam.so.0/security/pam_unix2.so
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) illegal module type: @include
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM pam_parse: expecting return value; [...common-auth]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) no module name supplied
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM unable to dlopen(<*unknown module path*>)
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM adding faulty module: <*unknown module path*>
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) illegal module type: @include
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM pam_parse: expecting return value; [...common-account]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) no module name supplied
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) illegal module type: @include
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM pam_parse: expecting return value; [...common-password]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) no module name supplied
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) illegal module type: @include
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM pam_parse: expecting return value; [...common-session]
Apr 18 09:54:19 xeon vmware-authd[14194]: PAM (other) no module name supplied
Apr 18 09:54:19 xeon vmware-authd[14194]: pam_unix_auth(vmware-authd:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=jonta


```Ok, so i can't view my machines, but they are still there i i'll try the vmrun command
j```
onta@xeon:/fileserver/virtual-machines/Unsafe Windows Server$ sudo vmrun start Windows\ Server\ 2003\ Standard\ Edition.vmx
Error: Command failed: A file was not found
```
```
jonta@xeon:/fileserver/virtual-machines/Unsafe Windows Server$ sudo vmrun start "Windows Server 2003 Standard Edition.vmx"
Error: Command failed: A file was not found
```
Strange, let's look at the logs

```
Apr 18 09:56:07: app| New connection on socket server-vmdb from host localhost (ip address: local) , user: root
Apr 18 09:56:07: app| SP: New user session for user: root, pos: 0
Apr 18 09:56:07: app| The vm-list file has changed! Reloading the list of registered vms
Apr 18 09:56:07: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
```

Now after alot of googeling i found a similar problem with not being able to connect with vmware-console and suggesting adding/changing things in the /etc/pam.d/vmware-auth file
but nothing have worked.

Here is some info about my machine:
Description:    Ubuntu 9.04
Release:        9.04
Linux xeon 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64 GNU/Linux
Running on a Quad Core Xeon processor.
Also i have installed the ia32-libs

---

### Post by JockVSJock on 2009-06-24
This is a good thread, I was able to get my VMWare working ok with help from this thread. 

thanks

---

### Post by dcstar on 2009-11-11
Please be aware that the **xkeymap.noKeycodeMap** keymap fix can go in:

```
/etc/vmware/config
```

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439&sliceId=1&docTypeID=DT_KB_1_1&dialogID=47682481&stateId=0%200%2047686729](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1007439&sliceId=1&docTypeID=DT_KB_1_1&dialogID=47682481&stateId=0%200%2047686729)

This has fixed my keymapping problems in my clients (I use 9.04 64-bit VMware Server 1.0.10).

---

