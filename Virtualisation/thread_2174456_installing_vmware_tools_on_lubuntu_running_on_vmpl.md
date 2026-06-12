---
title: "installing vmware tools on lubuntu running on vmplayer: location of GCC?"
date: 2013-09-14
forum: Virtualisation
---

### Post by physman2 on 2013-09-14
okay so I am trying to isntall VMware tools from the command line with the tar installer using these instructions:
[http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html#wp1118025](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html#wp1118025)

Like the title says, I am installing vmware tools on lubuntu which I have running as a virtual machine using vmplayer.
After step 5, when responding the configuration questions on the screen, it said 

the installatinon of vmware tools 9.2.3 build-1031360 for linux completed sucessfully. you can devide to remove this software form your system at any time by invoking the following command:
"/usr/bin/vmware-uninstall-tools.pl".
before running vmware tools for the first time, you need to configure it by invoking the following command:
"usr/bin/vmware-config-tools.pl". Do you want this program to invoke the command for you now?
[yes]

I pressed enter and accepted the default [yes] value and now it says

---------
Before you can compile modules, you need to have the following installed...
make
gcc
kernel headers of the running kernel

Searching for GCC...
the path "" is not valid path to the gcc binary. 
Would you like to change it? [yes]

What is the location of the gcc program on your machine?
--------

I tried

locate gcc

and found that there is a folder called /usr/lib/gcc, so I tried to put that in as the location but it says that the path "/usr/lib/gcc" is not valid path to the gcc binary.
How do I find out where the gcc library is on my machine is?

---

### Post by physman2 on 2013-09-14
[COLOR=#000000][FONT=Arial]Found the answer. What I did was was first[/FONT][/COLOR]
sudo apt-get install aptitude
sudo aptitude install libglib2.[COLOR=#800000]0[/COLOR]-[COLOR=#800000]0[/COLOR]
sudo aptitude install gcc-[COLOR=#800000]4.7[/COLOR] make linux-headers-`uname -r` -y[COLOR=#000000][FONT=Arial]and tried it but it didn't work so I continued and did[/FONT][/COLOR]
sudo apt-get install build-essential
sudo apt-get install gcc-[COLOR=#800000]4.7[/COLOR] linux-headers-`uname -r`[COLOR=#000000][FONT=Arial]after doing these two steps and trying again, it worked[/FONT][/COLOR]

---

