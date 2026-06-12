---
title: "Ubuntu Server 7.04 Setup Help - Virtual Server on Home Network"
date: 2007-09-18
forum: Server Platforms
---

### Post by bronzemonkey on 2007-09-18
The past 3 days have been an exercise in failing to get Ubuntu Server Edition 7.04 to work for me. I am coming from an "absolute beginner" position with regards to Linux and servers.

I am a web designer trying to create a LAMP testing server (in VirtualBox) on a home network so that I can test my webpages (for multiple sites) and install Wordpress/Textpattern to learn and experiment with CMS.

I would really appreciate help because it is essential for me to have a testing server and numerous tutorials, forums, and guides have failed to help me produce something that works. To make my situation as clear as possible I'm going to go into some detail below:

=============================

Home Network Router
Host OS: Windows Vista
Virtualization software: VirtualBox 1.5
Ubuntu Server Edition 7.04 LAMP
Server needs to be inaccessible/secure outside the network

I have installed the LAMP setup of Ubuntu Server Edition 7.04. In order to get it working in VirtualBox I followed this guide - [http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/](http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/)

From here I followed another tutorial on making sure that the virtual server has it's own IP. In the VirtualBox network settings for the Ubuntu VM, I selected "Host Interface" instead of NAT and created a new virtual network adaptor. I then bridged the connection between this virtual adaptor and the physical one. Now, when I pinged google.com I was getting a response.

My PC is connected to the local network and the internet via a single ethernet cable. I believe it uses eth0. My router has a static IP in the format 10.0.0.100.

=============================

This is as far as I have gotten without problems/confusion setting in. I do not know how, and have not been successfully guided, to configure the static IP for the server, put files onto the server from my host OS, and then view them from Firefox/Opera in my host OS.

