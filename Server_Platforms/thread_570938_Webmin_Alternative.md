---
title: "Webmin Alternative"
date: 2007-10-08
forum: Server Platforms
---

### Post by quietas on 2007-10-08
First off, I have used Webmin many years and understand it os poo. So much poo that it was removed from Ubuntu repos and the devs cried they were so happy. There, that's done.

Webmin works. With all it's bugs and flaws, it works.

At work I use it for user creation for login's, LDAP, and Samba. Multiple servers, easy batch user creation that is dumped out for each user from my MS Access user database.

At home I use Webmin to manage my Samba logins, and CUPS for my 3 printers.

I know everyone despises Webmin lately, but is there a working alternative? Web based like Webmin would be optimal. It needs to be able to do: Users, LDAP, Printers, Samba.

Anything out there that fits the bill?

---

### Post by netlogic on 2007-10-08
Not exactly, but you can try cpannel. There is another one that runs top of Debian. I just can't remember it. I played with it earlier this year. If it comes up, I will gladly let you know.

---

### Post by HermanAB on 2007-10-08
Well, there is virtualmin, which is specifically geared towards Apache with virtual domains.  Essentially it is a webmin extension so just another kind of poo.

---

### Post by netlogic on 2007-10-08
Now, it came up... Old age is starting to creep up and I'm not that old!
Try ebox
[http://ebox-platform.com/](http://ebox-platform.com/)

---

### Post by netlogic on 2007-10-08
WARNING: ebox is a bit buggy during the setup. You will manually edit the configuration files. After you got it running, you can run it with the browser.

---

### Post by codmate on 2007-10-09
> **quietas said:**
> First off, I have used Webmin many years and understand it os poo. So much poo that it was removed from Ubuntu repos and the devs cried they were so happy. There, that's done.

Webmin works. With all it's bugs and flaws, it works.

At work I use it for user creation for login's, LDAP, and Samba. Multiple servers, easy batch user creation that is dumped out for each user from my MS Access user database.

At home I use Webmin to manage my Samba logins, and CUPS for my 3 printers.

I know everyone despises Webmin lately, but is there a working alternative? Web based like Webmin would be optimal. It needs to be able to do: Users, LDAP, Printers, Samba.

Anything out there that fits the bill?

Sorry to be cheeky but...
SSH  :p

;)

---

### Post by twistedtwig on 2007-10-09
netlogic, 

do you mean cpanel or is there a cpannel as well?

Is Cpanel available freely ( I did a very quick look and didn't think it was but could be wrong, just had a look while at work).

Thanks

---

### Post by quietas on 2007-10-09
Hehe, I use SSH on a daily basis via putty, but honestly it's slow when you need to input 20 users. I have an Access database with my users at work that I run a query to join all the data and dump it into a batch line for Webmin user creation. 20 lines 20 users, 2 minutes or less.

I've thought about Cpanel, but as I understand it's geared towards ISP's and end user's doing their own setup. Does it actually function as an admin tool replacemnt for Webmin also?

---

### Post by codmate on 2007-10-09
> **quietas said:**
> Hehe, I use SSH on a daily basis via putty, but honestly it's slow when you need to input 20 users. I have an Access database with my users at work that I run a query to join all the data and dump it into a batch line for Webmin user creation. 20 lines 20 users, 2 minutes or less.

I've thought about Cpanel, but as I understand it's geared towards ISP's and end user's doing their own setup. Does it actually function as an admin tool replacemnt for Webmin also?

Could you write a little script that queries the database and makes the required users?

Perl is great for this sort of thing!

I'm sure there are some nice user-creation scripts flying around the web at least  :)
Maybe you can find a script that you just need to feed a list of names too?

Good luck and have fun  :)

---

### Post by quietas on 2007-10-09
Yeah, I could easily change my Access database to give me a useradd line that would do it, but the visual capabilities of seeing and searching 300 users via Webmin is just plain easier. Also I can ctrl-F and fine a specific user faster that CLI. I guess it's all in the way you look at it.

In Webmin's batch mode I feed it lines like this on my file server or mail server:```
create:username::password::100:FirstName Lastname:/home/username:/bin/false:::::
```

I could adjust it for CLI sure, but I also want to be able to set it up for easy use by my peons so that I don't have to create every single user. It's hard to find beginning sysadmins with Linux experience, if they have a web or gui of somesort it speeds up the learning.

---

### Post by netlogic on 2007-10-09
> **quietas said:**
> 
I've thought about Cpanel, but as I understand it's geared towards ISP's and end user's doing their own setup. Does it actually function as an admin tool replacemnt for Webmin also?

Many Control Panel apps are geared towards ISPs now. There are many start an ISP overnight tools. Why don't you try ebox? It is a bit buggy at the install, but once you manually edit few things, it will become a full working system. Also, I tried it early this year, so they might have fixed everything. I still say text processing in UNIX is more power than Access for things you want to do, but some times you need a graphical interface. I had to setup a custom webmin interface for help reset passwords for Help Desk. Try Ebox. I think that is what you need.

---

