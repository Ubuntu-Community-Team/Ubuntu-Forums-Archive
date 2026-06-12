---
title: "How to rename a program installed via apt-get in Ubuntu"
date: 2016-10-01
forum: Security
---

### Post by Salil_Surendran on 2016-10-01
Hello,
   I had installed a program using apt-get in Ubuntu. Anyway to rename the program other than uninstalling and reinstalling it?

---

### Post by cariboo on 2016-10-01
Why would you want to do that? You can use Nautilus, the file manager, to rename a file, or in a terminal use the following command:

```
mv [old_name] [new_name]
```

where [old_name] = the files old name
where [new_name] = the new file name

**Note:** you may need to use sudo if the files are not in a directory that you own.

---

### Post by &amp;KyT$0P# on 2016-10-01
Which program?  Are you renaming the program executable or its menu entry?

If the program executable, creating a renamed symlink to it might be a safer option if that would work.
```
ln -s [old_name] [new_name]
```

If you want to rename just the menu entry, you'll have to edit a .desktop file somewhere.  Can't say more on that without specifics.

Let us know, thanks.

---

### Post by vasa1 on 2016-10-01
> **Salil_Surendran said:**
> Hello,
   I had installed a program using apt-get in Ubuntu. Anyway to rename the program other than **uninstalling and reinstalling it**?
How would "uninstalling and reinstalling it" help in renaming the program :confused:

---

### Post by sisco311 on 2016-10-01
> **halogen2 said:**
> Which program?  Are you renaming the program executable or its menu entry?

If the program executable, creating a renamed symlink to it might be a safer option if that would work.
```
ln -s [old_name] [new_name]
```


Symlinks are safer, but they may change the application's behavior.  For example, when bash is invoked as sh it enters in posix mode. (systemd's) shutdown  is a symlink to  systemctl and it acts very differently. And of course there is Busybox... If its executable is renamed to one of the commands it supports, it will act as that command.

The safest way to `rename' an executable is to use an alias or a shell function.  

> **halogen2 said:**
> 
If you want to rename just the menu entry, you'll have to edit a .desktop file somewhere.  Can't say more on that without specifics.

Let us know, thanks.

+1

---

### Post by Salil_Surendran on 2016-10-01
I had installed a program on a server that logs who all are the users who had logged onto that server and what time using sudo apt-get "program name". However if someone finds that this particular program is running on that server they could delete the log file it is writing to. Just want to be extra careful. I could go and rename that program itself but I am wondering wouldn't it have ".so" files etc. named as itself. I just want no trace of the fact that the program is installed.

---

### Post by ian-weisser on 2016-10-01
> **Salil_Surendran said:**
> However if someone finds that this particular program is running on that server they could delete the log file it is writing to. 
[...]
I just want no trace of the fact that the program is installed.

Seems unwise. Both of those techniques could also be used to hide a nefarious process from you.
Use proper account permissions and file ownership to protect files, including logs.

If you are hiding some kind of monitoring or logging software, don't. Tell your users up front that their actions are monitored or logged and that unacceptable activity will have consequences.
If you believe that a user on your server can successfully conduct a privilege escalation attack to gain root, delete that user.
If you believe that a user has already gained root, take the compromised server offline and reinstall immediately.

---

### Post by sisco311 on 2016-10-02
Since 1851, we know that `Security through obscurity' is not security at all. 


Thread moved to the Security forum.

---

### Post by &amp;KyT$0P# on 2016-10-02
> **Salil_Surendran said:**
>  if someone finds that this particular program is running on that server they could delete the log file it is writing to. 
Yeah?  What **exactly** is this particular program, that a few [FONT=Courier New]chmod[/FONT] commands and configuration file tweaks couldn't take care of that problem?

Why do you think a user would deliberately delete only this specific log file, but leave others alone?

> I just want no trace of the fact that the program is installed. 
Why would you want that?

---

### Post by HermanAB on 2016-10-09
"they could delete the log file it is writing to"
If that is the case, then change the log file permissions.

---

