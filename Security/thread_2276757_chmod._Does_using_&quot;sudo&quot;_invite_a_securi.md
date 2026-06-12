---
title: "chmod. Does using &quot;sudo&quot; invite a security risk?"
date: 2015-05-04
forum: Security
---

### Post by mikodo on 2015-05-04
Somewhere in the lost recesses of my mind, I remember reading something to the effect, that using sudo for something in the below sequence, is not advised due to the "possibility" of it adding an unnecessary security risk.

 I am thinking it has to do with "sudo chmod" but, could very well wrong.

Can I have opinions on this please?  

Thank you.

```
sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#**sudo chmod** 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
**sudo chmod** -R a+rwX /mnt/data
```

---

### Post by TheFu on 2015-05-04
The answer is "it depends." Could be safe or not, depending on the end-goal you seek.

You can read what each of those commands does, if you like. Since Linux is a multi-user OS and file and directory permissions are at the center of the security model, it is important to understand these things to run a secure system.

---

### Post by mikodo on 2015-05-04
> **TheFu said:**
> The answer is "it depends." Could be safe or not, depending on the end-goal you seek.

You can read what each of those commands does, if you like. Since Linux is a multi-user OS and file and directory permissions are at the center of the security model, it is important to understand these things to run a secure system.

Edit: Well. I read about it.

I don't see why anyone, should have the ability to change permissions on data I have access with my user. So, I am going to try using the chmod command, without sudo.

Thank you.

---

### Post by TheFu on 2015-05-05
There are subtle ways that improper file permissions can be used against you and the system. There is no substitute for understanding.
If you want to learn more and be more confident, then become a **power user** of Linux - [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) 
Later, after you have that level, you can start reading the Ubuntu Security Guides. I've placed the best links in my profile here [http://ubuntuforums.org/member.php?u=1037685](http://ubuntuforums.org/member.php?u=1037685) - click on the visitor messages. There is a section about Security.

We are all still learning, since Linux security is ever-changing and attackers are always finding new techniques.

Sudo is only necessary when your userid doesn't have permissions to do what you want. chown **always** needs sudo.  chmod may need sudo, if your useid is not the "owner" - **ls -al** will show the permissions.  Only the userid that was entered during install gets to uses sudo - if you create other userids later those do not get sudo authority without explicitly adding it for each userid.  If you work through that first link, you'll come to understand.

Always remember that Linux is a mult-user OS and file/directory permissions are the first line of security.

---

### Post by Morbius1 on 2015-05-05
> sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
So far so good. You created the directory and changed ownership to you.
> #sudo chmod 766 /mnt/data
Not sure what you were going for here but it your intent was to make the folder read / writeable to everyone it will not work. A "6" does in fact allow R/W but you didn't make the folder executable so no one but the owner will be able to open the folder to get inside. A chmod on a folder using octal notation always has to be odd ( like a 5 or a 7 ) to make it so a user can open it.
> #OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
Those two chmod expressions are not equivalent.

Forgetting the recursive nature of the last expression, at a folder level a "chmod 766" produces ... well ... 766 permissions.
A "chmod -R a+rwX" produces a folder ( and all subfolders ) with 777 permissions.

---

### Post by mikodo on 2015-05-05
Alright. Thanks folks. The time you took to think, write and provide links, about this for me, is appreciated.

More reading, after I switch out drives and install a new Xubuntu 14.04.1 today.

Edit. deleted the rest. I need to read more.

---

