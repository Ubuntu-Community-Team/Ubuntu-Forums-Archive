---
title: "First Server Goal for Novice"
date: 2011-09-22
forum: Server Platforms
---

### Post by BEEDO on 2011-09-22
Now that I have installed a server, my FIRST GOAL is to learn how to be able to and actually move .html and .php files from Windows XP into the Apache server and have Apache serve them to a browser in XP. 

I also want to learn how to use Ubuntu 11.04 server with LAMP, which is what I just installed into VirtualBox(which I am also new to) on Windows XP and to install and learn how to use WebMin and PHPmyadmin, but unless those latter two help me achieve my first goal, I can get to them later

MY EXPERIENCE: Very little with Ubuntu command line, or command line in general. I was able to log in and shutdown, which took me awhile to figure out. Still, a tiny victory!

I have a little experience with WAMP. I've edited httpd.conf in Apache and php.ini on XP. I've created and moved .html and .php files (without FTP) into Apache htdocs and was able to open and interact with websites in my browsers. I've made some simple databases in MySQL. (All on XP) I feel a little lost in this command line in a virtual machine, but am enthusiastic to embrace the learning curve!

MY QUESTION: What steps would any of you recommend that I take to achieve my objective?

Thanks, in advance!

---

### Post by Lars Noodén on 2011-09-22
Here are some bash tutorials to help you get familiar with the shell:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

It's well worth it to learn your way in the shell.  Anything you can do manually can be automated.

Edit: Here is a third, which shows common mistakes:

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by BEEDO on 2011-09-22
A friend of mine gave me *Linux Command Line and Shell Scripting Bible*, but I like these tutorial links because they give you exercises. The 800+ page book is a good compliment to these tutorials. I think I should set up a user to do the exercises rather than root? I am, alas, not even sure how to do that. Doesn't change my first goal, but I can see the benefit of studying bash commands and will. Thank-you Lars Noodén!

---

### Post by Dangertux on 2011-09-22
Also you will find that alot of it will be the same as in Windows, not the CLI so much. But in terms of MySQL commands, and your php.ini and apache.conf a lot should carry over.

---

### Post by dtfinch on 2011-09-22
I usually use WinSCP for uploading from Windows to Linux servers, being secure, easy, and requiring no setup (apart from installing openssh-server), and putty for other remote administration over ssh.

Edit: just noticed the virtual machine part. If you have virtualbox set up in NAT mode (meaning the box does not have an accessible IP), you might be able to still get to it by going to the vm settings, network, select the adapter, and open "port forwarding" in advanced to add the appropriate forwards (probably ports 22 for ssh and 80 for http), then you could connect to it through localhost. Though I haven't personally tried that yet.

---

### Post by drdos2006 on 2011-09-22
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by BEEDO on 2011-09-24
It sounds like I should have installed openssh server when I installed the Ubuntu 11.04 server. I was trying not to get too complicated. Although I feel like I know next to nothing, I think I can do that. I will also find out more about putty, which will be easy since I know nothing about it.... I think I should get the openssh and have my access ports figured out before I install webmin.

drdos2006:
> You could also install the Desktop and run the server as a virtual machine using Virtualbox.I am doing that also; 11.04, too. Learning some file management, vim, nano...

dtfinch:
> Edit: just noticed the virtual machine part. If you have virtualbox set  up in NAT mode (meaning the box does not have an accessible IP), you  might be able to still get to it by going to the vm settings, network,  select the adapter, and open "port forwarding" in advanced to add the  appropriate forwards (probably ports 22 for ssh and 80 for http), then  you could connect to it through localhost. Though I haven't personally  tried that yet. This part is not intuitive for me. I get to the "Port Forwarding Rules" and I see six blank tabs(?): Name, Protocol, Host IP, Host Port, Guest IP, Guest Port. ????????????

---

### Post by dtfinch on 2011-09-26
> **BEEDO said:**
> dtfinch:
This part is not intuitive for me. I get to the "Port Forwarding Rules" and I see six blank tabs(?): Name, Protocol, Host IP, Host Port, Guest IP, Guest Port. ????????????

Testing it, I was able to leave the guest and host IP fields blank, entering only the port number (22 in both for ssh). Then I was able to connect to it through localhost with putty and winscp.

There is an issue (I ran into, but I don't know if you will) in VirtualBox where if you change the networking settings for the vm, it generates a random new mac address so the vm sees it as a new network card, and assigns it a new name (eth1, eth2, etc.). In Ubuntu Server (10.04 at least), dhcp is only enabled on eth0 by default, so the vm can't get online until you run "dhclient" manually. Then to make it permanent you need to edit /etc/network/interfaces to reflect the correct interface name.

---

