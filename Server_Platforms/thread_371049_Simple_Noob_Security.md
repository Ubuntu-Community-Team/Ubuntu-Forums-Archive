---
title: "Simple Noob Security"
date: 2007-02-26
forum: Server Platforms
---

### Post by icedogchi on 2007-02-26
Hello all, I looked around but I didn't find the information I was after, so I was hoping someone might answer these security questions for me or point me in the right direction.

First, [COLOR="Lime"]I'm still green on Ubuntu[/COLOR], but I am trying to make sure that my computer is secure before I open it to the outside world.

I see that /var, /root, /bin, etc are owned by the user root and the group root, but my question is on the permissions.  All of these high-level folders have rwxr-xr-x and I'm not certain they should have.  

[COLOR="Red"]1)  Why should the groups and others have read and execute permission to these folders?[/COLOR]

Second, on the Ubuntu install, root is hidden and can only be accessed via sudo from the priviledged user that was created on install.  I normally log in and do stuff as this privilidged user.  

[COLOR="Red"]2)  Is that acceptable, or should I create another user for myself that has more restricted access?[/COLOR]

I created a user in its own group to run Tomcat so that it does not run as root.  I changed all of the folder and file permissions I could find to be owned by this user and group.  All others have no permissions.  
[COLOR="Red"]3)  This is a good idea, right?[/COLOR]

Apache2 runs 4 processes, 3 as www-data and 1 as root.  

[COLOR="Red"]4)  I'm not sure why there are 4 processes and 1 is running as root, any thoughts?[/COLOR]

[COLOR="Red"]5)  Finally, are FTP, rlogin, and rcp disabled when I install OpenSSH, or is there a manual way to disable those?[/COLOR]

I realize that is quite a few questions and I appreciate your responses!

-jt

---

### Post by gaten on 2007-03-01
>  [COLOR=Red]1)  Why should the groups and others have read and execute permission to these folders?[/COLOR]

This is necessary for the OS to run properly. Its a bad idea to mess with system set preferences, however the /root directory can be set readable only to root w/o worry. The command for this would be
```
sudo chmod -R 700 /root
```

> Second, on the Ubuntu install, root is hidden and can only be accessed via sudo from the priviledged user that was created on install. I normally log in and do stuff as this privilidged user. 

[COLOR=Red]2)  Is that acceptable, or should I create another user for myself that has more restricted access?[/COLOR]

Generally, this is acceptable. If you are extra paranoid, creating another user with less privileges is a great idea.

> I created a user in its own group to run Tomcat so that it does not run as root. I changed all of the folder and file permissions I could find to be owned by this user and group. All others have no permissions. 
[COLOR=Red]3)  This is a good idea, right?[/COLOR]

This is a very good idea, and shows that your head is in the right place security-wise. You might also want to look up **chroot **or **jail a process** on google or Ubuntu forms, its another great security measure.

>  [COLOR=Red]4)  I'm not sure why there are 4 processes and 1 is running as root, any thoughts?[/COLOR]

In order to bind a service to a privileged port (any port less than 1025), it needs to be run as root. However, the service will pass all requests to the webserver to the other processes (the ones owned by www-data). To secure this process more, check out mod_chroot ([http://core.segfault.pl/~hobbit/mod_chroot/](http://core.segfault.pl/~hobbit/mod_chroot/))

>  [COLOR=Red]5)  Finally, are FTP, rlogin, and rcp disabled when I install OpenSSH, or is there a manual way to disable those?[/COLOR]

Those services shouldnt be running at all under an Ubuntu install. To see, run this command:
```
sudo netstat -pan --ip
```

This will output a list of running processes that are using the network (in one form or another). 

OK, hope that helps.

---

