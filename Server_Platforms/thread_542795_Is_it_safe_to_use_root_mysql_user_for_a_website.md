---
title: "Is it safe to use root mysql user for a website"
date: 2007-09-04
forum: Server Platforms
---

### Post by viciouslime on 2007-09-04
I am installing something called AmpJuke and by default it wants to use the root mysql account, is this safe? Whenever I install anything else that uses mysql, joomla! for exmaple, I always create a new account and database manually then set it to use that. I just realised though that the only reason I do this is because I thought it was more secure, I don't actually know if it is and now these default settings in AmpJuke have made me wonder...

So, is it actually good practice/any more secure to create a new user with only rights on the one database, or am I actually just wasting my time?

---

### Post by LaRoza on 2007-09-04
No, make a new account, with the privileges the app needs. NEVER use the root acount.

(Those default settings are what a cracker would exploit)

---

### Post by viciouslime on 2007-09-04
> **LaRoza said:**
> No, make a new account, with the privileges the app needs. NEVER use the root acount.

(Those default settings are what a cracker would exploit)

Thanks LaRoza, i thought this would be the case, but I wasn't sure :)

---

### Post by LaRoza on 2007-09-04
No problem!

(Never accept default passwords and accounts on anything, they are easily exploited)

---

### Post by Brazen on 2007-09-04
yeah never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever never ever use the root database account.

If it is hardwired in to the application, then I would use a different application because it's programmers are idiots.  If for some reason your would still want to use such an application, then I would create a new admin account with rights to entire server (just like root) and then restrict root down to a single database.  You'll just have to use the new account for all your administration.

also: ampjuke is now on my short list of cool software.

---

### Post by viciouslime on 2007-09-05
> **Brazen said:**
> 
also: ampjuke is now on my short list of cool software.

It is quite cool, there are lots of things like it, but all of them seem to be unmaintained...

---

### Post by KevinM1 on 2007-09-05
Another $0.02 regarding root access to a MySQL server:

In addition to creating another user for web apps that only has the bare minimum of access to the server in order for those apps to do their job, I also like renaming the root user to something else.  I'm not sure if it really adds another layer of security, but not having the root user actually *named* root makes *me* feel a bit safer.

Just an idea.

---

### Post by LaRoza on 2007-09-05
> **KevinM1 said:**
> I'm not sure if it really adds another layer of security, but not having the root user actually *named* root makes *me* feel a bit safer.

Just an idea.

Good idea.

Admins and root accounts in any system should not have names reflecting that. If a "bad guy" sees an account named "admin" or "root", who do you think they'll focus on? Also, if an account has a default name, change it, it is a lot easier to crack if there is a constant.

---

### Post by Brazen on 2007-09-05
> **LaRoza said:**
> Good idea.

Admins and root accounts in any system should not have names reflecting that. If a "bad guy" sees an account named "admin" or "root", who do you think they'll focus on? Also, if an account has a default name, change it, it is a lot easier to crack if there is a constant.

Oh yeah, a lot of trojans and script kiddies depend on the admin name being something like 'root', 'administrator', 'admin', 'super user', etc.  Changing it to something less obvious is a usefull security measure.  I always create a new admin account on my linux machines and then disable the 'root' account.

---

### Post by viciouslime on 2007-09-05
Good idea, thanks :D

---

