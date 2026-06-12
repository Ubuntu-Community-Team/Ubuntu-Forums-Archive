---
title: "Ubuntu Server Adding Multipul Users with a script"
date: 2009-04-17
forum: Server Platforms
---

### Post by FarehamWeather on 2009-04-17
I would like to know if it is possible to add multipul users with a script and how I can do it?

Basicly I have a list of 50 users that need to be setup on the domain system (ubuntu server running samba). 

I take it the script will would look somthing like this?


useradd -m -G group username1
smbpasswd -a username1
password
password
useradd -m -G group username2
smbpasswd -a username2
password
password
useradd -m -G group username3
useradd -m -G group username4
useradd -m -G group username5

How can I setup the users so that they can not logon to the server directly?

Thanks, Chris

---

### Post by PacSci on 2009-04-17
An improvement would be:

```
#!/bin/sh
# addsmbusers.sh
for username
do adduser $username -s /bin/false --disabled-login
adduser $username group
echo Giving password to $username
smbpasswd -a $username
done
```

First off, it cuts down on code duplication. Second off, putting passwords in scripts is the worst idea since Windows Vista. You'll have to enter the passwords manually, but it's much more secure.

Third off, you can specify the usernames on the command line - e.g. "sh addsmbusers.sh username1 username2 username3". If you have the users in a text file - one username per line - you can run "userlist > xargs sh addsmbusers.sh".

The not logging in directly is handled by "--disabled-login", and "-s /bin/false" will still prevent it in the event that you must give them a system password.

---

### Post by FarehamWeather on 2009-04-17
So I create the script with the code:

---------------------------------------------------
#!/bin/sh
# addusers.sh
for username
do adduser $username -s /bin/false --disabled-login
adduser $username group
echo Giving password to $username
smbpasswd -a $username
done
----------------------------------------------------

then save it as addusers.sh ? and then run it using:

-----------------
sh addusers.sh
-----------------

To run it and get the usernames from a txt file run:

--------------------------------
userlist.txt > xargs sh addusers.sh
--------------------------------

So I take it to change the default group of the user you would change 

"adduser $username group" to adduser $username groupname ?

So if that works, how can I list the users and the groups on the system and how can I add a user to different groups?

usermod -G group1 group2 group3 username ?

Thanks Chris

---

### Post by PacSci on 2009-04-17
Right on so far. If you want to list the users on the system and their groups, run:

```
awk '$3 > 1000 { print $1 ":"; system("groups " $1)}' FS=: /etc/passwd
```

It will list the users on the first line and the groups on the second.

However, if you want to add users to groups, run:

```
usermod -G group1,group2,group3 username
```

You were mostly right, it's just that there's commas instead of spaces between groups in the usermod command.

---

### Post by BkkBonanza on 2009-04-18
I think this,
**userlist.txt > xargs sh addusers.sh**
needs to be 
**cat userlist.txt | xargs sh addusers.sh**
unless I'm forgetting something.

---

### Post by FarehamWeather on 2009-04-18
What do I need to do to set the password of each new user to the same thing?

I need to add the new users to the system and to samba and set the password for every user to password I want to be able to run the script without any need to enter a password for every user.

I would like it to get the usernames from a file which I can edit.

I also need to force the users to change their passwords when they logon to the domain using windows. I have the password sync working between samba and unix working.

Once I have that complete the server can be put on to the network and I can setup the users using the script :)

---

### Post by PacSci on 2009-04-18
@BkkBonanza: You're right.

@FarehamWeather: Another solution would be to nullify the user's password. If you set "null passwords = yes" in smb.conf under the [global] section, you can give everyone blank passwords with this version:

```
#!/bin/sh
# addsmbusers.sh
for username
do adduser $username -s /bin/false --disabled-login
adduser $username group
smbpasswd -a $username
smbpasswd -n $username
done

```

Then, once everyone can log in and has changed their passwords, just switch it to "null passwords = no".

