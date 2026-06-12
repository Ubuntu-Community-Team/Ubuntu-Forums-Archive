---
title: "Dedicated server"
date: 2007-10-06
forum: Server Platforms
---

### Post by codeking on 2007-10-06
A church in my town is planning on making a website and getting there own dedicated server.  Can you just take a normal computer, install Ubuntu Server on to it, and connect it to a normal internet connection?

Also, I've always avoided 64-bit OS's because not much software supports them.  But if all I'm going to be installing on it is Ruby on Rails and MySQL, will having Ubuntu Server 64-bit improve the performance?

---

### Post by elvis on 2007-10-06
> **codeking said:**
> A church in my town is planning on making a website and getting there own dedicated server.  Can you just take a normal computer, install Ubuntu Server on to it, and connect it to a normal internet connection?
Absolutely.  But do make sure you take adequate care to secure the system.  Don't use simple/default passwords, and firewall any ports you don't need.  Also make sure you include the Ubuntu security repos in your sources.list and keep on top of security releases.

> **codeking said:**
> Also, I've always avoided 64-bit OS's because not much software supports them.  But if all I'm going to be installing on it is Ruby on Rails and MySQL, will having Ubuntu Server 64-bit improve the performance?
Generally speaking, the lack of 64bit support affects desktop users far worse than server users.  Third party / closed source drivers are the biggest pain (you are at the whim of the device manufacturers to support your distro and release - for example, some wireless drivers).  Additionally things like desktop Adobe/Macromedia Flash players and plugins.

For server users, these things are rarely an issue.  Most servers have hard-wired ethernet devices (the vast majority of which are supported via free drivers inside the linux kernel).  Likewise, any applications like the Linux kernel itself, MySQL, PHP, Ruby, etc all got 64bit support eons ago thanks to AMD opening the x86_64 specs early on, and the free/open nature of Linux.

Will 64bit give you better performance?  That depends.

32bit addressing can only "see" 4GB of information in a single area (2^32 = 4 billion and a bit = 4GB).  

If you need any sort of data storage/retrieval system that requires access to numbers that are bigger than this (say, very high-end databases, or servers with more than 4GB of physical memory installed), then 64bit will give you a boost (assuming you use all of those resources within one process).

For your average web server, the answer is no.  It's highly unlikely that unless you run an eBay/Amazon.com size operation that 64bit will be necessary for you.  Most websites/servers will have databases and RAM much smaller than that. :)

With that said, Linux development (well, the kernel at the very least) is primarily focusing on 64bit development, and likewise 32bit hardware will be becoming rarer and rarer as time goes on.  At a server level (especially just a simple LAMP [Linux Apache MySQL PHP/Perl/Parser] server) there is no penalty going 64bit.  If your hardware supports it, there's no reason to avoid it.

---

### Post by codeking on 2007-10-06
thanks, elvis.  I new to linux (but I've almost completely transfer from Windows), so how do I do those things you were talking about, like firewalling the ethernet port and adding security updates to sources.list?

---

### Post by HermanAB on 2007-10-06
The most important thing is to add an uninterruptable power supply and once the system is working - to Leave it Alone.  Most Linux problems are caused by finger trouble and bad updates.  Update it once a year, with the latest Ubuntu system.

Also use long passwords of at least 9 characters. (Common brute forcers use 8 character dictionaries.)

Cheers,

Herman

---

### Post by MJN on 2007-10-06
> **HermanAB said:**
> The most important thing is to add an uninterruptable power supply and once the system is working - to Leave it Alone.  Most Linux problems are caused by finger trouble and bad updates.  Update it once a year, with the latest Ubuntu system.

Once a year? If an applicable critical security update needs doing it needs doing, whenever that might be.

Or were you referring to updating the distribution to a new release? Even so, I'd recommend sticking to the LTS (Long Term Support) releases (e.g. Dapper 6.06 now, and Hardy when it comes out ~Apr '08 as they are ultra-reliable and supported for longer than the 'standard' releases.

> Also use long passwords of at least 9 characters. (Common brute forcers use 8 character dictionaries.)

The key to strong passwords (against dictionary attacks) is not so much the length but choosing passwords that aren't in a dictionary...

Mathew

---

### Post by Catsworth on 2007-10-06
> **HermanAB said:**
> [...]once the system is working - to Leave it Alone

[...]

Update it once a year, with the latest Ubuntu system.

[...]

.....and that's why so many servers get hacked.

Securing a server is not a 'fire and forget' process.  If a patch appears for any application on the server it should be tested (on a seperate, but identically configured, box to make sure it is compatible) and then it should be installed on your live server as soon as possible.

Doing anything other than that is reckless, flawed, and utterly unforgiveable.

---

### Post by Catsworth on 2007-10-06
Oh yeah.....

'Brute Forcers' don't use dictionaries, they try every conceivable combination for a given character set.  'Dictionary Attacks' use dictionaries. 

Given the above, it shouldn't take much to work out that the wider the character set you use (and the greater the number of characters you employ) the better your password.

Ideally you should choose a selection of characters including some from all of the following sets:

a-z
A-Z
0-9
Special Characters (!"£$%^&*:@{}~><?)

As a minimum length I'd agree on somewhere between 8 and 10 characters.  I'd also agree that you should *never* use a dictionary word, from any language, and no matter how well you think you've disguised it (@dministrat0r, p@$$word, s£rv£r, s3cur1ty - all *very* naughty, bad admin!).

All of the above being said, you may want to tailor the length/complexity of your passwords according to the accounts they are for.  Your root /administrative account(s) should have more complex accounts than those for your non-privileged users and you may want to make passwords for these special accounts even longer (15 characters is a good length ;)  ).

---

### Post by netlogic on 2007-10-06
1. set a cron job update once a day during the night to download all the patches. try to stick to supported applications by ubuntu before using universal, multiversal, commercial, etc. 
2. DON'T USE PASSWORD. Use a private/public key with a LONG passphrase
Why do you bother if someone can brut force or not? If you must use password, combine your ssh port with fail2ban, and change your password every 30days.. Also, change your keys if your home folder isn't encrypted. In case someone steals your key by physically accessing your machine

---

