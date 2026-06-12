---
title: "PHP add Linux users"
date: 2011-03-26
forum: Security
---

### Post by biohazard135 on 2011-03-26
Hello! First post!

I'm having trouble with PHP adding Linux users. I am building a system that will take advantage of Linux's built in users however you need to execute under sudo to actually add the user.

So here comes an obvious security concern. Although I sanitize all my commands & requests I'll never run PHP as root. I've thought about setting /etc/passwd to 777 (well not that bad but similar) so it can be accessed by PHP ("nobody") Maybe I could create one just like "nobody" but It can make users?

I would have to set that to Apache as that executes PHP.

Thanks

PS) Sorry If anything isn't correct, I come from Windows.

---

### Post by SeijiSensei on 2011-03-26
> **biohazard135 said:**
> Although I sanitize all my commands & requests I'll never run PHP as root.

Whew, you had me worried there at the start.

> I've thought about setting /etc/passwd to 777 (well not that bad but similar) so it can be accessed by PHP ("nobody") Maybe I could create one just like "nobody" but It can make users?

Yikes, don't do that.

The only way I know of to use PHP securely as a frontend for tasks that require root permissions is to separate the tasks that root needs to run into a separate script.  In PHP, you'd write a file to a directory to which the Apache user has permissions that includes the names of the users that were entered in the form on separate lines.  Then, using crontab, you can periodically run a script as root that reads the file and adds the users like this:

Run "sudo nano /etc/crontab" and add this line:

```
* * * * * root sh /usr/local/sbin/addmyusers
```

This will run the script once per minute.

Now run "sudo nano /usr/local/sbin/addmyusers" to create the script like this:

```
#!/bin/bash

USERLIST="/var/www/userlist"

for U in $USERLIST
do
    adduser $U
done

rm -f $USERLIST
exit 0
```
Then use "sudo chmod u+x /usr/local/sbin/addmyusers" to make the script executable by root alone.

I'll leave the PHP side to you.  If you've not written a file to the OS in PHP before, see the fopen() and fwrite() commands.

There will obviously be as much as a one-minute delay between when you enter the usernames in PHP and when their accounts are created.  If you want some kind of confirmation, install the "bsd-mailx" package, then modify the script like this:

```
#!/bin/bash

USERLIST="/var/www/userlist"
NOTIFY=you@example.com

OK=''
BAD=''

for U in $USERLIST
do
    adduser $U
    if [ "$(grep $U /etc/passwd)" == "" ]
    then
       BAD="$BAD $U"
    else
       OK="$OK $U"
    fi
done

MSG="These users were added successfully:  $OK\nThese users could not be added: $BAD"

echo $MSG | mail -s 'User account update' $NOTIFY

rm -f $USERLIST
exit 0
```
Now the $NOTIFY address should receive a confirmation email when the script runs.

---

### Post by biohazard135 on 2011-03-26
Thanks for you're reply, it didn't seem to work well though:

[PHP]
<?php
    $file = fopen('/var/www/priv/newaccounts','w');
    fwrite($file,'Alpine');
    fclose($file);
    $last_line = system('/usr/local/sbin/newaccounts', $retval);
    echo($retval);
?>
[/PHP]
Output: 126

```

semiroot@peer0:/tmp$ cat /usr/local/sbin/newaccounts
#!/bin/bash

USERLIST="/var/www/priv/newaccounts"

for U in $USERLIST
do
    adduser -h $U
done

rm -f $USERLIST
exit 0
semiroot@peer0:/tmp$ 

```Just to confirm, /var/www/priv/newaccounts was meant to be a file right? Anyway, I used -h because the user needs to be able to store some files. However after a few minutes (You said it was slow right?) The folder /home/Alpine/ doesn't exist :(

Also I just realized this script wouldn't add passwords.

---

### Post by SeijiSensei on 2011-03-26
PHP's system() command doesn't run as root.  It runs as the Apache user, "www-data" in the case of Ubuntu.  That's why I said you need to have separate scripts, with the one needing root privileges running from crontab.

Still, you're right, there's no way to add the password as well.  Having re-read the man pages for both adduser and useradd, I don't see any way to include the password on the command line as well. "sudo useradd -p password" doesn't encrypt the password first; it simply stuffs the string "password" into /etc/shadow.  I suppose you could encrypt the passwords in PHP first, but you'd need to read up on which hashing method Ubuntu uses (I think its SHA1 with a "salt" but I'm not sure).

Perhaps we should take a step back and discuss why you need to do this.  Are you trying to make it easy for someone to create accounts?  Is the graphical user account manager available in GNOME or KDE not simple enough?  For something as crucial as secure account control, forcing someone to sit in front of the Ubuntu box to add accounts doesn't seem that onerous to me.  If you need to do this remotely, you can run "ssh -X" on a *nix client when connecting to the remote server.  Then if you run the remote's account manager from the command line, it's graphical interface will appear on the local machine.

Frankly, I think anyone granted the authority to create user accounts should be able to use SSH to connect to the remote and run the "adduser" script.  Someone who finds that intolerable probably shouldn't be responsible for account maintenance on a *nix system.  Even if they are Windows users, give them a copy of [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") and teach them how to connect and add accounts.

---

### Post by biohazard135 on 2011-03-26
> **SeijiSensei said:**
> Are you trying to make it easy for someone to create accounts?  Is the graphical user account manager available in GNOME or KDE not simple enough?

I'm trying to make it easy for myself, I am creating a shared seedbox where people can sign up, it creates an account & home directory (which is accessible via pureftpd). It also creates the appropriate .rtorrent.rc & launches rtorrent under there user name.

I thought if I just added a system user I wouldn't have to add separate configuration in for example pureftpd as that can inherit system users (so can ssh and some others)

---

