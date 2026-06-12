---
title: "whats the default root password?"
date: 2010-06-02
forum: Server Platforms
---

### Post by rswitzer on 2010-06-02
I just loaded Ubuntu server 10.04 on and old dell, install went perfect, but it never asked for me to provide a root password. (I could have passed it and hit default, I don't know)I did supply a username and password for a non-root user.

Is there a default root password? What do I do, reload and look closer for a chance to select the root password?

Thanks,
Bob - Melbourne Florida

---

### Post by arrrghhh on 2010-06-02
Ubuntu doesn't really have a 'root' user...

Your non-root user (which is the machine's administrator accout essentially) is what you use to modify things that need 'root' access.  You just precede any command that needs to be run as root with sudo.  Like ```
sudo apt-get update
``` to update the machine.

---

### Post by Bachstelze on 2010-06-02
> **arrrghhh said:**
> Ubuntu doesn't really have a 'root' user...

Yes, it does. Really.

---

### Post by redmk2 on 2010-06-02
> **arrrghhh said:**
> Ubuntu doesn't really have a 'root' user...

The system does have a root user.  The password to access the account is what is elusive.  A simple look at ***ps -ef *** from the command lind will show you the root user owned processes.> 

Your non-root user (which is the machine's administrator accout essentially) is what you use to modify things that need 'root' access.  You just precede any command that needs to be run as root with sudo.  Like ```
sudo apt-get update
``` to update the machine.

@ rswitzer,
For more information on sudo see [**_here_**]("https://help.ubuntu.com/community/RootSudo").

---

### Post by arrrghhh on 2010-06-02
Details, details.  I just said Ubuntu doesn't *really* have a root user, because it doesn't get used... Try to su to root.  You can't unless you put a password on the account AND enable it.  Don't confuse that with saying that no root access exists, that would be silly.

---

### Post by Bachstelze on 2010-06-02
> **arrrghhh said:**
> Details, details.  I just said Ubuntu doesn't *really* have a root user, because it doesn't get used...

That's like saying your car doesn't have an ashtray if you don't smoke, because it doesn't get used...

---

### Post by redmk2 on 2010-06-02
> **arrrghhh said:**
> Details, details.  I just said Ubuntu doesn't *really* have a root user, because it doesn't... Try to su to root.  Don't confuse that with saying that no root access exists, that would be silly.

It always the details.  Whether its "really, kinds like, or maybe" the system has a root user.

To be VERY specific the term su means "switch user" and if you don't have the password you can't switch.  This in no way means that root user doesn't exist.

Read the link I provided.  Here is a quote for the second: paragraph 
"**By default, the root account password is locked in Ubuntu**. This means that you cannot login as root directly or use the su command to become the root user. However, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in - it allows authorized users (normally "Administrative" users; for further information please refer to AddUsersHowto) to run certain programs as root without having to know the root password."

---

### Post by arrrghhh on 2010-06-02
I've read the article.  I know there's a root user, but Ubuntu locks it... so effectively there is no root user.

It's all semantics, I think we can quit here.  The OP has more than enough answers to his questions, and that doc on root/sudo has a plethora of good information.

---

### Post by redmk2 on 2010-06-02
> **arrrghhh said:**
> I've read the article.  I know there's a root user, but Ubuntu locks it... so effectively there is no root user.

> Not so! 

It's all semantics, I think we can quit here.  The OP has more than enough answers to his questions, and that doc on root/sudo has a plethora of good information.

You can only control you.  If you wish to stop then do so.

---

### Post by arrrghhh on 2010-06-02
> **redmk2 said:**
> You can only control you.  If you wish to stop then do so.

Some people's children...

---

