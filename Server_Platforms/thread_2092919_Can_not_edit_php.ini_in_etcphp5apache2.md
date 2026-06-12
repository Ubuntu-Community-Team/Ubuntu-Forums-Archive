---
title: "Can not edit php.ini in /etc/php5/apache2"
date: 2012-12-09
forum: Server Platforms
---

### Post by swanside on 2012-12-09
Hello.
I am very new to ubuntu and I have just grabbed my old computer out of the loft and installed 10.04 LTS on it.

I found a guide and set up apache2, MySql and PHP and PhPMyAdmin.

What I want to do now is increase the import size of my SQL files. In my PHPMyAdmin, its only letting me import about 2m.
I have gone into /etc/php5/apache2 and I can open the php.ini file, but when I edit the parts I need to which will allow me to upload larger files, I get a permission denied.
Can anybody please help me edit the permissions for the php.ini file so I can make the changes?
Cheers
Swanny

---

### Post by TheFu on 2012-12-09
> **swanside said:**
> Hello.
I am very new to ubuntu and I have just grabbed my old computer out of the loft and installed 10.04 LTS on it.

I found a guide and set up apache2, MySql and PHP and PhPMyAdmin.

What I want to do now is increase the import size of my SQL files. In my PHPMyAdmin, its only letting me import about 2m.
I have gone into /etc/php5/apache2 and I can open the php.ini file, but when I edit the parts I need to which will allow me to upload larger files, I get a permission denied.
Can anybody please help me edit the permissions for the php.ini file so I can make the changes?
Cheers
Swanny

Congratulations for joining the Linux and Ubuntu communities.
* Files located under /etc almost always are protected such that only root can and should edit them.  Use **sudo {editor} {filename}** to gain the elevated access permissions from the account you setup the system with. Other accounts should not work.
* I'd point out that 10.04 is an older release and you really should install 12.04 if you are running a desktop since 10.04 will not be supported with patches in a few months (April 2013). 
* If you are running the server edition, 10.04 has 5 yrs of support - no hurry to update, but I'd still encourage that you load 12.04 which will be supported until 2017.  On a server, this longer support period is helpful.  For example, we have a few 8.04 servers running still, but are planning a migration for each to 12.04. We also have a few 10.04 servers, which I am not planning to migrate for a few more years, but those have been running a few years already. If we needed to update the main application running on each box, the latest LTS OS available for each app would be used.  Waiting a year after a new LTS release happens is usually when most enterprise apps begin support. Hence, many apps do not support 12.04 yet, but will in 6-12 months.

In Linux and UNIX systems, file permissions are used much more than under Windows. It is important to understand them, but generally you should not change them. Often, these permissions are critical to the overall security of the system.  Making files under /etc owned by a non-root userid opens up possible security breaches.

To see normal permissions, use **ls -al {file}|{directory}**.  The current directory is assumed if you do not specify it.  [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html) seems like a good introduction.

---

### Post by xxmontyxx on 2012-12-09
first go to terminal by ctrl+alt+t
then type" sudo -i" without quotes
now type "gedit /etc/php5/apache2/php.ini" without quotes



if work add me friend in ubuntuforum and "facebook as Bhavdeep" also if doesnt work):P

---

### Post by swanside on 2012-12-09
Thanks for the info.
I will take a look and see.
I have set it up as a server, as I want to run MySQL databases and php pages to access them, once I am happy its all working, I am going to put the old computer back up in the loft, and run a network cable to it.

Regards
Paul

---

### Post by swanside on 2012-12-09
Did this as gedit would not work, even after installing it

> sudo -i

nano /etc/php5/apache2/php.ini

Cheers guys
Swanny

---

### Post by TheFu on 2012-12-09
> **swanside said:**
> Did this as gedit would not work, even after installing it

gedit is a GUI program. If you are on a "server" or running without an X/Windows interface, it will not start. You must use a CLI-based editor. I support **nano** can work, but most self respecting programmers/hackers/Unix-types will use **vim** for all the power it provides across every platform. I'm not interested in spawning an editor war, but vim/vi will work on any platform. nano won't be on that new router.

Also, there is no need for 2 steps.
```
$ sudo nano /etc/...../file-to-edit
```
will work fine and helps with auditing, should that be necessary later.

---

### Post by swanside on 2012-12-15
Thanks,
It all sorted now using the nano command.
Cheers
Swanny

---

