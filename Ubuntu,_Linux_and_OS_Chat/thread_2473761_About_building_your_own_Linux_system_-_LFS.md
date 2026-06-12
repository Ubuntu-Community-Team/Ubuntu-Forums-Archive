---
title: "About building your own Linux system - LFS"
date: 2022-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by satimis on 2022-04-12
Hi all,

Welcome to Linux From Scratch!
[https://www.linuxfromscratch.org/](https://www.linuxfromscratch.org/)

Has any folk on the forum recently building his own Linux system - Linux From Scratch (LFS)?  How long will it take on a recently PC?

I have tested building it long long time ago on a single-core PC.  I started my computing on Windows -> Free BSD -> Unix -> Linux.  The 1st Linux system run by me was Red Hat.

It took me 5 days and nights continuously to finish building my own Linux system (Linux From Scratch) on a single-core PC.  The building was fully automatic, just switching on the PC.  I can go to sleep and have to check the PC at night after going to wash room.  The PC will halt if needing me to input -> my own selection on how the Linux system being built.

After finishing building there was only one Text Editor available.  I have to continue building web browsers, office editor, photo editor and other packages etc. for daily application.  LFS is a very rigid Linux system.

I'm interested test-building LFS on a AMD 12-cores PC.  Please shed me some light.

Thanks

Regards

---

### Post by grahammechanical on 2022-04-13
Years ago I choose Ubuntu because it had the reputation of it being for  the ordinary user who did not have or need to be educated about Linux. I  now have a lot of experience of installing and using Ubuntu and an  increased knowledge of Linux. I am thankful for this forum and the  Ubuntu wiki for educating me.

I am not interested in build it  myself Linux. Although I have done build it myself machines. If I was  you I would be concerned about hardware drivers. I recently purchased a  laptop with Ubuntu 20.04 pre-installed. It had an OEM Linux kernel. I  was concerned that when I upgraded to 22.04 some hardware drivers would  not be available in the Ubuntu generic kernel.

So, I installed  Ubuntu 22.04 (development) and there are no problems. It seems that when  an OEM patches the Ubuntu kernel to make sure all the hardware works,  then in time those patches get absorbed into the official Ubuntu generic  kernel. The kernel on this machine has been upgraded several times  since I purchased the machine and everything is still working even  though the OEM kernel is no longer being used.

So, I ask how do  the developers of Linux From Scratch deal with the need for hardware  drivers? Do they rely on the Linux developers to sort out new hardware  drivers? 

Regards

---

### Post by satimis on 2022-04-18
> **grahammechanical said:**
>  - snip -

So, I ask how do  the developers of Linux From Scratch deal with the need for hardware  drivers? Do they rely on the Linux developers to sort out new hardware  drivers? 


It just builds the core of the Linux system, others to be added/download on Internet.

The core is very important.  Your LFS system won't be easily hacked because hackers don't know how you build/configure the core of your Linux system.  For the read-built Linux system the hacker can download it to check/analysis.

Besides you would only include the packages used by yourself.  The ready-built Linux system includes some packages which you never use in your life-time.  So your LFS system is light-weight, easy to boot and quick to operate.

Once you have tried building your own LFS system you would recognize the advantage.  What would I mostly concerned is its building time.

I'll ask my question on LFS mailing list.

Regards

---

### Post by mIk3_08 on 2022-04-18
> **satimis said:**
> It just builds the core of the Linux system, others to be added/download on Internet.

The core is very important.  Your LFS system won't be easily hacked because hackers don't know how you build/configure the core of your Linux system.  For the read-built Linux system the hacker can download it to check/analysis.

Besides you would only include the packages used by yourself.  The ready-built Linux system includes some packages which you never use in your life-time.  So your LFS system is light-weight, easy to boot and quick to operate.

Once you have tried building your own LFS system you would recognize the advantage.  What would I mostly concerned is its building time.

I'll ask my question on LFS mailing list.

Regards
I Agree with this. When you already have the core and knows the basic on building your own Linux System. This has a big advantage. Almost all others tools to be added is already available on the internet. Linux core itself is already the core of a secured machine. When you decide to choose to build it, Its the symbol of security in terms of web. Regards and cheers.

---

### Post by satimis on 2022-04-18
> **mIk3_08 said:**
> I Agree with this. When you already have the core and knows the basic on building your own Linux System. This has a big advantage. Almost all others tools to be added is already available on the internet. Linux core itself is already the core of a secured machine. When you decide to choose to build it, Its the symbol of security in terms of web. Regards and cheers.
Hi,

One of the advantage building your own core:-

Hackers are most interested on wp-login.php, to take control of your website.  They would use BOT to attack it continuously.

I can,
either
relocate wp-login.php to another location

or
rename wp-login.php to some-obscure-name.php

My major intention building LFS is to learn.  In the past, I built LFS only once, on a single-core PC.  

I have about 36 websites running on Internet, hosted on a Hosting company and subscribing shared hosting.  I'm not allowed to build my own Operating System on their server, unless renting a Blade Server.

I have their cloned sites running on local server, serving as back-up.  In case a live-site goes into problem for whatever cause, I just clone the respective site on local server to replace it.  It is very convenient.

I'll build LFS system on my local server.

My major concern is the approximate time in building LFS, not 5-days and 5 nights again.

compiling is time consuming, such as;
/lib/libc.so.6
/usr/bin/ld
/usr/bin/gcc
/usr/bin/startx
etc

Regards

---

### Post by mIk3_08 on 2022-04-19
> **satimis said:**
> Hi,
One of the advantage building your own core:-
Hackers are most interested on wp-login.php, to take control of your website.  They would use BOT to attack it continuously.
I can,
either
relocate wp-login.php to another location
or
rename wp-login.php to some-obscure-name.php
Regards

Wordpress... It can be done thru php for this. in some cms I uses htacess for this redirection. it was very easy and safe with 256bit security. I am more comfortable using htaccess for this. Regards and cheers.

---

### Post by satimis on 2022-04-19
> **mIk3_08 said:**
> Wordpress... It can be done thru php for this. in some cms I uses htacess for this redirection. it was very easy and safe with 256bit security. I am more comfortable using htaccess for this. Regards and cheers.
Hi,

Whether following 2 documents are relevant ?

1)
How to Fix WordPress Login Page Refreshing and Redirecting Issue
[https://www.wpbeginner.com/wp-tutorials/how-to-fix-wordpress-login-page-refreshing-and-redirecting-issue/](https://www.wpbeginner.com/wp-tutorials/how-to-fix-wordpress-login-page-refreshing-and-redirecting-issue/)

2)
How to use .htaccess to secure wp-login.php and /wp-admin on WPMU WordPress
[https://wpquestions.com/How_to_use_htaccess_to_secure_wp_login_php_and_wp_admin_on_WPMU/8863](https://wpquestions.com/How_to_use_htaccess_to_secure_wp_login_php_and_wp_admin_on_WPMU/8863)

Regards

---

### Post by bobgrjr on 2022-04-20
Nice catch, satimis! Thanks for sharing.

---

