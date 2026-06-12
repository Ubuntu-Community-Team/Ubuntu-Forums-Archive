---
title: "root acces required"
date: 2014-07-17
forum: Server Platforms
---

### Post by preston3 on 2014-07-17
I am trying to move my web server (from my raspberry pi to my new ubuntu machine) i have all of the files on my lap top and am trying to use filezilla to move them. my problem is i can't access the www folder. on my pi i just changed the root password and logged in. with ubuntu server it doesn't work that way. help me please

---

### Post by Iowan on 2014-07-17
Moved to Server Platforms.
Is it an access issue, or a location problem? As I understand it, the www directory location got moved.

---

### Post by TheFu on 2014-07-17
Logging in as root isn't the debian or ubuntu way.  We prefer to use "sudo" to escalate rights for 1 command, only when necessary.  I would use sftp to remote into the PI and pull all the files back with a recursive mget to a temporary directory. Then I'd change the permissions as needed for the Ubuntu web server location (whatever userid/groupid it prefers) and move them there.

Of course, there are 1,000 different ways to accomplish the same thing by using different userids, different accounts, changing the permissions in the website root, adding the userid to the web-groupid, or ...  lots of different ways to solve this.

If you want exact commands, post the exact file/directory ownership for the source system+directories and the target system+directories.  Also the userid+grouid that runs the web-server is necessary.  There are different web server and they probably use different owners/groups.

BTW, FTP really shouldn't be used anymore and shouldn't have been used the last 15 yrs.  sftp is a drop-in, secure, replacement that works over ssh (auth, keys, port).  Or you could use rsync over ssh (the default for rsync).

Lots of different solutions are possible. An understanding of userids, groupids and file/directory permissions makes this stuff easy.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a good place to brush up on that stuff.

---

### Post by nerdtron on 2014-07-17
So what is the problem here? 
You can't get the files on /vaw/www/ on the pi?
Or you can't upload the files on the /var/www/ of Ubuntu?

And since you are using Filezilla how do you connect? Using port 22 I assume?

I you would just like to move you files from the pi to ubuntu, have you tried rsync? Assuming you can ssh from Ubuntu to the Pi (and rsync is intalled on both machines), here's what you can try.
On the Ubuntu machine:
```
cd /var/www/
sudo rsync -avrh --proress root@IPaddressofPI:/var/www/* .
```

Then when you type ls -l to see the files you have just copied.

---

### Post by preston3 on 2014-07-18
ok so i tried the rsync command and it says that my user (that used sudo yesterday) is not part of the sudoers file. how do i add me back

---

### Post by thnewguy on 2014-07-18
To add your user to the sudo group you probably want to login as a user who does have admin access and then run "sudo adduser <yourname> sudo".

Regarding the permission issue, the problem is your user does not have access rights to write to /var/www. Make sure the /var/www folder is writeable for your user. Typically you would probably do this by making sure the folder was owned by a specific group (perhaps called "web") and that your user was a member of that group. There are other ways, but the key thing is to make sure the /var/www folder is writeable to your regular user account.

---

### Post by preston3 on 2014-07-18
see the problem is i can't log into my root account and my only user doesn't have sudo actions because while tinkering around yesterday i think i took those privileges away on accident. what do i do? how do i get the sudo back

---

### Post by thnewguy on 2014-07-19
Reboot the computer into single user mode, this will give you admin access. Then re-add sudo access to your regular user account or enable the root account. [http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub](http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub)

---

