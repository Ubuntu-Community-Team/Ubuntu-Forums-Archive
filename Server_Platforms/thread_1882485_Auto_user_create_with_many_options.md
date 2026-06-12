---
title: "Auto user create with many options"
date: 2011-11-17
forum: Server Platforms
---

### Post by MadFly-SA on 2011-11-17
Hi
 
I am trying to create a script that will do the following:

[LIST]
[*]Create user
[*]Set user password
[*]Set user shell to /bin/false
[*]Create user home dir at /var/www/custom_dir
[*]chown /var/www/custom_dir user
[/LIST]I want to use this script on my LAMP server, when creating new domains for users. The username and the custom_dir will everytime be different, so I tried something with $1, but it kicked out the --help for adduser, and messed up rest of script. I am planning to use my lamp serve with vsftpd.
 
Any help?
 
So that I can run the script with:
 
./setup.sh username password custom_dir

---

### Post by koenn on 2011-11-17
so, 
you want people to debug a script without actually seeing the script.

Interesting.


anyway:

```

useradd  -p $(mkpasswd $2) -m -d /var/www/$3 -s /bin/false  $1
chown $1  /var/www/$3 

```

The second line may be unnecessary.

---

### Post by Jonathan L on 2011-11-17
> **MadFly-SA said:**
> Hi

I am trying to create a script that will do the following:

[LIST]
[*]Create user
[*]Set user password
[*]Set user shell to /bin/false
[*]Create user home dir at /var/www/custom_dir
[*]chown /var/www/custom_dir user
[/LIST]
I want to use this script on my LAMP server, when creating new domains for users. The username and the custom_dir will everytime be different, so I tried something with $1, but it kicked out the --help for adduser, and messed up rest of script. I am planning to use my lamp serve with vsftpd.

Any help?

So that I can run the script with:

./setup.sh username password custom_sir

Hi Madfly

As Koenn says, you might show us the script!  His script with mkpasswd is good, but you might consider adding -m sha-512 and some extra quotes if you want passwords which have spaces.

Also, you'll need to add /bin/false to /etc/scripts or you won't be able to log in with ftp.  Securing your ftp server is an entire project in itself.

In general you have to be careful if you're writing passwords in literally, as they might show up in all kinds of places which aren't very safe: sudo log files, bash history, ps lists.

I'd also recommend a password generator if you're going to do many of these: it's hard to think of good passwords frequently.  If your network is public in any way you need to think of these things: bad people _will_ come knocking on your door.

Confusingly, Linux has both adduser (use this by hand) and useradd (use this in scripts).  And of course you'll need sudo to run it.

Anyways:
```
#!/bin/sh

set -e

if [ $# -lt 3 ]; then
    echo "Usage: $0 username password directory"
    exit 1
fi

user="$1"
pass="$2"
dir="/var/www/$3"

useradd --shell /bin/false --home "$dir" -M "$user"
mkdir "$dir"
chown "$user" "$dir"
(echo "$pass" ; echo "$pass") | passwd "$user" > /dev/null 2>&1

```Kind regards,
Jonathan.

---

### Post by MadFly-SA on 2011-11-18
At the time of my original post I did not have a script to show, :(, after a while of wondering, I started writing the script step by step, and eventually got it working, but I am still not sure if it works for the ftp, as I am still trying to figure out how I configured vsftpd last time when i used it. ( now trying to login to the old server, but cannot remember login details :D )
 
But anyhow...
 
I'll have a look again tonight, but I like Jonathan L's script very much. Once at home tonight I'll upload the script I wrote for comparison or whatever :D

---

### Post by MadFly-SA on 2011-11-18
The script I ended up with last night looks like this:
 
#!/bin/sh
#
#
mkdir /var/www/$1
#
useradd -d /var/www/$1 -s /bin/false $2
#
passwd $2
#
chown -R /var/www/$2
#
chmod -R 755 /var/www/$1
 
I managed to get the vsftpd.conf file off the old hard drive, will now copy it to new server, and test ftp with new user creation.

---

### Post by Jonathan L on 2011-11-18
Hi Madflay

Looks like you're getting good progress.  Having to do the password interactively looks good.

I really do recommend a check on the number of command line arguments, and -e to stop on errors.  It just saves the aggravation when you mistype it, and stops you having to undo something silly: remember, you are root when you're running these commands.[FONT=monospace]
[/FONT]```
set -e
if [ $# -lt 2 ]; then
  echo "Usage: $0 username directory"
  exit 1
fi
```Kind regards
Jonathan

---

### Post by MadFly-SA on 2011-11-18
I tried again setting up a user for use with vsftpd, no way it wants to work. I managed to get the vsftpd.conf file of the old hard drive, and replaced the one on the new server, but still the new user cannot ftp. I cannot even ftp in on vsftp with root.
 
Could it be that apparmor is causing this issue?
 
Will test the user creation script some more, but look VERY nice so far:D

---

### Post by Jonathan L on 2011-11-18
> **MadFly-SA said:**
> I tried again setting up a user for use with vsftpd, no way it wants to work. I managed to get the vsftpd.conf file of the old hard drive, and replaced the one on the new server, but still the new user cannot ftp. I cannot even ftp in on vsftp with root.
 
Could it be that apparmor is causing this issue?
 
Will test the user creation script some more, but look VERY nice so far:D

Hi Madfly

By default (and it's a good idea), vsftpd will not let someone log in unless their shell is listed in /etc/shells, and that doesn't normally include /bin/false.  Either edit /etc/shells (preferred) or adjust your vsftpd.conf.

Also: you won't be able to log in as a local user unless your vsftpd.conf has:
```
local_enable=YES

```You won't be able to log in as root unless you've given it a password (not a good idea anyways), and though I haven't tried it I'm sure vsftpd won't let you log in as root even if you do. (Edit: default installation has /etc/ftpusers preventing users root, daemon etc from logging in, very sensibly)

Try it with a normal user and their password.

Apparmor: I doubt it's what's stopping you logging in.  But if you suspect it, switch it off

Kind regards,
Jonathan.

---

### Post by MadFly-SA on 2011-11-21
my ftp is working ok now, able to create new users with the script, and login to home dir, and ONLY access home dir.
I changed the shell to /bin/fake, after adding /bin/fake to /etc/shells. User is not able to login on server with ssh.
 
Thanks for all the help.

---

