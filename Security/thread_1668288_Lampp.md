---
title: "Lampp?"
date: 2011-01-16
forum: Security
---

### Post by rysliv on 2011-01-16
Ive gotten hacked on my website Penalty.bz

How do I better secure it so they cant change my files remotely?

Ive looked all over the net for hours, No luck finding any help.

---

### Post by Joeb454 on 2011-01-16
Thread moved to **Security Discussions**.

---

### Post by TheHackOps on 2011-01-16
Depends how "they" got into your Fileserver in the first place, more info would be nice ill be on for a few more hours before i go to sleep

---

### Post by rysliv on 2011-01-16
I changed some php configs to disallow php execution stuff...

---

### Post by rysliv on 2011-01-16
see look at the site - i edited it =P   TIMES SUCKS!!!! what a dumb hacker.

---

### Post by CharlesA on 2011-01-16
That's not the way to combat someone compromising your site.

I'm tempted to close the thread because of it.

In any case, don't have your web directory writable by the outside world, use strong non dictionary passwords and always have good backups.

---

### Post by CharlesA on 2011-01-16
That's not the way to combat someone compromising your site.

I'm tempted to close the thread because of it.

In any case, don't have your web directory writable by the outside world, use strong non dictionary passwords and always have good backups.

---

### Post by bodhi.zazen on 2011-01-16
> **rysliv said:**
> Ive gotten hacked on my website Penalty.bz

How do I better secure it so they cant change my files remotely?

Ive looked all over the net for hours, No luck finding any help.

See post #3, we need more detail.

In general, I keep files in /var/www owned by root.www-data with permissions of 440 (ro).

Transfer files to your server vis sh (scp) and not FTP, or harden FTP.

Do not use weak passwords.

Be very careful with uploading files via php. In general I would not use this method, use ssh (scp).

---

### Post by rysliv on 2011-01-16
This hacker wont stop.

I did though find out what he was using to hack me with

