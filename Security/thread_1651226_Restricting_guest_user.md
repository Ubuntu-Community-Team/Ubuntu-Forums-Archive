---
title: "Restricting guest user"
date: 2010-12-22
forum: Security
---

### Post by chroniccommand on 2010-12-22
I've recently created a guest user account for users to SSH into my system. I want to set permissions so the guest user cannot view my home folder(/home/chronic). But I want them to be able to view /home/guest. I want the guest to be locked down for security issues so I can't be screwed over. How can I set the account up like this?

---

### Post by bodhi.zazen on 2010-12-23
Your first line of defense is linux permissions. One can not change system files without  root access.

If you need something beyond that, you need to use apparmor or selinux.

See :

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

### Post by chroniccommand on 2010-12-24
> **bodhi.zazen said:**
> Your first line of defense is linux permissions. One can not change system files without  root access.

If you need something beyond that, you need to use apparmor or selinux.

See :

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)
Yes I know somewhat about file permissions, and I have sensitive files encrypted with GPG. But I'm not very good with permissions. How would I make it so the guest user can't access certain directories, but other users can. For example, I want the other users to be able to access /var/www/ but not guest. Another example, I want the guest to be unable to delete /home/guest/message but may read it.

---

### Post by bodhi.zazen on 2010-12-24
> **chroniccommand said:**
> Yes I know somewhat about file permissions, and I have sensitive files encrypted with GPG. But I'm not very good with permissions. How would I make it so the guest user can't access certain directories, but other users can. For example, I want the other users to be able to access /var/www/ but not guest. Another example, I want the guest to be unable to delete /home/guest/message but may read it.

Well for the first, you may want to look at acl

for the second, you can either make /home/guest/message owned by root:root with permissions of 444 , or you can write an apparmor profile.

---

### Post by chroniccommand on 2010-12-24
> **bodhi.zazen said:**
> Well for the first, you may want to look at acl

for the second, you can either make /home/guest/message owned by root:root with permissions of 444 , or you can write an apparmor profile.
Alright thanks. Thing is, when I change the owner to root:root with
```
chown /home/guest/message root:root
```
They can still remove it.

Also, how can I restrict certain programs for that guest user. For example, I want the guest user to be able to run most programs, but not ssh.

---

### Post by bodhi.zazen on 2010-12-24
> **chroniccommand said:**
> Alright thanks. Thing is, when I change the owner to root:root with
```
chown /home/guest/message root:root
```
They can still remove it.

Also, how can I restrict certain programs for that guest user. For example, I want the guest user to be able to run most programs, but not ssh.

You will need to change permissions on /home/guest so guest can not write to home, or move message to a sub directory, ~/msg/message perhaps

Then
sudo chown -R root:root msg
sudo chmod 755 msg
sudo chmod 444 msg/message 

Did you change ownership and permissions using sudo ?

If you wish to further restrict the guest user, you need to use apparmor. apparmor. apparmor.

Have you even bothered to look at apparmor ?

It is going to take some effort to "lock down" the guest, a lot of reading, and apparmor is by far the easiest and most secure method.

Again, this link will walk you through it : [http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

### Post by chroniccommand on 2010-12-24
> **bodhi.zazen said:**
> What are the permissions of the file ?

Did you change ownership and permissions using sudo ?

If you wish to further restrict the guest user, you need to use apparmor. apparmor. apparmor.

Have you even bothered to look at apparmor ?
The permissions are:
```

chronic@ubuntu:/home/guest$ ls -l message
-r-------- 1 root root 118 2010-12-24 16:33 message

```
And yes, but It's kinda confusing me at the moment.

---

### Post by tad1073 on 2010-12-24
> **chroniccommand said:**
> Alright thanks. Thing is, when I change the owner to root:root with
```
chown /home/guest/message root:root
```They can still remove it.

Also, how can I restrict certain programs for that guest user. For example, I want the guest user to be able to run most programs, but not ssh.

Actually I think it would be:
```

sudo chown root:root /home/guest/message
then
sudo chmod 744 /home/guest/message

```or you could create groups for those user, apply group permissions then individual folder/file permissions

---

### Post by bodhi.zazen on 2010-12-24
> **tad1073 said:**
> Actually I think it would be:
```

sudo chown root:root /home/guest/message
then
sudo chmod 744 /home/guest/message

```

No, that will not work. As long as guest has w access to /home/guest they can delete message, try it.

---

### Post by tad1073 on 2010-12-24
> **bodhi.zazen said:**
> No, that will not work. As long as guest has w access to /home/guest they can delete message, try it.

from left to right isn't it R W X?

that is strange behavior

---

### Post by bodhi.zazen on 2010-12-24
> **tad1073 said:**
> from left to right isn't it R W X?

that is strange behavior

It is strange. The user has write access to the directory ( /home/guest ) so they can delete the file.

I miss this detail all the time.

---

### Post by tad1073 on 2010-12-24
> **bodhi.zazen said:**
> It is strange. The user has write access to the directory ( /home/guest ) so they can delete the file.

I miss this detail all the time.
  but 4 would be read only for the group and the owner being root has full control (7), how a user can delete a file owned by root is beyond me

---

### Post by bodhi.zazen on 2010-12-24
> **tad1073 said:**
> but 4 would be read only for the group and the owner being root has full control (7), how a user can delete a file owned by root is beyond me

I understand, it is an odd detail of Linux permissions. Basically the file is a "child" of the parent directory, so since the user has write access (read access is not needed) to the directory the user can delete files they do not own or have write access to.

To over ride this, to some extent, you can set a sticky bit on the parent directory, then only the file owner can delete a file, this is how /tmp is managed.

It just goes to show you, test your security settings :p

---

### Post by sisco311 on 2010-12-24
> **tad1073 said:**
> but 4 would be read only for the group and the owner being root has full control (7), how a user can delete a file owned by root is beyond me

In Unix/Linux everything is a file. If something is not a file, it is a process. :)

So directories are files too. They contain just the [inode]("http://en.wikipedia.org/wiki/Inode") number and the name of a file.

For example, if you have a directory foo with two files bar1 and bar2 you can think of it as a file with the following info:
```
inode1 bar1
inode2 bar2
```

If you have write permission for foo, you can edit this info. Rename a file:
```
inode1 bar1
inode2 bar3
```

Delete a file:
```
inode1 bar1

```

Add a new file:
```
inode1 bar1
inode2 bar2
inode3 bar3
```

Check out:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by bodhi.zazen on 2010-12-24
> **sisco311 said:**
> In Unix/Linux everything is a file. If something is not a file, it is a process. :)

Thank you for the explanation siso311

See also [http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

---

### Post by chroniccommand on 2010-12-25
Alright well I got most restrictions working. I just used MOTD to replace message. But how exactly could I block the guest from running certain programs such as iptables or ettercap or ssh.

---

