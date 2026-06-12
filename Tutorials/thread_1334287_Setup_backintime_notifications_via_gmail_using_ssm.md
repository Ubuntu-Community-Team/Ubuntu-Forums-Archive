---
title: "Setup backintime notifications via gmail using ssmtp"
date: 2009-11-22
forum: Tutorials
---

### Post by nunki on 2009-11-22
I recently setup a raid1 array to handle all my household backups, and decided on using backintime to handle this task. Given how important these backups are, I wanted to keep a close watch on them to make sure they were happening without issue.

After a bit of reading I decided to use backintimes user callback functionality to email me when backups were created, and if any errors had occurred.

[LIST=1]
[*]Install ssmtp
```
 sudo apt-get install ssmtp 
```

[*]Configure for sending through gmail
```
 sudo gedit /etc/ssmtp/ssmtp.conf
```

Modify the following in ssmtp.conf
```

root=youraddress@gmail.com
mailhub=smtp.gmail.com:587
AuthUser=gmailusername
AuthPass=gmailpassword
UseSTARTTLS=YES

```

[*] Test out ssmtp by sending email to your gmail
```

ssmtp youraddress@gmail.com

```
Then type the following:
```

To:youraddress@gmail.com
From:youraddress@gmail.com
Subject:Testing ssmtp

This is a test

```

Press ctrl+D when you finish. 
*Note there are 2 newlines after the Subject line.


[*] Setup backintime
```
 sudo apt-get install backintime 
```

The gui is very self explanitory. Setup your backups and their frequency for whatever suits your needs.


[*] Setup user.callback

Backintime is setup to call a user defined callback at certain times during the backup process. Backintime will look for a file called "user.callback" at ~/.config/backintime during its execution, and call it with a specific set of arguments if it exists.

Lets create that file now:
```
 gedit ~/.config/backintime/user.callback 
```

Add the following to the file:
```
 
#!/bin/sh
address ="<youruser>@gmail.com"
msg="To:<youruser>@gmail.com\n";
msg="${msg}Subject:Backup\n\n";
mailmsg=0;
case "$1" in
1);; ##Backup starting
2);; ##Backup finishing
3)msg="${msg} Backup completed for ${2} ${3}"
  mailmsg=1
 ;;
4)msg="${msg} An error occurred:"
  mailmsg=1
  case "$2" in
  1)msg="${msg} Application not configured";;
  2)msg="${msg} Process already running";;
  3)msg="${msg} Can't find directory";;
  4)msg="${msg} A snapshot for 'now' already exists";;
  esac
 ;;
esac
if [ $mailmsg = 1 ]
then
/bin/echo -e $msg | /usr/sbin/ssmtp $address
fi

```


Replace <youruser> with your gmail user name.
*Note: I only want to be notified when a snapshot is taken, or an error occurs. I'm not interested in when the backup starts or finishes. This is why the first two items in the case statement are left blank.


[*]Save the file and set the appropriate permissions
```
 chmod 755 ~/.config/backintime/user.callback 
```

[*] Test out script manually
```
 ./.config/backintime/user.callback 4 3 
```

If everything worked well, you should have recieved an email with one of the error conditions listed.

You should now receive an email whenever a backup occurs, or an error is encountered. If you setup backintime to do frequent backups i.e. more than once a day, and the emails start to get annoying, just delete the user.callback file. This will not effect your backups. 
[/LIST]

---

### Post by morsedl on 2012-11-04
For what it's worth, both the man page and the file /usr/share/backintime/common/config.py indicate that the callback file in $HOME/.config/backintime/ should be named "user-callback", not "user.callback", at least on Ubuntu 12.04 LTS. I've not tested yet but will report back if this is correction is not correct. :)

---

### Post by morsedl on 2012-11-05
Verified.

At least for backintime-common 1.0.10 on Ubuntu 12.04 LTS (precise), the callback file is "user-callback", not "user.callback".

There are two other issues as well:

[LIST=1]
[*]The author has changed the parameters sent to user-callback (see [http://backintime.le-web.org/documentation/usercallback/](http://backintime.le-web.org/documentation/usercallback/)).
[*]There is a typo in the script above ("address =<your..." should not have a space after the equal sign).
[/LIST]
As an example of 1, these are the callback calls on my host:

> /root/.config/backintime/user-callback 1 "Main profile" 1
/root/.config/backintime/user-callback 1 "Main profile" 3 20121104-231358-878 /srv/backups/backintime/myserver.com/root/1/20121104-231358-878
/root/.config/backintime/user-callback 1 "Main profile" 2
Thus, what used to be the first parameter is now the third.

To correct these two issues, then, simply change the first two lines:

```
#!/bin/sh
address ="<youruser>@gmail.com"
```to these three:

```
#!/bin/sh
address="<youruser>@gmail.com"
shift; shift;
```And of course, name the file user-callback, not user.callback.

I hope this is helpful to others.

---

