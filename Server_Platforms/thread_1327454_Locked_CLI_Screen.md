---
title: "Locked CLI Screen"
date: 2009-11-15
forum: Server Platforms
---

### Post by slick666 on 2009-11-15
Dear Forum members,

I'm trying to find a way to lock the CLI screen but I'm afraid I can't seem to find a way to do this. I think this might be because there are so many search return for graphically locking the screen. I'm running an ubuntu server with a CLI interface only. What I would like to do is set each server with the local screen displaying live information about the system.

The iftop for an example. I would like to have iftop running but I would not want to leave the system in a state where someone could cancel the the program and then use the account that is logged into the machine. Ideally I would like to set the system running and then have some secret key combo that prompts me for my login credentials. It is not essential to run the server but it would be nice to have a system that I want to monitor continuously display that info where I can glance across the room and instantly see that info.

Any info or some search words would be helpful.

---

### Post by koenn on 2009-11-15
```
logout
```
or```
exit
```
would solve your immediate problem of not leaving a session open.

For the eye candy, you can probably find ncurses- or framebuffer-based screensavers.

You could also look into programs that can run in the background but still send output to your screen - even when you're logged out.
I've seen this happen, so I know it's possible, but I don't know if just any program will do this.

---

### Post by hictio on 2009-11-15
> **slick666 said:**
> Dear Forum members,
The iftop for an example. I would like to have iftop running but I would not want to leave the system in a state where someone could cancel the the program and then use the account that is logged into the machine. Ideally I would like to set the system running and then have some secret key combo that prompts me for my login credentials. It is not essential to run the server but it would be nice to have a system that I want to monitor continuously display that info where I can glance across the room and instantly see that info.


This sounds like really insecure thing to do, unless I don't understand completely what you are trying to do...
The first thing that comes to mind is removing the keyboards from the boxes, so, the users can see the monitor with whatever program you want to be continually shown, but they can't interact with those programs; of course, you would have to access thru SSH the servers to kill the programs.
But, if the boxes are near the monitors, a careless user might simply turn off the given box.
Does the server have an Apache running? Wouldn't be more secure to have a webfront for the app (or MRTG, or Munin, or Zabbix, or Nagios, etc) you want to display info available thru a web page, and so the the users can see that without being near the box itself?

---

### Post by shaggy999 on 2009-11-15
EDIT: Nevermind my idea, it won't work.

---

### Post by kewlrichie on 2009-11-16
How about making a limited account with that you would log into and run the program you want and even if you have to sudo wouldn't the sudo run out in 15 mins anyways? So if anyone just cancelled the program they wouldn't be able to do much

---

