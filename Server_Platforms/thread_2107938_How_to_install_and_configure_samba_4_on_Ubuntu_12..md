---
title: "How to install and configure samba 4 on Ubuntu 12.04 ?"
date: 2013-01-23
forum: Server Platforms
---

### Post by honey_bee on 2013-01-23
hi,
    Can any one tell me that is it possible to install and configure  samba 4 in my ubuntu 12.04 box  so I may replace windows server 2008 and use samba as a AD ?
 
thanks
honey.

---

### Post by volkswagner on 2013-01-23
I used the [SAMBA4 wik]("http://wiki.samba.org/index.php/Samba4/HOWTO")i to install via the recommended GIT method on Debian 6.  This should give you a complete set of instructions for getting SAMBA 4 up and running.

---

### Post by honey_bee on 2013-01-23
thanks for the reply. Well in Ubuntu world has some one configure samba 4 according to the wiki?
 
 
thanks

---

### Post by lingpanda on 2013-01-23
> **honey_bee said:**
> hi,

    Can any one tell me that is it possible to install and configure  samba 4 in my ubuntu 12.04 box  so I may replace windows server 2008 and use samba as a AD ?

 

thanks

honey.



I've used this tutorial with success. [http://paulcolfer.ie/category/os/linux/](http://paulcolfer.ie/category/os/linux/) Let me know if you have issues. I've been able to join windows and ubuntu clients to the samba4 DC.

---

### Post by honey_bee on 2013-01-23
Thanks "lingpanda" for guiding me. Well the purpose to use Samba 4 is to kick out my windows Server and use Samba 4 as a complete alternate of windows server and impliment group policies.
 
So I think Samba will help me in it as well.
 
I want to add one thing more which is out of the scope of my thread is preior I have Fedora,Centos 6.3 experience on server side. To use Ubuntu as a server it is a will be my 1st experience which is a bit confusing me.Becuase preior I use su,yum,yum update etc etc  commands as a root user  but here in ubuntu server  it is different.
 
To learn Ubuntu full fledge should I 1st learn Debian and then switch to Ubuntu ?
 
thanks
honey.

---

### Post by lingpanda on 2013-01-23
> **honey_bee said:**
> Thanks "lingpanda" for guiding me. Well the purpose to use Samba 4 is to kick out my windows Server and use Samba 4 as a complete alternate of windows server and impliment group policies.

 

So I think Samba will help me in it as well.

 

I want to add one thing more which is out of the scope of my thread is preior I have Fedora,Centos 6.3 experience on server side. To use Ubuntu as a server it is a will be my 1st experience which is a bit confusing me.Becuase preior I use su,yum,yum update etc etc  commands as a root user  but here in ubuntu server  it is different.

 

To learn Ubuntu full fledge should I 1st learn Debian and then switch to Ubuntu ?

 

thanks

honey.



I have no experience outside of Ubuntu and Windows on other platforms. I'm not sure what your learning curve will be. Once your Samba4 server is setup you can use Windows RSAT tools to administer.

---

### Post by lingpanda on 2013-01-23
> **honey_bee said:**
> Thanks "lingpanda" for guiding me. Well the purpose to use Samba 4 is to kick out my windows Server and use Samba 4 as a complete alternate of windows server and impliment group policies.
honey.



I'll add a link to this tool I use with my Ubuntu server. [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) I have a strong Windows background and it helped me with my transition to Ubuntu.

---

### Post by IJselflearner on 2013-02-21
Hi All,
 
I tested deploying Samba 4 in my Ubuntu 12.10 Server, I used Samba4.0.1 instead, since I can't find the 4.0.0 i followed this tutorial [[COLOR=#444444]http://paulcolfer.ie/category/os/linux/[/COLOR]]("http://paulcolfer.ie/category/os/linux/") almost completed but encountered an error on adding user "Client1", this is the response: 
ERROR(ldb): Failed to add user &#8216;Client1&#8242;: -objectclass: Cannot add CN=Client1, CN=Users,DC=mydomain,DC=local, parent does not exist .
 
anyone who have ideas on this? pls. help.
 
Thanks so much.
 
-IJ-

---

### Post by lingpanda on 2013-02-21
> **IJselflearner said:**
> Hi All,
 
I tested deploying Samba 4 in my Ubuntu 12.10 Server, I used Samba4.0.1 instead, since I can't find the 4.0.0 i followed this tutorial [[COLOR=#444444]http://paulcolfer.ie/category/os/linux/[/COLOR]]("http://paulcolfer.ie/category/os/linux/") almost completed but encountered an error on adding user "Client1", this is the response: 
ERROR(ldb): Failed to add user ‘Client1&#8242;: -objectclass: Cannot add CN=Client1, CN=Users,DC=mydomain,DC=local, parent does not exist .
 
anyone who have ideas on this? pls. help.
 
Thanks so much.
 
-IJ-

Looks like during your provision you didn't create a complex password for the admin. Try running the provision tool and creating a complex password.

