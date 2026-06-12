---
title: "Server update blog."
date: 2009-08-22
forum: The Cafe
---

### Post by dragos240 on 2009-08-22
Hi!

Dragos240 here again. Someone in one of my topics about the server asked me how many topics about the server I was going to make. He had a point. I will now post the updates about the server's status on my blog located below:

[http://webnerdblog.wordpress.com/](http://webnerdblog.wordpress.com/)

If you at any time at all want to check out the blog, please do. Posting on the blog makes this a whole lot cleaner.

---

### Post by pwnst*r on 2009-08-22
;)

---

### Post by PurposeOfReason on 2009-08-22
Once you get your server up you should just blog there. ;)

---

### Post by dragos240 on 2009-08-22
> **PurposeOfReason said:**
> Once you get your server up you should just blog there. ;)

I will.

---

### Post by dragos240 on 2009-08-22
And here, but not in a different topic!

---

### Post by dragos240 on 2009-08-22
Ok. Update for the forum, the server is UP! On hamachi:
Network: Dragos240
Pass: lokalhost

User: ubuntuforums
Pass: ubuntu
Port: 45
IP: 5.239.37.83
I have added 2 things:
Xorg through ssh, and
an easter egg.

Try it. Have fun. You are limited to your own folder, and is recommended that you create a sub-home for yourself. You are limited to 50 processes. Latest kernel updates.

EDIT: Hamachi acting wierd.......

---

### Post by Sporkman on 2009-08-22
Can we try to crash the server?

---

### Post by dragos240 on 2009-08-22
It's right here. Sure, but tell me how you did so after you do.

---

### Post by dragos240 on 2009-08-22
Anyone want to crash the server? Tell me how you do so.

---

### Post by -grubby on 2009-08-22
Uhh... it doesn't appear that you're logged into Hamachi.

---

### Post by dragos240 on 2009-08-22
Really? It says so here, that I am logged in. Also I can see myself on another machine? Are you logged in?

---

### Post by dragos240 on 2009-08-22
Nevermind, it's connected, but it's not working.

---

### Post by dragos240 on 2009-08-22
Errrr...... it's up though....... 

OH! Let me try something....

Errrr..... nevermind.

---

### Post by Sporkman on 2009-08-22
> **dragos240 said:**
> Anyone want to crash the server? Tell me how you do so.

I'd write a script that continuously writes to disk until your hard disk ran out of space & your system comes to a halt.

Also, If I run 50 processes which allocate large amounts of memory, that'll bring your system down as well.

---

### Post by hanzomon4 on 2009-08-22
What is the command to login... I can't seem to get it to work

---

### Post by dragos240 on 2009-08-22
> **Sporkman said:**
> I'd write a script that continuously writes to disk until your hard disk ran out of space & your system comes to a halt.

Also, If I run 50 processes which allocate large amounts of memory, that'll bring your system down as well.

I have an idea on how to prevent the first, user quotas. But not the second....

Also, hamachi is acting up, it's down for now.

---

### Post by dragos240 on 2009-08-23
Server UP!

Server: 24.34.53.70
Webserver: 80
SSH: 45
FTP: 21

Enjoy.
Goals: Find easter egg, start X application, and MOVE 'ZIG'.

---

### Post by dragos240 on 2009-08-23
Well.... it's definitely up.... but nobody is going on, it's sunday, 2 days before the estimate. The server is up. Anyone want to come on in??

User: ubuntuforums
Pass: (the distro this forum is about)

---

### Post by PurposeOfReason on 2009-08-23
The website is up just fine but can't connect through ssh. Did you make sure to open port 45 on your router?

---

### Post by dragos240 on 2009-08-23
Yep. I did that.

---

### Post by dragos240 on 2009-08-23
Canyouseeme.org sees port 80, 45, and 21.

---

### Post by PurposeOfReason on 2009-08-23
> **dragos240 said:**
> Canyouseeme.org sees port 80, 45, and 21.
Whatever just happened it's up now. Don't know what was wrong before, might have been my end.

---

### Post by dragos240 on 2009-08-23
It wasn't. I set up hosts.deny to deny all sshd.

I fixed that.

Also find the easter egg. Lol. Also if you want you can run some X programs by:
ssh -X -p 45 ubuntuforums@24.34.53.70

---

