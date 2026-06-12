---
title: "Not Quite an ABSOLUTE Beginner, but close"
date: 2012-02-21
forum: Server Platforms
---

### Post by zarberg on 2012-02-21
Hello all,
 
Some background on me so you know what you're dealing with:
 
I've been in IT since 1993, when I got a job at my college's helpdesk. I mostly dealt with Mac and Windows until my senior year when I was volunteered to run the DEC Alpha backup since none of the full-time staff members wanted to be on campus on a Saturday. My next few jobs were Windows/Mac server and desktop support, but I have played around from time to time with Red Hat, Suse, and a few other Linux flavors. I've been running a simulation baseball league with a program that makes heavy use of online stuff - up until now I've been running it on a Win2008 server with Apache. A few weeks ago I discovered there is a group of Perl scripts out there for use with the baseball sim program that I run my league with that have extensive grep and ls usage, so I've decided to take the plunge and setup a Linux server with Apache and FTP (the two things I absolutely need to make the league run). Ubuntu seems like the friendliest/easiest way to go.
 
So, what am I here for? As I said, my Linux experience is limited, but my general computer experience is fairly high. Essentially I want to do the following:

[LIST]
[*]setup a Linux virtual server using VirtualBox on my home machine (that is constantly connected to the internet). I have Dynamic DNS setup so my registered DNS name gets forwarded to my router which then handles port forwarding based on port/protocol. The basic Linux setup seems pretty straight forward, although the lack of a root user makes me wonder if it's the best choice
[*]setup on that Linux server FTP access for 2 accounts - 1 account I'd like to have complete access to the entire server, the other account I'd like to have access to a specific folder so players in my league can upload their team files (done through the game). Since I never know when players in the league will update their teams they'll probably need write and delete access (in case they have a team file already there and go to write a new one - team files are always the same name, that's handled by the game and can't be changed). I've played around a bit with VSFTPD, but never quite ironed out the details with permissions and folders and if I should use system users or virtual ones.
[*]setup on the Linux server a web server with CGI -specifically Perl- capabilities. I'd prefer to use Apache because I have quite a bit of experience with Apache for Windows, but I'd be willing to try out another if someone convinces me it would be better. Essentially the web server needs to display a lot of pages (there's more than a few thousand seperate HTML files), and be able to run the perl scripts. The following URL goes to a forum that explains what the perl scripts to and has a link to the readme.doc for instructions on the scripts: [http://www.ootpdevelopments.com/board/ootp-mods/161441-ootpou-online-utilities-2-1-a.html](http://www.ootpdevelopments.com/board/ootp-mods/161441-ootpou-online-utilities-2-1-a.html)
[/LIST]I've given it a couple of tries already and Apache2 for Ubuntu is different enough from Wintel that it's slowing me down, specifically I'm used to having just an httpd.conf file, not a bunch of little files that tie off a single config. Is there a decent link/doc/site that talks about the heirarchy of how Apache2 works compared to 1?
 
As far as FTPing goes, I'm wondering if it would be better to setup real system users or have virtual users, especially since I want one of those FTP accounts to be able to access anything in the www folder. I suppose if this is too much of a hassle I can run the league output on my Windows machine and just copy stuff if there is an easy way to to map my Windows machine on Linux or my Linux machine on Windows. I tried that already, but permissions always seem to get in the way and when copying 3 folders each with a few thousand files I didn't really want to do it via command line.
 
Thanks in advance for any advice people may give.

---

