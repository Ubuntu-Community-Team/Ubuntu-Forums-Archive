---
title: "How to rise security using a kernel module with a custom firewall"
date: 2019-05-19
forum: Tutorials
---

### Post by coolervoid on 2019-05-19
HiddenWall is a Linux kernel module generator for custom rules with  netfilter. (block ports, Hidden mode, rootkit functions etc).  The motivation: on bad situation, attacker can put your iptables/ufw to fall... but if you have HiddenWall, the attacker will not find the hidden kernel module that block external access, because have a hook to netfilter on kernel land(think like a second layer for firewall).

 My beginning purpose at this project is protect my personal server, now is protect the machines of my friends. When i talk "friends", i say peoples that don't know how to write low level code. Using the HiddenWall you can generate your custom kernel module for your firewall configuration.

 The low level programmer can write new templates for modules etc...

Don't do bear here with bad eyes, this is not official Ubuntu/Linux.* module, this is a informal solution to make more protection, do you like to write code ? you can contribute, because is a open source module.

 **First step, understand before run**

 Verify if the kernel version is 3.x, 4.x or 5.x:
 ```
uname -r

``` Clone the repository

 ```
git clone https://github.com/CoolerVoid/HiddenWall

``` Enter the folder
 ```
cd HiddenWall/module_generator

``` Edit your firewall rules in directory  rules/server.yaml, the python scripts use that file to generate a new firewall module.
 ```
$ cat rules/server.yaml
module_name: SandWall
public_ports: 80,443,53
unhide_key: AbraKadabra
hide_key: Shazam
fake_device_name: usb14
liberate_in_2_out: True
whitelist: 
- machine: 
   ip: 192.168.100.181
   open_ports: 22,21
- machine:
   ip: 192.168.100.22
   open_ports: 22


``` If you want study the static code to generate, look the content at directory "templates".
 **Second step, generate your module**

 If you want generate a kernel module following your YAML file of rules, follow that command:
 ```
$ python3 WallGen.py --template template/hiddenwall.c -r rules/server.yaml

``` This generate a generic module with rules of server.yaml, if you want  to use another template you can use "wall.c", so template module  "hiddenwall" have option to run on hidden mode(is not visible to "#  lsmod" for example).
 **Third step, install your module**

 To test module:
 ```
# cd output; make clean; make
# insmod SandWall.ko

``` The rule of YAML to generate module is simple, drop all out to in  packets, accept ports 80,443 and 53. The machine 192*.181 can connect at  ports 22 and 21...
 if you use nmap at localhost/127.0.0.1 you can view the ports open... because rule liberate_in_2_out is true.
 Password to turn Firewall visible is "AbraKadabra".
 Password to turn Firewall invisible is "Shazam".
 You need to send password for your fake device "usb14".
 To exit module, you need turn visible at "lsmod" command ...
 ```
# echo "AbraKadabra" > /dev/usb14
# lsmod | grep SandWall
# rmmod SandWall

``` **Random notes**

 Tested on ubuntu in the kernels "3.x","4.x" and "5.x".

 **TODO(at the future)**

 Suport to IPV6. 
Macro to select the interface(to use multiple modes for each interface). Option to remove last logs when turn hide mode. 
Option to search and remove others toolkits... Code generator to BFP...

 **References**

 *Wikipedia Netfilter* [https://en.wikipedia.org/wiki/Netfilter](https://en.wikipedia.org/wiki/Netfilter)
 *Linux Device Drivers* [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)
 *M0nad's Diamorphine* [https://github.com/m0nad/Diamorphine/](https://github.com/m0nad/Diamorphine/)

---

