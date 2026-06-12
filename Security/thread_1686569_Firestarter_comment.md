---
title: "Firestarter comment"
date: 2011-02-12
forum: Security
---

### Post by Irihapeti on 2011-02-12
No, I don't use Firestarter, though I did at a time in the dim, dark past, so this is not about how to use it, but something else.

I see a recurring scenario: a new user talks about using Firestarter, and is promptly told that it's no longer supported and that UFW is the current option.

My question is this: how come it is still available in the repository? Where is the proper place to suggest getting it removed, so that it no longer confuses new users? Has this been suggested in the past and been ignored?

---

### Post by cariboo on 2011-02-12
I actually tried to get firestarter removed from the repositories last year, but until there is no maintainer, and it's popularity drops, it will remain where it is. My efforts actually had the opposite affect, more people use it now than when I started my campaign. :)

From [http://popcon.ubuntu.com/by_inst:](http://popcon.ubuntu.com/by_inst:)

> 
Rank  Name                             installed Vote  old           recent  no-files  Maintainer 
2826  firestarter                    153883  3427 149694   710    52 (Paul Cupis)         

---

### Post by Irihapeti on 2011-02-12
I did wonder if something like that might be the case. 
:confused:

---

### Post by Rubi1200 on 2011-02-13
> **cariboo907 said:**
> I actually tried to get firestarter removed from the repositories last year, but until there is no maintainer, and it's popularity drops, it will remain where it is. My efforts actually had the opposite affect, more people use it now than when I started my campaign. :)

From [http://popcon.ubuntu.com/by_inst:](http://popcon.ubuntu.com/by_inst:)
Yes, it does seem that despite many of us on the forum telling people not to install Firestarter, it is still being downloaded and used as much as, if not more than, previously.

I always recommend gufw if they want a GUI app.

---

### Post by movieman on 2011-02-13
> **Rubi1200 said:**
> Yes, it does seem that despite many of us on the forum telling people not to install Firestarter, it is still being downloaded and used as much as, if not more than, previously.

It's a while since I've used firestarter, but I suspect the problem is that, from what I remember, gufw's GUI feels very clunky in comparison. It's more powerful if you want to set up complex rules, but firestarter was easier to set up the kind of rules that normal users want to configure (e.g. 'turn on ftp access').

---

### Post by Irihapeti on 2011-02-13
gufw will let you set up simple rules as well, quite easily. (see thumbnail)

I think it might be a relatively new addition to gufw, though.

---

### Post by cariboo on 2011-02-13
I think the reason the majority of people that install firestarter continue using it, is because of the logging function, they can see connections being blocked while the interface is running.Of course this is wrong, as the usage instructions (but who reads those anyway) say that you should start the gui to set up firewall rules, then you never need to run it again.

I guess if people are going to continue running it, we should at least instruct them on how to use it properly.

---

### Post by Irihapeti on 2011-02-13
> **cariboo907 said:**
> I think the reason the majority of people that install firestarter continue using it, is because of the logging function, they can see connections being blocked while the interface is running....

And then, as we know, they freak out about all the dangerous connections that are attacking their computer... :)

---

### Post by COMPUTIAC on 2011-02-14
I removed firestarter and installed gufw. Will this run all the time from start-up. When I click on the icon, it calls for me to enter a password. Is this normal?

COMPUTIAC

---

### Post by cariboo on 2011-02-14
You only need the variuos firewall frontends to set the rules initially, once that is done, you don't need to run them again until you need to adjust the rules. To check if ufw is running, open a terminal and type:

```
sudo ufw status
```

---

### Post by COMPUTIAC on 2011-02-14
It comes up saying I need to be root to view it. How do I set myself up to access root. Already have Adm. rights.

COMPUTIAC

---

### Post by The Cog on 2011-02-14
> I removed firestarter and installed gufw. Will this run all the time from start-up. When I click on the icon, it calls for me to enter a password. Is this normal?
...
It comes up saying I need to be root to view it. How do I set myself up to access root. Already have Adm. rights.

You need to take admin rights temporarily - you don't "have admin rights", you have the right to assume admin rights - like the right to borrow the keys. You don't carry the keys all the time, in case you get mugged. Hope that makes sense. 

To run a program with admin rights (run as root) you prefix a command with "sudo" - meaning SuperUser Do. E.g. "sudo ufw status" as you have already been shown. For GUI applications, prefix the command with "gksu" instead. Some GUI applications know they need root rights, and ask for the password themselves.

See this better explanation:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

P.S.
Recent windows has an equivalent to sudo, called "Run as administrator".

---

