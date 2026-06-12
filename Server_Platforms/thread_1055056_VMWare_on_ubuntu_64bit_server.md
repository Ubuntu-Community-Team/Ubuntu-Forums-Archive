---
title: "VMWare on ubuntu 64bit server"
date: 2009-01-30
forum: Server Platforms
---

### Post by e24ohm on 2009-01-30
Forum,
I am looking at my options in the down turn of the economy, and wanted to know if anyone is running VMware EX server on Ubuntu 64bit or any other server build. If so, what performance level does it perform at for your needs? Any insight, tips, or complants are welcomed, just want to know if this would be the best solution in my  homes labs, and at work.

thank you,
E

---

### Post by Neural oD on 2009-01-30
have u taken a look at virtualbox 
fairly stable too - it's what i use :)

---

### Post by e24ohm on 2009-01-30
> **Neural oD said:**
> have u taken a look at virtualbox 
fairly stable too - it's what i use :)No, i have not checked out virtualbox. I will do a google search on this. thanks.

---

### Post by tomwerner470 on 2009-01-30
It depends what you are trying to get out of Virtualisation, I have had experience of VMWare Server and Virtualbox on ubuntu and  to me the main determinant will be the number of VMs. Virtualbox seems to have more features suitiable for Desktop virtualisation, however, performance wise, there isn't much between them.

The big advantage that vmware has over virtualbox is headless management. To manage virtualbox vms in a headless environment, all the maintenance will have to be done from the command line, whereas VMware gives you a nice web based gui. Depends on what your host is (server or desktop) and what you are virtualising...

If you want any more advice or help on installing either feel free to post...

Regards, Tom

P.S-- What I use each for - 4 x VMware Servers @ work for virtualising approx 20 servers (db, app, web, windows server etc) and Virtualbox for a Windows XP vm (work and home) for anything that can't run under wine and has no linux equivalent :-)

---

### Post by e24ohm on 2009-02-02
> **tomwerner470 said:**
> It depends what you are trying to get out of Virtualisation, I have had experience of VMWare Server and Virtualbox on ubuntu and  to me the main determinant will be the number of VMs. Virtualbox seems to have more features suitiable for Desktop virtualisation, however, performance wise, there isn't much between them.

The big advantage that vmware has over virtualbox is headless management. To manage virtualbox vms in a headless environment, all the maintenance will have to be done from the command line, whereas VMware gives you a nice web based gui. Depends on what your host is (server or desktop) and what you are virtualising...

If you want any more advice or help on installing either feel free to post...

Regards, Tom

P.S-- What I use each for - 4 x VMware Servers @ work for virtualising approx 20 servers (db, app, web, windows server etc) and Virtualbox for a Windows XP vm (work and home) for anything that can't run under wine and has no linux equivalent :-)

I was going to try and run my copy of XP via virturalbox at home. Missing visio for my network graphs. thanks for the insight. I will post if i run into problems, because i am thinking about doing the install this coming weekend. Question: is it better to get a extra drive, and put the OS that Virturalbox will run on a second drive with it's own partition?


cheers!!!

---

### Post by tomwerner470 on 2009-02-02
Virtualbox sounds great for what you need it for (I am a System Designer and can't live without Visio or the MySQL graphical modelling tools :-)) - I don't think there is much performance advantage of using a partition based store for your virtualised OS, I use the single flat file type and it works well for me on my relatively slow laptop hard disk. Additionally, I think you can only get the raw disk passthru/access option with the non-gpl edition - it's still free but you may not want to use it depending on your morals :-).

What I would reccomend though is that you pre-assign your hard drive space (I can't remember the exact option, but it should be obvious in the create drive wizard) - it is supposed to give a sizeable performance boost, however, I have always chosen this option as default so I can't comment the truth on this...

Lastly, having a single file for the OS makes backing up easy (although I don't keep any data on the VM), I just use shared folders and dump it back in my ubuntu docs...

All the best,

Tom

---