they use something called WOS 2.4
[http://hack-stars.ru/?p=963]("http://hack-stars.ru/?p=963")

A Russian PHP code
Allows you to change any file on the system no matter what, upload any file and what ever you want to do. Complete package for hackers to use on web hacking.

I have tried to enable Safe mode, it appears off no matter what
 OF COURSE i rebooted apache, Who wouldn't
I also tried to see if i could at least get the directory to only be httpd, with that one function thingy in php.ini i forgot name to obviously, Theres way to many to name.

I currently have most of his IP's blocked behind Peer Block 


I have tried reducing the Post data to around 2KB and uploads disabled, yet this WOS still bypasses that and uploads.

I REALLY don't know what else I'm suppose to do to stop hackers, I've literally tried everything i could possibly do with apache to stop him, IT DOESN'T work!

How does Youtube and other corporation sites do it??!
<snip>

---

### Post by rysliv on 2011-01-16
IF i need to add to this I DO NOT use FTP or anything of that matter.  Strong passwords wont make a difference, He gets through them like slicing through a cake.

---

### Post by bodhi.zazen on 2011-01-16
Well, honestly, I suggest you need to bring your server off line, perform a fresh install, make sure you use strong passwords.

If you do not know  how you were compromised, then it is going to be impossible to fix.

Now that the server is compromised it could be most anything, including a root kit or a custom php script, we would be guessing.

With your fresh install, use strong passwords, engage apparmor, take a look at mod_security, consider selinux, and only allow uploads via ssh (sco).

Without more detailed information or unless you give me shell access, access to logs, details of your php scripts, etc what do you expect us to say.

---

### Post by rysliv on 2011-01-17
You need to understand this.

THEY ARE **_NOT_** trying to login to the server using command consoles. Strong passwords wont make a difference >.>

There are **_MULTIPLE_** servers attacking me

I DO **_NOT_** use FTP to upload files or anything, THIS IS a Local server that I am able to access without need of FTP or sharing over the network.

My IP address wont change and I Do Not want to loose my domain address just to get rid of a hacker.

I'm trying to limit them from being able to access folders and files outside the main HTTPD folder (like /home or /opt/lampp)

I'm also trying to disable **_ALL_** file uploads from PHP and any access to directory listings from a PHP script. And disallowing PHP to Delete files & Executing anything.

Yet everything I try to look at simply does not work, Safe Mode doesn't turn on period. And Theres no other way I can think of or something that actually works that will stop hackers from getting into my server.

Please don't ever reply with Use strong passwords and crap about FTP, because thats not anything that relates to this case. They get in by injecting a PHP code, go to the php code that allows access to all my files (can upload, delete, edit, and change CHMOD values).

---

### Post by rysliv on 2011-01-17
I looked somewhere, Would CHMOD 511 for httpd be better than 777 & 555?

---

### Post by CharlesA on 2011-01-17
511 would be r-x--x--x, which would effectively make the site unaccessible for everyone.

To be honest, I'd just take the server down. If it's a local machine, you can just deny all traffic on port 80 (or whatever port Apache is listening on) until you can figure out what you want to do.

---

### Post by rysliv on 2011-01-17
It is currently offline and only accessible by me ONLY.

I'm trying to figure out a few things with the security, looking over php security blog posts again.

isn't 511 Read+Execute for owner, and Read for everyone else?

Websites use the Read function mainly and rarely the Write function. I'll try it out anyway

---

### Post by rysliv on 2011-01-17
OOps I meant CHMOD 544 my calculator was bugged

---

### Post by rysliv on 2011-01-17
Great, now my server wont power on =(

I found the cable in my server which causes it to shut off.
it was a mini 4 pin thing that went to the CD drive, if moved it shorts and causes the entire system to shut off completely.

---

### Post by bodhi.zazen on 2011-01-17
> **rysliv said:**
> You need to understand this.

THEY ARE **_NOT_** trying to login to the server using command consoles. Strong passwords wont make a difference >.>

There are **_MULTIPLE_** servers attacking me

I DO **_NOT_** use FTP to upload files or anything, THIS IS a Local server that I am able to access without need of FTP or sharing over the network.

My IP address wont change and I Do Not want to loose my domain address just to get rid of a hacker.

I'm trying to limit them from being able to access folders and files outside the main HTTPD folder (like /home or /opt/lampp)

I'm also trying to disable **_ALL_** file uploads from PHP and any access to directory listings from a PHP script. And disallowing PHP to Delete files & Executing anything.

Yet everything I try to look at simply does not work, Safe Mode doesn't turn on period. And Theres no other way I can think of or something that actually works that will stop hackers from getting into my server.

Please don't ever reply with Use strong passwords and crap about FTP, because thats not anything that relates to this case. They get in by injecting a PHP code, go to the php code that allows access to all my files (can upload, delete, edit, and change CHMOD values).

You keep saying the same thing over and over.

First you had to have had some initial vulnerability and second they need to be accessing your system somehow.

But it sounds as if you really do not understand how or what happened to your system.

Without further information it is therefore hard for us to give you specific advice.

I suggest you re-install your server and try to perform forensics to determine what happened. Please note" performing forensics is quite technical and you may need to seek more professional assistance.

If you re-install I suggest you monitor the logs and you may wish to look at tools for HIDS such as OSSEC (see the stickies).

---

### Post by OpSecShellshock on 2011-01-17
This sounds as though it might be the result of a remote file inclusion, which is a problem under some circumstances with PHP. However, that's just a guess on my part. If that is in fact what happened, then a lot of the right damage (from the attacker's perspective) is already done, and very little that you do to restrict access is probably going to work at this point. Your server may well be setting up connections to the attacker's machine from the inside out by now, which means they'll always have a way in as long as it's running. Every solution I can think of starts with reinstalling the OS.

---

### Post by rysliv on 2011-01-18
Yeah I am too, but  I was on a windows operating system before, and saw a few processes that shouldnt be running, i closed them and deleted the exe file

I dont know of anything that could be in the ubuntu operating system atm, but I do need to re install because I used the WUBI installer, i have the host folder which i cannot hide from the user nobody and group nogroup  he will be able to change what ever he wants in there. Like completely screwing up my computers boot.

So far. I haven't found anything wrong with the server after I took it down and blocked port 80 so only local networks can connect to it, I've never noticed a change.

I've been messing with the hackers tool to make sure every aspect of it does not function at all period, so he cant do anything but read files. Even though that is quite dangerous, I have managed to CHMOD everything with 775/755   Allowing read access but not write or execution access. I'll CHMOD some files that are very important like configuration files with something else to stop them from reading the file, I'm in the process of doing so.

---

### Post by rysliv on 2011-01-18
I think I got the security stuff worked out. I don't think anyone externally can inject code and run it anymore, or attempt to upload anything.

I'm going to back up and re-install ubuntu

---

### Post by CharlesA on 2011-01-18
Were you able to figure out how they were able to compromise your site in the first place?

---

### Post by CharlesA on 2011-01-18
Were you able to figure out how they were able to compromise your site in the first place?

---

