---
title: "how to limit sudo user's permissions"
date: 2012-06-04
forum: Security
---

### Post by Inderpreet Singh on 2012-06-04
Hi,

I have created a new user and I have added that user into sudo users, now I want that sudo user must not have permissions to delete the contents of **/var/www/html **even using command **sudo rm -rf** . So how can I restrict sudo user to do this??

---

### Post by sanderd17 on 2012-06-04
A user that can execute sudo has all the rights. Period.

What you can do is remove them from admin group and add specific rights to the user. To do that, you should read the sudoers documentation CAREFULLY: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by bodhi.zazen on 2012-06-04
> **sanderd17 said:**
> A user that can execute sudo has all the rights. Period.

What you can do is remove them from admin group and add specific rights to the user. To do that, you should read the sudoers documentation CAREFULLY: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

That is not exactly true, you can configure sudo to allow access to some commands and not others.

See: [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

If you need more then that, then you need to configure apparmor.

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

### Post by stmiller on 2012-06-05
You can restrict a command from being run by using bang (!), but in this case it would restrict the 'rm' binary command from being run with sudo.

For example, username bob would not be able to run sudo rm anything, or sudo apt-get but could run everything else.

```

/etc/sudoers

bob ALL=!/usr/bin/rm,!/usr/bin/apt-get

```

---

### Post by Inderpreet Singh on 2012-06-06
> **stmiller said:**
> You can restrict a command from being run by using bang (!), but in this case it would restrict the 'rm' binary command from being run with sudo.

For example, username bob would not be able to run sudo rm anything, or sudo apt-get but could run everything else.

```

/etc/sudoers

bob ALL=!/usr/bin/rm,!/usr/bin/apt-get

```

I have tried this and I have only blocked !/usr/bin/rm command but it blocked many other commands too for sudo user like mkdir,touch ....so what can be the issue??

---

### Post by zombifier25 on 2012-06-08
There's no /usr/bin/rm, there's /bin/rm. That might be your issue.

---

### Post by Lars Noodén on 2012-06-08
> **Inderpreet Singh said:**
> I have tried this and I have only blocked !/usr/bin/rm command but it blocked many other commands too for sudo user like mkdir,touch ....so what can be the issue??

Also, blacklisting commands won't work because there is such an easy work-around: just make a copy of the program and run it under its new name.

What you'll want to do is white list which programs the user (group) is allowed to run.

So, which programs *do* you want the user to be able to run as root?

---

### Post by Inderpreet Singh on 2012-06-11
Ploblem has been resolved by doing following setting 

"your sudo user" = ALL=ALL,!/bin/rm

now sudo user can do anything but can not run command rm

---

### Post by Lars Noodén on 2012-06-11
> **Inderpreet Singh said:**
> now sudo user can do anything but can not run command rm

No but they can do this:

```

cp /bin/rm /tmp/foo
sudo /tmp/foo -rf /path/to/something

```

What is needed instead is to whitelist the programs that you wish to allow the user to run as root.  

Which ones are they?

---

### Post by bodhi.zazen on 2012-06-11
> **Lars Noodén said:**
> No but they can do this:

```

cp /bin/rm /tmp/foo
sudo /tmp/foo -rf /path/to/something

```

What is needed instead is to whitelist the programs that you wish to allow the user to run as root.  

Which ones are they?

You really need to both:

1. Take care who you give root access to.

2. Use apparmor.

There are many ways to circumvent your (sudo) configuration.

---

### Post by SeijiSensei on 2012-06-11
One alternative, if you're sure the contents of /var/www is fixed, is to set the "immutable" attribute on the files you wish to preserve.  See "man chattr" for details.  The root user can obviously defeat this limitation by turning off the attribute first, but it's a sufficiently obscure feature of Linux filesystems that most people don't know that it exists.  

Of course, if the web site files are constantly being changed, this approach won't work.

Why not put these people in a group of their own and use regular permissions on files and directories to limit what they can access and change?

---

