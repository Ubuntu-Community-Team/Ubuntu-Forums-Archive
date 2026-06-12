---
title: "My first server..."
date: 2008-04-30
forum: Server Platforms
---

### Post by Kaptain_Xabriel on 2008-04-30
Hi everyone.

I've put together some old computer parts, and bought a new hard drive, and I want to make a server.

Problem is, I barely know where to begin.

Let me explain what I want to do:
1. I want to use it as a network drive on my home network
2. I would like to set up a web page that I, or my friends can access over the internet from any computer.
3. I would also like to use it to download and seed torrents.

For the web page, I want to have a username/password login that is quite secure. ie; 3 failed logins = permanent IP ban (unless I remove it) And for the web page interface, all I really need is maybe a couple text-based pages, then a directory system where I can access my files.

I would like to know what distro I should use, what programs I should use, and most importantly: HOW.

I am still relatively new to linux, so I will probably need a lot of guidance :)

Thanks in advance!

---

### Post by natrixgli on 2008-04-30
Hi,

All the things you've mentioned are pretty easy to do. A few suggestions though:

1) For home use, I created my first server on a virtual machine using VMWare Server. That way I could practice with minimal investment. You can probably do the same with Virtualbox, Qemu, etc.

2) Some ISP's have rules and/or measures in place to prevent home users from running servers. I would check with your provider.

3) There are lots of howto's, etc for building servers, I would recommend searching google, and the forums for the "perfect ubuntu server" guides, etc. A lot of the info you need will be easier to get in a prepared howto. Also many of the things you want to do will not always be easy with GUI (graphical) tools, so it's handy to know some command line, and how to use nano or vi to edit configuration files. (don't worry, they're all very well documented!)

Some programs for you to check out would be:

OpenSSH Server - secure remote access for commands & files. (learn how to change the port number!)
Apache Web Server - for servin' up web pages (read up on htaccess and ssl)
Denyhosts - will block hosts who fail SSH authentication more than a specified number of times
Webmin - modular, web based system administration tool
Samba - for sharing files with Windows computers

There's tons of documentation for these programs here and elsewhere on the web, you just have to go have a look.

Another thing that might help is downloading a pre-build server appliance from VMWare and running it in VMWare Player to fool around with. 

Good luck,

-n8

---

### Post by SuperCzar on 2008-04-30
Are you planning to have a monitor/keyboard/mouse for this?

If so install a copy of Ubuntu Desktop. It'll ease you into the linux transition

Otherwise install a copy of ubuntu server.

for the concerns you raise:

1. look into samba, if you have ubuntu desktop installed there's a sharing preference that makes it easy to set up shared folders.
2. look into setting up apache, there are a lot of good guides and it's not that hard.
3. there are plenty of torrent applications for osx, but i would look into torrentflux, might be right up your alley.

---

### Post by natrixgli on 2008-04-30
Also I have to stress that while the GUI tools greatly simplify server administration, it's still essential to at least know how to access and edit configuration files from time to time.

Some of the GUI's will miss little bits & pieces, and sometimes it's just easier to edit a few lines of text.

It would be a good idea to know how nano or vim works. OH and also how to read log files so you can troubleshoot.

A lot of times when I'm having a problem, say, with Apache I will do:

```

tail -f /var/log/apache2/error_log

```
Which displays the logs AS they are written...


then in another term, do:

```

sudo /etc/init.d/apache2 start

```

And watch to see if any errors pop up. 


So while the GUI tools are handy for basic day to day setup & maintenance, it's very helpful - some would say essential, even - to know the CLI tools as well.


Good Luck,

-n8

---

### Post by hyper_ch on 2008-04-30
> **Kaptain_Xabriel said:**
> 1. I want to use it as a network drive on my home network
If you want to mount the remote partitions on a linux box have a look at NSF or SSHFS... if you want to mount on a windows box, have a look at Samba

> **Kaptain_Xabriel said:**
> 2. I would like to set up a web page that I, or my friends can access over the internet from any computer.
Here is probably the simplest solution to isntall apache and a dyndns service like no-ip or dyndns

> **Kaptain_Xabriel said:**
> 3. I would also like to use it to download and seed torrents.
Use rTorrent (and screen) for that... rtorrent is a cli/ncurses based torrent client.

> **Kaptain_Xabriel said:**
> For the web page, I want to have a username/password login that is quite secure. ie; 3 failed logins = permanent IP ban (unless I remove it) And for the web page interface, all I really need is maybe a couple text-based pages, then a directory system where I can access my files.
Why bother at all with a webserver if you're basically sharing files? I'd use SSH/SCP for that.

> **Kaptain_Xabriel said:**
> I would like to know what distro I should use, what programs I should use, and most importantly: HOW.
For servers I generally recommend Debian Etch (Server)

---

### Post by Kaptain_Xabriel on 2008-05-01
Thanks for all the suggestions guys.

For now I think I will go with Ubuntu Desktop, and use the GUI to manage the server. Eventually I will learn more, and be able to handle a command line server. But for now I need to keep things relatively simple.

---

