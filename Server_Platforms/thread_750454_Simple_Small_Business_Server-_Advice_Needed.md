---
title: "Simple Small Business Server- Advice Needed"
date: 2008-04-09
forum: Server Platforms
---

### Post by Geeman20000 on 2008-04-09
Dear All, 
I have been a long time lurker at the site and have looked at the various ways that people are using ubuntu, as a server platform.  

Over the last few months I have been increasingly looking at the small business sector particularly those organizations with less than 10 users.

Over on the wiki, there are a few drafts for a small business server version of ubuntu,   Each of which have made excellent progress, however seem to have been made over complicated due to feature creep etc.  

I recently sent round a questionnaire to about 80 businesses in nearby area under the guise of a bit of market research.

Basically what I've found is that about 15 of them are using Google apps and interestingly enough about 40% planned on implementing it for mail within the next 3 years. 

Therefore it is not necessary to have a full small business server, however a simple business server will suffice.( at least for a start!)

What aspects would need to be done to have a single box that will:
a) Create itself as a domain controller.
 b) Allow admins to create users and allocate quotas as simply as uploading a csv file?
 Eg Bart, Simpson, email , password, department, role, quota.

 Optionally
 c) connect to a nas server for raid storage. (eg buffalo NAS can fit into Active
 directory domain) admin specifies ip etc
 d) Automatically create vpn for all users and allow for remote access at the tick of a check box!
e)integrate with google apps

---

### Post by HermanAB on 2008-04-09
Hmm, the best way to do that is with Suse or Mandriva and with either of those, it is pretty much a no-brainer.  Good luck achieving that with Ubuntu though.

---

### Post by Geeman20000 on 2008-04-10
really? pity. 

I did some research work into what is being done on the Ubuntu small business server, front and it seems to have hit a wall...
WIth 3 different versions of the project, perhaps they could be merged into 1?

Here is the summary: [https://wiki.ubuntu.com/SmallBusinessServer](https://wiki.ubuntu.com/SmallBusinessServer)

---

### Post by jonabyte on 2008-04-10
I shared your view while first looking/installing the server edition, but to be honest with you I kind of like the basic install.

I have found adding "features" such as samba, etc quite easy and the documentation gives all the info you need to install/config.

I will be doing my 50th server install/setup/config soon and the setups are all a little different.

Not sure if that really helps you or not, but I like you suggestions for adding users in (b), I wonder if someone has already created a script to do this.

---

### Post by songshu on 2008-04-10
mmmmm,

ubuntu server (basically debian) is more robust, easy and flexible then for example suse or mandriva.....IF and definitely IF you as an admin are willing to learn to do this the debian way, and that would be via the command line.

If you would be the one installing and maintaining those servers for these companies as described in your post, the required study to learn this would be well worth it in my opinion.

But i guess that is not what you are looking for if you simple want to setup a box in small companies and let them do the easy daily tasks themselves when it comes to adding new users etc....

I know however that attempts are being made to get the ebox-platform in hardy universe and apparently they are making good progress.

my guess is if you want to with ubuntu for described task then e-box on hardy would be the way to go.

[http://ubuntuforums.org/showthread.php?t=707492&page=1](http://ubuntuforums.org/showthread.php?t=707492&page=1)

---

### Post by Geeman20000 on 2008-04-11
Thanks for the support people, I did some research work and scouting around, and was really surprised to see how many times this has been tried.  Some of the original projects go way back to 2005. 

I added my initial research here: [https://wiki.ubuntu.com/SmallBusinessServer](https://wiki.ubuntu.com/SmallBusinessServer)

which summarizes all the current (and past) efforts. (all 13 of them!)

From looking around, the most popular way to do what I want is to wait around for ebox. I wanted to investigate the ebox for gutsy unfortunately the site is 404 at moment.

---

### Post by bluefrog on 2008-04-11
installing a ubuntu server or a ubuntu desktop if you don't feel like working only with command line and then reading/following the menu "by example" of [http://samba.org](http://samba.org) will give you what you want in no time.

James Dupin

---

