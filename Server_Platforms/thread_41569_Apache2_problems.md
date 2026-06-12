---
title: "Apache2 problems"
date: 2005-06-13
forum: Server Platforms
---

### Post by stuffradio on 2005-06-13
Hey,

I'm behind a router, I have installed Apache2 and when I go to [http://localhost](http://localhost) on the linux machine it goes to the default apache install page. However when i try to access it else where I can't access it for some reason, should be able to :S. Another thing, I have vsftpd setup, everything works but how do I make user accounts for ftp and how do I set the passwords up for it in the config file? I know it's under /etc, just don't know what to put for config.


Thanks

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=stuffradio]Hey,

I'm behind a router, I have installed Apache2 and when I go to [http://localhost](http://localhost) on the linux machine it goes to the default apache install page. However when i try to access it else where I can't access it for some reason, should be able to :S. Another thing, I have vsftpd setup, everything works but how do I make user accounts for ftp and how do I set the passwords up for it in the config file? I know it's under /etc, just don't know what to put for config.


Thanks[/QUOTE]
 How are you trying to connect to Apache -- unless you setup a firewall, it should just work.

As for vsftpd, unless you're using virtual accounts, FTP accounts are just system accounts usually with an invalid or non-interactive shell.

---

### Post by stuffradio on 2005-06-14
[QUOTE=LordHunter317]How are you trying to connect to Apache -- unless you setup a firewall, it should just work.
[/QUOTE]

How do you mean? I am just going to [http://myiphere](http://myiphere)
and it should work, I even tried using a dyndns.org I have setup a dyndns called:
[http://freemudhosting.dyndns.org](http://freemudhosting.dyndns.org) and it still doesn't display the page :(. 

For vsftpd how can I tell if I'm using virtual users?

---

### Post by stuffradio on 2005-06-14
I know how to get my website setup on localhost, but I don't know how to get it on the net :(, I also need help determining how to tell if your ftp server is virtual users or not

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=stuffradio]How do you mean? I am just going to [http://myiphere](http://myiphere)[/quote]If it doesn't work connecting via IP address (make sure you're using the address of the machine) then you either have a firewall blocking you, a serious network misconfiguration, or a serious apache misconfiguration.


> and it should work, I even tried using a dyndns.org I have setup a dyndns called:
[http://freemudhosting.dyndns.org](http://freemudhosting.dyndns.org) and it still doesn't display the page :(. Don't bother yet, you'll just confuse things.

---

### Post by stuffradio on 2005-06-14
Great! It's working, now all I need to do is get my ftp server to work. How can I tell if it's using virtual users? I want to make the username the username that I make when you do something like adduser in the command line, I want that to be the username and pass. I am using vsftpd in case you forgot :).

---

### Post by stuffradio on 2005-06-14
Ok, I have a new problem and an old problem.
The new problem is, I got the web server working, it's on a different port... 20000
I'm using [http://freemudhosting.dyndns.org:20000](http://freemudhosting.dyndns.org:20000).
I want to know how to make it so I don't have to put the 20000 at the end, also how do I make it so the web server is setup for all the users that have accounts on my machine?
Now for my old problem, I want to have my ftp server setup so I can specify the username and account passwords, where do i do this? How can I set it up to do this task?

Also, are there any free cpanel like programs I can use for this? It'd be much more easier, and a lot more professional looking.

Thanks

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=stuffradio]I want to know how to make it so I don't have to put the 20000 at the end,[/quote]You umm, run it on port 80.

>  also how do I make it so the web server is setup for all the users that have accounts on my machine?I'm confused by what you mean.  If you mean, give them space to place HTML files, you can use mod_userdir for that.  Note that using that isn't safe for dynamic content with PHP,so don't consider it.

> Now for my old problem, I want to have my ftp server setup so I can specify the username and account passwords, where do i do this?I already told you they are regular system accounts.  If you don't know how to add regular system accounts, you need to **stop** and go do some serious reading on basic UNIX system administration first.

These are fundamental enough questions that if you don't understand how to do them, you'll never be able to reach your intended goal.  Moreover, even if you did, as soon as something breaks/something bad happens, you'll have no clue how to fix it.

I'm not saying this to be mean, I'm saying this to help.  Go read first.  Go buy a book.  Anything.  But you need to take some time to understand what you're trying to do, the implications, and how to do it before blindly rushing through this any further.

> Also, are there any free cpanel like programs I can use for this? It'd be much more easier, and a lot more professional looking.Yes, and no, they're not any more professional.  Unless you intend to do mass host providing, which you're not ready to do.

---

### Post by stuffradio on 2005-06-14
[QUOTE=LordHunter317]You umm, run it on port 80.

I already told you they are regular system accounts.  If you don't know how to add regular system accounts, you need to **stop** and go do some serious reading on basic UNIX system administration first.

[/QUOTE]

I try logging in with a user name and password I made with it, but it doesn't work.

---

### Post by stuffradio on 2005-06-14
Ok nevermind guys, as far as I am concerned, ftpd is wayyyyyyyyy easier to use then vsftpd. I installed it, went to ftp and it worked right away without any configuration! Now all I need help with is how to setup a dns server so I can host domain names on my computer.


Thanks

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=stuffradio]Ok nevermind guys, as far as I am concerned, ftpd is wayyyyyyyyy easier to use then vsftpd. I installed it, went to ftp and it worked right away without any configuration! Now all I need help with is how to setup a dns server so I can host domain names on my computer.


Thanks[/QUOTE]
 The daemon installed by ftpd is an insecure mess, don't use it.

If you can't figure out how to install vsftpd, read the documentation.  You haven't even posted your configuration anywhere, so how do yu expect anyone to help you if it's a configuration error.  What about logs?  Did you look at them?

---

