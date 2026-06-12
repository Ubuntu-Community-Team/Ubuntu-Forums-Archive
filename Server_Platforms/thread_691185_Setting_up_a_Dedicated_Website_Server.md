---
title: "Setting up a Dedicated Website Server"
date: 2008-02-08
forum: Server Platforms
---

### Post by Closetheloop on 2008-02-08
Hi

I am starting the process of setting up a dedicated website server for the first time. I am a Windows user and my experience is primarily in Marketing and Sales...but I do have HTML, PHP and some MySQL experience.

The datacentre that I will probably use provides a range of OS options but my gut feeling is to go with a good version of Linux. They mentioned Debian but my research then found that Ubuntu would be a good choice.

I have now seen that 7.10 does not have LTS and will be supported until 2009. My objective is to have a good stable server that I don't have to muck around with for a year or two...my questions are:

1) will a new LTS release be announced anytime soon?
2) should I just go with the 7.10 LAMP installation and try to upgrade when no longer supported?

Thanks

Closetheloop

---

### Post by PmDematagoda on 2008-02-08
Moved to the Servers & Security section.

---

### Post by comandrei on 2008-02-08
1)Ubuntu 8.04 will be LTS.
2) You can install the server separatly with:
```

sudo aptitude install apache2 php5 php5-gd php5-mcrypt phpmyadmin mysql-server-5.0
```

---

### Post by PmDematagoda on 2008-02-08
> **Closetheloop said:**
> 
1) will a new LTS release be announced anytime soon?


Yes, Ubuntu 8.04(Hardy Heron) is currently under development and is expected to be released on April this year.

---

### Post by Dr Small on 2008-02-08
1) The next LTS version is 8.04 (the next version)
2) I have never used a LAMP install, but I do use it's cousin XAMPP, which has Apache / Php / MySQL / PhpMyAdmin, and it is very simple plus easy to install.

---

### Post by Closetheloop on 2008-02-08
Great, thanks for your quick replies...I reckon my best plan is to wait for the next LTS version 8.04 (the next version) due in April.

In the mean time I'll load a copy of 7.1 onto an IBM Thinkpad I have and learn about the XAMPP installationl.

BTW I see there are 'Thanks' fields for users. How do I get to them.

Cheers

Closetheloop.

---

### Post by Closetheloop on 2008-02-08
Also do you know the URL to get the download for 7.10 XAMPP?

Cheers

---

### Post by 3dcandy on 2008-02-08
Apache friends look after XAMPP. I would have thought that installing a lamp serverstraight from source would work just as well as a XAMPP installation, nearly all the parts installed can be easily installed via adept or other package handlers...

during installation you can specify a lamp installation if you wish. I have ubuntu x64 edition here, and it has been great to get working, and I have had no real problems with it at all. I used xampp on a windows box, and that was a great timesaver, but I'm not so sure on Linux...

---

### Post by Dr Small on 2008-02-08
Here is my tutorial on how to setup XAMPP:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

---

### Post by jd65pl on 2008-02-09
Here is a tutorial on settingjup LAMP
[http://jamiedumbill.com/index.php?page=37](http://jamiedumbill.com/index.php?page=37)

---

### Post by The Titan on 2008-02-09
i use a LAMP server, im not sure really what a XAMPP is but i intend to find out.  
BTW.  Do thanks by the little star next to the "quote" button in a post!

---

