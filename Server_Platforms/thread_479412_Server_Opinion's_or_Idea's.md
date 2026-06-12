---
title: "Server Opinion's or Idea's"
date: 2007-06-20
forum: Server Platforms
---

### Post by blmartin777 on 2007-06-20
I am setting up some servers and had some general questions. 

1) Is it a good idea to keep a web server separate from a email server separate from a ftp server and so on, or is running them on the same server no big deal? 

2) How much space on a hard drive does a average webpage take up?

3) Is webmin the best config tool out right now or is there better? I have read about ISPconfig (What are your thoughts of ISPconfig?) but if I separate the servers that wouldn't work I don't think. 

Thanks

---

### Post by blmartin777 on 2007-06-20
bump

---

### Post by blmartin777 on 2007-06-20
I actually have another question know also that I thought of.

Is xen stable? Stable enough to run on a live server?

Thanks

---

### Post by chris.zeman on 2007-06-20
Hi,

I run a server at home and at work. Running all your services on the same machine won't give you any trouble so long as you have adequate resources available (CPU, RAM, hard disk space). Linux doesn't require nearly the amount of resources that Windows does. You can get away with a fairly modest machine, but I guess it depends on your situation. You didn't mention what your servers will be doing. :)

There is no such thing as an average web site. What will the site contain? You also mentioned an FTP server. What will be available on your FTP site? That is a major factor to consider in determining what size hard disk you'll need. If you're like me, you'll need a fairly large drive to hold all the email you retain. I have e-mails saved from almost 3 years ago. lol Hard disks are so cheap now that you might want to consider installing a couple of 160GB drives and mirror them so you have a hot backup.

I have found the Webmin is the best configuration tool for my situation. I don't have multiple domain names resolving to my servers either, though. Will you? Are you planning on hosting multiple sites? Do you want your users to configure email accounts and such themselves? I don't know if Webmin will allow you to restrict others to specific domains or not, but ISPConfig will. 

There are lots of questions you need to ask yourself about what you want to accomplish. What is your mission and which tools will do what you require? I would write everything down, and then read the documentation for the various control panels available so you can make an informed decision.

Good luck!
Chris

---

### Post by blmartin777 on 2007-06-20
I am very impressed with ISPconfig, so I think I will be looking at that. The main purposes of the server will be mainly web and email but will branch out as I go on. I will have multiple domains.

I have one 500GB hard drive and a 80GB hard drive. I haven't dealt with mirroring but do I have any options with what I have? Could I do that with xen?

Is xen a stable choice? is it reliable?

Thanks

---

### Post by chris.zeman on 2007-06-21
I haven't dealt with mirroring yet myself, but will be attempting it here very soon. I think you'll have a great setup with the hard disks you have. I have a 40GB drive in my server that Linux uses, and then a 160GB drive that I moved /home to and also contains my SAMBA shares.

I've never messed with Xen, so I don't have an opinion on it. I am quite happy with Ubuntu. I decided on Ubuntu after having tried many difference Linux distros, including Debian. I am also impressed the Ubuntu community. I have never seen such a great support community. 

There are excellent guides in these forums and on other sites, such as [http://howtoforge.com](http://howtoforge.com), that will guide you in setting up your servers should you decide on Ubuntu or another flavor of Linux.

Chris

---

### Post by Aberrix on 2007-06-21
I've been using ISPConfig for the past 6 months along with the Ubuntu 6.06LTS 'the perfect setup' and I would never us anything else. imho, anything you can do in webmin you can do from the command line.

---

