---
title: "Installation of Apache 2.2.15 on Ubuntu server 10.04"
date: 2012-07-23
forum: Server Platforms
---

### Post by robertdbuckley on 2012-07-23
Hi,
I have been told I need to install inteproxy ([http://inteproxy.wald.intevation.org/index.html](http://inteproxy.wald.intevation.org/index.html)) on my 10.04 Ubuntu server. The software requires apache 2.2.15 which is only available from Ubuntu maverick 11.04. I had a look at the messages when I type "apt-get install apache2" after updating my sources.list file with "deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) maverick main" and php5 gets updated with 2 new files and the old ones will be overwritten....or words to that affect.

My question is....If I upgrade to apache2.2.15 on ubuntu 10.04 and my applications fail to start....can I simply remove the source, deinstall apache2.2.15 and reinstall 2.2.14 and carry on as if nothing had happened....or am I playing with fire?

What would be the best way to go about this?


thanks for any advice,

Rob

---

### Post by drmrgd on 2012-07-23
I don't have a specific answer or complete solution for you.  However, I would definitely say to be very careful here.  I was forced by our IT security staff to upgrade to 2.2.20, and went through the same basic process as you describe (except I used the US archives and not the CZ ones).  The upgrade went well.  However that version of Apache broke other components of the system, and the tech who was working on it managed to hose the entire system in his effort to revert to the old version of Apache (it was a stupid mistake on his part).  

However, upgrading to 2.2.15 might be fine for your purpose and you might find that everything works very well. Just be sure that you have a backup plan to get back up and running quickly if something goes haywire.

---

### Post by TheFu on 2012-07-23
I would start by talking with the developers over at [http://wald.intevation.org/projects/inteproxy/](http://wald.intevation.org/projects/inteproxy/) and [http://inteproxy.wald.intevation.org/index.html](http://inteproxy.wald.intevation.org/index.html) .  This appears to be a very specialized solution.  Join their mailing list. Lurk and ask questions after a few days AND **after** you've read the FAQs.

inteproxy is the hard part here, so that will be the thing that drives the rest of your software stack completely.

---

