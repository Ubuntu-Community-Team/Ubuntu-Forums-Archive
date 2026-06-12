---
title: "Apache2 on small Pc ? Recommendation  reqest"
date: 2011-03-31
forum: Server Platforms
---

### Post by highspider on 2011-03-31
---------------------------------
I have built a website for my dads business; on my ubuntu.  It works great.
---------------------------------
I want to put it on a old, small office pc with Linux.  
(it ran xp pro slowly, and I will not leave anything windows on it). 
----------------------------------
Its a small Plumbing company. (so its not going to get a 1000 hits a day)
---------------------------------
The only things I need are:
[COLOR=SeaGreen]Apache2, 
sendmail, 
Perl (web CGI),  
IPtables (firewall),
SHH (for admin).[/COLOR]
----------------------------------
I don't need a X11 or programs, ect, ect, ect
I manage it by s-shell from my Ubuntu.
----------------------------------
Is there a guild for removing Ubuntu stuff I don't need. 
Or should run a smaller linux distro or Freebsd to just run the Apache2 server.
----------------------------------
.
.

---

### Post by CharlesA on 2011-03-31
Just do a server install and install apache, perl, sendmail and ssh.

---

### Post by highspider on 2011-03-31
> **CharlesA said:**
> Just do a server install and install apache, perl, sendmail and ssh.

But thats a giant operation system how can shrink it down.  This pc wont even have a monitor, mouse, or keyboard hooked up to it.  Just a cat 5" and power cord.  And I will never use the other programs.

---

### Post by CharlesA on 2011-03-31
> **highspider said:**
> But thats a giant operation system how can shrink it down.  This pc wont even have a monitor, mouse, or keyboard hooked up to it.  Just a cat 5" and power cord.  And I will never use the other programs.
The server install has no GUI. It's what I run on my server.

What are the specs of the pc you want to run it on?

---

### Post by highspider on 2011-03-31
> **CharlesA said:**
> The server install has no GUI. It's what I run on my server.
What are the specs of the pc you want to run it on?
[COLOR=Red]Who! IDK that! [/COLOR]"my own stupid ceases to amaze me!"
--------------------------------------
its small
Specs are here... (its not good)
[http://www.laptopsetc.net/Article-Dell_dimension_3000_specs.shtml](http://www.laptopsetc.net/Article-Dell_dimension_3000_specs.shtml)
---------------------------------------
[COLOR=SeaGreen]Intel P4 @ 2.8 GHz 
512 ram -- I think it has 1gz its at home right now[/COLOR]
--------------------------------------
NOTE: sites only 6 .htm's + 3 .css + guessing 3 perl htms for logs/usage/warnings (no java or sql)
          graphics stored at (-- on a free graphic storage site)
          a perl sendmail.pl w/ captica 
          some basic check firewall warnings and usage scripts (not wrote yet)
          and service NO-IP2 for dynamic ISP (forgot on other post)
--------------------------------------
.
.

---

### Post by CharlesA on 2011-03-31
That should run it fine.

---

### Post by highspider on 2011-03-31
> **CharlesA said:**
> That should run it fine.
Thank you.
Took awhile (get pc to and fro home to office + download & burn to disk + install)
   install was the fastest .

Have to play around more to set up cloud and ssh 
[COLOR=Red]THANK YOU

I came back and edited this because the ubuntu server ROCKS.  
 It's loading my pages just fine-fast on very small computer.
    Getting my first .com address took longer to figure out (the host forwarding delay part) 
          then whole server install (I have past linux exp)

[/COLOR]  [FONT=Arial][COLOR=SeaGreen][COLOR=Black]I have my first website up and running good[/COLOR][SIZE=3][COLOR=Black]!
[/COLOR]
&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][COLOR=SeaGreen]
[/COLOR][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829; I [/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829; MY [/COLOR][/SIZE][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]UBUNTU[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]  &#9829;
[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3] &#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][COLOR=SeaGreen][SIZE=3]&#9829;[/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=SeaGreen]&#9829;[/COLOR][/SIZE][/FONT]

---

