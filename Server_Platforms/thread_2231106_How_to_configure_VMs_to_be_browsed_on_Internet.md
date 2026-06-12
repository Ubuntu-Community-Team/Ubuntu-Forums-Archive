---
title: "How to configure VMs to be browsed on Internet"
date: 2014-06-23
forum: Server Platforms
---

### Post by satimis on 2014-06-23
Hi all,

How to configure VMs to be browsed on Internet

One Static IP
VMs - Apache web server running WordPress, having its own domain.
OS
host	Ubuntu 14.04 desktop
VMs	Ubuntu/Linux Mint/Debian

Each VM is a web server with website installed which can be browsed locally.

I'm now searching for guides to make each VM to be browsed on Internet.  I did it several years ago making use of Perdition and Mysql for routing.


On googling I found following document.  I hesitate whether they are suitable for me to follow?

1)
Setting up a Virtualbox Virtual Machine for Web Development with Multiple Sites using mod_vhost_alias and VirtualDocumentRoot
[http://otaqui.com/blog/1652/setting-up-a-virtualbox-virtual-machine-for-web-development-with-multiple-sites-using-mod_vhost_alias-and-virtualdocumentroot/](http://otaqui.com/blog/1652/setting-up-a-virtualbox-virtual-machine-for-web-development-with-multiple-sites-using-mod_vhost_alias-and-virtualdocumentroot/)

2) 
Configure several Apache servers on multiple VMs
[http://www.crocoware.com/2012/12/configure-several-apache-servers-on-multiple-vms/](http://www.crocoware.com/2012/12/configure-several-apache-servers-on-multiple-vms/)


Pointer and advice would be appreciated.  Thanks.

Regards
satimis

---

### Post by SeijiSensei on 2014-06-23
Isn't a simple approach to use Apache's [mod_proxy]("http://httpd.apache.org/docs/current/mod/mod_proxy.html") to redirect requests for each site to its corresponding VM?  I presume the VM's have private addresses on their own virtual network since you have only one real IP.

---

### Post by satimis on 2014-06-23
> **SeijiSensei said:**
> Isn't a simple approach to use Apache's [mod_proxy]("http://httpd.apache.org/docs/current/mod/mod_proxy.html") to redirect requests for each site to its corresponding VM?  I presume the VM's have private addresses on their own virtual network since you have only one real IP.
Yes, each VM has local IP assigned by router.

Apache is not installed on host.  I'm not prepared to install it on host.  Can I use one VM for routing?

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2014-06-24
If you want to support name-based virtual hosts on a single IP, you need something like Apache. Why aren't you "prepared" to install it?  It's not hard, especially if you're only using it as a proxy.  Nor is it especially insecure.

---

### Post by satimis on 2014-06-24
> **SeijiSensei said:**
> If you want to support name-based virtual hosts on a single IP, you need something like Apache. Why aren't you "prepared" to install it?  It's not hard, especially if you're only using it as a proxy.  Nor is it especially insecure.
Hi,

All websites on VMs are running Apache, LAMP.  I only reject installing Apache on Host because I expect keeping the Host clean.

Edit
===
To make my question simple.  My problem is "routing".  

- All domains are now pointing to the static IP (only ONE), say 111.222.333.444
- All VMs are now assigned with internal static IP, say e.g. 192.168.0.10. 192.168.0.11 etc.
- Name-based website are now running on VM.  They can be browsed locally on their VMs running /localhost/site-name.
- WAN, broadband is now connected to router.

How to make the websites browsed on Internet?

On googling I found several links with different suggestion.  What will be the reliable steps for me to follow.

Regards
satimis

---

### Post by SeijiSensei on 2014-06-25
I'll just say this one more time.  If you are using a single IP and name-based virtual hosting, you cannot solve these problems with routing.  There needs to be a piece of software like Apache that can interpret the URL request and route the connection to the relevant web host.  Routing only works at the IP level and will not help with this problem.

I think your fervor for a "clean" host is a bit misplaced.  A proxy-only Apache isn't going to be very vulnerable since the connections will be sent on to the actual web servers.  They are the ones that might be vulnerable.

---

### Post by volkswagner on 2014-06-25
If you don't want to install Apache on the host, you should be able to create a new VM to act as proxy/reverse proxy server or "promote" one of the existing
VM's to act as the main Apache or gate keeper.  Provided each VM is on the same LAN, any one Apache server can perform this duty.

Simply forward all port 80 traffic to the proxy VM and setup name virtual hosts for each site.  For any domain that needs to be forwarded, put the reverse
proxy info in the vhost conf file.  I created a simple [how-to]("http://ubuntuforums.org/showthread.php?t=1920715") for this setup. SeijiSensei was
kind enough to point out that this solution is only intended for http not https.  So if you have a few domains requiring https, you'll want them residing on
the machine doing the reverse proxy server duty.

If you decided to setup a dedicated vm for the purpose you could use Nginx as the proxy server.  I have no experience with it, but I've heard
it's very lightweight and does a tremendous job for this specific task.

---

