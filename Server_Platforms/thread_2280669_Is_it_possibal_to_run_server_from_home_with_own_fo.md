---
title: "Is it possibal to run server from home with own forum on it?"
date: 2015-06-01
forum: Server Platforms
---

### Post by patrikmellq on 2015-06-01
Hello...
I would like to run a gambling forum for the casino game Baccarat - can i do that with my own Ubuntu server.
It does not has to be any fancy forum with alot of fancy tools.

I belive i can install a server and secure it or at least i will find topics about it.
But how would i download a existing forum with tools for Admin and manage posts and topics.

All suggestion where to start is welcome.
I have a fiber connection with 10 MB up and 10 MB down.

The server will be a small laptop.

Cheers

---

### Post by QIII on 2015-06-01
Moved to Server Platforms.

---

### Post by patrikmellq on 2015-06-01
I find miniBB [http://www.minibb.com/](http://www.minibb.com/) made simple - maybe that is something for me to try - i read what Requirements needed - web server - i can install a web server and make it secure.
But then i read further installation knowledge:


[LIST]
[*]how to work with plain text files, i.e. open, edit them, cut and paste the codes; I CAN DO THAT 
[*]how to properly edit PHP files, having basic knowledge about their structure; I CAN LEARN THAT 
[*]how to work with FTP client, having FTP access to the hosting server; I THINK I DONT NEED THAT AS I WOULD RUN MY SERVER FROM HOME 
[*]if required, how to create mySQL database and assign necessary user privileges to it, like for example from [cPanel]("http://www.cpanel.com/"); NOT SURE WHAT THIS MEANS 
[*]finally, how to backup your forums and files for archiving purposes, using external software. I CAN LEARN HOW TO DO THAT 
[/LIST]

So my first task now is to read and see how to set up a web server with Ubuntu - or does any one has another suggestion?
Then i have to costumize and secure the web server with firewall and tripwire.

Next step would to install miniBB software or am i missing something?

Any suggestion would be welcome ...

Cheers

---

### Post by cariboo on 2015-06-01
It looks like you don't have very much experience with Ubuntu server. I'd suggest you setup a test server, that isn't connected to the internet and play with it for several months. Be aware that the server iso does not include a gui, so all interactions with the server will done on the command line.

I'd suggest you forget about using FTP, and just stick with SSH, the openssh server includes sftp which is a much more secure way of uploading and downloading files, and can be done from a remote system using a gui file manager.

---

### Post by mastablasta on 2015-06-02
> **patrikmellq said:**
> 
I have a fiber connection with 10 MB up and 10 MB down.

how many people do you aim will be going to your forum? how often?

> 
The server will be a small laptop.

bad idea.

Simple machines forums is also simple.

> **patrikmellq said:**
> 
[LIST]
[*]how to work with FTP client, having FTP access to the hosting server; I THINK I DONT NEED THAT AS I WOULD RUN MY SERVER FROM HOME
[/LIST]

you might want to access it from outside. then what will you use?
> 

[LIST]
[*]if required, how to create mySQL database and assign necessary user privileges to it, like for example from [cPanel]("http://www.cpanel.com/"); NOT SURE WHAT THIS MEANS
[/LIST]

forums use database in the backend. you need to create users and give the privileges. in Ubuntu server you will likely do that via command line or use phpmyadmin GUI.
> 
So my first task now is to read and see how to set up a web server with Ubuntu - or does any one has another suggestion?
Then i have to costumize and secure the web server with firewall and tripwire.


if you don't want to do all configuration and such you can use preloade images such as Bitnami (ubutnu based): [https://bitnami.com/stacks/forum](https://bitnami.com/stacks/forum)  or Turnkey Linux (debian based): [http://www.turnkeylinux.org/taxonomy/term/25](http://www.turnkeylinux.org/taxonomy/term/25)


you can also try them a bit in the virtualbox, which is where you can start. 

I am still not sure what Tripwire actually does, but Ubuntu has other ways of hardening that prevent things before they even come to tripwire.

make sure backups of forums and system are good and safe.

you have a difficult job and I am not sure where you live, but here it is cheaper and less hassle free to rent some server space for forums  and let the host do all the server administration.

---

### Post by patrikmellq on 2015-06-02
Thanks for the support - that sound great using complete server distro with complete forum - then i only need to learn how to costumize - if i understand all correct.
I go to Bitnami (Ubuntu based) and check out MyBB - looks great.

The reason i want to run a forum from home - first is my hobby and i like to learn more about Ubuntu and i like to fix and try new things.
I just tought it was a cool idea running my own forum from home with my own server.

Now i find a great Ngnix web server howto - so i might try that to start my own web page running from home with my own server - The configuration getting up and running with Ngnix web server does not seam to be to complicated.
Now i have two projects - Forum and Web server.

I will post how i do with MyBB solution from Bitnami - if i succed i will post step by step how to get up running with MyBB and make this topic SOLVED.
I am pretty sure that other then me with little coding skills and programming want to learn more and do cool stuff like running own server from home.

Many Thanks Patrik

---

### Post by mastablasta on 2015-06-02
well if you do deploy Bitnami and open it to outside world make sure you harden it afterwards. expect it to be attacked fast. mine was under attack less than 6 hours after I opened the port. 

laptop is ok for experimenting but if you run it nonstop... I am not sure it's a good choice.

---

### Post by SeijiSensei on 2015-06-02
Another vote for [Simple Machines Forum]("http://www.simplemachines.org/")

---

### Post by patrikmellq on 2015-06-02
I will buy a computer that will run as server - but for now - when learning i will try to set up MyBB forum with my laptop.
I install XUbuntu with XFCE LTS 14.04 and will install Firestarter to configurate my firewall and i will install Tripwire on removable media.

I assume MyBB is secure by default - but i will search for security issues using MyBB forum.
So i might tweak it or change common settings to secure the MyBB forum.

Will test it with free .TK domain ...

---

### Post by patrikmellq on 2015-06-02
[B]
I run the MyBB and notice some questions and fields that i don't know what to type.[/B]

Step 1: This i understand ...

[IMG]http://i61.tinypic.com/293kbw8.png[/IMG]

Step 2: This i understand ...

[IMG]http://i60.tinypic.com/znvvhv.png[/IMG]

Step 3: This i understand ...

[IMG]http://i60.tinypic.com/mjnuwl.png[/IMG]

Step 4: This i understand ...

[IMG]http://i57.tinypic.com/25ivp7p.png[/IMG]

Step 5: This i understand ...

[IMG]http://i60.tinypic.com/m7weiq.png[/IMG]

Step 6: This i understand ...

[IMG]http://i57.tinypic.com/mloz7m.png[/IMG]

Step 7: This i not understand - i understand the field with my user name and password - but not what to type in the field "smtp host" and "smtp port" and what kind of "secure connection" to pick.
And this is the last step in the installation guide.

[IMG]http://i62.tinypic.com/10xvn6w.png[/IMG]

---

### Post by patrikmellq on 2015-06-02
How about i use gmail, as i provide that in the beginning of the tutorial.

SMTP Host:

```

tls://smtp.gmail.com

```

And STMP Port

```

465

```

Is this correct settings - well i will try ...

---

### Post by TheFu on 2015-06-02
> **patrikmellq said:**
> I assume MyBB is secure by default - but i will search for security issues using MyBB forum.

NEVER assume any thing you install on a server is secure by default. That is fantasy land - it doesn't exist.
BB systems are pretty well known for being hacked. These forums were hacked last year and if Canonical cannot run a secure forum/BB system, then what hope do you have?

The suggestion to spend 6 months learning was a good one. I know you won't listen - I wouldn't and I didn't back when I was new. 

There is a sub-forum here on security with lots of useful links. Review the "sticky" thread for basic security, then review the "server security" thread.  Nothing is secure by default. Never assume that.  Linux and Unix security is about details and not making any small mistakes. Practice is needed to avoid those mistakes and a little more than a basic understanding of Linux at the CLI level is necessary.

Still - this should be fun.

---

### Post by patrikmellq on 2015-06-03
> **TheFu said:**
> NEVER assume any thing you install on a server is secure by default. That is fantasy land - it doesn't exist.
BB systems are pretty well known for being hacked. These forums were hacked last year and if Canonical cannot run a secure forum/BB system, then what hope do you have?

The suggestion to spend 6 months learning was a good one. I know you won't listen - I wouldn't and I didn't back when I was new. 

There is a sub-forum here on security with lots of useful links. Review the "sticky" thread for basic security, then review the "server security" thread.  Nothing is secure by default. Never assume that.  Linux and Unix security is about details and not making any small mistakes. Practice is needed to avoid those mistakes and a little more than a basic understanding of Linux at the CLI level is necessary.

Still - this should be fun.

Thank you - i will read the sticky topics about security. But i don't run server the common way. I run a package that is install on my computer that include "PHP my admin" & "MyBB" - are you saying i should modifie does files?
I mean i install this on my computer Ubuntu LTS 14.04 with UFW & TRIPWIRE. So should i worry that some one will make intrusion on my computer or the "MyBB" Package & PHP my admin" software?

So what is the conclusion - that i secure my computer running the - MyBB & PHP My Admin package - or should i start to modife and change things with the software package with MyBB & PHP My Admin package.

The MyBB & PHP My Admin software is running from my /home/patrik/ folder

Lets say some one hack my /home/patrik/ folder with MyBB & PHP My Admin package - then Tripwire will notice this change as i monitor the /home/patrik folder.
I know that Tripwire does not prevent intrusion, but it will show me if i have one intrusion, so that feels like a secure solution, that some one from the bad internet can not hack my computer without me notice.
I mean they can not hack Tripwire and hide the intrusion as i have the Tripwire database running on removable media.

I search for security issues at Bitnami and find the following: (This has to be the latest known security issues by Bitnami)


[LIST]
[*][2013-11 PHP security issue]("https://wiki.bitnami.com/security/2013-11_PHP_security_issue") 
[*][2014-04 Heartbleed Bug]("https://wiki.bitnami.com/security/2014-04_Heartbleed_Bug")
[LIST]
[*][Heartbleed on Windows]("https://wiki.bitnami.com/security/2014-04_Heartbleed_Bug/Heartbleed_on_Windows") 
[/LIST]
  
[*][2014-06-05 OpenSSL CCS Injection Vulnerability]("https://wiki.bitnami.com/security/2014-06-05_OpenSSL_CCS_Injection_Vulnerability") 
[*][2014-09-25 Critical security issue in bash (CVE-2014-6271, CVE-2014-7169)]("https://wiki.bitnami.com/security/2014-09-25_Critical_security_issue_in_bash_CVE-2014-6271_CVE-2014-7169") 
[*][2014-10-15 POODLE issue with SSLv3 (CVE-2014-3566)]("https://wiki.bitnami.com/security/2014-10-15_POODLE_issue_with_SSLv3_%28CVE-2014-3566%29") 
[*][2015-01-27 GHOST: glibc gethostbyname buffer overflow CVE-2015-0235]("https://wiki.bitnami.com/security/2015-01-27_GHOST%3a_glibc_gethostbyname_buffer_overflow_CVE-2015-0235") 
[/LIST]

So PHP security issue i should read and understand - as i have PHP My Admin installd - it clear explain how to watch out for script and changes from a hack - it show how to prevent, discover and remove hack script.
I read does topics and study them - then i should be pretty secure.

---

### Post by mastablasta on 2015-06-03
he is saying and (I can confirm this) that default settings on server software install are very lax regarding security. you need to harden it yourself after install.

PHP & other server things need to be hardened as much as it makes sense. of course hardening might make it more difficult for users to sign up. so you need to balance it all well.  read, learn, try/play before opening the port to outside world.

as for smtp over gmail - it does work, however my account got blocked by google for some reason. I told them on numerous times that it should not be blocked as it didn't violate their ToS. they basically had an automated email sent out telling me how to unblock it. I used to do it once or twice before. but this time that unblocking page sends me back to their "complaint form" rather than unblocking it. no idea what is wrong and how to get help on that. anyway I plan to make a new account once I do the restore of server (has a system drive crash) sometime next week.

it's just all easier with the host (if you plan webservices) - the goods ones have good and regular backups, protection, help you harden website etc.

---

### Post by patrikmellq on 2015-06-03
i Have been thinking about what your wrote and what TheFu wrote - maybe it more easy to rent a forum - but i was thinking it could have been fun as hobby to run your own forum - Bitnami show how to look for intrusion and how to deal with intrusion.
 But when i am at sleep or at work i cant check for intrusions and hacks and does are common if i understand it all correct.

I will make a last effort and see if i can install and run Tripwire with PHP and make Tripwire email me if there is one intrusion - that would be safe and secure.
As i have my email online with my mobile phone so would i notice email from Tripwire in the same moment there is one hack or intrusion towards my forum - but i am not sure if you can costumize Tripwire with PHP

One other solution i start to think about is running a closed web server on cd - once you burn it and get it up running - then there can not be any instrusion.

---

### Post by TheFu on 2015-06-03
> **patrikmellq said:**
> 
I read does topics and study them - then i should be pretty secure.

"Security" is not a checkbox. It is a process. Nothing can replace understanding the system, understanding the possible attack vectors, and placing multiple fences (never just 1) in the way for every method that a bad-guy-hacker might use to attack your server.  Tripwire can be hacked. Every tool can.

"pretty secure" can only be proven by history, not current actions or predictions. Until you've been hacked, it is hard to really understand.  

I've had 2 servers hacked - most recently in 2002. Guess what was the most important item for knowing what actually happened and when it happened?








Backups.  Versioned, daily, automatic, backups. 

With those I could see exactly what had be touched on the hacked system. Without those, I would have been guessing and the only answer would have been to reload the OS from scratch and rebuild the applications and configuration again.  I did get an email after-the-hack every time they tried to escalate to root - had about 14,000 emails in the morning waiting for me.  Attackers are smarter these days. I find it highly likely that I wouldn't know about the hack for over a month.  Just look at all the spam emails with fishing links on webservers out there. Every one of those web server has been hacked in some way.  Right now, I'd guess that 2 million web servers are hacked and their owners don't know it.  I suspect that 1.5M of them are running php - no, I don't have any proof, but php webapps have been proven to be less secure over the years. Don't know why, just that they are the most hacked things.  Sorta like Windows is the most hacked OS. It is probably just a numbers thing - regardless of the real reason, it is just easier to avoid php webapps for our company. We still have multiple layers of security for every service. 

**Being paranoid is a good thing for people running services on the internet.**

So - be certain to have a recovery plan for after your system(s) are hacked. What will you do then? It is smart to have this plan regardless of OS and service. How much data will you loose? Is that acceptable?

My intent is not to stop you try doing this, rather it is to set proper expectations for the level of effort necessary. Many people run servers and don't get hacked. Many people run servers, get hacked and do not know it.  Many people run servers and are secure (as far as they know).  Nobody runs a server and KNOWS it is secure. NOBODY.

---

### Post by patrikmellq on 2015-06-03
TheFu - point is taken - i understand your perspective - no one is secure and you are on a jorney keeping things running smooth.
So it might be best to skip the idea of running my own forum from home - to much work to keep it secure and running smooth.

What else can i do? If i still want to learn and experiment - maybe i can create a logserver to check all my traffic with all my computers.
I assume that could be much easiar to run and try to keep secure for a home network.
What would i get out of that - i assume i would learn how to administrate a server and learn how to read traffic with logs.
This would help if i later would like to advance.

---

### Post by andrew.coughlin@gmail.com on 2015-06-07
This is information that you will need to connect to a mail server.  If you are doing testing you will probably want to setup a mail server, if not you might be able to leave it blank or give it some dummy information and go on.  But if it tries to validate the information then you will probably need to setup a mail server using sendmail or some other kind of mail program.

---

### Post by mastablasta on 2015-06-08
> **patrikmellq said:**
> TheFu - point is taken - i understand your perspective - no one is secure and you are on a jorney keeping things running smooth.
So it might be best to skip the idea of running my own forum from home - to much work to keep it secure and running smooth.


well it is easier if you transfer that "privilege" to a good host

> 
What else can i do? If i still want to learn and experiment - maybe i can create a logserver to check all my traffic with all my computers.
I assume that could be much easiar to run and try to keep secure for a home network.
What would i get out of that - i assume i would learn how to administrate a server and learn how to read traffic with logs.
This would help if i later would like to advance.


what do you want to do? you could setup soem LAn server for your own use like NAS or maybe some picture gallery or a media server. or maybe even a VPN.

the thing with security is the less things you are running the less things can get hacked and the easier it is to secure it and monitor it. while dedicated hacker will get you hacked most are just probing attacks for known weaknesses. good backups help you recover from a hack fast.

i had a misfortune that my host had only 2 backups (1 week and 2 weeks). both were compromised. i did have a manual backup, so i could restore from that and added additional security after cleanup. it still get's attacked but at least the IP's get blocked and there are periodic scans and i setup my own additional backups.

but like it was mentioned even security software is not allmighty. i remember how a few months ago fail2ban failed to register certain hack attempts. reading throguh forums i found a workarround until the bug is fixed. it's constant battle.

but with good backups it's much easier. ok hacked, let's restore 3 months old image, analyze attack vector and close it.

---

### Post by LHammonds on 2015-06-09
"Is it possibal to run server from home with own forum on it?"

Sure is as you have already found out.

As others have mentioned, the less you install and have running, the smaller the target for hackers and automated scans/probes.

But don't let the fear of security stop you from learning.  Setup a forum like you'd want for your "main" forum.  Learn how to setup, use, backup/restore and monitor it.

If your main PC is Windows, you can install Oracle VirtualBox and run the server in a VM (Virtual Machine) and spin it up when you want to play around with it and shut it down when you don't.  Learning inside a VM is extremely beneficial because of snapshots (point-in-time backup...but not an "actual" backup).  You can Install the OS, take a snapshot...then install your database and take another snapshot...then install your app and take another snapshot.  If you messed up somewhere, don't start over from scratch, simply go back to a snapshot and pick up where you left off.  I do this with new/unfamiliar systems or trying out upgrades so I can easily revert without doing full-blown restores.  Keep in mind that snapshots are supposed to be temporary so don't make a snapshot of your production server and never look back.  They work like a database transaction log where any changes after the snapshot are recorded so as you can imagine, storage requirements will start to creep up on you rather quick because it will continue to grow and grow even though your "system" does not.

If your forum does not contain "sensitive" information, it might not be a big deal being exposed to the big bad Internet.  Make sure you keep your OS and applications patched on a regular basis on top of initially configuring the system to be a harder target.

I have a few articles in my sig that point to my forum that document how I have installed a basic Ubuntu server and other articles on how I install MySQL/MariaDB, SFTP, MediaWiki, etc.  They might help you to understand some basics of building and maintaining a system over a long period of time.  I'm no expert but I've kept various Ubuntu servers running since version 10.04

LHammonds

---

