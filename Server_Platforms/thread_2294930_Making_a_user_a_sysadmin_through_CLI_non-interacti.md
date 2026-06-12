---
title: "Making a user a sysadmin through CLI non-interactive."
date: 2015-09-14
forum: Server Platforms
---

### Post by cole12 on 2015-09-14
Hi I am brand new to Linux and I am starting to go through a class about Linux server. I have been trying to figure out harder commands for a week now, until one person told me that there was a community that can help. As the title states I am trying to a user a sysadmin that should be able to sudo with no root password. so far I got echo "(user) ALL (ALL:ALL) >> /usr/sbin/visudo. But nothing seems to be working. I am hoping the community will be able to help me understand linux better in the semester to come because at the moment I am thrown into the deep end with no clear way of which way is up.

---

### Post by darkod on 2015-09-14
I don't know if that method for editing the sudoers file is correct, I have never seen it. In ubuntu I use:
```
sudo visudo
```

Of course, you need to have at least one user with sudo rights first (for example the first created user when installing). Under the line for root add lines for each user you need. Save and close the file. Next time you log in with the new user, it will have sudo rights.

---

### Post by Habitual on 2015-09-14
> **cole12 said:**
> echo  "(user) ALL (ALL:ALL) >> /usr/sbin/visudo. But nothing seems to be working.Missing the closing quote.
Try 
```
echo "(user) ALL (ALL:ALL)" >> /usr/sbin/visudo
```

---

### Post by cole12 on 2015-09-14
Hmm I put in the closing quote, but now I am greeted with a blank line as if I am missing something. Now I know I can use the sudo visudo, but I am somehow suppose to put the user into the group without having the person installing the script manually touch anything. Thus the non-interactive part. If it wasn't for that, then this would be slightly easier.

---

### Post by cole12 on 2015-09-14
I tried adding in the closing quote and was greeted with something I have yet to see. I basically get a > on the next line. I'm not so sure if I put in the right code now?

---

### Post by nerdtron on 2015-09-15
Better not logout from the system,  I think /usr/sbin/visudo is a binary file and redirecting output to a file is dangerous.

From your original post, you need to edit the /etc/sudoers file, so it should be like this:
become root first:
```
 sudo -i 
```
Then use the echo command: (sysaduser is the username of the systemadmin you want to be passwordless on using sudo )
```
 echo 'sysaduser ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers 
```

Just do it ONCE only. If you have an error, post the screenshots here. and also post the last line of the sudoers file:
```
tail /etc/sudoers
```

---

### Post by darkod on 2015-09-15
I still fail to see any real benefit from this. If it's a learning exercise, there are other ways to learn without playing with /etc/sudoers, one of the most important files in linux system.

For a small number of users, I can see no benefit of scripting especially when the sudoers file specifically says "you MUST edit it with visudo". Just use ssh and add the user you want to add. After all, how often will you be modifying the file???
For a large number of users you will probably use some sort of directory like LDAP, so that gives you other options to create administrators.

One thing I found researching this topic, is the built-in sudo group. I have never tried doing it like this, but you can try. How about just adding a user to the sudo group without touching (manually or by script) /etc/sudoers. Will that achieve your goals?

Try something like:
```
sudo usermod -aG sudo <username>
```

That will add the user <username> to sudo group. Then try if it has sudo rights. If it works, this would be much easier and safer to script, compared to playing with /etc/sudoers like you are not supposed to.

PS. I just tested this and it works perfectly. Just add the user to the built-in group sudo and that's all you need. Much better solution than messing with /etc/sudoers with echo.

---

