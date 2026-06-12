---
title: "upstart/inittab change - solutions to display messages at system boot"
date: 2009-01-05
forum: Server Platforms
---

### Post by digitalage on 2009-01-05
I'm looking for a way to have a clean boot up process, in terms of displaying.

1. In console, I need to disable the timeout of when the screen becomes blank. I tried changing BLANK_TIME=0 and POWERDOWN_TIME=0 (BLANK_DPMS=on) in /etc/console-tools/config with no success, the screen becomes blank again after a few minutes if no keyboard activity.

2. When ubuntu server edition is first installed, the boot processes is displayed nice ending with the command prompt login. After installing applications (servers/daemons), everything gets messy: newer applications show up on the screen after the command prompt login, and some of them are not displayed arranged each on one line, some are arranged one after another and no lines between. First, I want to have all processes started **before the command prompt **appears. Secondly, I wish there is a simple way to arrange them one at a line as it suppose to be, and correct what developers didn't finish when compiled the source of package. In other words, a config file which allow me to move displaying of a process during boot on the next line, and let me add only the processes I need (from /etc/init.d/ directory). Is this possible?

3. There's also cases when some processes need longer time to start at boot. In this case I'd like to choose **not to have them displayed** on boot before command prompt login show up (because I may have a very slow boot up process), but send this information to the log as a notification so that I know if it started just in case I need to check that later.

I wish I know if it's possible to make all these changes in a separate config file without changing the startup scripts or their links, so that I can easily move the config files to other machines. It could be itself a script made of commands, I don't mind.

Solutions?

---

### Post by digitalage on 2009-01-06
Hmm... not much action here... Or maybe not in the right section...

---

### Post by koenn on 2009-01-06
There is no configuration file for this. 
Processes start during the startup process in the order of the links in /etc/rcX.d where X is the runlevel, or event-driven in the case of upstart. 

The reason the output seems disorganised is because upstart doesn't run scripts in order, but event-driven, so the order can vary.
That's also the reason you can get a login prompt while there are still services starting up (and producing output, which will then be displayed below the login prompt)

I don't know of a way to change all this without modifying the scripts and/or their links and or the contents of /tec/event.d.
I also don't see why that would be necessary. servers usually don't get rebooted that often, so it's a minor issue.

---

### Post by digitalage on 2009-01-06
Thanks for input, koenn.

It may be weired, but the reason I want such things is consistency (I'm a bit paranoid to have things in order) and as a way to learn. I know a server is suppose to work, but I kinda play a lot with ubuntu server edition (that's why I restart it often) and I hardly find things I used to find easily in inittab, with this new upstart (for which documentation is very poor at this moment, or at least it needs improvement).

My goal is to have a server with all applications installed (usually DNS, LAMP and few other stuff) which boot up as described above. I'll add some salt and pepper at the end, moving focus on tty8, a virtual console which only display critical messages - such that whenever I'm around the monitor I can easily see if smth wrong goes mad. This part shouldn't be that hard, but right now I want to achieve the knowledge for stuff earlier described.

Any luck with you to find out how to stop the screen getting blank so that I see salt and pepper at the end?

---

### Post by cariboo on 2009-01-06
You don't have to reboot every time you make a change to your server, just restart the service that your modifying for example if you make a change to /etc/network/interfaces, and if you are connected remotely at the prompt type:

```
sudo /etc/init.d/networking restart
```

For any other service I usually just use <service> stop and start. Most of the server scripts are located in /etc/init.d

Jim

---

### Post by digitalage on 2009-01-06
> **cariboo907 said:**
> You don't have to reboot every time you make a change to your server, just restart the service that your modifying for example if you make a change to /etc/network/interfaces, and if you are connected remotely at the prompt type:

```
sudo /etc/init.d/networking restart
```

For any other service I usually just use <service> stop and start. Most of the server scripts are located in /etc/init.d

Jim

I appreciate, cariboo907. However, it doesn't solve my issue, which is what I asked at the beginning. It's true that whenever I need to install a new server (application), it's enough to just start the service/process. 

One reason I restart often is for tuning (boot up faster) or when I mess things up and need a refresh. Like iptables, for example. Or scripts I make to run automatically at start up... Or when investigating errors at start-up in logs (and have to check if they replicate after fixing). There are maybe others I probably don't remember right now. Anyhow, as long as it can be changed the way I want, why not? 

Help I need to achieve the knowledge for what I started this thread. This could be helpful for others too.

---

### Post by digitalage on 2009-01-22
hmm... not much action here. I'm curious where are those linux freaks who know everything...

---

