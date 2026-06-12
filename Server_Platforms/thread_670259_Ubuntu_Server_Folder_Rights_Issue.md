---
title: "Ubuntu Server Folder Rights Issue"
date: 2008-01-17
forum: Server Platforms
---

### Post by tet3828 on 2008-01-17
I just installed my first ubuntu server at my office... well actually my first server period and I am swimming in a sea of questions.

I have a LAMP server running as well. I am to the point where I can type the ip of the server into the browser of any computer in my office and pull up the pages within the www directory of the server.

That directory is where I am running into my problem. I can't copy anything into it with out using WEBMIN. Is an nnoying and timely process since I am writing the php/mysql database in dreamweaver on a different computer. 

[B]While writing the script on my XP box I want to be able to drag and drop or even save my scripts directly to a folder on the server, so I can test my script as I go. but it says I don't have premission.

Is there a way I can give myself permission using WEBMIN? or at least the pesky terminal?[/B]

the only login name I have setup on the server the the one I configured when I installed the server. 

the whole su and sudo thing confuses me because it seems like SOMETIMES it gives me root rights for what I need to do but it asks me for the password for the non-root user I created. hmmm. Will I ever understand this stuff.:confused:

---

### Post by jingo811 on 2008-01-17
Is this the answer to your permission problems?
[http://virtualseafarer.com/renaissance/desktop_lamp/chapter4.html#ch4](http://virtualseafarer.com/renaissance/desktop_lamp/chapter4.html#ch4)

[COLOR="Red"]If you use my solution for a commercial server then you're probably gonna get hacked some day!!![/COLOR]
The proper way is to manage the groups permission accounts on your Linux system but I haven't experimented with it so I can't give such advice at this time.  Maybe next year.

---

### Post by tet3828 on 2008-01-17
Thank you that worked! If anyone has the time can you please explain why.

From my under standing the sudo command proforms the action as the root user. it did, great. but why did it as my for my password I am obviously not the root user if it wouldn't let me write to the folder begin with..

where is the security in letting a non-root user change permissions of a folder owned by the root user? 

Thanks! relieved but still moderatly confused.

---

### Post by Dr Small on 2008-01-17
Check out RootSudo at the wiki:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

That should help explain some things.

Dr Small

---

