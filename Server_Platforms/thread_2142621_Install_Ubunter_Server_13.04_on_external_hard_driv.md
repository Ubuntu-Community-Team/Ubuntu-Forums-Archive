---
title: "Install Ubunter Server 13.04 on external hard drive"
date: 2013-05-06
forum: Server Platforms
---

### Post by Advait on 2013-05-06
Hi All,

Is this the right forum for this q? If not, please move as needed.

I did an internet search and a search on these forums and didn't find any solutions (let me know if I missed something). I have 12.04 Desktop installed on an external hard drive and its working great. I followed the instructions at 

[http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/](http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/)

Now I want to install 13.04 Server on another external hard drive. Can this be done? If yes, you have link to a good tutorial? The link above is an excellent step by step tutorial; I will need something like that. Vague instructions that assume I know all the in-between detailed steps will be useless for me.

Will the tutorial at the link also work for 13.04 Server?

I want to set up a simple 13.04 Server LAMP stack so I can mess around with creating some simple web pages, and start learning about the basics of Ubuntu Server. That's it.

Thanks!

Advait
Homeward bound...

---

### Post by Ruann on 2013-05-06
Are you running the Machines on a Virtual Machine program like Virtual Box or will you use 2 physical Machines to Run the Operating Systems on ?

---

### Post by Advait on 2013-05-06
> **Ruann said:**
> Are you running the Machines on a Virtual Machine program like Virtual Box or will you use 2 physical Machines to Run the Operating Systems on ?

My hope is to run 13.04 Server just like I run my 12.04 Desktop on an external drive. I plug the drive into a USB port on my laptop. I power up. I hit F12 to bring up the "Boot From" menu. I select the external drive that has 13.04 Server installed. I hit enter. 13.04 Server boots up on my laptop. I log in and have fun.

I could try 13.04 Server in a Windows 7 Virtual Box, but my experience was that 12.04 ran VERY SLOW in my Win 7 VB. I'm guessing 13.04 Server would also run slow.

Does this answer your question? Let me know if you need any more details. Thanks,

Advait

---

### Post by Ruann on 2013-05-06
OK I see, well when run your "boot from" option your laptop searches the drive for any bootable files, so if you have more than one Operating system on there It will show both from your initial screen, Ubuntu Server is the same as Desktop Just that it Lacks the X windows environment. Its only a terminal and you would have to have that server running WITH another Operating system that has a GUI browser (like windows 7 or ubuntu desktop) to view ur websites.   So the only way you can test ur LAMP with Ubuntu Server is with 2 OS alongside one another, whether it be a Virtual Machine or two Computers.

Id suggest you install ur LAMP on the Desktop Version, You would install apache2 and then from there enable whichever modules u need like php

Once you have the server up you can create your sites and have them run on that server  and view them from your local host via A web browser.

Then concerning tutorials and that You can just youtube installing LAMP on Ubuntu Desktop

---

### Post by Advait on 2013-05-07
> **Ruann said:**
> OK I see, well when run your "boot from" option your laptop searches the drive for any bootable files, so if you have more than one Operating system on there It will show both from your initial screen, Ubuntu Server is the same as Desktop Just that it Lacks the X windows environment. Its only a terminal and you would have to have that server running WITH another Operating system that has a GUI browser (like windows 7 or ubuntu desktop) to view ur websites.   So the only way you can test ur LAMP with Ubuntu Server is with 2 OS alongside one another, whether it be a Virtual Machine or two Computers.
* Id suggest you install ur LAMP on the Desktop Version, You would install apache2 and then from there enable whichever modules u need like php
* Once you have the server up you can create your sites and have them run on that server  and view them from your local host via A web browser.
* Then concerning tutorials and that You can just youtube installing LAMP on Ubuntu Desktop

There is no GRUB on my Win7 laptop. Only Win7 and nothing else on the internal hard drive. I only boot and run Ubuntu Desktop from an external hard drive. This setup is working well.

Ahh, ok, It sounds like the LAMP stack will run totally fine on Ubuntu Desktop. Is that correct? If that is correct then I can install VirtualBox in Ubuntu and use that as the 2nd OS to to view the web pages I create. Does that sound OK? The LAMP stack (and the web pages I create) would reside on the host OS and I would view the pages from the guest Ubuntu OS running simultaneously in VBox. That sound correct?

I was under the mistaken impression that the LAMP stack *must* run on a Server (like Ubuntu Server or some other Linux Server distro).

I'm sorry for my newbie questions, but I need to get a correct conceptual overview before I can dive into the details.

Thanks!

Advait

---

### Post by Ruann on 2013-05-07
Yea it will run  on Ubuntu Desktop.

You can do that with the VM but its just unecessary effort.
No need for Virtual machine you just Run ur LAMP stack on the desktop version and  View the websites on the Desktop version as a local host.

If ur Apache2 is running on The Desktop version all you do is go into the Internet Browser and browse "localhost" or "127.0.0.1'' 

Seeing as you running it as a testing environment theres no need for a PC that will Only be a server. 


[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by Advait on 2013-05-08
> **Ruann said:**
> Yea it will run  on Ubuntu Desktop. You can do that with the VM but its just unecessary effort.
No need for Virtual machine you just Run ur LAMP stack on the desktop version and  View the websites on the Desktop version as a local host.
If ur Apache2 is running on The Desktop version all you do is go into the Internet Browser and browse "localhost" or "127.0.0.1'' 
Seeing as you running it as a testing environment theres no need for a PC that will Only be a server. 
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Perfect. Thanks! I just want to play around with the LAMP stack and start learning some of the basics. I don't plan to build a production server or anything like that.

 I'm glad I can do this using Ubuntu Desktop. And I'm glad I don't have to go thru the learning curve for Ubuntu Server (I'll do that later).

Cheers,

Advait

---

