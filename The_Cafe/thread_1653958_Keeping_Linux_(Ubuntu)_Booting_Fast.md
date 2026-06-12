---
title: "Keeping Linux (Ubuntu) Booting Fast"
date: 2010-12-27
forum: The Cafe
---

### Post by tekkidd on 2010-12-27
Hi, I just wrote an article on how to keep linux booting fast. Any comments or suggestions would be appreciated [HTML]http://tekkidd.tumblr.com/post/2487356742/5-ways-of-keeping-linux-boot-times-down[/HTML]

---

### Post by earthpigg on 2010-12-27
[clickable link]("http://tekkidd.tumblr.com/post/2487356742/5-ways-of-keeping-linux-boot-times-down")

[http://tekkidd.tumblr.com/post/2487356742/5-ways-of-keeping-linux-boot-times-down](http://tekkidd.tumblr.com/post/2487356742/5-ways-of-keeping-linux-boot-times-down)

---

### Post by cariboo on 2010-12-27
You've got some mistakes on the page: 

the command to clean out archived packages is:

```
sudo apt-get clean
```

using the **clear** gives you and invalid command error.

Installing webmin just to find running services is wrong, just go to System->Administration->System Monitor->Processes, to see what is running. To disable programs at startup go to System->Administration->Startup Applications.

---

### Post by tgalati4 on 2010-12-27
My boot times are irrelevant because my machine is up for several months at a time.

tgalati4@tubuntu2:~$ uptime
 17:39:55 up 184 days,  4:08,  3 users,  load average: 0.00, 0.00, 0.00

This is a Dapper Drake (6.06) desktop that is running several services.  Boot time is dog slow, but I only reboot a couple of times a year.  It's been running continuously since, well 6.06.

---

### Post by psusi on 2010-12-27
> **tgalati4 said:**
> My boot times are irrelevant because my machine is up for several months at a time.

tgalati4@tubuntu2:~$ uptime
 17:39:55 up 184 days,  4:08,  3 users,  load average: 0.00, 0.00, 0.00

This is a Dapper Drake (6.06) desktop that is running several services.  Boot time is dog slow, but I only reboot a couple of times a year.  It's been running continuously since, well 6.06.

So you are running a poorly functioning and badly insecure system?  You really should upgrade to a release that is still supported and gets security fixes.

---

### Post by foxmulder881 on 2010-12-27
> **tgalati4 said:**
> My boot times are irrelevant because my machine is up for several months at a time.

Yeah I've learned to use suspend lately. I only reboot after kernel updates.

---

### Post by tekkidd on 2010-12-27
Thanks for that, thank god for tumblrs ability to edit published posts
> **cariboo907 said:**
> You've got some mistakes on the page: 

the command to clean out archived packages is:

```
sudo apt-get clean
```

using the **clear** gives you and invalid command error.

Installing webmin just to find running services is wrong, just go to System->Administration->System Monitor->Processes, to see what is running. To disable programs at startup go to System->Administration->Startup Applications.

---

### Post by tgalati4 on 2010-12-27
I though Dapper might be insecure, but you know, it still gets updates!!

And that requires me to reboot every 6 months whether I need to or not!!

---

### Post by earthpigg on 2010-12-27
what'cha use the 6.06 system for?

where do you get your updates from?

---

### Post by marshmallow1304 on 2010-12-27
> **tekkidd said:**
> http://tekkidd.tumblr.com/post/2487356742/5-ways-of-keeping-linux-boot-times-down

I have serious doubts about the claim made in (2) (not to mention that I consider going outside the repos like that foolish in terms of security and stability) and (3) is Ubuntu/Debian specific (also: there/their).  Maybe the title should be "4 Ways of Keeping Ubuntu/Debian Boot Times Down".

---

### Post by NightwishFan on 2010-12-28
Ubuntu Dapper is still supported by Canonical on servers:
[http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)

---

### Post by Megaptera on 2010-12-28
To tekkidd 

(1) The "Guide" says (quote) ") Go portable instead of installing, one of the reasons computer boot times go up is because people install to many apps from the repos, using portable apps will keep boot times down." Unless these apps are running at startup - which is easy to prevent - how does this help?

(2) Again from the "Guide" (quote) "Run bleachbit, Windows has CCleaner to stay clear of crap and linux has bleachbit. Running it will remove many things bloating your home directory."  
Firstly, Bleachbit needs to be used with caution by newbies such as me 'cos its default settings can be quite aggressive.
Secondly you say "Running it will remove many things bloating your home directory." Such as what & how do these "things" slow a system?

Thanks for clarifying.

---

### Post by NightwishFan on 2010-12-28
They do not. I have my 300gb disk nearly full and I do not have any slow downs. Bleachbit is mostly useful for privacy. I agree with avoid not needed packages that have daemons though.

---

### Post by nhianho on 2010-12-28
I'm a newbie and I hope the OP will answer me some questions.

In the first tip, you talked about the programs that run on boot. But seriously, how can a newbie like me tell which programs will run on boot and which ones will not?

Secondly, you said that installing apps in the repo will slow down the booting but I heard that it's always better and safer to use apps in the repo. Or is it wrong?

---

### Post by mysteriousdarren on 2010-12-28
nhianho, 
to check the programs that will run on boot go to System>Preferences>Startup Applications. Uncheck the unimportant ones to make it boot faster. If you do not use a bluetooth then switch it off, same goes for remote desktop, and several others. This will decrease the boot-time. 2nd installing apps in the repos is more stable and usually includes older versions than what is available online. If you want to boot from usb very little will change and things will be pretty consistent for boot-times. I would just install and go from there. If you want to continue to try it out use the usb or live-cd, but for the full experience install it. good luck.

---

### Post by K.Mandla on 2010-12-28
If you're willing to get your hands dirty, there is quite a bit more you can do to speed up an Ubuntu boot.

[http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/](http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/)

Granted, that's a little old, but most of what's there will still apply.

---

