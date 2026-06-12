---
title: "Need to upgrade Samba"
date: 2012-07-07
forum: Server Platforms
---

### Post by ndnd on 2012-07-07
Hello all,
I have 9.10 Server edition. I want to only upgrade Samba package which I downloaded using $wget

Now how do I install it on the system.  I am not familiar with linux system and therefore need some help with the exact commands to help me install.


I believe the steps would 

1) Download the binary
2) Find the right file in the directory  (how to find it ? what would be the command what would be the extension of the binary ?) 
3) use some sort of installer like 'apt' or 'dbkg'  (how to link apt or dbkg to the binary  to start installation) 

Please note I can't directly updgrade using apt-get install since the source lists points to the older location of the ubunut repository. 

Thanks in advance for your help.

---

### Post by Bucky Ball on 2012-07-07
You are kinda thinking windows there. Samba is FULLY compatible with Unix/Linux and there are no difficult tweaks really. The bad news is 9.10 is well out of support and you are probably as 'new' as you can get with that release. 

[http://au.search.yahoo.com/search;_ylt=A0oGkmFzzfdPTwIAyi8L5gt.?p=samba%20repository%20ubuntu&fr2=sb-top&fr=altavista&rd=r1](http://au.search.yahoo.com/search;_ylt=A0oGkmFzzfdPTwIAyi8L5gt.?p=samba%20repository%20ubuntu&fr2=sb-top&fr=altavista&rd=r1)

There may be a repository but your release reached end of life (and is not necessarily secure, bad for a server) in April last year. 

You don't need to download Win stuff or look for bin files, though. But again, if you run these commands:

```
sudo apt-get update
sudo apt-get upgrade
```

... you will find that very little will happen. You would be well advised to upgrade your Ubuntu release on your server. Good luck. ;)

---

