---
title: "Cross platform office setup with Ubuntu server, Ubuntu clients and Mac clients"
date: 2012-01-12
forum: Server Platforms
---

### Post by dckirba on 2012-01-12
Hi guys,

How are you doing?

I am unofficial network admin at the ad agency where I work and when I set up a server for the office a couple of months ago I decided to go with Ubuntu. Mainly because there are no virus headaches and once Ubuntu is set up it usually runs with no problems.

The server currently acts as:
[LIST=1]
[*]a gateway to the internet
[*]A web server for our wiki and project management software
[/LIST]

I am also trying to set up the server as a WINS server so users can log in and access their own shares.

Now this is where I hit a major bump.

Since we are a small startup, most of the staff bring their own laptops in to work. I can't reinstall OSs and configure them to work with the server. So my fileshare idea went bust.

But now, we've made a profit! And we're buying new equipment including computers for all our staff.

I'll have all staff except designers on Ubuntu. Designers will be on Macs.

Now that you know the story (and hopefully aren't asleep), my questions:

[LIST]
[*]How do you set up Ubuntu as a client that has to login to the server? I can't seem to find documentation anywhere.
[*]Is it possible to get Macs to login to the server so they can also access the shares the same way?
[*]Can I map all these users to users and groups on my server to have more control of access to various shares and services?
[/LIST]

Other plans I have for this server include a chat server, a backup solution (with Bacula), and a print server, but there is plenty of documentation on these so I should be OK.

I'm really trying to avoid Windows because we have a lot of virus issues here.

I have read the Server Guide and it has helped me immensely. however, it is more geared towards Windows clients and doesn't say anything about Ubuntu clients :(

Thanks for your time,

David K

---

### Post by Lars Noodén on 2012-01-12
> **dckirba said:**
> 
Now that you know the story (and hopefully aren't asleep), my questions:

[LIST]
[*]How do you set up Ubuntu as a client that has to login to the server? I can't seem to find documentation anywhere.
[*]Is it possible to get Macs to login to the server so they can also access the shares the same way?
[*]Can I map all these users to users and groups on my server to have more control of access to various shares and services?
[/LIST]

Have you looked at [Samba](https://help.ubuntu.com/community/Samba) yet?  If you are looking for a way to connect to the server over the LAN, it is one way.  Macs and Ubuntu can be clients.  If you are looking to connect to Samba over the WAN then you will need to supplement it with a VPN like OpenVPN.

Another way, which works both on LAN and WAN, is SSHFS.  It is not mutually exclusive with Samba.  With it you get the usual POSIX (rwx) permissions.

---

### Post by dckirba on 2012-01-12
Hi Lars,

Thanks for the reply.

I have looked at Samba, but the information I read talked about setting up as a windows domain controller. I guess that would work if you had samba client running off the Macs and Ubuntu machines though.

So it is possible to create a Samba Workgroup and connect Unix machines to that... Sorry, I'm not thinking clearly. Thanks for pointing me back to Samba.

---

### Post by spynappels on 2012-01-12
Samba Client is part of the default Ubuntu install IIRC, and while it can be used as a domain controller, it's most common use is as a shared filesystem.

To connect to a samba share from Nautilus you go to smb://<ip-of-samba-server>/share-name

Macs can also connect to Samba shares no problem.

---

### Post by dckirba on 2012-01-13
Hi spynappels

I did try this. However, it only allows me to connect with the administrator account on the server.

I tried creating different users and groups with access to different shares, but any other username/password combo besides the administrator one doesn't work from other Ubuntu or Mac computers (and Windows as well). However, I can access ALL shares when I log in with the administrator account from these machines. But that's not what the setup needs.

This is what led me to believe that I had to configure them as clients that need to login to the workgroup to access their respective shares.

---

### Post by spynappels on 2012-01-13
> **dckirba said:**
> Hi spynappels

I did try this. However, it only allows me to connect with the administrator account on the server.

I tried creating different users and groups with access to different shares, but any other username/password combo besides the administrator one doesn't work from other Ubuntu or Mac computers (and Windows as well). However, I can access ALL shares when I log in with the administrator account from these machines. But that's not what the setup needs.

This is what led me to believe that I had to configure them as clients that need to login to the workgroup to access their respective shares.

It's been a while since I've done any Samba work, but if you create different users on the server, you can use the smb.conf file to give each access to a limited personal share as well as to global shares.

Do some specific searching on help on configuring Samba as it will do what you want it to.

---

### Post by drdos2006 on 2012-01-13
Zentyal will get your machine running in an office environment while you learn the more detailed operations of a server. [http://www.zentyal.org/](http://www.zentyal.org/)   [http://www.zentyal.com/](http://www.zentyal.com/)
Uses a GUI at the server, was based on Ubuntu 10.4 Long Term Support last time I looked.

Or alternatively.

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You can also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server to install Webmin..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
[edit]
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000)
[/edit]

regards

---

### Post by SeijiSensei on 2012-01-14
In a *nix-only world like you describe (Ubuntu+Mac), I'd go with [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") over Samba.  Access control would be based on ordinary Unix permissions for users and groups.  

If you throw [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") into the picture, you can consolidate account management on the server as well. [OpenLDAP]("https://help.ubuntu.com/community/OpenLDAPServer") offers an alternative method to manage accounts, but I've never had the patience to try and comprehend the arcane syntax of LDAP.  [RADIUS]("http://www.mydeveloperblog.com/linux-tutorial/radius/radius-servers-installation-guide-freeradius-ubuntu-mysql/") provides yet another account management solution, one used extensively by ISPs.  All three of these are supported on Ubuntu.  As for Macs, I've never used them, but since the OS is Unix-based I'd imagine they could be integrated into a NIS, LDAP, or RADIUS authentication system.

---

### Post by Dry Lips on 2012-01-14
> **SeijiSensei said:**
> 
If you throw [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") into the picture, you can consolidate account management on the server as well. [OpenLDAP]("https://help.ubuntu.com/community/OpenLDAPServer") offers an alternative method to manage accounts, but I've never had the patience to try and comprehend the arcane syntax of LDAP. 

**drdos2006** mentioned Zentyal. As far as I know, OpenLDAP is included in the LDAP installation. So LDAP should work pretty much out of the box with Zentyal, or what?

---

