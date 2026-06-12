---
title: "[SOLVED] changing an existing user into a system account"
date: 2008-08-14
forum: Server Platforms
---

### Post by jerome1232 on 2008-08-14
Currently on my little teamspeak server I have a limited account creativly called teamspeak, it has a home directory of /home/teamspeak. Teamspeak server and tss2perlmod are installed in that home directory

Now I'm thinking instead I want to create a system user called teamspeak, move the files to /opt/teamspeak  chmod/own them as root:teamspeak rwxrwx--- (or what would be the "correct" directory to place the program) and then put my main user (the one I can ssh in as) in the teamspeak group (it already is).

I also want to create a new user give it admin rights and take admin away from my current admin user.

Is there a better way to arrange things? 

Are the following steps the correct way to do things.

```
sudo -i
mv /home/teamspeak /opt/
chown -R root:root /opt/teamspeak
deluser jeremy teamspeak          # remove current admin from the group
deluser teamspeak  
rm -rf /home/teamspeak           # makeing sure the old home direcotry is gone
adduser --system teamspeak
adduser joe  #made up admin user the real name will be different I will be adding any user other than jeremy and teamspeak that I see under my current admin user actually
adduser joe admin
deluser jeremy admin  # this won't break my current root shell will it?
adduser jeremy teamspeak
chown -R root:teamspeak /opt/teamspeak
chmod -R ug+rwx,o-rwx /opt/teamspeak   # Give owner and group rwx access other no access is this a secure type of permission?
exit

```

---

### Post by wdaniels on 2008-08-14
Looks sane enough to me.

There are always other ways to do things (for example you could modify teamspeak to be a system user instead of recreating it) but this way seems clear, simple and so far as I can tell should do what you want.

---

### Post by jerome1232 on 2008-08-14
lol yeah turns out system users don't get a group so I just removed teamspeak user completely and chown'd the files as root:teamspeak

---

### Post by wdaniels on 2008-08-15
> **jerome1232 said:**
> lol yeah turns out system users don't get a group so I just removed teamspeak user completely and chown'd the files as root:teamspeak

AFAIK there's nothing inherently special about system users other than the id range and the default conventions that they are created with no login shell and with the "nogroup" group. It might be worth bearing in mind that you can change the id with "usermod -u <id> username" in future.

Unless anyone knows something I don't about system users?

---

