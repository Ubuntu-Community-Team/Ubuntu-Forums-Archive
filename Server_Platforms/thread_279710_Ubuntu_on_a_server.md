---
title: "Ubuntu on a server"
date: 2006-10-18
forum: Server Platforms
---

### Post by idowindows on 2006-10-18
Hello,

Noob to Ubuntu.

I work for a school district - we have a number of servers not in use.

If I was to install Ubuntu on a server for deployment, What benefit would this have in our educational environment?

I need a reason for my boss.

What benefit will the kids have by accessing this server?

Will I then have to install Ubuntu on PCs to access this server?  

What can Ubuntu-based server do to benefit our kids.

Thanks in advance.

---

### Post by dcherryholmes on 2006-10-18
> If I was to install Ubuntu on a server for deployment, What benefit would this have in our educational environment?

This is a question that deserves a much longer answer.  I suggest some Googling, since there are many articles that have been written on this subject.

> What benefit will the kids have by accessing this server?

They will learn something in addition to windows.  They should understand computing fundamentals, as opposed to the common misunderstanding that "Word == text document".  They will also benefit by the (practically) complete absence of malware.

> Will I then have to install Ubuntu on PCs to access this server?

Certainly not.  You haven't really said what you mean by "server", but you can run email, web, and ftp servers in linux and access them with clients on a Windows PC.  This is sort of contra to my answer above, as a transparent linux environment, but it's really up to you.

> What can Ubuntu-based server do to benefit our kids.

Free up the money you piss away towards Redmond for an inferior product year after year, allowing it to be used for soccer balls and pencils.

---

### Post by Jussi Kukkonen on 2006-10-18
> What benefit would this have in our educational environment?
You are in the best position to answer that, since you know what your requirements are.

> Will I then have to install Ubuntu on PCs to access this server? 
Probably not, but that depends... What is the server supposed to do? If it's a samba file server, then kids can just access the files from windows. The same goes for an e-mail server: kids just use whatever email programs you provide on whatever platform you provide... 

You may want to look at edubuntu: [http://www.edubuntu.org/](http://www.edubuntu.org/), if you're looking for clients too.

> I need a reason for my boss.
No offence, but why do you feel you need to get a ubuntu server if you don't know what you would use it for? 

Any changes in IT infrastructure should be done by people with the needed skills -- otherwise you'll end up with broken systems that do the wrong things even when they're not broken... That being said, it's great that you are interested in free software: kids should be shown something else than the windows monoculture once in a while, and free software could mean savings (but it too needs proper administration, it's not without costs). I'm sure the edubuntu site will give you some ideas.

---

### Post by peanut butter on 2006-10-18
i could see using ubuntu with samba as a Domain Server or File server. As far as for a school you might find schooltool helpful as a calender system. I also agreewith the earlier poster that edubuntu would help you depending on what you want to do with the server. If you have some idea of what you want to use ubuntu for please reply and we can help you better.

---

### Post by IYY on 2006-10-18
My answer in this thread: [http://www.ubuntuforums.org/showthread.php?p=1629819#post1629819](http://www.ubuntuforums.org/showthread.php?p=1629819#post1629819)

---

### Post by Chayak on 2006-10-18
The easiest way to do it is in small steps.  Start with something simple such as a file server then give everyone time to get use to it then slowly change over other things.  It'll save money in the long run that can be used for IT improvement rather than software licenses.

---

### Post by idowindows on 2006-10-18
I do suppose the cost of licensing (Ubuntu for servers IS free, right?) might be a good incentive to at least get them on my side...

Hmmm.......

---

### Post by Chayak on 2006-10-18
Yes it's free and your support group is right here.  The biggest savings by far is you don't have to by CALs to access it, in addition to the server being free. ;)  If you want something more cost effective than windows and very easy to manage I'd look into Nitix.  It's not free but it's a turnkey solution that runs linux.  I really wish someone would put that kind of management interface on ubuntu server.

---

### Post by Iowan on 2006-10-18
> **IYY said:**
> My answer in this thread: [http://www.ubuntuforums.org/showthread.php?p=1629819#post1629819](http://www.ubuntuforums.org/showthread.php?p=1629819#post1629819)
Mine too. (My bad - I'm the one who suggested the Servers forum... but I didn't mean BOTH!!:mrgreen: )
I will add that if the servers are unused, and the software is free, the resistance to a testbed server *should* be minimal.  The only investment will be your time.
You could use the aforementioned LAMP (Linux,Apache,MySQL,PHP) server to allow students to create their own web pages (without actually exposing their product to the world). 
What features a(n) Ubuntu server could provide also depends on what services currently exist on your network.  It could be a mail server if you don't already have one. It could do DHCP - but I suspect your network already has one.

---

