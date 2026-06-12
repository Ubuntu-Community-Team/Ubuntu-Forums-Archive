---
title: "Gutsy upgrade lost VMWare"
date: 2007-11-09
forum: Virtualisation
---

### Post by Shinobi326 on 2007-11-09
When I upgraded to Gutsy a few weeks ago I appear to have lost my VMWare. It won't start and I have no idea if I still have it or not.  

It was a 10 gig allocation with Win XP installed on it.  I hate to wipe it out and start over.  Is there a way to resurrect it?

---

### Post by arkangel on 2007-11-09
Most probably the vmware kernel-module doesn't match your current kernel open a terminal > %sudo vmware-config.pl it will tell you something like, "i can't find a suitable module for your kernel , I need to build one ..." follow the instructions if you have all dependencies it shouldn't be a problem if not post your error output

---

### Post by grokwik on 2007-11-09
I had exactyl the same problem and fixed it usingthis very good article, you need to uninstall it first but considering that it doesn't kill your virtual machines, there's no problem.

[http://www.paperblog.fr/260653/vmware-server-1-0-4-sur-ubuntu-7-10-gutsy-gibbon/]("http://www.paperblog.fr/260653/vmware-server-1-0-4-sur-ubuntu-7-10-gutsy-gibbon/")

Another tiny detail.... It's a french post....:-\"
...but the command lines are the same and the text only explains the command lines, the only thing "important" that it tells is that you'd better store your virtual machines in your home directory (and knowing that you already have some, you already have their path).

---

### Post by Shinobi326 on 2007-11-10
Well I tried following along but it failed at the end

```
 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/system] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function ‘pte_t native_make_pte(long unsigned int)’:
include/asm/page.h:112: error: expected primary-expression before ‘)’ token
include/asm/page.h:112: error: expected ‘;’ before ‘{’ token
include/asm/page.h:112: error: expected primary-expression before ‘.’ token
include/asm/page.h:112: error: expected `;' before ‘}’ token
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

HELP!?

---

### Post by bcom on 2007-11-10
I followed a "How to Install VMware on Ubuntu 7.10" guide (not the one in French) and received the same error message.  

I haven't tried to decipher the posting at [http://www.paperblog.fr/260653/vmware-server-1-0-4-sur-ubuntu-7-10-gutsy-gibbon/](http://www.paperblog.fr/260653/vmware-server-1-0-4-sur-ubuntu-7-10-gutsy-gibbon/) but perhaps there is a fix there at the end of the posting.

Perhaps it is a problem with Ubuntu 7.10

---

### Post by Shinobi326 on 2007-11-10
I'm scared to do anything I don't fully understand, especially if it's in another language.

Anyone else?

---

### Post by grokwik on 2007-11-12
Here's the translation :


[SIZE=4]**VMware Server 1.0.4 on Ubuntu 7.10 Gutsy Gibbon**[/SIZE]
Here's the informations needed to install VMware Server 1.04 and it's admin UI (MUI) on Ubuntu 7.10 Gutsy Gibbon.
**[SIZE=3]VMware Server 1.04 Install[/SIZE]**
Create a directory that'll contain the virtual machines
```
$ mkdir ~/vmware
```
Install the necessary packages (7.10 32bits)
```

$ sudo apt-get install ssh openssh-server libx11-6 libx11-dev libxtst6 xinetd wget build-essential
$ sudo apt-get -y install linux-headers-`uname -r` && cd /usr/src && sudo rm -f linux && sudo ln -s linux-headers-`uname -r` linux
$ sudo apt-get install gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc libc6-dev-amd64 lib64gcc1

```
Download VMware Server 1.04 : VMware-server-1.0.4-56528.tar.gz, and then untar it.```

$ cd /tmp
$ wget http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz
$ tar -xvzf VMware-server-1.0.4-56528.tar.gz

```
  Start the install
```

$ cd vmware-server-distrib
$ sudo ./vmware-install.pl

```
  Answer to all the questions by the default answers except for the virtual machine storage directory :
  ```
In which directory do you want to keep your virtual machine files? [/var/lib/vmware/Virtual Machines] votre_home_directory/vmware
Please enter your 20-character serial number.
Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  entrer_ici_le_numero_de_serie

```
VMware server 1.04 install is now over, available in the menu. Let's now clean the temporary files we created :
```
$ rm -rf /tmp/*ware*
```

[SIZE=3]**VMware MUI 1.04 Install**[/SIZE]

Download VMware MUI 1.04 : VMware-mui-1.0.4-56528.tar.gz, and then untar it.
```

$ cd /tmp
$ wget http://download3.vmware.com/software/vmserver/VMware-mui-1.0.4-56528.tar.gz
$ tar -xvzf VMware-mui-1.0.4-56528.tar.gz

```
Launch the isntall script
```

$ cd vmware-mui-distrib
$ sudo ./vmware-install.pl

```
Answer to all the questions by the default answers. At the end of the script, the /etc/init.d/httpd.vmware command fails. This type of error occurs :
```

Generating SSL Server Certificate

Starting httpd.vmware:-ne                                                     failed

```
To fix this bug, you need to edit the /etc/init.d/httpd.vmware file. Replace the following block :
```

    start)
        vmware_exec "Starting httpd.vmware:" vmware_start_httpd 
        ;;
    stop)
        vmware_exec  "Shutting down http.vmware: " vmware_stop_httpd
        ;;

```
By this one
```

    start)
        if [ ! -d /var/run/vmware/httpd ]
        then
                echo "Directory: var/run/vmware/httpd Not found. Creating it."
                mkdir /var/run/vmware/httpd
                echo "Setting user and group ownership to: User: www-data, Group: nogroup"
                chown www-data:nogroup /var/run/vmware/httpd
                echo "Setting directory permissions to: RWX------ (700)"
                chmod 700 /var/run/vmware/httpd
        fi         
        echo "Starting httpd.vmware:"
        vmware_start_httpd
        ;;
    stop)
        echo "Shutting down http.vmware: "
        vmware_stop_httpd
        ;;

```
Also change all the SIGHUP par HUP by replacing this block :
```

  if [ "$VMWARE_DEBUG" = 'yes' ]; then
    (trap '' SIGHUP; "$func" "$@")
  else
    (trap '' SIGHUP; "$func" "$@") >/dev/null 2>&1
  fi

```
By this one
```

  if [ "$VMWARE_DEBUG" = 'yes' ]; then
    (trap '' HUP; "$func" "$@")
  else
    (trap '' HUP; "$func" "$@") >/dev/null 2>&1
  fi

```
The VMware MUI 1.04 install is done, the UI is available at this address : [https://localhost:8333](https://localhost:8333), now let's clean the temporary files to finish :
```

$ rm -rf /tmp/*ware*

```

---

### Post by tofagerl on 2007-11-13
Thanks, that helped me :D

---

