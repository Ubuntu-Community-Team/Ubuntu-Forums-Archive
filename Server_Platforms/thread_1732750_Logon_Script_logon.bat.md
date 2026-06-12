---
title: "Logon Script logon.bat"
date: 2011-04-18
forum: Server Platforms
---

### Post by collisionystm on 2011-04-18
Hey guys,

I am running a Zentyal 2.0 box ( its AWESOME. ) And I am currently building it to replace our 9.10 server that is an acting PDC and file share for 100 users.

I have built a few groups and shares and my intention is as follows: Each share belongs to a specific group. Sales share would have a sales group. Marketing has a marketing group... etc. Everyone has access to the Everyone drive. I am using this script

net use * /delete /yes
NET USE L: \\APOLLO\EVERYONE
NET USE M: \\APOLLO\MANAGERS ;nul
NET USE N: \\APOLLO\ADMINISTRATOR ;nul
NET USE O: \\APOLLO\MARKETING ;nul
NET USE P: \\APOLLO\ACCOUNTING ;nul
NET USE S: \\APOLLO\SALES ;nul
NET USE Z: \\APOLLO\Master_Share ;nul

I added the ;nul at the end of the command because if a user does not belong to the share's group, it prompts for a username and password. Having the ;nul makes it skip to the next. The neat part is, it really works and only maps certain drives to certain people who need them. The bad part, it is super fast on Windows XP and slow on 7. What I would like to do is hide the output of my batch here and replace it with a message saying "Mapping your network drives, please do not close this window. It will close automatically upon completion."

Any ideas???? I do not know visual basic very well. This is all done with .bat

Thanks guys!

---

### Post by collisionystm on 2011-04-18
bump

---

### Post by Sirkyuubi on 2011-04-18
you need to do this in ur batch file...

echo Mapping your network drives, please do not close this window. It will close automatically upon completion.
@echo off // turns off the verbose
net use * /delete /yes
NET USE L: \\APOLLO\EVERYONE
NET USE M: \\APOLLO\MANAGERS ;nul
NET USE N: \\APOLLO\ADMINISTRATOR ;nul
NET USE O: \\APOLLO\MARKETING ;nul
NET USE P: \\APOLLO\ACCOUNTING ;nul
NET USE S: \\APOLLO\SALES ;nul
NET USE Z: \\APOLLO\Master_Share ;nul


Chances are this will go so fast that the users wont even have time to read your echo anyways.

let us know how this works out.

P.S. This is not visual basic its simply batch scripting.

---

### Post by collisionystm on 2011-04-18
Well the problem is the @echo off  does not hide all of the output. And it remains slow on Windows 7. And I do know the difference between .vbs and .bat =) sorry for the confusion!

---

### Post by Sirkyuubi on 2011-04-18
here you go

[http://malektips.com/dos0020.html](http://malektips.com/dos0020.html)

If you can't get it to work with this VBscript might have your answer.

Or you could also try writing a simple program that will do it all for you in c.

---

### Post by dtfinch on 2011-04-18
I'd prefix the net use commands (except the delete one and maybe the first one after) with "start /b " to run them in parallel in the same window.

With the number of shares you have, I'd suggest looking into creating a DFS root share, which would let you combine several shares (even from several different servers) under a single drive letter. We have a Z: drive set up like that with a couple dozen shares.

---

### Post by collisionystm on 2011-04-19
> **dtfinch said:**
> I'd prefix the net use commands (except the delete one and maybe the first one after) with "start /b " to run them in parallel in the same window.

With the number of shares you have, I'd suggest looking into creating a DFS root share, which would let you combine several shares (even from several different servers) under a single drive letter. We have a Z: drive set up like that with a couple dozen shares.

Well we currently do have a root share called the F: drive. 

However, I am trying to clean it up. There are tons of folders on there and I feel like users should only see the folders they need to see, whether they have access or not.

Can I make the folders invisible with chmod's? Or do I just need to continue on my quest

thanks!

---

### Post by collisionystm on 2011-04-19
> **Sirkyuubi said:**
> here you go

[http://malektips.com/dos0020.html](http://malektips.com/dos0020.html)

If you can't get it to work with this VBscript might have your answer.

Or you could also try writing a simple program that will do it all for you in c.

Thanks! I renamed logon.bat to logon2.bat and created a primary batch with call logon2.bat  > NUL The > NUL worked great for hiding 80% of the output. If only Windows 7 would map as fast as XP. It times out on each attempt to map and it takes about 10 second intervals. XP just fly's through it. =(

---

