---
title: "problem in installing vmware server"
date: 2008-09-08
forum: Virtualisation
---

### Post by sp.mahapatra on 2008-09-08
Hi,

i am new to Ubuntu.
i am having problem while installing Vmware server in my Ubuntu 6.06 server version.

this is the complete detail about my kernel of the Ubuntu server 
Distributor ID: Ubuntu

Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper
And the kernel is “Linux ubuntu 2.6.22-8-server”
 #1 SMP Thu Jul 12 16:28:57 GMT 2007 i686 GNU/Linux

so as per my knowledge i have to 1st install the c-header with the command 
# apt-get install linux-headers-`uname -r` build-essential

after this command i am getting this output
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.22-8-server
even after this i tried to install the vmware server ,

But i get again this error 


Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.0.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.0.3" anyway?

so what can i do here ,How can i install the vmware server in my Ubuntu server .


please help me.plssssssssssssssssss

---

