---
title: "VMware installation problem"
date: 2008-05-16
forum: Virtualisation
---

### Post by thanhluan001 on 2008-05-16
Hi, I try to install VMware today following the sticky thread but can't make it to work. At the end, I see the summary like this:
```


Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.5 build-80187 for Linux for this running
kernel completed successfully.

luan@luan-laptop:~/Desktop$ cd vmware-any-any-update116/

```

I run vmware by typing on the terminal "vmware" then it tells me I have not configure the vmware correctly and rerun the script again. 

Since it about the network, I try to recompile vmware without any network but I run into different problem. Now instead of asking me to rerun the installation script I have the following error . 

```
luan@luan-laptop:~/Desktop/vmware-any-any-update116$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

---

### Post by fjgaude on 2008-05-16
Did you run these commands after configuraton:

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

Let us know how you do.

---

### Post by wednesday allfather on 2008-05-17
fjgaude, that helped me.  It has been a chore, but vmware is running on 8.04.  Thanks for post.

---

### Post by fjgaude on 2008-05-18
So many issues, likely because so many people have such differenet setups... these forums usually get us the answer one way or the other.

Glad you have it working. Some things that worked for us in Gutsy are now no longer needed in Hardy... drum rolls as time moves along.

---

### Post by fjgaude on 2008-05-18
> **thanhluan001 said:**
> 

Since it about the network, I try to recompile vmware without any network but I run into different problem. Now instead of asking me to rerun the installation script I have the following error . 

```
luan@luan-laptop:~/Desktop/vmware-any-any-update116$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

See Sticky at the top of this Forum, message #84. That might be a solution to your problem.

frank

---

### Post by franky_88 on 2008-05-18
I also tried to install VMware today following the sticky thread on the subject. I had to create the folder src manually and the VMware also. So i did what the sticky said and save the VMware server.tar and the update patch in /src/VMware. I go in the terminal and it gives me this: 


francis@francis-laptop:~$ cd ~/src/VMWare
francis@francis-laptop:~/src/VMWare$ tar xzf VMware-server-1.0.5-80187.tar.gz
francis@francis-laptop:~/src/VMWare$ tar xzf vmware-any-any-update116.tar.gz
tar: vmware-any-any-update116.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
francis@francis-laptop:~/src/VMWare$ 
francis@francis-laptop:~/src/VMWare$ cd ~/src/VMWare/vmware-server-distrib
francis@francis-laptop:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl
sudo: unable to resolve host francis-laptop
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.


What should I do??


Thank you,

Frank

---

### Post by fjgaude on 2008-05-18
Okay, you must remove the previous install piece that resides in /etc. I recommend simply renaming using the mv command and after you are successful installing vmware you can come back and delete th folder:

```
sudo mv /etc/vmware /etc/vmwarebak
```

Try again and let us know how you do.

---

### Post by franky_88 on 2008-05-18
Okay so I paste the code you gave me and checked in etc folder and saw that it was renamed to VMwarebak. I followed the instructions on that website: [http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu](http://www.bauer-power.net/2007/07/installing-free-vmware-server-on-ubuntu). I save and extracted VMwareserver.taz and the patch in my home folder. I went in the terminal and it gave me this: francis@francis-laptop:~$ cd vmware-serv*
francis@francis-laptop:~/vmware-server-distrib$ sudo ./vmware-install.pl
sudo: unable to resolve host francis-laptop
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the next step?

Thank you,

Frank

---

### Post by franky_88 on 2008-05-18
okay so I played around with it a bit, and here is what it gave me: francis@francis-laptop:~$ sudo rm -R /etc/vmware
sudo: unable to resolve host francis-laptop
francis@francis-laptop:~$ sudo vmware-uninstall.pl
sudo: unable to resolve host francis-laptop
Uninstalling the tar installation of VMware Server.

Unable to find the tar installer database file (/etc/vmware/locations)

Execution aborted.

francis@francis-laptop:~$ sudo rm -R /etc/vmware
sudo: unable to resolve host francis-laptop
rm: cannot remove `/etc/vmware': No such file or directory
francis@francis-laptop:~$ cd ~/src/VMWare
francis@francis-laptop:~/src/VMWare$ tar xzf VMware-server-1.0.5-80187.tar.gz


francis@francis-laptop:~/src/VMWare$ tar xzf vmware-any-any-update116.tar.gz
tar: vmware-any-any-update116.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
francis@francis-laptop:~/src/VMWare$ 
francis@francis-laptop:~/src/VMWare$ 
francis@francis-laptop:~/src/VMWare$ cd vmware-serv*
francis@francis-laptop:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl
sudo: unable to resolve host francis-laptop
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] bin

The path "bin" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] usr

The path "usr" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] vmware

The path "vmware" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] bin

The path "bin" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] src

The path "src" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] local

The path "local" is a relative path. Please enter an absolute path.

In which directory do you want to install the binary files? 
[/usr/bin] /usr/bin/local

The path "/usr/bin/local" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] yes

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] /etc

What is the directory that contains the init scripts? 
[/etc/init.d] /etc/init.d

In which directory do you want to install the daemon files? 
[/usr/bin/sbin] /usr/bin/sbin

The path "/usr/bin/sbin" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] yes

In which directory do you want to install the library files? 
[/usr/bin/lib/vmware] /usr/bin/lib/vmware

The path "/usr/bin/lib/vmware" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] yes

In which directory do you want to install the manual files? 
[/usr/bin/man] /usr/bin/man

The path "/usr/bin/man" exists, but is not a directory.

In which directory do you want to install the manual files? 
[/usr/bin/man] /usr/bin/vmware

The path "/usr/bin/vmware" exists, but is not a directory.

In which directory do you want to install the manual files? 
[/usr/bin/man] /usr/bin/VMware

In which directory do you want to install the documentation files? 
[/usr/bin/doc/vmware] /usr/bin/doc/vmware

The path "/usr/bin/doc/vmware" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] yes

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

francis@francis-laptop:~/src/VMWare/vmware-server-distrib$ 


What did I do wrong??


Thank you,

Frank

P.N: I just uninstalled it just to make sure that I didn`t do anything wrong. here is a copy of the terminal: francis@francis-laptop:~$ sudo vmware-uninstall.pl
sudo: unable to resolve host francis-laptop
Uninstalling the tar installation of VMware Server.

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
inetd: no process killed
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.5 build-80187 for Linux completed 
successfully. Thank you for having tried this software.

---

### Post by fjgaude on 2008-05-18
You know, Linux may not like the idea of the "-" in your home folder name. Just a thought.

---

