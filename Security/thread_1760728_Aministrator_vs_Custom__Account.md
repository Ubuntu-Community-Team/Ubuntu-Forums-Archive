---
title: "Aministrator vs Custom  Account"
date: 2011-05-17
forum: Security
---

### Post by Frogs Hair on 2011-05-17
I have a friend that has a custom instead of a user account on his Wubi installation . From a security standpoint what is the difference between an administrative account and a custom account since both appear to login as root. I know there are slight permission differences , but are they equally a bad idea to use unless needed.

---

### Post by 3xp10r3r|X13 on 2011-05-17
[FONT=Courier New]Hello there,
I'm not sure about the situation after a wubi installation, but usually a custom user has to type sudo to perform an administrative task. This is very useful, because that way you don't have to worry about some program accessing your actual system and making fatal changes to it.

However, if both would log in normal it's just a matter of groups your type of account belongs to. The admin account is surely able to access more functions than the custom account, therefore a harmful program would be able to access those functions as well(referring to the admin account)

The thing I still don't get, is that the custom account logs in as the root user. This would mean that it has the rights of the root user, who usually has all rights.

So root user equals root user --> So it doesn't matter which account you're using --> you have the same privileges (The ones of a root user)

So why are you logging in as a root user? It's sort of "NOT SAFE"!!!

Hope this helped :)

PS: If I got sth. wrong please correct me, because as I said, I'm not used to the wubi installation (there might be some differences I don't know of, although there shouldn't)
 [/FONT]

---

### Post by Frogs Hair on 2011-05-17
I don't log in as root , If you read the the post I am asking on behalf of a friend who logs in to the custom account .

---

### Post by 3xp10r3r|X13 on 2011-05-17
[FONT=Courier New]Oh sry, I got the question wrong and a part of your statement.
So you mean the ability of logging in as root.

In this case it's just the groups they belong to. You can check them out and change them by going on to system and the group management (as far as I remember)[/FONT] [FONT=Courier New]

It's really just a slight difference of rights. The custom account has surely less rights.[/FONT] [FONT=Courier New]

But you already knew that.[/FONT] [FONT=Courier New]

Sorry, I couldn't help[/FONT]

---

### Post by 3xp10r3r|X13 on 2011-05-17
[FONT=Courier New]But you might want to check this out:

[http://ubuntuforums.org/showthread.php?t=1082837](http://ubuntuforums.org/showthread.php?t=1082837)

It's pretty much a discussion about the topic you're interested in.


Good luck :)
[/FONT]

---

### Post by bodhi.zazen on 2011-05-17
Are you asking about Linux or Windows accounts ?

In general, on Linux, an administrative account is one which has access to the root account, either by sudo or su. On Ubuntu this means the user is part of the admin account.

A custom account is one that has whatever groups memberships and permissions you set.

I would assume similar logic applies to the Windows configuration options.

---

### Post by Frogs Hair on 2011-05-17
> **bodhi.zazen said:**
> Are you asking about Linux or Windows accounts ?

In general, on Linux, an administrative account is one which has access to the root account, either by sudo or su. On Ubuntu this means the user is part of the admin account.

A custom account is one that has whatever groups memberships and permissions you set.

I would assume similar logic applies to the Windows configuration options.

In Users and Groups on Ubuntu there are three account types , User , Administrator , and Custom . Is the custom account the equivalent of logging in as root or administrator in terms of security ?

---

### Post by sisco311 on 2011-05-17
> **Frogs Hair said:**
> In Users and Groups on Ubuntu there are three account types , User , Administrator , and Custom . Is the custom account the equivalent of logging in as root or administrator in terms of security ?

Users and Groups (a.k.a users-admin from the gnome-system-tools) is a GUI application for managing (guess what) users and groups.

According to /etc/gnome-system-tools/user-profiles.conf 

a *Desktop User* is a member of the following groups:
cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,video

an *Administrator* is a member of:
cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,**admin**,sambashare,lpadmin,video

and a *Custom* user is a *customized* user who is not an *Administrator* or a *Desktop User*. ;)

Some or most (citation needed from a more knowledgeable person) groups are deprecated on a modern Linux OS like Ubuntu. But, by default, the most important group on Ubuntu is the **admin** group.

By default, all users from the **admin** group are allowed to run any command as another user including root via sudo (they need password authentication) and policykit allows them to run some commands as another user via the GUI.

---

### Post by Frogs Hair on 2011-05-19
a *Custom* user is a *customized* user who is not an *Administrator* or a *Desktop User*. :wink:

This is what I was wondering about , because my friend uses a root password (only password) to login to the custom account as his only account . I don't think it's the best idea ,  that is why I was trying to find some clear difference between the Custom and Administrative  account when only only one password is in use.

---