Trying to follow certain steps in these tutorials produced no luck:
[http://linuxgazette.net/141/lazar.html](http://linuxgazette.net/141/lazar.html)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Hopefully someone will be kind enough to go through this with me, step-by-step, because I'm feeling pretty lost at sea right now. Many thanks for any assistance.

---

### Post by bronzemonkey on 2007-09-19
I have gotten to the point where I can see the default apache server from my host OS.

I would like to be sure that the server is secure so that it can only be accessed and see from within our home network (or just my PC if that is easier). Where does openssh fit in with this?

- If I just install openssh, and then webmin, will I be ready to go?
- What about fiddling with the network interfaces? Do I need to make the server IP static even if I use a router?
- And finally, how do I set up several domains on my virtual server? For example, for websites like: [www.myblogtest.com](www.myblogtest.com) ; [www.clienttest.com](www.clienttest.com).

Once again, thanks to anyone who takes the time to point me in the right direction.

---

### Post by koenn on 2007-09-19
> **bronzemonkey said:**
> I have gotten to the point where I can see the default apache server from my host OS.

I would like to be sure that the server is secure so that it can only be accessed and see from within our home network (or just my PC if that is easier). Where does openssh fit in with this?

- If I just install openssh, and then webmin, will I be ready to go?
- What about fiddling with the network interfaces? Do I need to make the server IP static even if I use a router?
- And finally, how do I set up several domains on my virtual server? For example, for websites like: [www.myblogtest.com](www.myblogtest.com) ; [www.clienttest.com](www.clienttest.com).

Once again, thanks to anyone who takes the time to point me in the right direction.
ssh has nothing to do with it. 
If your web server has an address in a private range, it will be inaccessible from anywhere outside that private network. Even more so if it's behind a firewall, or if  firewalling software running on the machine itself. 
You can add additinal access limitations in the apache config files - but I don't know those by heart.

Servers should always have fixed addresses. It's just good practise, and makes live easier. Having a router has nothing to do with it.  

"several domains on my virual server" -> Look for info on 'virtual hosts' for apache, on these forums or in the apache documentation. 
the 'virtual' in virtual hosts has nothing ot do with the fact that you're running on a virtual machine, it indicates a web server hosting multiple websites. You may need some sort of DNS - the easiest would be to list all "web sites" in /etc/hosts of the client machines, pointing to the ip address of the web server, eg
```

192.168.1.1  www.blog.xx
192.168.1.1  www.somesite.xxx

```

---

### Post by bronzemonkey on 2007-09-20
Thanks, based on your pointers and a lot of google work, I have got the server working and can access my virtual hosts from my guest OS. It was a bit of a messy job and I'm sure it's not set up as it should be, but given I don't really know what I'm doing I'm just grateful for what I have!

However, at the moment I have to upload the files from my host OS (using WinSCP to access the server) to the guest VM (the server). The document roots are /home/administrator/test.domain.com/htdocs , /home/administrator/test.domain2.com/htdocs , etc. But while looking for help setting up my virtual hosts I came across this article where the document root for the virtual host was c:/programfiles/...

[http://www.thewatchmakerproject.com/journal/378/virtual-hosts-and-the-proper-way-to-work-offline](http://www.thewatchmakerproject.com/journal/378/virtual-hosts-and-the-proper-way-to-work-offline)

What's going on here? Is it possible to avoid uploading my files to the server and just get the server to look in the folder on my host OS?

---

### Post by koenn on 2007-09-20
when i use virtual machines, i usually treath them as real machines, so I'd use standard network apps to move/copy files from the host system to the guests. 
However, yes, some (all) VM applications have there own file sharing system between the host system and the guests, to allow the user to easily get files from the host system to the guests (and vice versa). I know for a fact that MS VirtualPC had that feature, I assume VirtualBox does the same - I use VMWare nowadays and, as i said, i use standard networking as a matter of principle because most of my VM-stuff are tests/exercices for real live situations anyway. 
So, given that there's filesharing between host and guest, i suppose you could even let the guests use directories on the host system permanently, same as you could "map a drive letter to a share" or "mount a network share" in a non-virtual situation. 

Re your "messy but it works". Consider it a first draft. Now you know what you're dealing with and with what you've learned, you can start over and do it right  :) 
It's the 'you always throw one away" effect : To fully understand a problem, you need to have solved it, and afterwards, as you now 'fully understand" it, you can solve it better.

---

### Post by bronzemonkey on 2007-09-20
I think you are right about just treating the virtual machine as a real one. It will make it easier if the virtual hard disc has to be moved to another computer and it is a truer simulation of a live environment.

And I don't think I really solved the problem! It's a very bare setup and being on a network seems to have made it easier. I don't understand all parts of the process or what has been missed, but I kept notes as I went along so that I can trace my steps. When I've got time to learn about what I actually need to take care of, and how to configure apache2 correctly, then I can go back and do it properly.

---

### Post by bronzemonkey on 2007-09-21
I've come across a few problems that I can't get my head around. I  have the following appearing when the server boots up. I have two virtual hosts which were set up using webmin and which I can view/access.

[B]*Starting web server (apache2)...
apache2: Could not reliably determine the server's fully qualified domain name, using 10.0.0.20 for ServerName

[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results[/B]

Those vhost errors also tie in with my difficulties to get the logs for each vhost to work. Everything I google talks about the httpd.conf file (which is found at /etc/apache2/httpd.conf on my server) but that file is completely empty on my server. Instead the vhost information has been placed in files at /etc/apache2/sites-enabled and sites-available, which each vhost creating a new file in each directory with its info inside.

How do I go about giving the server a fully qualified domain name and avoiding the errors associated with my virtual hosts?

And one last thing, under the webmin controls I can restrict access to certain IP address, but what is the format for restricting access only to a network? Is it network/netmask? So would 10.0.0.0/255.0.0.0 do the trick?

---

### Post by koenn on 2007-09-21
These are 2 separate problems : 
1- the "can't resolve hostname" warning
2- the "ports not supported" error

It's been a while since I set up apache, and I only did 1 or 2 really simple setups so you'll have to do some reserch again, but here's a few things to get you started

1- 
I think you can specify a server name in the apache config, and i think apache will try to resolve (= translate to an ip address) that name using  standard name resolving machanisms. Usually that's DNS, but entries in /etc/hosts should work just as well. 
I don't remember if you'd use 1 server name for multiple sites - in any case, you'd need a DNS or /etc/hosts entry for whatever your server is called in its apache conf.

a fully qualified domain name is a name of the form "mywebserver.mydomain.yx", as opposed to a simple hostname 'mywebserver". 

2-
apparently you've specified a port number ( :80) for both sites. This is not necessary, as 80 is the default pport, and you're using the same port for both sites. Specifying (sdifferent) ports for each site is a workarond to host multiple sites on 1 server, and is only needed if your web server can't handle 'virtual hosts. That explains the errors, and the fix is obvious : get rid of those :80 's


httpd.conf used to be the default conf file for any http daemon, but is no longer used in apache (it would probably still work, but it makes more sense to just use apache's dedicated conf dirs / files. 

So would 10.0.0.0/255.0.0.0 do the trick? 
probably. 
another way to write that would be 10.0.0.0**/8**
most configs that accept ip addresses, also accept this network address notation. I suppose you could find that in the apache docs.

quick guide to network masks :
/8 = 255.0.0.0
/16 = 255.255.0.0
/24 = 255.255.255.0

a network mask is 4 groups of 8 bits, and the number n in /n indicates the bits that =1 (the others are 0)
so "/8" = IIIIIIII.00000000.00000000.00000000 or  IIIIIIII.0.0.0
and IIIIIIII binary = 255 decimal.

---

### Post by bronzemonkey on 2007-09-21
Using webmin to select 2 of my 5 vhosts and remove the '80' from the port option. After I removed the 80s as suggested, apache2 restarted with the following error:

[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
httpd (no pid file) not running
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[error] Virtual Host *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[[COLOR="Red"]fail[/COLOR]]

I couldn't connect to any of the 5 vhosts. I return to webmin and put the 80s back into those 2 vhosts. Restart apache2 and get presented with the same error. What has happened, how can I fix it, and what did I do wrong?

---

### Post by koenn on 2007-09-21
oops.

going by the text of the error and what i remember of apache config:
check whether your sites (including the default site) mix <VirtualHost *> with <VirtualHost xxx.xxx.xxx.xxx> declarations and make them all one or the other. Also make sure you have a "NameVirtualHost" directive for each site. 

Note that your webserver is not running / fails to start; thats the reason you cant reach any of the sites. 

You have now reached the limits of my apache knowledge ... :)

---

### Post by bronzemonkey on 2007-09-21
The point is that it didn't go back to working when I reversed the changes you suggested. Why is that?

I've tried to add the NameVirtualHost directive for the conf files of every vhost but that hasn't worked either.

Each /etc/apache2/sites-available/domain.com.conf file looks like this

NameVirtualHost *
<VirtualHost *>
DocumentRoot "/home/administrator/domain.com/public_html"
ServerName domain.com
<Directory "/home/administrator/domain.com/public_html">
allow from all
Options +Indexes
</Directory>
ErrorLog /home/administrator/domain.com/log
LogLevel warn
</VirtualHost>

And the web server puts out the following for 4 out of 4 vhosts:

[warm] NameVirtualHost *:0 has no VirtualHosts
[warm] NameVirtualHost *:0 has no VirtualHosts
[warm] NameVirtualHost *:0 has no VirtualHosts
[warm] NameVirtualHost *:0 has no VirtualHosts
[fail]

---

### Post by koenn on 2007-09-22
> The point is that it didn't go back to working when I reversed the changes you suggested. Why is that?
Beats me ...

In any case, the VirtualHost errors have changed with your latest changes. This indicates that it's indeed a problem with the VirtualHosts config. I suspect it has something to do with the *. 
There are some other threaths about virtualhosts floating around, maybe you can go have a look there to see how they do it.

---

