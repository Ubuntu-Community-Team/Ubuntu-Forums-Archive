---
title: "Need a little help creating an init.d script"
date: 2010-07-12
forum: Server Platforms
---

### Post by NDLunchbox on 2010-07-12
I'd like to have a simple application I need automatically start on startup and stop on shutdown.  I planned on using update-rc.d to automatically configure the run levels, but I guess I first need a script in the init.d directory.

I tried doing this based on a Python template I found but failed miserably.  I was hoping, if this is easy, someone could bang out a quick script for me or at least point me in the right direction of where to find a basic template and how to modify it...

I have a dynamic DNS update client provided by my ISP that came with next to no documentation.

As best as I can figure out it's a simple binary that encrypts and stores my username / password somewhere (I hope) and regularly updates the dynamic dns service.

I put the binary in /bin/ and found the options when you run it are:

ddnsd [option]

--status (display current status)

--help (displays list of options)

--stop (sets status to Offline and exits)

--start (this is the default option; it starts the daemon)

--offline (sets status to Offline)

--online (sets status to Online)

--config (re-configures client; requires Client Reset in SiteControl)

---

### Post by TechBeastie on 2010-07-12
Here's something that looks promising:
[http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian)

Some additional notes:

* Note that you start out all scripts with 
```
#!/bin/bash
```
where "bash" is your shell of choice.

* Make sure that none of the commands you wish to run remain foregrounded by default (that is, they "take over" the terminal session that they're run in, and don't allow further input until killed).  If any commands do remain forgrounded by default, you'll want to append a "&" to the end of them in your script, so that they are automatically backgrounded instead.

* Once you've created your script, and put it in the correct location(s) within the init.d hierarchy, you'll need to make it executable with ```
 chmod a+x <name of file> 
```

---

### Post by NDLunchbox on 2010-07-13
Thanks,
I used your link, plus this one from Novell: [http://www.novell.com/coolsolutions/feature/15380.html]("http://www.novell.com/coolsolutions/feature/15380.html")
And came up with this:
```
#! /bin/sh

# (c) Copyleft 2010 Lunchbox the Cruel
# All wrongs reserved.
#
# /etc/init.d/optonline-ddnsd

  case "$1" in
    start)
        echo -n "Starting optonline-ddnsd client: "
        /bin/ddnsd
        ;;
    stop)
        echo -n "Shutting down optonline-ddnsd client: "
        /bin/ddnsd --stop
        ;;
    status)
        echo -n "Checking of optonline-ddnsd client: "
        /bin/ddnsd --status
        ;;
    *)
        ## If no parameters are given, print which are avaiable.
        echo "Usage: $0 {start|stop|status}"
        exit 1
        ;;
esac

exit 0

```

Seems to work ok, I'm going to try adding it to the run levels now.

---

### Post by NDLunchbox on 2010-07-13
Success!
Here is what I did:

First I moved the executable I got from my ISP to **/bin/**, set the permissions so only root users can execute it (using chown and chmod) and ran through the initial config as prompted.  ***NOTE TO AMD64 USERS:** The app won't run without ia32-libs installed*

I created the above script in the file **/etc/init.d/optonline-ddnsd**

Next I made it executable with **$ sudo chmod 754 optonline-ddnsd**
*(I don't want non-admins running it - the config file is in the root user's home dir since I ran the setup with sudo)*

Finally I added it to the runlevels with **$ sudo update-rc.d optonline-ddnsd defaults**.

I restarted the server and watched on my ISP's dynamic dns config page as the client went offline and then came back online and updated the IP.

For the benefit of people searching on Google, this is how to setup the dynamic DNS client called ddnsd provided by Cablevision for use with the Optimum Online Boost service and have it automatically start with the server (configured on Ubuntu Server 10.04LTS 64-bit).

---

### Post by onlyfoolsnhorseswk on 2013-04-25
I came across this thread while setting up my oon ddns on debian 6 (squeeze). I thought I would add a little to Lunchbox's post for anyone else who comes across this. My browser is not cooperating with formatting options, so I apologize in advance for a tedious read. To begin, I booted the box I have my webserver on and logged in as root. I then changed directory to /bin. While in bin I typed wget [https://sitecontrol.webhosting.optimum.net/SiteControl/static/com/hostway/plugins/ddns/bin/ddnsd-linux.tar.gz](https://sitecontrol.webhosting.optimum.net/SiteControl/static/com/hostway/plugins/ddns/bin/ddnsd-linux.tar.gz) (note the missing js ending from the original link you can see on the site). This downloads the compressed files into the bin directory. The files must be uncompressed and extracted using tar zxvf ddnsd-linux.tar.gz . You can remove the original download using rm ddnsd-linux.tar.gz . When extracted you should have the file ddnsd in the bin folder. I couldn't run it when I did this (typing in ddnsd <enter>) so I found this thread. I then followed lunchbox's first two steps, "create the above script in /etc/init.d/" by navigating to that directory and typing nano optonline-ddnsd. This opens a file to type Lunchbox's script into. Once that's entered and correct, type Ctrl+X to save, type Y for yes, then enter the commands chmod... and update... listed above in lunchbox's post without sudo/su (we're logged in as root already). Once those commands are accepted, restart the server and log back in as root. When logged in enter apt-get install libcurl3 to use a missing library ddnsd needs to run. Once installed type ddnsd and hit enter. You should be able to set up first time configuration for the daemon using your DDNSD optonline username and password -- this is not your normal optonline username and password; this one has to be set up from within your normal account. When you log back in to your account after entering your un and pw, your status should be set to online. Assuming you have a server ready to go (e.g. apache2), all that should be left is configuring your router to accept the connection. glhfddnd

---

### Post by wildmanne39 on 2013-04-27
Thanks for sharing! Old thread closed.

---

