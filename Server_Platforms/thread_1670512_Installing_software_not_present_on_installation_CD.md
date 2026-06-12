---
title: "Installing software not present on installation CD"
date: 2011-01-19
forum: Server Platforms
---

### Post by radnovichca on 2011-01-19
Hello,

This is my first time on a forum and the first time I tried to set up a web server.

I am following a tutorial on how to set up a web server here: **[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/). **We get to a part were I have to install a firewall. The tutorial suggests shorewall. The command I am told to use is sudo aptitude install shorewall. However, all that is returned is could not find package shorewall. I have searched the net and could not find anything on my issue. I then attempted to search aptitude but no luck. I found shorewall online but how do I download it without a GUI. 

This is also my first time having an OS that is only command line. I have done other things from the command line only before. Things such as computer science homework on the computer science servers.

For simplicity, how do you install software off the internet on to ubuntu server without creating a CD or using a flash drive?

Thank you,
Chris

---

### Post by spynappels on 2011-01-19
Hi Chris,

First things first. Will this server be behind a router or directly internet facing?

The problemwith following how-tos is that they rarely completely fit the situation you are planning to use them for, and just following the how-to without thinking which parts you need and which parts you don't rarely works.

So, if your server is behind a router, you do not need a firewall at all, as the only traffic getting to the server from the big bad Internet is what you forward to it through your router. For a normal webserver this is only port 80 (or 443 if you use https) and only apache is listening on those ports.

If it is directly Internet facing, you will probably need to run some form of firewall, but Linux has one built in which you can interact with through iptables or UFW. There is no need to add another package to do this. Bodhi.zazen on this forum has put together good information on using both these front ends and if you search for this info, you will learn a lot about how and why they work, and how to configure them properly.

And it can all be done through CLI!;)

---

### Post by radnovichca on 2011-01-20
Thank you for responding!

It is going to be behind a router. Thank you for helping me out!

What I am actually trying to do is set up a web cam to watch my dogs while I am not home. When I started researching this, I saw an opportunity to expand my knowledge by creating a website. When I looked into that, I found out that I could learn how to create a web server to host my website. It was free, always a plus, because my wife had an extra laptop laying around. It gets better though because the laptop over heats. I was planning on taking it apart and building a bench for it. I will  finally have something in my home that looks like a computer engineer lives here. My overall goal is to do stuff outside of classes. This is a start.

---

