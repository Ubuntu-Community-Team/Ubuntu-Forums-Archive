---
title: "Can't change user password"
date: 2011-08-25
forum: Security
---

### Post by Compgeke on 2011-08-25
Ok, I'll start with the basics of what I'm running, Ubuntu 10.04 LTS with all the latest updates. The problem is I had to change my computer password to "password" so I could have my laptop checked by the school before I could connect it to the network and I was very reluctant to give my actual password to anyone, especially if the contract says that you can take anything off my computer without needing permission from anyone.

Well, I changed the password and now that I'm trying to change it back the users window just freezes when I try and change the password. I've tried 4 times, let it sit overnight once and it never changes. I really hate the password of password and it's as insecure as having no password at all.

Now, I've also been getting a message to enter my key chain password since I changed the password that I didn't have before I changed the password. This I'm assuming will go away once I have the password changed back or am I stuck entering this every time?

I know for sure that no settings could be changed because everything needs the root password and I never gave the root password to him.

Also, one more question, since I can't get this to change using the Users Settings control panel would changing it using passwd mess anything up? I've done that before on an old server we had as volunteers to play around with and the one that set the password had left.

---

### Post by sidzen on 2011-08-25
sudo 
[PHP]passwd username[/PHP]and follow instructions.

[[SIZE=2]Reference[/SIZE]]("http://www.slackbook.org/html/essential-sysadmin.html#ESSENTIAL-SYSADMIN-USERS-PASSWDS")

---

### Post by AlexDudko on 2011-08-25
Yes, passwd will do the same thing for you.
Why not making a new account for school?

---

### Post by Compgeke on 2011-08-25
Just need one account because if anything I do at home the school tries to blame on me sudo rm -rf / works great...

I will use the command and let you know the result (it should change the password unless my install is corrupt).

---

### Post by bodhi.zazen on 2011-08-25
> **Compgeke said:**
> Just need one account because if anything I do at home the school tries to blame on me sudo rm -rf / works great...

I will use the command and let you know the result (it should change the password unless my install is corrupt).

sudo rm -rf /

will not work in Ubuntu.

---

