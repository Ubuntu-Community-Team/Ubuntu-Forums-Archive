---
title: "Apache HTTP + Subversion"
date: 2018-07-04
forum: Server Platforms
---

### Post by kirkkaf2 on 2018-07-04
Hello,

Please bare with me as I am a software developer and not a network administrator.

I have managed to get Apache2 webserver up and running on a Ubuntu 16.04 server, this is currently serving a singple web-app currently being developed in Python/Django. As the project has grown I have thought about setting up SVN or Git, doesn't really matter. Currently it's all stored locally on my development machine, which isn't ideal. Is it common to have a SVN/Git server running on the same machine as my webserver?

As I am using Apache2 for serving my application I read that I can use a module [LEFT][COLOR=#000000][FONT=Tahoma]**mod_dav_svn **to also use a Apache as a repository, can my sever do both simultaneously? 

Thank you. [/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2018-07-04
You should use git.  Git doesn't really have a "server process".  It is just ssh with directories and permissions. If you don't understand DVCS already, there are youtube videos which explain there isn't a "central" server, but purely a social contract. Randal Schwartz did an hour presentation at Google about it.

With git, you can store the files local or remote or both or in 50 places. Which is the main repo is purely your decision. Regardless of what you do, you still need backups.

I wouldn't connect a web server to any version control system that is on the internet. Too dangerous.  You can script a git pull into your production area, assuming it isn't a compiled  language.   NEVER leave compilers on a production server. Why pre-install tools for hackers? 

Developers need the mindset of security first, before functionality.   It is hard to add security into a system that begins without security considered.  In general, a web server should be a web server and nothing else. Security.   Backups - daily, automatic, versioned, are my #1 security tool so  that when something bad happens (not if), there is a way to get back and figure out when the issue was first applied to the system. Without versioned backups, you'll never know.

BTW, apache is capable of running 3,000+ websites via virtual domains, with hundreds of plugins assuming you have the RAM, CPU, disk, networking and don't really care much about security. Webhosts take all sorts of steps trying to secure their massive "shared hosting", but with hundreds-to-thousands of sites on a single OS install, there are bound to be some bad apples who know how to view/take files from other accounts on the same machine.  If you control everything and lock down things correctly, those risks can be mitigated.  But how to do that is beyond what forums can cover.

---

