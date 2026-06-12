---
title: "Sql Problem"
date: 2006-07-05
forum: Server Platforms
---

### Post by jordans on 2006-07-05
Can some one please help me figure out what is going on with setting up MySQL. When I try to start it it says: ```
Check that mysqld is running and that the sockedt: '/var/run/mysqld/mysqld.sock' exists!
```
Well I checked and it doesn't exist. I don't know what is wrong but I need it to work. I have reinstalled and rebooted, the works.
Please help!
Jordan

---

### Post by mssever on 2006-07-05
Have you tried this?
```
/etc/init.d/mysql-ndb start #or restart, if appropriate
```
This is how MySQL is started on my machine (Dapper).

Also, have you done [FONT="Courier New"]ps -ef|grep mysql[/FONT] to see if mysql is in fact running?

Just some thoughts...

---

### Post by jordans on 2006-07-06
I tried restarting that file but it doesn't excist. this is what it read when I ran ps -ef|grep mysql
```
root     4204  4191   0  20:59 pts/0     00:00:00 grep mysql
```
I am new to all this so i don't know if this means its running.

Thanks, What should i do next.

---

### Post by mssever on 2006-07-06
That means that MySQL isn't running (expected, since you're having problems).

Please post the result of doing [FONT="Courier New"]ls -l /etc/init.d/mysql*[/FONT]

---

### Post by jordans on 2006-07-06
```
-rwxr-xr-x 1 root root 4368 2006-05-15 05:10 /etc/init.d.mysql


```

Thank you for helping with this!

---

### Post by mssever on 2006-07-06
Is this the actual result, or is it a typo? Also, did you get the asterisk (*) at the end of the ls command?
[QUOTE=jordans]```
-rwxr-xr-x 1 root root 4368 2006-05-15 05:10 /etc/init.d.mysql
```[/QUOTE]
I expected something more like ```
-rwxr-xr-x 1 root root 4368 2006-05-15 05:10 /etc/init.d**/**mysql
```

What command are you using when you try to start MySQL?

---

### Post by jordans on 2006-07-06
Yes that was a typo. Sorry. This is the command i am using ```
 sudo /etc/init.d/mysql restart
```
What is the next step?

---

### Post by mssever on 2006-07-06
What version of MySQL are you using? You can do [FONT="Courier New"]mysql --version[/FONT] to find out.

It appears that MySQL isn't installed properly on your system, though I'm not sure why. You said that you reinstalled MySQL. Did you completely remove MySQL in Synaptic (or its equivalent) before installing it again? I'd expect Synaptic to install it correctly.

I'm running out of ideas. :( 

You COULD compile MySQL from source, although the last time I did that, it was quite the headache.

---

### Post by jordans on 2006-07-06
version 4.0.24: what is Synaptic? I will try once again to reinstall unless you have a better way for me to reinstall. Thanks?

Anyone else out there have any ideas?

---

### Post by mssever on 2006-07-06
Synaptic is a package manager (at least in Dapper; I've never used Breezy). Other package managers are aptitude and dselect (both are text-based). Are you using one of these, or apt-get, to install? If not, I highly recomend that you do so.

---

### Post by jordans on 2006-07-06
I am using apt-get. Could it make it not work? What should i do to get one of those to run to install mysql? Thanks

---

### Post by mssever on 2006-07-06
Apt-get can do everything that the others can, but the other programs are easier tu understand. You probably already have aptitude installed; not sure about Synaptic. Try [FONT="Courier New"]gksudo synaptic[/FONT]. If that doesn't work, try [FONT="Courier New"]sudo aptitude[/FONT]. Failing both of those, do [FONT="Courier New"]sudo apt-get install synaptic[/FONT]. It should appear in your System menu, or you can start it like above.

In synaptic, look for mysql in the list of installed programs. Click the green box and select remove completely from the menu. Click the apply button, then when the changes have been made, find and install the package [FONT="Courier New"]mysql-server[/FONT].

In aptitude, type "/" to search, "n" to jump to the nex result, "_" to purge (remove completely), "+" to add a package, and "g" to apply changes.

If it still doesn't get installed correctly, it might be time to upgrade to Dapper :( .

---