---

### Post by IJselflearner on 2013-02-26
lingpanda,
 
Thanks for your reply.
Yes, I think it's the issue that everyone needs to consider.
Reinstalled Ubuntu Server, configure Samba, and create a complex password. tested and working fine.
 
Is it possible to join an Ubuntu machine to the domain?
 
Thanks!
 
-IJ-

---

### Post by LHammonds on 2013-02-26
> **IJselflearner said:**
> 
Is it possible to join an Ubuntu machine to the domain?
 
Your answer lies with Likewise

---

### Post by IJselflearner on 2013-02-26
LHammonds,
 
I tried likewise following the tutorial on youtube.
 
Seems that it cannot connect to my server,
~$ domainjoin-cli join <FQDN> <username>
Error:     NERR_DCNotFound [code 0x00000995]
 
Do you have idea on this?
Pls. help.
 
Thanks,
-IJ-

---

### Post by IJselflearner on 2013-03-08
> **lingpanda said:**
> I've used this tutorial with success. [http://paulcolfer.ie/category/os/linux/](http://paulcolfer.ie/category/os/linux/) Let me know if you have issues. I've been able to join windows and ubuntu clients to the samba4 DC.


Hi lingpanda,

I've been trying to add Ubuntu clients, but failed.
Do you have any tutorial on adding Ubuntu clients, or link maybe?

thanks so much!

-IJ-

---

### Post by lingpanda on 2013-03-08
Here is my quick and dirty tutorial I made. I basically copied and pasted various info across the net.

Configure nsswitch.conf
 Before you attempt to join an Active Directory domain, make sure the
 /etc/nsswitch.conf file contains the following line:
 hosts: files dns
 The hosts line can contain additional information, but it must include the
 dns entry, and it is recommended that the dns entry appear after the files
 entry.
 Computers running Solaris, in particular, may not contain this line in
 nsswitch.conf until you add it.
 When you use PowerBroker Identity Services with Multicast DNS 4
 (mDNS4) and have a domain in your environment that ends in .local, you
 must place the dns entry before the mdns4_minimal entry and before the
 mdns4 entry:
 hosts: files dns mdns4_minimal [NOTFOUND=return] mdns4
 The default setting for many Linux systems is to list the mdns4 entries
 before the dns entry&#8212;a configuration that leaves PBIS unable to find the
 domain.
 Important: For PBIS to process changes to your nsswitch.conf file, you
 must restart the PBIS input-output service (lwio) and the authentication
 service (lsass). Running the following command as root restarts both
 services:
 /opt/pbis/bin/lwsm restart lwio
 For PBIS to work correctly, the nsswitch.conf file must be readable by
 user, group, and world.
 For more information on configuring nsswitch, see the man page for
 nsswitch.conf.
 

 Configure resolv.conf
 Before you attempt to join an Active Directory domain, make sure that
 /etc/resolv.conf on your Linux, Unix, or Mac client includes a DNS
 server that can resolve SRV records for your domain.
 Example: [root@rhel5d Desktop]# vi /etc/resolvconf/resolv.conf.d/head
 search cimglocal.local
 nameserver 192.168.68.132
 

 Step 2: Install PBIS Open on Linux
 You install PBIS Open by using a shell script that contains a self-extracting
 executable&#8212;an SFX installer with a file name that ends in sh. Example:
 pbis-open-6.5.0.3499-linux-i386-rpm.sh.
 1. As root, run the installer, substituting the file name of the installer that
 you have selected for the one shown below:
 sh ./pbis-open-6.5.0.3499-linux-i386-rpm.sh
 Alternatively, you can run the installer as a regular user:
 sudo sh ./pbis-open-6.5.0.3499-linux-i386-rpm.sh
 2. Follow the instructions in the installer.
 Note: On SLES and other systems on which the pager is set to less, you
 must exit the end user license agreement, or EULA, by typing the
 following command: q
 Enable Other Login
 

 1) You have to be root to perform this how-to.
 If you are not root then be root by executing following command :-
 ubuntu-12.04lts@tejas-barot-linux-ahmedabad:~$ sudo su &#8211; ( Single Hyphen )
 

 2) First of all Please take backup of original file, execute following command :-
 root@tejas-barot-linux-ahmedabad:~# cp -p /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.orig
 

 3) Execute Following command :-
 

 root@tejas-barot-linux-ahmedabad:~#/usr/lib/lightdm/lightdm-set-defaults -m true
 root@tejas-barot-linux-ahmedabad:~#/etc/init.d/lightdm restart
 

 

 

 

 Disable Guest Account
 

 Open /etc/lightdm/lightdm.conf file from your terminal using the following command
 
sudo gedit /etc/lightdm/lightdm.conf Add the following line
 
allow-guest=false Save and exit the file

After adding the above line you should see similar to the following in lightdm.conf file
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
allow-guest=false

Finally you have to restart lightdm using the following command from your terminal
 
sudo restart lightdm Enjoy

---

