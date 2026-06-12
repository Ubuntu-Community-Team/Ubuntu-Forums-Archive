---
title: "Moving current server to completely new machine"
date: 2009-12-27
forum: Server Platforms
---

### Post by mistypotato on 2009-12-27
There doesn't seem to be much help available for Ubuntu server migration at least that I have found so far.

My old server is beginning to fail (mainboard).

I am going to need to move my server to a new computer.  I need my new server to be configured exactly like the current server with all programs and settings and data etc.

Basically, I want the exact same server on totally different hardware.

I've been using ubuntu for over a year now and it seems I can move all the configuration files safely.  The only files that might cause trouble are the HARDWARE configuration files.

So, it seems that the "best (and only) way at present to do this is to follow these basic steps....

1). Prepare the new server hardware
2). Install ubuntu Server (or whatever version you choose) on the new server
3). Install ALL the software (programs) that were on the old server so you have a "base"
4). Find & copy ALL the configuration files for all the programs you want to migrate
5). Cross your fingers and pray

Step 4 is the most tedious since some programs can have bits and pieces installed across several locations and/or directories.

Maybe someone can come up with a nice script that will automatically TAR all the correct files into neat, organized packages that can be un-tarred on a new server.

I could envision a script with clearly defined sections that can be commented so that they wouldn't be included in the script in case that software was not installed on a particular machine.

This script would have SECTIONS for each software package and cover all the most critical software including but not limited to....

1). Apache Server
2), MySQL
3). PHP
4). Postfix
5). Awstats
6). Webmin

I use Intrepid 8.10 Server and I am not sure if different versions install software into different locations.  But if that IS the case, scripts might need to be customized for those different versions.  Also, if people install into locations other than the Defaults, then they would have to customize their own script accordingly.

---

### Post by Barriehie on 2009-12-27
Edit: Whoops, I just reread and saw about the configs so not all of this will apply.

While not entirely able to answer your post I can provide this bit of help.
If you run:
```

dpkg --get-selections > SomeFileName

```
you'll get a list of everything installed on your old server.  If you then take that file and remove the trailing spaces/status and run:
```

sudo apt-get install < SomeEditedFileName

```
you'll have apt-get installing and configuring everything that was on the old server.

I use some of this to put a list of installed packages with my backups.

HTH,
Barrie

PS: I'm sure someone on here has done this before so this is my $.02 worth! :)

---

### Post by Cheesemill on 2009-12-27
You could just take the hard drive out the old machine and put it straight in the new one (or clone the disk onto the new machine).

Unlike Windows, Linux scans for hardware and loads the appropriate drivers every time it boots. I've used this technique several times before with no issues.

It's a least worth trying as it would save you hours of work.

---

