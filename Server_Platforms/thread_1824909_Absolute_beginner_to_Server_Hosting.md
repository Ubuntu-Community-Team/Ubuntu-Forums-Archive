---
title: "Absolute beginner to Server Hosting"
date: 2011-08-14
forum: Server Platforms
---

### Post by Jakemurray on 2011-08-14
Hi, i have been interested in starting up a website of my own, but i want to host it on my own personal server.
unfortunately i have absolutely no experience with servers, and i dont even know where to begin.
i have done some reading up and i think my choice will be a LAMP server.
now to the question, lets assume that i know nothing but html, css, JS,  etc. where would be the best place to start learning about servers, how  to operate within a server, and the such? and which ubuntu server OS  would be the best choice?
any help would be very much appreciated, i will also post my email  address for an alternate method of communication. thank you so much.

[EMAIL="jake.murray81@hotmail.com"]jake.murray81@hotmail.com[/EMAIL]

---

### Post by arrrghhh on 2011-08-14
Well I would recommend you pay to have someone host it.  These are the reasons:

You won't have to worry about bandwidth on your home, residential internet connection.
If there's any hardware or otherwise failures, your website should be moved automatically to another piece of hardware assuming the hosting company does VM's and something like vmotion...
Security, and all of that mess is taken care of for you.  No need to worry about people hacking into your server remotely, any of it - depending on the setup you purchase, obviously.

I seriously doubt a server in your house will be cheaper to run with electricity & internet bills.  Not to mention hardware...

If you truly do want to embark on this adventure with a home grown server, we're here to help.

The server guides are a good place to start:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

I would recommend 10.04LTS if you're building a server.  That way you only have to do major upgrades every 2 years (which I would still recommend a fresh install for...)

There's a lot of tools that make hosting websites easy, like cpanel... Googling around I found this as well - [http://ehcp.net/](http://ehcp.net/) - never used it myself.  My website is really simple and for internal use only, so I just use Apache.  A basic LAMP server like you mentioned above.  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Enjoy!

---

### Post by HermanAB on 2011-08-14
Howdy,

Linux is Linux is Linux...

Just install ordinary Ubuntu and use the desktop and GUI tools till you know what you are doing in a few years from now.

---

### Post by Jakemurray on 2011-08-14
@[arrrghhh]("http://ubuntuforums.org/member.php?u=323523")
thanks for the links, and yes i know i might seem crazy for wanting to do this myself instead of hiring, but i feel like if i do that id be cheating =/ so im gonna take it slow and learn all i can before actually publishing the site, thanks!

@HermanAB
is there a way to run a server with 11.04 thats what im running now. or did i completely miss what you were trying to say =/ thanks

---

### Post by Ant01 on 2011-08-14
Hi Jakemurry

Hope you don't mind me joining in on your post. I am in a similar position and know the frustration you are going through. I posted a similar query on [http://ubuntuforums.org/showthread.php?t=1822365](http://ubuntuforums.org/showthread.php?t=1822365) and am slowly working my way through it.

I currently have a number of sites which I use a hosting service. I am also interested in learning the ins & outs of how the server side works and therefore want to set up a hosting my own website server.

I have limited knowledge of ubuntu desktop and cli so I decided to use the ubuntu desktop version with gui to get started. I have installed webmin which I am able to run on my local host but now am stuck how to go live with setting up the server.

I am also used to Cpanel but it seems that you have to purchase a license. I am not sure what free admin systems are available for managing multiple sites. I checked [http://ehcp.net/](http://ehcp.net/) but it seems there was a security breach with sites being hacked.

Any feedback on this post will be appreciated, especially how to get my server up live so that I can practise in the meantime using webmin, without having to go via the unbuntu server.

---

### Post by Jakemurray on 2011-08-14
no i dont mind at all, you have some very good points and any feedback to your post will be greatly appreciated by me as well.

---

### Post by arrrghhh on 2011-08-14
To both of you guys.

If you already have 11.04 Desktop installed, that's great.  You can simply use that box and install all the same LAMP stuff you would on Ubuntu Server - you just get a desktop user interface to work with, hopefully making it easier for you.

Ubuntu Server is purpose-build for servers.  The Desktop Edition is more generic, so that would be best to start with for sure.  Once you get the hang of it and you want to build a dedicated server that does nothing but host your website for example, then you can start looking at the Server Edition again ;).

---

### Post by Jakemurray on 2011-08-14
so i just installed apche2 mysql and php5 with this tutorial
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
but at the end where it says to get php5 and mysql to work together i need to change a line in a specific file,
when i opened the file the specified line wasnt there. did i do something wrong?

---

### Post by Jakemurray on 2011-08-14
and once i have everything installed what do i do from there?

---

### Post by Ant01 on 2011-08-14
I've installed LAMP but am not sure how it works?

---

### Post by Ant01 on 2011-08-14
apologies, not sure if I have LAMP installed, phpadmin, mysql, apache, php installed and working. Is there different command to install LAMP and how does it work. 

The server works on my local host but I need to make it live ? How do I do about this?

---

### Post by arrrghhh on 2011-08-14
> **Jakemurray said:**
> and once i have everything installed what do i do from there?

> **Ant01 said:**
> I've installed LAMP but am not sure how it works?

Depends on what you guys want to do.

The default folder for your website is usually /var/www on Apache.  If you go to [http://localhost](http://localhost) you should see a basic "It Works!" page.  This is assuming you're running the browser on the machine that has Apache/LAMP installed.

---

### Post by Ant01 on 2011-08-14
> **arrrghhh said:**
> Depends on what you guys want to do.

The default folder for your website is usually /var/www on Apache.  If you go to [http://localhost](http://localhost) you should see a basic "It Works!" page.  This is assuming you're running the browser on the machine that has Apache/LAMP installed.

Thats correct,  "It Works!" on my local machine.

How do I set it up live so that I can browse it from the internet?

---

### Post by arrrghhh on 2011-08-14
> **Ant01 said:**
> Thats correct,  "It Works!" on my local machine.

How do I set it up live so that I can browse it from the internet?

Great!

The first step is the firewall on your server.  I like UFW, so ```
sudo ufw enable
``` To turn on the firewall, ```
sudo ufw allow 80
``` Will allow any IP address to hit port 80 on your box.

The next step to get it outside your LAN is going to be on your router.  Look on PortForward.com for your router, every one is slightly different - but the basic idea is that you are telling the router to forward any traffic that hits it on port 80, to the LAN IP of your Apache server.

So my server is 192.168.0.99.  My "outside IP" is obviously different - I tell my router to point any requests from the outside on port 80 to 192.168.0.99.  Sometimes called NAT, port forwarding, etc.

That should be all your need - assuming your ISP doesn't block the traffic, your web page should now be available from your public (outside) IP.  Only way to verify is to get a friend, or use your phone's internet - some other internet connection - and go to [http://x.x.x.x](http://x.x.x.x) - put your public IP in for the x's.  Find it by going to [http://whatismyip.com](http://whatismyip.com), it will tell you what the IP address is on the public internet.

---

