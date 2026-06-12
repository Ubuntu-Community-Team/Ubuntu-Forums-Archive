---
title: "What did I actually do here?"
date: 2010-02-07
forum: Security
---

### Post by Silvertones on 2010-02-07
Before I really knew what I was doing I had that Windows mentality and thought I needed to be able to have root priviliges without using the terminal & sudo. I went into sys/admin/users & groups. I clicked on root then clicked on unlock. I then highlighted root, clicked on properties and "set password manually. I then locked back up.
So what have I done? Should I reverse this? how do I reverse this?

Thanks

---

### Post by zeroseven0183 on 2010-02-07
Did you enter anything in the Set Password By Hand field?

By default, the root password is locked in Ubuntu. Entering something on that field sets the root password (which is not necessary in most cases).
You may want to revert it and have it stay that way (default) and use **sudo** instead when doing administrative tasks.

For more information, you can check out this page [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Silvertones on 2010-02-08
yes i did set a pssword. I do not log in as root i always login as me. If I can set the password is there any point in resetting it back to the default? Does this command```
 sudo usermod -p '!' root
``` just reset the password or is it deeper then that? Help me out here with the right thing.

---

### Post by cdenley on 2010-02-08
> **Silvertones said:**
> yes i did set a pssword. I do not log in as root i always login as me. If I can set the password is there any point in resetting it back to the default? Does this command```
 sudo usermod -p '!' root
``` just reset the password or is it deeper then that? Help me out here with the right thing.

That sets the password hash back to the default value, which I think is what you want.

---

### Post by Silvertones on 2010-02-08
OK thanks I'll do that.

---

### Post by Silvertones on 2010-02-08
OK so I reset it but I'm trying to get my head around this. OK now the root account has no password set so at the login screen someone can't log in as root but if they log in as me they can just set the password for root. What's the difference guessing my password or guessing the root password. AM I MISSING SOMETHING?

Thanks

---

### Post by amac777 on 2010-02-08
You are correct that if someone knows your password, they can do anything on your system. Make sure your password is a strong password.

---

### Post by cdenley on 2010-02-08
Almost all attempts to authenticate remotely will attempt to use the "root" user. Everyone knows it is there, and it has full access. At least now they have to know your username AND your password. Of course, if your computer is already compromised and they have local access, then it doesn't really matter since they can see who is an admin user, guess that user's password just as easily as root's, then use "sudo". Automated attacks probably wouldn't assume you're using ubuntu, though. In fact, they would probably waste time trying to guess the "root" password for hours, since they wouldn't know it has no password unless they realized it is ubuntu.

---

### Post by Silvertones on 2010-02-08
OK now it makes sense. From the outside they already know the user name,root, so only need to guess the password but as you say you can't guess  something that doesn't exist. I would think to guess both user name and password would be next to impossible.
Thanks for all the replies.

---

### Post by doas777 on 2010-02-08
I've always seen it as 
```
sudo passwd -l
```
based on man it looks like that command and the usermod -p do similar things.

---

### Post by cdenley on 2010-02-08
> **doas777 said:**
> I've always seen it as 
```
sudo passwd -l
```
based on man it looks like that command and the usermod -p do similar things.

Yes, similar. "passwd -l" will simply insert the "!" before the password hash, so it is effectively the same as replacing it with "!" except the original password hash can easily be restored/recovered. If I remember correctly, in previous versions, that option expired the account which caused problems, so I always use the "usermod -p" command.

---