As for forcing password changes, I don't know how that works. Your best bet would be to just ask everyone to change their password, unless someone else has a solution for that.

Also, a better way to run this script using a text file with one username per line is:

```
xargs sudo sh addsmbusers.sh < usernames.txt
```

---

### Post by BkkBonanza on 2009-04-18
For regular linux accounts you can use,
**sudo passwd -e -u user**
to expire the password. This allows it to work once but then forces a password change after login. I couldn't find a similar option for smbpasswd and it probably doesn't make sense. How would you change password for smb when you have disabled normal logins for the user accounts? If users can in fact login then you could use that expire command in your script to force the pwd change. And if you have passwords syncing between linux and samba then I expect that would in turn relay the change onto samba too.

I suppose you could initially enable logins and then after you know all the users are done changing their passwords update the accounts to be login-disabled.

Or generate high quality random passwords in the script and just give the users their passwords right off.

---

### Post by FarehamWeather on 2009-04-18
how can I automaticly create passwords for the users and be able to view them so I can tell the user what it is? :D

---

### Post by BkkBonanza on 2009-04-19
You can generate random passwords from /dev/urandom.
Use a line like this in a script,

rndpwd=`< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8`
echo $rndpwd

For password prompts you will need two entries, like this,

rndpwd=`< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8`
echo -e "$rndpwd\n$rndpwd"

or from the console try,

echo `< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8`

---

### Post by FarehamWeather on 2009-04-19
ok so how do I get the random password it generates to set as the user's password?


Somthing like this?

#!/bin/sh
# addsmbusers.sh
for username
do adduser $username -s /bin/false --disabled-login
adduser $username group
smbpasswd -a $username
smbpasswd $username
rndpwd=`< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8`
echo -e "$rndpwd\n$rndpwd"
done

---

### Post by koenn on 2009-04-19
> **FarehamWeather said:**
> ok so how do I get the random password it generates to set as the user's password?


Somthing like this?

...


try something like this :
```

#!/bin/bash

USERLIST="./userlist"

while read USER; do
	PASS=$(tr -dc _A-Z-a-z-0-9 </dev/urandom  | head -c8 )
        
	# unix account
	  # see -g and -G options to handle groups, see also usermod
 	  # new account is disabled by default; see man useradd
 
        useradd -s /bin/false $USER
	
	    ## alt: enabled unix account with password: 
            # EncryptedPASS=$( mkpasswd --hash=md5  $PASS )
	    # useradd -s /bin/false -p $EncryptedPASS $USER
    
	# samba account
        (echo $PASS ; echo $PASS )|smbpasswd -s -a $USER

        # output so you can tell users their password
         echo $USER $PASS; echo ;

done < $USERLIST

```

test it with a list of test accounts to debug /customize as needed

---

### Post by FarehamWeather on 2009-04-19
Great Thank You very much guys!

Now I have one other problem with file permissions.

When a user logs on to a windows machine to the domain it creates a folder and stores the profile data.

on 4 accounts it keeps saying it cant find the profile or can write to it. I have set the permissions to the owner (being the user creating the files) and left the group and others blank. Now the way I have setup the permissions so they are the same as the other folders and the other users can write data to their profiles.

This is what is set:

drwx------  2 user.1 user.1 4096 2009-04-19 18:38 user.1
drwx------ 13 user.2 user.2 4096 2009-04-19 18:30 user.2
drwx------ 13 root root 4096 2009-04-19 18:27 root

user.2 and root can logon and profiles work correctly. when user.1 logs on it give a error message saying it cant find it or write to it.

I have a feeling its to do with the numbers e.g. user.1 the number is 2 and on the other accounts its 13. Is there away of changing the number and if so what does it do?


current:
drwx------  2 user.1 user.1 4096 2009-04-19 18:38 user.1

number changed:
drwx------  13 user.1 user.1 4096 2009-04-19 18:38 user.1

its really anoying me! :-?

any ideas?

---

