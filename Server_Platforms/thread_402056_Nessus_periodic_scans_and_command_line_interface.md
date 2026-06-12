---
title: "Nessus periodic scans and command line interface"
date: 2007-04-05
forum: Server Platforms
---

### Post by seppe on 2007-04-05
I'm configuring nessus on a Dapper server to perform periodic scans: I need a command line interface to nessus client.
Unfortunately the cli for the client resides on the *nessus* package which includes the graphical client too. When I try to install the package, it wants to install a bunch of graphical stuff: 
```

$ sudo aptitude install nessus
[...]
The following NEW packages will be installed:
  hicolor-icon-theme libatk1.0-0 libatk1.0-data libcairo2 libgdchart-gd2-noxpm libglib2.0-0 libglib2.0-data 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0 libpango1.0-common libtiff4 libxext6 libxft2 
  libxi6 libxinerama1 libxrandr2 nessus 
[...]

```

I don't want to install graphical packages on a server (besides that, they're not supported more than three years), Could you please point me to a solution for this problem? Is there a package with a command line nessus client only?

Thanks.

---

### Post by grittyminder on 2008-05-28
This is an old post, but it asks a good question. In case anybody else wondering about this...

nessus is the nessus client package; nessusd is the nessus server package. If you want to avoid installing unnecessary graphical packages on the server side you should install the server package only:

sudo apt-get install nessusd

Next, install the nessus client on your workstation. The nessus client is available for many flavors of Linux, Unix, Mac, and even Windows. 

If you want to run the nessus client unattended as a job, you will have to run  nessus in batch mode. (I'm not sure if the non-Linux clients allow you to create nessus jobs). The general syntax is like this:

nessus –q [-pPS] <nessusdHost> <nessusdPort> <nessusdUser> <nessusdPasswd> <targets-file> <result-file>

You'll have to read the man pages for additional information on how to configure nessus, such as what information to put in the .nessus file. However, from my experience running the GUI client makes the initial configuration much easier. I recommend using the the client GUI to create the necessary configuration files, then run the command line client as a cron job.

---

### Post by seppe on 2008-05-29
**grittyminder** thank you for your reply, but unfortunately it doesn't fit my needs: I know I can install the *nessusd* package on a server and the client on another (typically a workstation) machine, but I need a scenario that expects only one pc (this is a server that acts as a network monitor, a LAMP server with Wiki guides and auditing centre too) that performs periodical scans and creates web html reports.

I've installed the nessus client on the server machine (with all his dependencies of graphical packages... :(), created an ad-hoc user, a target-hosts file, a crontab entry and a bash script. The whole thing it's a personalization of a guide I found on a [blog (http://www.redbrick.dcu.ie/~svan/blog/)]("http://www.redbrick.dcu.ie/~svan/blog/?p=36").

In case anyone's wandering, these are some of the dependencies installed with the *nessus* package (the client) on Ubuntu Server:

[INDENT]*defoma fontconfig laptop-detect libatk1.0-0 libcairo2 libfontconfig1 libfreetype6 libgd2-noxpm libgdchart-gd2-noxpm libglib2.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libjpeg62 libpango1.0-0 libpango1.0-common libpng12-0 libtiff4 libx11-6 libxau6 libxcursor1 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxpm4 libxrandr2 libxrender1 nessus ttf-bitstream-vera ttf-dejavu ttf-freefont x11-common [...]*[/INDENT]

Too bad I can't install the cli nessus-client only...

Maybe I could compile the nessus client from source wiping out the graphic frontend... (but I'll loose the ubuntu package update utility)

---

### Post by munwin on 2008-06-23
bump - I am also interested in a CLI only client, for exactly the same reasons as above.

---

