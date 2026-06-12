---
title: "Script for checking logs and file permissions on Ubuntu Servers (or any other)"
date: 2007-11-29
forum: Server Platforms
---

### Post by akvik on 2007-11-29
Hi,

I don't know about you, but I need a way to condense my log files to be able to check them in an effective way. The checking of log files are extremely important from a security point of view, but the first thing to be neglected when time is short.

Link to sticky about security, for reference:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I recommend running Tiger btw.

I've made a little script for checking my server logs and some file permissions, and I wanted to put it up here in case someone wants to use it or improve it. 

The script is highly modifiable and needs some variables and file paths declared by you, unless you are running with the same (default) Ubuntu Server 7.10 setup as me. Check the script for explanations.

You can also disable or enable checks according to your liking.

The script doesn't change any files on your box, it just reads files and puts the information on the standard output. In other words, it shouldn't be able to do bad things...

It can be run as root, but I run it as myself, since I have access to the different log files and the files in the webroot. Root to me is overkill in this case. However, users without correct permissions won't be able to run it.

**Features:**
[list]
[*] It checks Shorewall logs and creates a top ten intrusion list from source IPs. Makes it easy to block certain IPs if that is your wish.
[*] It checks file permissions in the webroot folder - assuming here that apache access the files through its group (in my case www-data). In my setup, no others have access to the files, apart from some textpattern folders. I have 770 as permissions in my webroot. You can change your criterias if you want to.
[*] It checks if the webserver is up, by fetching the index-file (I know it's an awkward procedure, but I have php/mysql and I want to check that too..)
[*] It gives a top ten list of logged in users, through a shell and through ssh.
[*] It gives a top ten list of files causing apache errors
[*] It scans the server's ports and checks them against your own list of allowed ports.
[/list]

**Prerequisites:**
[list]
[*] I have the Shorewall firewall installed and working. If you don't, just disable the shorewall test.
[*] I have nmap installed, which you need for the portscanning - otherwise just disable the test.
[*]I use logcheck, but I don't think this inflicts on the running of the script.
[/list]

**Things to do:**
[list]
[*] A versatile way to assign to-and-from dates - right now it only checks "today".
[*] Silent mode and mail function for cron jobs - easy but inflicts on the "read-files-only" rule.
[*] disk sizes and quotas.
[*] file permissions in other places (logfiles, conf-files, bin-files, etc.).
[*] mysql checks, that necessary databases run smoothly.
[*] other common security flaws.
[*] output to html and store in protected web directory?
[*] ..and more?
[/list]

 [color=red]PLEASE FEEL FREE TO CHANGE AND REVISE THE SCRIPT - POST THE UPDATED SCRIPT HERE[/color]

It would be great if we could make an all-in-one log and integrity check script - it is certainly needed - so please go ahead and change it all if necessary!

[Update]: updated the script with some more reports on login attempts.

---

### Post by MJN on 2007-11-30
> **akvik said:**
> Hi,
 
I don't know about you, but I need a way to condense my log files to be able to check them in an effective way. The checking of log files are extremely important from a security point of view, but the first thing to be neglected when time is short.
 
Have you considered Logwatch?
 
Mathew

---

### Post by akvik on 2007-11-30
Yes,

logwatch is great, and very versatile. I can't make it check permissions though (maybe it can?), or open ports, but I suppose a fine tuned combination between tiger and logwatch can do pretty much anything you like. My script doesn't match these at all of course, but it is easy to add things that are of interest; local permission policies for instance. 

akvik

---

### Post by MJN on 2007-11-30
Ah okay. I just wanted to point it out in case you weren't aware - didn't want you reinventing any wheels!
 
It's clear you're not though - you have many more requirements besides those satisfied by Logwatch (I'm not familiar with Tiger - will take a look).
 
Mathew

---

### Post by akvik on 2007-11-30
Thanks,

you're right though - reading the text again it sounds as if no other log analysis or permission check is out there :) 

The reason for writing the script was two-fold: firstly, it was a way for me to formalize the permission policies on the server, and realising how many files were read- and writable by users that really shouldn't be. When a server works, admin is happy, without considering that the server work "too well", sharing out this and that. I think that many security issues comes from admins that are not bothered with the hassle of having a strict permission policy, but I could be wrong :) Secondly, I needed certain tests that match my own situation, running a LAMP server that just _have_ to work. Our last server (os x) was hacked and it made me think that this time around this _will not happen_. But who knows, right?

:)

---

