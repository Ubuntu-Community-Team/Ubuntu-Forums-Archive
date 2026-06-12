---
title: "Need help setting up some server apps"
date: 2008-03-29
forum: Server Platforms
---

### Post by aetherh4cker on 2008-03-29
I'm going to be setting up a ventrilo server on my Ubuntu 7.04 machine and I have quite a few questions.  If you can answer any of them, I would greatly appreciate the help.

First, I've read that you should create a new user to specifically run the ventrilo server, or something like that.  Here is a quote on what I read:

> **xarmian said:**
> While I've never used ventrilo, this is likely to be the same as any other service.. so since ventrilo will be started as a service, don't worry about the password, make it something random.. Also, set it to an unprivileged account, and i'd assume you can leave the privileges as-is.  Then change to the "Advanced" tab and change the shell to "/bin/false"

In reality you should set it to no password.. this would mean editing the shadow file (/etc/shadow) with sudo (such as 'sudo pico /etc/shadow' or 'sudo gedit /etc/shadow'), find the line starting with 'ventrilo' and remove the random sequence of characters between the following colon and the next colon and replace it with an "!".

So, my issues with this is simply my lack of knowledge.
1.  How do I setup a new user completely from command line (via ssh)?
2.  How will I set the machine to run the ventrilo server on startup using the special user?

3. As for installing the server itself, I think I'll be able to manage just from reading the ventrilo FAQ, however I'm still open to any advice there.

4. And my final issue is how do I set IPTables to allow ventrilo to go through?

I guess that's all.  I eagerly await your replies!

---

### Post by IceaTronic on 2008-03-29
> 
1. How do I setup a new user completely from command line (via ssh)?

Ok, if your using SSH to remote into said server, the easiest way is to go:

sudo adduser

and follow the prompts from there, you can ignore all the pazazz about phone numbers and what not, just make sure you give it a username password and the NAME field, just put in like Ventrillo Server User

> 
2. How will I set the machine to run the ventrilo server on startup using the special user?


cronjob at start up, or some other form of script that is run at boot.

> 
3. As for installing the server itself, I think I'll be able to manage just from reading the ventrilo FAQ, however I'm still open to any advice there.


Yep, thatd be the easiest way, and if you do get stuck, if they have forums etc, that would be good place to start

> 
4. And my final issue is how do I set IPTables to allow ventrilo to go through?


Uhm, im never brilliant when it comes to iptables, so i cheat and use webmin:

sudo apt-get install webmin

then [http://yourservernamehere:10000](http://yourservernamehere:10000)

Hope this can get you pointed in the right direction dude!

Cheers,

IceaTronic

---

### Post by aetherh4cker on 2008-03-29
Alright, I set up the user "ventrilo", but how do I do this part of what he said:  

Also, set it to an unprivileged account, and i'd assume you can leave the privileges as-is. Then change to the "Advanced" tab and change the shell to "/bin/false"


Also, if anyone has more info about making ventrilo run on startup, I'd appreciate that.  The last thing I made run on startup I just put it's path in rc.local.  However, I didn't specify what user runs it, or anything fancy like that.

---

### Post by IceaTronic on 2008-03-29
Hmm, good question, cant remember off the top of my head about the /bin/false thing.

The unpriveledged account, basicalyl means, dont give it any privledges, so creating it and leaving it as is, is fine ;)

the cron side of stuff, googleisyourfriend :)

---

### Post by aetherh4cker on 2008-03-29
For the life of me, I cannot get this server to run as the user "ventrilo".

I'll keep searching, but if anyone wants to give me a hint, I'd appreciate it.

---

### Post by Sef on 2008-03-29
moved to server platforms.

---

### Post by aetherh4cker on 2008-03-31
Hmm, I somehow knew being moved to Server Platforms would be the death of this thread.

Google has let me down, so I'm bumping my post.  How do I get it to run as user "ventrilo"?

Thanks...

---

