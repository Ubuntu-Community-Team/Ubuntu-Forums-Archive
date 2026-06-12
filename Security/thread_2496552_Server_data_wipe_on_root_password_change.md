---
title: "Server data wipe on root password change"
date: 2024-04-03
forum: Security
---

### Post by nvkedvkem on 2024-04-03
Hi! Is there any way to setup server full data wipe on  root password change attempt? 
I have my own product which i sell and do not want anyone to see what is inside, so i do not let customers have root access to server, but i know that someone can just reset root password. 
Please if you know the way, help me.

---

### Post by TheFu on 2024-04-03
> **nvkedvkem said:**
> Hi! Is there any way to setup server full data wipe on  root password change attempt? 
I have my own product which i sell and do not want anyone to see what is inside, so i do not let customers have root access to server, but i know that someone can just reset root password. 
Please if you know the way, help me.

Is the software not compiled?

If you do not use FDE with LUKS and only provide the LUKS password to the user's login, they will always be able to bypass anything you setup.

However, if FDE is used, backups are mandatory, since any small issue in the wrong part of the disk can make the system totally locked up and inaccessible.  Data recovery tools don't work with FDE. Backup are the only method.

BTW, you can setup all sorts of methods to do what you are suggesting, but I don't feel comfortable helping to create a closed system when F/LOSS has done so much for me over the decades.  

At a place I worked, we would install enterprise software from our company onto the client's server farm. That could be 1 system or 10 servers and thousands of clients.  Some of the software we used had licenses that limited the number of concurrent users, but didn't enforce it. Most of our customers wanted us to enforce the license using a license manager, though customers in 1 specific region of the world hated the license manager, because it meant they were restricted in some way.  Due to the requests, I got to select and implement license management.  I choose FlexLM at the time. 

The worried company never came close to using all their purchased licenses concurrently, but the idea of a restriction didn't make them happy.  Anyway, you can implement a license manager - there are commercial versions that can be integrated, or I suppose, though I haven't looked, there might be F/LOSS implementations.  Yep, google found some free, if not F/LOSS options. 

Anyway, those are some options and thoughts.  I'd suggest FDE - full drive encryption - as the best option. And don't give their user sudo rights.  Ubuntu doesn't enable the root account by default, so if you've done that, you've already broken that part of the security.  If you must provide sudo for specific needs, lock that down.  The sudoers file is very capable. Regardless, without FDE, anyone can boot from a Try Ubuntu flash drive and do whatever they want.

---

### Post by currentshaft on 2024-05-14
it r

---

### Post by TheFu on 2024-05-14
Anyone with a Linux distro on a USB flash drive can gain access outside the system you installed, so the root password is meaningless.  99% of the world will never look.  

Software developers often assume people are out to steal their stuff, which just isn't the case, unless it is a competitor. 

Learn from the guys invited into MSFT who had made a APT-like package management system,  AppGet, for MS-Windows.   [https://www.thurrott.com/windows/windows-10/235783/appget-creator-says-microsoft-stole-his-product](https://www.thurrott.com/windows/windows-10/235783/appget-creator-says-microsoft-stole-his-product) has the story. Anyway, don't do that.

---

