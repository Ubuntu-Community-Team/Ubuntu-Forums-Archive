---
title: "VMware workstation issues"
date: 2008-02-08
forum: Virtualisation
---

### Post by rd07f on 2008-02-08
hello,
first of all I would like to let it be known that I am completely new to Ubuntu and Linux in general.  I am experimenting with VMware workstation to learn to use Linux because everyone keeps telling me how wonderful it is.  I am using a Windows Vista home basic host and I am trying to run  an Ubuntu 7.10 gutsy Gibbons virtual machine.  my Dell vostro 1700 laptop is connected through a wireless router which is in turn connected to the main modem.

Problem number one: every time I power on my Ubuntu machine and go to download the package updates all the computers on my wireless network (except for the PC directly connected to the modem) lose connection.  I get the same results whether I am using bridged or NAT ethernet connections.  I end up having to reset my router every time.:confused::(:mad:

problem number two: this problem may be due to my lack of experience in Ubuntu, but I cannot seem to get VMware tools installed properly.it seems like my machine does not recognize.rpm and when I extract the.tar file, I cannot get the config tool or the installation to work properly.

I have been looking for other posts regarding these problems but none seem to quite match the description I have written above.

Thanks in advance for the help.

---

### Post by dpj23 on 2008-02-09
I think that when you connect your VM Ubuntu machine your maxing out the number of connections for your wireless router... My recommendation would be to try using bridged connection do that the host and quest are using the same wireless connection...

---

### Post by dpj23 on 2008-02-09
On the vm-tools issue if you want to try a virtual machine out you could go to VM's website and download a pre-built vm appliance...  There are prebuilt appliances for operating systems and you could download the Ubuntu OS with vmtools already installed...

---

### Post by dpj23 on 2008-02-09
here's the link:

[http://www.vmware.com/appliances/directory/1068](http://www.vmware.com/appliances/directory/1068)

---

