---
title: "Help with LAMP"
date: 2011-11-18
forum: Server Platforms
---

### Post by b0j on 2011-11-18
Hey everyone,
I was trying to set up a web server with LAMP. I have some questions:
1) Do you need Ubuntu Server to use it?
2) Can someone help me find an easy, updated guide for installing and using LAMP? I am a n00b to web hosting and I need help.

Background Info: I have already bought a domain, but did not want to pay GoDaddy to host the server. There won't even be 2 people on at one time.
Computer Specs: Intel(r) Pentium 4. Computer is a HP xw4600 Workstation.
Internet speed: Incoming: 1536 kbps
Outgoing: 384 kbps
Thanks in advance for any help!

--B0J

Edit: People have been saying you need a dynamic DNS service. I plan to use OpenDNS to redirect people from my domain to my IP.
Edit 2: Thanks for the help everyone!

---

### Post by darkod on 2011-11-18
1. Depends what do you mean by "use it". LAMP stands for Linux Apache MyPHP and it runs on a linux server. Ubuntu Server is one option. During the install, immediately after the installation of the core files is done, the installer will ask you about additional roles you want to install. There will be option for LAMP. Just select it, and that's it. Whether you want your server to do other roles, depends, and you can select more.
Note that in text installers you use the space bar to select options, not Enter. And it will show * when selected. Pressing just Enter will continue to the next screen without selecting LAMP.

As for running LAMP, the official ubuntu documentation is at:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

You can also google for setting lamp on ubuntu.

For any serious server roles people usually use LTS releases, not simply the latest ubuntu version. The current latest LTS is 10.04.

You are aware that with upload speed of only 384kb/s it's gonna be really really slow for anyone loading websites from your server right?
Also worth considering is that your ISP is probably issuing dynamic IP for your router, so you will need either a static IP from the ISP or using a service like dyndns or similar.

---

### Post by CharlesA on 2011-11-18
I run a LAMP stack on my Ubuntu desktop box since I use it for web development. I already run it on a Ubuntu server box for a few things.

Installing LAMP is an easy apt-get away.

In 10.04 you'd install it by using [tasksel]("https://help.ubuntu.com/community/Tasksel").

---

### Post by nickleboyblue on 2011-11-18
The clear answer: You can install a LAMP server on top of your basic Ubuntu desktop or as a part of Ubuntu server.  The difference in approaches depends on your goals.  If it's a simple development server and you want graphical capabilities, install a LAMP server on top of your typical Ubuntu desktop and you're set.  If you are setting up a production server, install it on Ubuntu server and access it through SSH.  If you don't know much about SSH, the graphical route is the one for you.

Now there IS a way of installing a lamp server on your computer with one command, but if I were to tell you what command that was right here and now, I would be sparing you the effort of finding out how for yourself, which is half of the process.

If you are getting into web development for the first time and don't know exactly what you're looking at yet, you might consider the difference between PHP and the Python framework known as Django.  If you are writing smaller applications, use PHP.  If you need something that is fast and easily maintained, use Django.  However, if you're looking for another button to put on your resume, use PHP as Django is less well known in most circles (though I don't know why).

Hope that helps.  Good luck, and happy coding!

Oh, and you'll probably want a dns service so you can see your websites from anywhere.  Use Freedns, not dyndns.com.  Freedns really is free.

---

### Post by crazy dave on 2011-11-19
It seems as if you want to host your own server at home.  There is a useful Ubuntu guide here:

[[COLOR="RoyalBlue"]Install a LAMP Server on Ubuntu[/COLOR]]("https://help.ubuntu.com/community/ApacheMySQLPHP#To_install_the_default_LAMP_stack_in_Ubuntu_6.06_LTS_.28Dapper_Drake.29")

and here is a guide to setting up a dedicated web server at home:

[[COLOR="RoyalBlue"]how-to-setup-a-dedicated-web-server-for-free/[/COLOR]]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/")

You'll need to set up a firewall and to take account of the fact that you'll probably have a Dynamic DNS IP address should you want the site to be indexed in the search engines(which you said you don't - just two users)

Regards

---

### Post by darkod on 2011-11-19
> You'll need to set up a firewall and to take account of the fact that  you'll probably have a Dynamic DNS IP address should you want the site  to be indexed in the search engines(which you said you don't - just two  users)

Configuring dynamic dns for the IP is not so much for search engines if I understand it correctly, it's more to allow website browsing to the outside world.

In fact, that's one thing the OP didn't specify. If all users accessing the web server will be on the local network, no dynamic dns is needed. But for anyone outside, even a single person to be able to access, the nameserver needs to know whether the website is at 1.2.3.4 or 5.6.7.8. When your ISP changes your dynamic IP, no one will be able to reach the web server from outside if there is no any sort of dynamic dns service configured.

---

### Post by crazy dave on 2011-11-20
> Configuring dynamic dns for the IP is not so much for search engines if I understand it correctly, it's more to allow website browsing to the outside world.

I did say > should you want the site to be indexed in the search engines.... having a static IP is preferable if you want consistent crawling of your website.

---

### Post by PCFreak2 on 2011-11-20
Install LAMP during Ubuntu Server setup
I would also recommend OpenSSH for remote administration (CLI, file management, etc.)

---

### Post by CharlesA on 2011-11-20
> **PCFreak2 said:**
> Install LAMP during Ubuntu Server setup
I would also recommend OpenSSH for remote administration (CLI, file management, etc.)
Just be sure to secure SSH properly if it is going to be accessed from the internet.

---

### Post by PCFreak2 on 2011-11-23
> **CharlesA said:**
> Just be sure to secure SSH properly if it is going to be accessed from the internet.
Yeah

---

