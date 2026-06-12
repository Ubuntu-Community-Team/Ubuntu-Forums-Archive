---
title: "General server Questions"
date: 2013-06-25
forum: Server Platforms
---

### Post by Birkinator on 2013-06-25
Hello all,

I am experimenting with a VM of Ubuntusrvr 13.04 to get myself acquainted and familiar before i install it on a few servers that i recently received from the company i work for. I want to open this mainly as a thread for me to ask questions and get reliable answers. I am in no way a noob to computers or networking, however, i am a noob to the functionality and configuration of the non-graphical ubuntu interface(cmd line). I have a bunch of the basic commands down, but i have never actually configured, installed, or the like through the unix cmd(apt-get, ect). 

I am intending to use the Ubuntusrvr to run VM's of multiple different OS's(win8, ubuntu desktop, winsrvr 2008 R2, ect), and perhaps setup a DHCP server, domain controller, ect. The gist, this is for experimenting, getting familiar, and building my knowledge off unix/ubuntu.

Now that the baseline and intentions are out there, to the topics. 

Were should i start when attempting to learn the functionality of and become proficient in Ubuntusrvr?

How do i scroll in the non-gui ubuntu cmd? I know of the |more/less cmd, but that doesn't help me for scrolling back up. 

Thank you ahead of time to those who help me out, and sorry for those who visit this looking for higher level information. More questions to come, assuming the preexisting get answered :)

---

### Post by Cheesemill on 2013-06-25
> **Birkinator said:**
> I am experimenting with a VM of Ubuntusrvr 13.04 to get myself acquainted and familiar before i install it on a few servers that i recently received from the company i work for.
First of all unless you have a good reason for doing so I would recommend ***not*** using Ubuntu Server 13.04.
13.04 is a normal Ubuntu release which means it only gets 9 months of support. This means that you would need to upgrade your server OS in a few months time when 13.10 is released. For servers it is recommended to only use LTS (Long Term Support) releases as these have a much longer lifecycle. The most recent LTS release is 12.04 which is supported until 2017 and I would recommend using this instead of 13.04.

> I am intending to use the Ubuntusrvr to run VM's of multiple different OS's(win8, ubuntu desktop, winsrvr 2008 R2, ect), and perhaps setup a DHCP server, domain controller, ect. The gist, this is for experimenting, getting familiar, and building my knowledge off unix/ubuntu.
If all that your server(s) are going to be doing is hosting VM's then I wouldn't use Ubuntu as the host OS at all. Instead you may want to go for a proper VM hypervisor such as the free version of [VMware vSphere]("http://www.vmware.com/products/vsphere-hypervisor/overview.html") or [Proxmox]("http://www.proxmox.com/proxmox-ve") (a KVM based Linux hypervisor running on Debian). I still use Ubuntu Server 12.04 as the OS for my guests though.

> Were should i start when attempting to learn the functionality of and become proficient in Ubuntusrvr?
The best place to start is the official server documentation.
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)
For more information on shell scripting and basic commands check out the links on this page.
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

> How do i scroll in the non-gui ubuntu cmd? I know of the |more/less cmd, but that doesn't help me for scrolling back up. 
To scroll the display you can use SHIFT+PGUP and SHIFT+PGDOWN. To scroll through the history of the commands you have entered you can just use the up and down arrows.
Most server administrators don't use the terminal directly, instead ssh is used to connect from a workstation. This way you get all of the goodies that  come with a terminal emulator such as a scrollbar and being able to cut/paste commands.

---

### Post by Birkinator on 2013-06-25
That first tip probably saved me a hastle or 5, Thank you! I suppose that i will need an older version of VMWare Free as the servers that were passed down to me are a bit, how you would say, ancient :P 32bit only. I have been recommended to ESXI 3.x(i think). Anyways back to the Ubuntu topics. 

I have the VM created and configured, now i need to figure out how to remote in to the VM from the local machine(keeping in mind that the VM is installed to the same machine). What method do you recommend for remote support? SSH as stated previously?

---

### Post by Cheesemill on 2013-06-25
Yep, SSH.

To install it on the server run the following command...
```
sudo apt-get install openssh-server
```

Then from your workstation you can connect using the ssh command...
```
ssh user@host
```
if you are running Linux or with PuTTY from a Windows machine.

Make sure that you have your VM set up to use bridged networking as this will make it appear to be a separate physical machine on the same network.

As to being 32-bit I think that rules out using vSphere or Proxmox as these are only available for 64-bit machines. If you do want your servers to run as VM hosts then you are probably going to have to use VirtualBox in headless mode.

---

### Post by Birkinator on 2013-06-25
yea, i was planning to run VBox if i couldn't get my hands on an older version of Vsphere. Its all about the experience though. 

I'm using Putty at the moment. Pretty easy to setup and configure OpenSSH on ubuntusrvr.

---

### Post by gordintoronto on 2013-06-26
A different take: I don't see any reason to run Ubuntu Server. Desktop can do everything Server can do. If you are a masochist and insist on doing everything through the terminal, you can do that in Desktop -- but you don't have to.

---

### Post by CharlesA on 2013-06-26
> **gordintoronto said:**
> A different take: I don't see any reason to run Ubuntu Server. Desktop can do everything Server can do. If you are a masochist and insist on doing everything through the terminal, you can do that in Desktop -- but you don't have to.

Cuz you can? :p

+1 to Proxmox, that is what I have been using as my VM software.

32-bit definitely rules out Proxmox too. Vbox would work well though.

---

