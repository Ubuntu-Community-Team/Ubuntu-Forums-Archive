---
title: "Lubuntu 13.10 and VMware Tools"
date: 2014-02-19
forum: Virtualisation
---

### Post by balubeto on 2014-02-19
Hi
  
 I tried to install the VMware Tools on the  Lubuntu 13.10 32 bit VM created with Workstation 10.x for  Windows.

I have noticed that, starting from the  file VMwareTools-xxx-yyyy.tar.gz, to install and configure the VMware  Tools without errors,  the build-essential package must be installed since it  also installs the gcc  compiler.

Now,  leaving all the default answers  during the process of configuration of these tools, when I  reboot my virtual machine, its screen will  not automatically enlarges even after having logged. How  come?

Also, I  noticed that if, after the Login, I run the **sudo su -c  /usr/bin/vmware-user** command, the screen  enlarges, but when I reboot the  VM, the screen will not automatically enlarges. How come?
  
 Thanks
  
 Bye

---

### Post by balubeto on 2014-02-20
I followed these instructions:
  
 > 
 sudo apt-get install build-essential
 cd /tmp
 tar -zxpf "/media/<Username>/VMware Tools/VMwareTools-<product version number>-<product release>.tar.gz"
 cd vmware-tools-distrib
 sudo su -c ./vmware-install.pl
 sudo su -c /usr/bin/vmware-user
 cd ..
 rm -fr vmware-tools-distrib
 
So, how do I automatically start the VMware Tools service when the Lubuntu is started?
  
 Thanks
  
 Bye

---

### Post by balubeto on 2014-02-20
I have found that in the  /etc/xdg/autostart directory there is the VMware User  Agent executable. Why it does not automatically start?
  
 Thanks
  
 Bye

---

### Post by balubeto on 2014-02-21
So, in the /etc/xdg/autostart, there is an icon called VMware User Agent in which content is:
> 
[Desktop Entry]
Type=Application
Encoding=UTF-8
Exec=/usr/bin/vmware-user
Name=VMware User Agent
# KDE bug 190522: KDE does not autostart items with NoDisplay=tru...
# NoDisplay=true
X-KDE-autostart-phase=1

Now, how do I make sure that this file is run during the system startup so that it applies to all users?
Thanks
Bye

---

### Post by balubeto on 2014-02-22
To make sure that VMware User Agent is run after the login of an user, go to Menu ---> Preferences ---> Default applications for LXsession ---> Autostart and, in the Settings section, select "no" as answer to the question "Disable autostarted applications?". 

The trouble is that this procedure is necessary to do it for each user since the value of the "Disable autostarted applications?" parameter is not global. Is there a way to make sure that this parameter is global? 

I also noticed that, during the Login screen, the VMware User Agent is not active. Is there a way to turn it on even at this stage?

Thanks

Bye

---

### Post by balubeto on 2014-02-23
From what I understand, the /etc/xdg/lxsessionsLubuntu/autostart directory contains the list of all programs that are launched for all users. Right? If so, I wrote the /usr/bin/vmware-user command in this file. After that, I restarted the computer but I have seen that this command is not executed. How come? 

However, if I run this command from a terminal window, it is executed.

Thanks

Bye

---

