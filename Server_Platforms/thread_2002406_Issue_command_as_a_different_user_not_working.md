---
title: "Issue command as a different user not working"
date: 2012-06-12
forum: Server Platforms
---

### Post by buee on 2012-06-12
Ok, so I've been trying to find a way to refresh the configuration files of FreeRadius from a PHP page that I've been working on. I can do this one of two ways:

    [LIST=1]
[*]/etc/init.d/freeradius force-reload
[*]/usr/sbin/freeradius -C
[/LIST]


However, the trouble I'm running in to is privileges. I know I have to do this from the sudoers file, but I can't seem to get it to work. The user for apache is www-data as default, the user for FreeRadius is freerad. My assumption is that I need to give www-data permissions to run one of those commands (preferably /usr/sbin/freeradius -C) as either root or freerad without prompting for a password. But HOW?!

I've edited the sudoers file a million different times. Anything that's bold is something I haven't changed:

```

www-data        localhost = (ALL) NOPASSWD: /usr/sbin/freeradius -C
```

I have a feeling it's something stupid like a space where it shouldn't be, but I've played around with different formatting and still can't get the command to work. What's worse is the /usr/sbin/freeradius -C doesn't return an output that I can tell nor does an entry appear to show up in /var/log/auth.log. My brain is shot, someone help me please.

---

### Post by SeijiSensei on 2012-06-12
Must the command be issued by one of those users?  Perhaps /usr/sbin/freeradius is only executable by root?  The simplest fix in this case is to let other users run the command with "sudo chmod a+x /usr/sbin/freeradius".  A more nuanced approach would create a group with executable rights on the file, then putting the www-data user into that group.

---

### Post by buee on 2012-06-12
> **SeijiSensei said:**
> Must the command be issued by one of those users?  Perhaps /usr/sbin/freeradius is only executable by root?  The simplest fix in this case is to let other users run the command with "sudo chmod a+x /usr/sbin/freeradius".  A more nuanced approach would create a group with executable rights on the file, then putting the www-data user into that group.

```
root@buee-ubuntu:/usr/sbin# chmod a+x freeradius 
root@buee-ubuntu:/usr/sbin# ls -al freeradius 
-rwxr-xr-x 1 root root 283912 2011-05-19 10:50 freeradius
root@buee-ubuntu:/usr/sbin# freeradius -C
root@buee-ubuntu:/usr/sbin# echo $?
0
root@buee-ubuntu:/usr/sbin# su - www-data
$ /usr/sbin/freeradius -C
$ echo $?
1
```

---

### Post by Cheesemill on 2012-06-12
> **buee said:**
> Ok, so I've been trying to find a way to refresh the configuration files of FreeRadius from a PHP page that I've been working on. I can do this one of two ways:

[LIST=1]
[*]/etc/init.d/freeradius force-reload
[*]/usr/sbin/freeradius -C
[/LIST]


However, the trouble I'm running in to is privileges. I know I have to do this from the sudoers file, but I can't seem to get it to work. The user for apache is www-data as default, the user for FreeRadius is freerad. My assumption is that I need to give www-data permissions to run one of those commands (preferably /usr/sbin/freeradius -C) as either root or freerad without prompting for a password. But HOW?!

I've edited the sudoers file a million different times. Anything that's bold is something I haven't changed:

```

www-data        localhost = (ALL) NOPASSWD: /usr/sbin/freeradius -C
```I have a feeling it's something stupid like a space where it shouldn't be, but I've played around with different formatting and still can't get the command to work. What's worse is the /usr/sbin/freeradius -C doesn't return an output that I can tell nor does an entry appear to show up in /var/log/auth.log. My brain is shot, someone help me please.
Are you still using sudo in front of the command to run the command as the www-data user, ie:
```
sudo /usr/sbin/freeradius -C 
```Editing the sudoers file still means you have to use sudo, you just aren't prompted for a password.

---

### Post by buee on 2012-06-12
> **Cheesemill said:**
> Are you still using sudo in front of the command to run the command as the www-data user, ie:
```
sudo /usr/sbin/freeradius -C 
```Editing the sudoers file still means you have to use sudo, you just aren't prompted for a password.

That got it.  I knew it was something stupid that I was doing.  Thank you for your help.  2 weeks of banging my head on a desk and you solved it in less than 2 minutes.

---

