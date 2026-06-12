---
title: "Server and Hosting ?'s"
date: 2007-05-30
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-30
I have been using linux for about 5 or 6 years but only on the desktop. I have recently made a ubuntu server and been testing it and it seems to work great. My question is a friend of mine is a graphic designer and creates web pages for clients. I am going to start hosting the sites but wanted some of your thoughts about what I am running as I don't know a lot about servers as of yet. 

1) The computer is a athlon xp 2600+ with 1 gb of ram and I need to put a new bigger hd in it. Is this a good enough computer?

2) What would you recommend partition scheme would you recommend? I have always used pretty basic ones.

3) Is ubuntu server reliable enough or should I be looking at debian, centos, or freebsd?

I want to make sure that I have a reliable setup for the clients. Just curious about your thoughts?

Thanks

---

### Post by tgm4883 on 2007-05-30
What is your upload speed?

---

### Post by blmartin777 on 2007-05-30
it is 512/kbs now. I am going to switch companies to at least 756/kbs but maybe more.

---

### Post by tgm4883 on 2007-05-31
what king of internet connection?  Make sure it doesn't violate your TOS

---

### Post by blmartin777 on 2007-05-31
It is a business line. they are aware of what I am doing.

any opinions on the best os for the job?

---

### Post by tgm4883 on 2007-05-31
I think the stable debian branch is more stable than the ubuntu server

---

### Post by craigp84 on 2007-05-31
It doesn't matter which OS you go for too much. Pick the one that solves your problem best - it'll save you time setting it up and maintaining it.

Centos / redhat have SE Linux out of the box. This means that even if there was an exploit available in apache, you wouldn't be vulnerable. Also it restricts the success of attacks against software like Wordpress etc. which runs inside apache.

A common mistake is to interpret the name "debian stable" wrongly. The stable in the name means that they will not frequently update the OS with new features etc. (but will still provide bug fixes). In that way, debian stable and Ubuntu Dapper are very similar, with differences boiling down to package versions more than anything else.

Ubuntu's biggest win is the size of it's community. There are so many people who've already done what you're trying to do, and have written up howto's etc. so it becomes very easy to extract the necessary knowledge to make a success of this task.

Freebsd could be a good choice, server hardware support is better than linux for example (out of the box). But that comes at a cost, it's better support because there are so many "blobs" - binary drivers without source code, supplied by 3rd parties - but it can be worse stability wise. For example: noone can see the bugs in the blobs to fix them.

You hardware, is plenty beefy. Your bandwidth will choke your site before that hardware gets anywhere near 50% loaded.

Hope this helps,

Craig

---

### Post by blmartin777 on 2007-05-31
Thanks, I have feisty installed now and seem to have had no problems. But I haven't put anything outside of my own stuff yet and am still checking and testing stuff. 

Is feisty stable enough or should I consider debian? I have read that debian and ubuntu our good for servers but the file structure is much different then other distros as servers. Does that really matter? I have read great things about centos but I have never been a fan of rpm based distros.

---