### Post by dragos240 on 2009-08-23
Use this for status:
[http://www.dnzh.com/serverstatus.php](http://www.dnzh.com/serverstatus.php)

Also ssh has changed to 53, so you can check it on that site. :D
[ ]("http://www.iwebtool.com/server_status")

---

### Post by dragos240 on 2009-08-23
Have fun, it's up.

---

### Post by dragos240 on 2009-08-23
Who created 9999 files? Lulz. At least they were all empty. The server is still up. Suggestions file created.

---

### Post by hanzomon4 on 2009-08-23
```
ssh -p 45 ubuntuforums@24.34.53.70
ssh: connect to host 24.34.53.70 port 45: Connection timed out

```

Not working

Nevermind the port changed

---

### Post by dragos240 on 2009-08-25
Hi everyone,

it looks like avahi is back. Yep, he used the ftp server that I left on to post offensive messages inside the home folder. I have copied all of this as proof that it was he who did this. Also I have found his ip, as he was the last one to logon to this server, and I saw his actions posted on the ftp log. He had also posted frequent links to topics on the linsux forums. Honestly, there are just some people out there. Some people, who's existance is solely based on getting people angry. Does anyone know where I can report this guy on linsux? I don't beleive they support what he is doing in any way, shape or form.

-Dragos240

---

### Post by jamieh on 2009-08-25
> **dragos240 said:**
> it looks like avahi is back.

A system which facilitates service discovery on a local network is "back"?

> **dragos240 said:**
> Does anyone know where I can report this guy on linsux? I don't beleive they support what he is doing in any way, shape or form.

He was banned on Linsux months ago. What could you possibly think Linsux would do about him? Feel sorry for you and cuddle all your problems away?
Do you think Linsux "owns" him or something?

Some people...

---

### Post by dragos240 on 2009-08-25
I didn't know he was banned.....

---

### Post by DeadSuperHero on 2009-08-25
Our staff doesn't approve of those types of things, but it's not our job to play parent for every member that comes in and out of this place.

---

### Post by -grubby on 2009-08-25
It's not like his banning from Linsux would have affected whether or not he'd have done things to your server.

---

### Post by jamieh on 2009-08-25
> **dragos240 said:**
> I didn't know he was banned.....

Believe me, he's been nothing but trouble since day one.

---

### Post by jamieh on 2009-08-25
> **jamieh said:**
> Believe me, he's been nothing but trouble since day one.

Reporting him on Linsux will somehow make it so he does no longer access your server.

---

### Post by DeadSuperHero on 2009-08-25
> **jamieh said:**
> Reporting him on Linsux will somehow make it so he does no longer access your server.

That makes absolutely no sense at all.

---

### Post by jamieh on 2009-08-25
> **Mr. Psychopath said:**
> That makes absolutely no sense at all.

My account MoFoJoseph is unbanned.

---

### Post by Viva on 2009-08-25
> **jamieh said:**
> Believe me, he's been nothing but trouble since day one.

Looks like he has taken your* campaign a bit too far.

*Your as in linsux's

---

### Post by gletob on 2009-08-25
Is it working for everybody else?  I'm getting nothing

---

### Post by ViperChief on 2009-08-26
> **jamieh said:**
> A system which facilitates service discovery on a local network is "back"?



He was banned on Linsux months ago. What could you possibly think Linsux would do about him? Feel sorry for you and cuddle all your problems away?
Do you think Linsux "owns" him or something?

Some people...

Interesting...since the only person I banned "months ago" was you...

---

### Post by ViperChief on 2009-08-26
> **jamieh said:**
> My account MoFoJoseph is unbanned.

Good for you.

dragos, I sent you a PM.

---

### Post by hoagie on 2009-08-26
I can't find your server at 24.34.53.70 using port 45 through ssh.

---

### Post by Tristam Green on 2009-08-26
> **Viva said:**
> Looks like he has taken your* campaign a bit too far.

*Your as in linsux's

campaign?

:confused::confused::confused:

---

### Post by dragos240 on 2009-08-26
> **hoagie said:**
> I can't find your server at 24.34.53.70 using port 45 through ssh.

It may be down for a bit..... and the ftp too. An announcemen has been made on the http server at:
[24.34.53.70]("http://24.34.53.70")

---

### Post by ViperChief on 2009-08-26
> **Viva said:**
> Looks like he has taken your* campaign a bit too far.

*Your as in linsux's

What campaign? I didn't know we had a campaign. 

And why are so many threads here derailed with Linsux as the new topic? This thread is about dragos' server, not members/banned members of Linsux.

---

### Post by Elfy on 2009-08-26
> **ViperChief said:**
> And why are so many threads here derailed with Linsux as the new topic? This thread is about dragos' server, not members/banned members of Linsux.

Indeed - let's keep this thread on topic please, there is no need to be talking about other forums. 


@dragos - Even if the person in question was indeed a member elsewhere then I don't see what could be done. Any issue you have with them is between you and them.

---

### Post by dragos240 on 2009-08-26
> **forestpixie said:**
> Indeed - let's keep this thread on topic please, there is no need to be talking about other forums. 


@dragos - Even if the person in question was indeed a member elsewhere then I don't see what could be done. Any issue you have with them is between you and them.

Yes, he shouldn't be a problem now, I traced his IP, and now he is blocked. I love /var/log

---

