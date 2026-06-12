---
title: "Linux server noob needs a project"
date: 2007-02-17
forum: Server Platforms
---

### Post by mrplaid on 2007-02-17
Howdy,
I'm a 3rd shift tech support guy with a lot of free time and I'm looking to learn more about Linux. I've got an Ubuntu box I've set up and I'm looking to start a project that will help me learn more about Linux and be beneficial to the rest of my department.
Rather than using Ubuntu to set up a web server that no one will use, I'm looking to set up either an (open source) asset management system or a VNC server. I'd really like to set up something like a remote desktop management server. I used to work at a school that did a lot of stuff with Apple software, and I loved Apple's Remote Desktop. 
If neither of those things are feasible, I'm open to suggestions. So please help me! I'm bored!

---

### Post by jom2000 on 2007-02-17
How about a remote desktop to login to Linux from Windows? One which works - there are various "solutions" which don't seem to work properly, as you can see in my recent rant: > **jom2000 said:**
> here

I've learnt quite a lot about Linux by trying to make a remote desktop work properly.

---

### Post by Mike'sHardLinux on 2007-02-17
Actually, a web server is likely to be the most useful thing you could set up, especially when used in conjunction with a database server like MySQL.

For example, an asset management system could/would likely be web-based. For that matter, any multi-user or single-user app that wants a database back end could be web-based.

What's the point of a VNC server? I mean, VNCing into a server that doesn't do anything else would be pointless. VNCing into a web server could have some uses. VNC is incredibly easy to set up. There's how-tos all over the net. So I doubt you will learn a whole lot about servers from doing that. (I am not saying don't set up VNC. But a VNC server wouldn't be nearly as useful as other services...in fact it'd be virtually useless without other services.)

I highly recommend setting up a standard LAMP server. You'd be surprised of all the things a web server can do. If you use Webmin, which *requires* a web server, you can do just about all server operations from a web browser - user/group administration, software package install/uninstall, stop/start services, configure services, etc.....

For me (and the company where I work), the most useful services have been web server/database server and file server; and in that order of usefulness.

---

### Post by elst on 2007-02-18
I'd agree with the previous poster - Web applications can be very useful, and are easy to deploy. HTTP and DB services aren't very interesting in themselves without an application to use them, but  there are buckets of Open Source Web applications, and you can get many of them from the Ubuntu repos.

FWIW, the Web application that I would most liked to have deployed when working in support was actually a Wiki. Specialized asset management and trouble-ticketing applications only become useful when people change their workflow to put data into the tracking systems, but you can use a Wiki to start building a useful documentation set within minutes. Since it's Web-based you will be able to access and update the notes, links, attached files etc. held on the Wiki from any networked system that isn't totally busted. The process of adding to a Wiki is also so much simpler than writing docs the usual way that it doesn't feel like a chore.

---

