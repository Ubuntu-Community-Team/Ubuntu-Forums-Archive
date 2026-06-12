---
title: "php script as root through apache"
date: 2008-07-07
forum: Server Platforms
---

### Post by Geran on 2008-07-07
Hi,

I'm trying to figure out how I can configure my php scripts to be able to run commands to the shell as root. All commands will work unless I have to use sudo. 

Ex. `touch something.php`

Will work because www-data has permissions to write in that folder.
However, for example,

`touch /home/something.php`

Will obviously not work, because only root can write to that directory. How can I give my web server root powers?

regards, 

G

---

### Post by sp00ki on 2008-07-07
> **Geran said:**
> Hi,

I'm trying to figure out how I can configure my php scripts to be able to run commands to the shell as root. All commands will work unless I have to use sudo. 

Ex. `touch something.php`

Will work because www-data has permissions to write in that folder.
However, for example,

`touch /home/something.php`

Will obviously not work, because only root can write to that directory. How can I give my web server root powers?

regards, 

G

Not the answer you're looking for exactly, but why not add apache (the user) to the GROUP that has write access to the directory in question?
For instance, if i want apache to write to /home/airplane, then i'd add apache to the airplane group.
this will allow apache to write to /home/airplane, assuming that /home/airplane is 770.

---

### Post by Geran on 2008-07-07
You're right on both points, that would work, and it's not what I'm looking for. I need to be able to run root commands in a script when it is called in a web interface.

---

### Post by Titan8990 on 2008-07-07
That doesn't sound very secure....

---

### Post by Geran on 2008-07-07
Is there not secure way of doing it? I can't imagine that I'm the first person to want to do this...

---

### Post by Geran on 2008-07-07
I've seen plenty of systems that have key aspects managed through a web page.

---

### Post by sp00ki on 2008-07-07
> **Geran said:**
> You're right on both points, that would work, and it's not what I'm looking for. I need to be able to run root commands in a script when it is called in a web interface.

i see-- i was basing my advise on your example.

but let's try this again:
if it's commands you're looking for, simply adding them to apache's path should do the trick (so instead of /usr/bin/acommand you can run acommand, which normally give you the old bash: acommand: command not found).
if you're referring to command permissions, though, you could chown the necessary commands to a group (called bin_group, for instance), then add apache to the bin_group group.  this would allow you to grant specific access to only the files and programs needed by apache.

alternatively (and i do recommend against doing this), you could add apache to the admin group, though doing so adds lots of potential to have your system compromised.

i'd be curious as to what it is you're doing-- sounds like it could be interesting.

---

### Post by Titan8990 on 2008-07-07
Typically, you want to work around this kind of thing whenever possible.

---

### Post by cdenley on 2008-07-07
You would have to allow www-data to sudo with your specific command without a password. I think you could also use the suphp module, but I never tried it. Be very careful whenever running commands in php, especially as root. You have privilege seperation by default for a reason.

---

### Post by Geran on 2008-07-07
> **cdenley said:**
>  I think you could also use the suphp module, but I never tried it. Be very careful whenever running commands in php, especially as root.

This suphp module sounds interesting... from the sound of it, it would allow you to exceute a script as a different user, yes? 

And yes, I know it sounds risky, but it's not like I'm saying HEY! COME USE MY FULLY POWERED ROOT SHELL FROM MY WEBPAGE! I really just need one command to be run as root. 

And what I'm doing? I'm making a web interface for controlling things like iptables, VLAN interfaces and other stuff. I really just need root powers for changing IPtables, restarting dhcp server and things like that. 

I have apache basic authentication set up and I'm looking at some other security possibilities, I understand the risks.

---

### Post by Geran on 2008-07-07
Looking at it, I don't see too much of a risk, I just need my web page to be able to run certain commands that I have already written into it. The commands don't vary at all, just the timing of them should be in sync with the web server's actions.

---

### Post by furlabs on 2008-07-09
Even so, if apache is running as root, hackers may be able to use vulnerabilities in your code or in apache itself to run any command they want. And I wouldn't rely on Basic Authentication to save you, it sends passwords in clear text and it's vulnerable to brute force attacks: [http://httpd.apache.org/docs/1.3/misc/FAQ-G.html#passwdauth]("http://httpd.apache.org/docs/1.3/misc/FAQ-G.html#passwdauth")

---

### Post by windependence on 2008-07-09
> **Geran said:**
> Looking at it, I don't see too much of a risk, I just need my web page to be able to run certain commands that I have already written into it. The commands don't vary at all, just the timing of them should be in sync with the web server's actions.

You can give your apache user access to single commands using sudo. I'll see if I can dig up some info for you.

-Tim

---

### Post by worldsayshi on 2010-01-20
How about this: Allow the apache server to execute, but not read, a script that states a sudo command with password. 

=> The password should be safely hidden inside the script and apache's root access is restricted to what the scripts are doing. Not a perfect solution but better than giving apache root access.

Not 100% sure it will work the way I'm describing but I can't see why not...

---

### Post by iponeverything on 2010-01-20
You can setup sudo nopasswd for specific commands.

I had to do this for a little web interface I made for people to add websites to a squidguard whitelist/blacklist.

---

