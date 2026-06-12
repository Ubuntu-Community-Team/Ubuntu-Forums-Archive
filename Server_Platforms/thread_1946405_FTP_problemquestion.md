---
title: "FTP problem/question"
date: 2012-03-24
forum: Server Platforms
---

### Post by NateC16 on 2012-03-24
Hey guys, I was wondering if I could get some help with FTP, atleast I'm pretty sure it has to do with FTP.

Now, for fare warning, I'm no ubuntu dominator, I'm pretty newb. Anyway, I've attempted to build a webserver to to test php and what not for a site I'm building. Now everything works, the php, the sql etc. 

By the way, I built this in VMware, so it's virtual, over a network, so I can access stuff from anywhere. I'm in a college right now so yeah. 

The one problem I have is this. I go into the terminal, and do ifconfig to find my IP. I get it and go to a browser on a different machine and type that IP in. I get the "index of/" page, where I can browse the website I'm making. I can click through folders and what not. I can click on things and they open up. 

Now lets say I'm working on my desktop and open up an FTP and drag and drop something into there, go to the IP in the browser again and try to open it. I either get 

"Server error
The website encountered an error while retrieving [http://10.15.6.110/phpinfo.php](http://10.15.6.110/phpinfo.php). It may be down for maintenance or configured incorrectly.
Here are some suggestions:
Reload this webpage later."

or "Forbidden

You don't have permission to access /html.html on this server."

But, lets say I make it on the server itself, and try, bam, magic it works. 

I'm sure I set the permissions to let everyone open and view the files, but maybe I didn't? I'm not sure, and this is where I was hoping I could get some help. 

By the way, I followed a tutorial on changing the www folder (apache) from /var/www to home/"user"/www. I can't recall how I did that, but it's there and my ftp goes to the home/"user"/www folder. 

But yeah, any and all help is appreciated. Like I said, I'm really new to this, but I do enjoy attempting to make these servers and learning how they work, so it's not like making this webserver is a project for a class, It's just assisting me in testing stuff for another class and possibly other websites later on down the road. 

Anyway, anyone who decides to help, thanks so much, I'd really appreciate it. 

Nate.

P.S. I'm using Ubuntu 11.10 desktop edition with a LAMP server

---

### Post by Hank_The_Dog on 2012-03-24
Nate,

Have you tried the chmod command?

---

