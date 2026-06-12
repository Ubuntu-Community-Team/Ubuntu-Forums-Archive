---
title: "Dansguardian segfault using blacklist"
date: 2008-08-06
forum: Server Platforms
---

### Post by thisismyname on 2008-08-06
I am trying to use the blacklist from [www.urlblacklist.com](www.urlblacklist.com) with dansguardian on 8.04 server.

I have found that if I include the porn and adult url catagories from the big blacklist in /etc/dansguardian/bannedurllist when I attempt to start dansguardian after a number of minutes it fails the output is:

/etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian
 Segmentation fault
                                                                         [fail]

The two lists are quite large
/etc/dansguardian/blacklists/adult/urls - 6213711 bytes
/etc/dansguardian/blacklists/porn/urls - 5553458 bytes

I am using some of the other smaller catagories without a problem.

I can include the porn and adult domains catagories in /etc/dansguardian/bannedsitelist without any problems yet these files are much larger than the urls files I am having problems with.

I have verified that the list itself is ok by using it on an older machine running 6.06 server without any problems.

Any ideas? Thanks in advance

---

### Post by slochewie on 2008-08-19
I am actually in the process of downloading the blacklist myself and configuring dansguardian for the first time. I've never used them with dansguardian before, but I have used them with squidguard before. It was quite some years ago when I first setup those blacklists to work with squidguard. It's does the same thing though with squidguard. Those files are just too large as txt files. I do know I had to convert them to a db file. I want to say I had to run them through berkeley db and convert them to db files. Then squidguard could efficiently parse them and not crash when it started up... I'm assuming something similar needs to be done for dansguardian. If I figure it , I'll try to remember and post my solution here.

---

### Post by slochewie on 2008-08-19
I'm pretty sure I was wrong about the berkeley db thing. I believe that to be purely a squidguard thing.

I think the answer is found on the following faq page
[http://urlblacklist.com/?sec=faq](http://urlblacklist.com/?sec=faq)

You'll need to install rl or random-lines
```
sudo apt-get install randomize-lines
```

Then cd to one of those trouble directories.
```
rl /etc/dansguardian/blacklists/adult/domains
```

Then uncomment the line for the adult urls list in /etc/dansguardian/bannedurllist and restart dansguardian

You can repeat this procedure for the porn and adult domains and urls lists

---

