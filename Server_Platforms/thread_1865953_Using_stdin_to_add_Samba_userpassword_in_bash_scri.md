---
title: "Using stdin to add Samba user/password in bash script"
date: 2011-10-20
forum: Server Platforms
---

### Post by RyanRahl on 2011-10-20
Hi, I am writing a script that will add a user to my server that includes a system user, samba user, shared samba and nfs home folder, access to a public folder and possibly an rsa key for my vpn. Anyway everything was going fine until I needed to add the Samba user and I can't for the life of me figure out how to use stdin to give the smbpasswd program the password that is/will be defined by a read input from the user, meant to be used for both the system id and the samba id. I like to divide my scripts into small functions to be added to a main routine later on so here is my function:

```

# Add user and password to Samba
function samba_add
{
	(echo $pass; echo $pass) | smbpasswd -s -a $user
}

```

and this is the output it gives me from bash -x
```

+ read user
user
+ read pass
password
+ echo password
+ echo password
+ smbpasswd -s -a user
Failed to add entry for user user.

```

and if I only have one instance of the password, ie:
```

# Add user and password to Samba
function samba_add
{
	(echo $pass) | smbpasswd -s -a $user
}

```

i get
```

+ read user
user
+ read pass
password
+ echo password
+ smbpasswd -s -a user
Mismatch - password unchanged.
Unable to get new password.

```

so it seems to me that it is taking the password, based on the results I get from the script using only one instance of the password variable because it gives a mismatch error. Meaning the password entered is not a match with nothing/empty. So how do I send the contents of the password variable to the initial prompt for the smbpasswd and the verification prompt?

---

### Post by vasile002 on 2011-10-21
you can try this:
```

echo -e "$pass\n$pass" | smbpasswd -s -a $user

```or
```

smbpasswd -a $user<<EOF
$pass
$pass
EOF

```I hope this helps

---

### Post by Jonathan L on 2011-10-21
> **RyanRahl said:**
> Hi, I am writing a script that will add a user to my server that includes a system user, samba user, shared samba and nfs home folder, access to a public folder and possibly an rsa key for my vpn. Anyway everything was going fine until I needed to add the Samba user and I can't for the life of me figure out how to use stdin to give the smbpasswd program the password that is/will be defined by a read input from the user, meant to be used for both the system id and the samba id. I like to divide my scripts into small functions to be added to a main routine later on so here is my function:
...

Hi Ryan

There's nothing wrong with your original shell script: the problem is with the configuration of samba passwords.  The output is consistent with no user called 'user' in /etc/passwd, and Samba configured to require one in /etc/samba/smb.conf ("security = user", I believe).  Perhaps you just need to add the user (with adduser or whatever you use) before smbpasswd?

To check it, try "smbpasswd -s -a user" on the command line and see if you get the same response.

Hope that helps

Kind regards,
Jonathan.

This test file worked exactly as you wanted it to.  Though you really need quotes around the password, to protect to allow  passwrds with spaces and so on.

Tested with smbpasswd that comes with smbd 3.4.0, Ubuntu 10.4

```
function samba_add
{
    (echo "$pass"; echo "$pass") | smbpasswd -s -a $user
}

user=ftp
pass=silly
samba_add
```I was able to run it as follows: the first time it adds a user, the second time it just modifies it.

```
$ sudo bash -x test
+ user=ftp
+ pass=silly
+ samba_add
+ echo silly
+ smbpasswd -s -a ftp
+ echo silly
Added user ftp.
$ sudo bash -x test
+ user=ftp
+ pass=silly
+ samba_add
+ echo silly
+ smbpasswd -s -a ftp
+ echo silly
```

---

### Post by RyanRahl on 2011-10-21
> **Jonathan L said:**
> Perhaps you just need to add the user (with adduser or whatever you use) before smbpasswd?

Ahhh, a very silly oversight on my part. As I was writing the script I was testing functions individually so the user in question did on exist on the system. Thank you for pointing that out. :)

> Though you really need quotes around the password, to protect to allow passwrds with spaces and so on.

Thank you for the tip. :)

@vasile002: Thank you for the suggestions, I have not tried them but I don't see any reason they wouldn't work. :)

So now my script is functioning perfectly. It adds a system user, home folder, samba share and user, gives group permissions to the user to access a predefined pubic folder and gives the "supervisor" permissions to access the new users folder. I'm thinking about adding a function to create an NFS export depending on what kind of client machines I get. Thank you for your help and here is the script for anyone who wants to use it. :)
(note: for this script to work you must have a working Samba server and a public folder and group)

```

#!/bin/bash
############
###Variables
############

user=user            		     # New user name
pass="password"     	          # New user password
admin_user=$USERNAME	          # Supervisor's account name
samba_config=/etc/samba/smb.conf   # Path to Samba config file (smb.conf)

############
###Functions
############

## Check for root access
root_check ()
{
     if [ $(id -u) != "0" ]
          then echo "Need to be root" >&2; exit 1
     fi
}

# Obtain variable values from user input
get_variables ()
{
     echo "+++++User Creation+++++"
     echo -n "Enter user name:"
          read user
     echo -n "Enter Password:"
          read -s pass
     echo ""
     echo -n "Verify Password:"
          read -s passv
          if [ "$pass" != "$passv" ]
               then echo "Passwords do not match" >&2; exit 1
          fi
     echo ""
     echo -n "Supervisor's user name:"
          read admin_user
}

# Add system user with home directory and public group permissions then
# set encrypted password
add_user ()
{
	useradd $user -m -G public -s /dev/null
	echo "$user:$pass" | chpasswd
}

# Add supervisor to users group for ease of administraton
admin2group ()
{
	usermod -a -G $user $admin_user
}
# Capitalize user name for Samba share name
capitalize_first ()
{
  firstchar=${user:0:1}
  user1=${user:1}
  FirstChar=`echo "$firstchar" | tr a-z A-Z`
  echo "$FirstChar$user1"
}

# Add user and password to Samba
add_samba ()
{
	(echo "$pass"; echo "$pass") | smbpasswd -s -a $user
}

# Add Samba share and public permissions for new user
# Public share must be formatted as follows for the first 5 lines:
#                 [Public]                                                    #
#                   path = /home/public                                       #
#                   comment = Public Folder                                   #
#                   valid users = (user names here)                           #
#                   write list = (user names here)          
add_share ()
{
	echo -e "\n[$capname]\n path = /home/$user\n comment = $capname's Folder\n guest ok = no\n browseable = yes\n write list = $user $admin_user\n create mask = 0771" >> $samba_config # Create private share for user
	sed -i '/\[Public\]/{n;n;n;s/$/ '$user'/;}' $samba_config # Add user to valid users in public share
	sed -i '/\[Public\]/{n;n;n;n;s/$/ '$user'/;}' $samba_config # Add user to write list in public share
}

# Restart Samba server
smbd_restart ()
{
	smbd restart
}

################
### Main Routine
################
root_check
clear
# Get user info and get going
get_variables
capitalize_first
# Create system and samba user with home directory
echo "Creating user"
     add_user && add_samba
          if [ "$?" = "0" ]; then
               echo "Completed user creation"
          else
               echo "Failed to create user" >&2; exit 1
          fi
# Create shares in smb.conf and add supervisor to user's group
echo "Creating shares and permissions"
     add_share && admin2group
          if [ "$?" = "0" ]; then
               echo "Completed share and permission creation"
          else
               echo "Failed to create share or permissions" >&2; exit 1
          fi
# Restart samba
echo "Restarting Samba sharing service"
     smbd_restart
          if [ "$?" = "0" ]; then
               echo "Complete"
          else
               echo "Fail" >&2; exit 1
          fi
exit

```

Thanks again for your help.

---

### Post by capscrew on 2011-10-21
> **RyanRahl said:**
> Ahhh, a very silly oversight on my part. As I was writing the script I was testing functions individually so the user in question did on exist on the system. Thank you for pointing that out. :)



Thank you for the tip. :)

@vasile002: Thank you for the suggestions, I have not tried them but I don't see any reason they wouldn't work. :)

So now my script is functioning perfectly. It adds a system user, home folder, samba share and user, gives group permissions to the user to access a predefined pubic folder and gives the "supervisor" permissions to access the new users folder. I'm thinking about adding a function to create an NFS export depending on what kind of client machines I get. Thank you for your help and here is the script for anyone who wants to use it. :)
(note: for this script to work you must have a working Samba server and a public folder and group)

```

#!/bin/bash


############
###Variables
############

user=user            		     # New user name
pass="password"     	          # New user password
admin_user=$USERNAME	          # Supervisor's account name
samba_config=/etc/samba/smb.conf   # Path to Samba config file (smb.conf)

############
###Functions
############

## Check for root access
function root_check
{
     if [ $(id -u) != "0" ]
          then echo "Need to be root" >&2; exit 1
     fi
}

# Obtain variable values from user input
function get_variables
{
     echo "+++++User Creation+++++"
     echo -n "Enter user name:"
          read user
     echo -n "Enter Password:"
          read -s pass
     echo ""
     echo -n "Verify Password:"
          read -s passv
          if [ "$pass" != "$passv" ]
               then echo "Passwords do not match" >&2; exit 1
          fi
     echo ""
     echo -n "Supervisor's admin user name:"
          read admin_user
}

# Add user with home directory and public group permissions
function add_user
{
	useradd $user -m -G public -d /home/$user -p $pass
}

# Add admin to users group for ease of administraton
function admin2group
{
	usermod -a -G $user $admin_user
}

# Add user and password to Samba
function add_samba
{
	(echo "$pass"; echo "$pass") | smbpasswd -s -a $user
}

# Add Samba share for new user
function add_share
{
	echo -e "\n[$user]\n path = /home/$user\n comment = $user's Folder\n guest ok = no\n browseable = yes\n write list = $user $admin_user" >> $samba_config
}

# Restart Samba server
function smbd_restart
{
	smbd restart
}

################
### Main Routine
################
root_check
clear
# Get user info and get going
get_variables
# Create system and samba user with home directory
echo "Creating user"
     add_user && add_samba
          if [ "$?" = "0" ]; then
               echo "Completed user creation"
          else
               echo "Failed to create user" >&2; exit 1
          fi
# Create shares in smb.conf and add admin to user's group
echo "Creating shares and permissions"
     add_share && admin2group
          if [ "$?" = "0" ]; then
               echo "Completed share and permission creation"
          else
               echo "Failed to create share or permissions" >&2; exit 1
          fi
# Restart samba
echo "Restarting Samba sharing service"
     smbd_restart
          if [ "$?" = "0" ]; then
               echo "Complete"
          else
               echo "Fail" >&2; exit 1
          fi
exit

```

Thanks again for your help.

Why are you creating interactive users (access to an interactive shell and a home directory)?  You might think about how to create a user that can't login to the server.  Maybe *useradd -r* (--system).  See the man pages.  Using the utility *adduser * this would be *adduser --system*.  See the  "add a system user" section of the man pages (man adduser).

---

### Post by RyanRahl on 2011-10-21
@capscrew, I am using pubkey authentication for ssh but you still make a very valid point. 

Revised function:
```

# Add user with home directory and public group permissions
function add_user
{
	useradd $user -r -m -G public -d /home/$user -p $pass
}

```

So if I wanted to give a user access to a shell later on will I be able to do this with usermod? Is access to an interactive shell and a home directory the only difference between interactive and system users?

---

### Post by capscrew on 2011-10-21
> **RyanRahl said:**
> @capscrew, I am using pubkey authentication for ssh but you still make a very valid point. 

Revised function:
```

# Add user with home directory and public group permissions
function add_user
{
	useradd $user -r -m -G public -d /home/$user -p $pass
}

```

So if I wanted to give a user access to a shell later on will I be able to do this with usermod? Is access to an interactive shell and a home directory the only difference between interactive and system users?
As far as I know the interactive shell access and home dir is all that separates a *mortal* user from a *system* user.  Think of samba server with 200 users of the share that you need to police from messing with your server.  Not to mention all those home directories that they have a right to.  I think I would drop the *-d /home/$user *from the script and see what happens.  All in all, a very nice script you have created.

Edit: There is one more thing about system users -- NO PASSWORD.  This means you do not have to sync the Ubuntu pass with the samba user pass.  No PAM problems either.  Yes the smbpasswd will work.  The limitation is that there must be a Ubuntu user, not whether it has a password.

Yes you can update the account with usermod.  You can add a home directory as well as an interactive shell.

---

### Post by RyanRahl on 2011-10-21
Thanks! You've been helpful. So if I want to give shell access to one of my users (it will be rbash) I will have to give the account a password even though it is a system account effectively making it an interactive account. Best to start a restricted as possible and give users access as needed. I have read permissions on the home folders only for the owner and the owner's group so the other users should not have access to other users home folders. For the interactive users I suppose I should add a chroot to their login script anyway. 

what would be the reason to drop the "-d /home/$user" from the function?

---

### Post by erixnow on 2011-10-22
food for thought..... let xinetd do the work for you.  inthe xinetd.d directory setup a service to your script (I happen to use perl since I am more comfortable with it) ... but std in will be bound to a port for input.


my $old_fh = select(STDOUT);
$| = 1; #kill buffering to filehandle so it doesnt delay sh**

while( my $line = <STDIN> )
{
    $line =~ s/\r?\n$//;
    if ($line =~ /quit/)
    {
        die "shutting down\n";
    }
    elsif ($line eq "panic")
    {
       print "PANIC forcing shutup !\n";
       system('/root/lockup.pl');
    }



just a clip from a script I had running to automatically do a couple of things from a remote socket connection.  This was the most basic example I had.  Hope that helps a bit.  If you decide to add users remotely this setup will work great for you.

-Eric Peyser

---

### Post by CharlesA on 2011-10-22
> **capscrew said:**
> Why are you creating interactive users (access to an interactive shell and a home directory)?  You might think about how to create a user that can't login to the server.  Maybe *useradd -r* (--system).  See the man pages.  Using the utility *adduser * this would be *adduser --system*.  See the  "add a system user" section of the man pages (man adduser).

I use this command to add my samba users:
```
useradd htpc -u 1001 -M -d /dev/null -s /dev/null -U -G raid
```

Is that the correct way to do it?

---

### Post by capscrew on 2011-10-22
> **CharlesA said:**
> I use this command to add my samba users:
```
useradd htpc -u 1001 -M -d /dev/null -s /dev/null -U -G raid
```

Is that the correct way to do it?

If it works, then great.  I've never tried this but here are my initial thoughts: The switch -M means don't create a home directory automatically, but then you manually crate one to nowhere.  If you didn't want one why run the -d switch at all.  Why create a shell (with -s) if you don't want one either.

---

### Post by Jonathan L on 2011-10-23
> **capscrew said:**
> As far as I know the interactive shell access and home dir is all that separates a *mortal* user from a *system* user.  Think of samba server with 200 users of the share that you need to police from messing with your server.  Not to mention all those home directories that they have a right to.  I think I would drop the *-d /home/$user *from the script and see what happens.  All in all, a very nice script you have created.

Edit: There is one more thing about system users -- NO PASSWORD.  This means you do not have to sync the Ubuntu pass with the samba user pass.  No PAM problems either.  Yes the smbpasswd will work.  The limitation is that there must be a Ubuntu user, not whether it has a password.

Yes you can update the account with usermod.  You can add a home directory as well as an interactive shell.

... just some thoughts: there are really a number of kinds of account here:

1. Samba users: accounts for those to use the file server (ie, the samba users we started with)
2. Interactive users: accounts of those to use shells (the potential users we've just been speaking about)
3. Admin users: accounts of those who run the system (ie, Ryan)
4. System users: accounts of those who never log in but just own directors (root, daemon, bin, ...)

It's traditional that those 'system users' in category 4 have low user ids, which helps keeps things straight (but isn't as far as I know used anywhere) from the users which are in higher numeric range..

For your samba users (case 1), I'd try putting them in the normal UID space, with disabled passwords, no home directory, no login shell etc.  But I wouldn't use the useradd -r method, I'd use the appropriate flags (-M don't create home, -s /usr/bin/nologin, and don't set a password.
   ```
useradd $user -d /home/$user -M -s /usr/sbin/nologin
```This makes an account with the home directory defined but not created, and no password (look in /etc/shadow), with a never-log-in shell, with a uid in the 1000 range.

For interactive users (case 2), you make another script to convert them (make directories, install dot files, change shell, apply password and so on.  Many times I've seen users categories as "samba-only", "mail-only", "ftp only" and so on. 

Script looks nice and tidy!  But did you know that the  "function" keyword is unique to bash? Given that the default system shell changes from time to time, I'd suggest being conservative with this script. 
If you run your script with  another implementation of the bourne shell (ie, the normal shell  /bin/sh, which is currently 'dash'), it's incompatible?  Given they both accept the original syntax, I'd recommend it:
```
useradd ()
{
...
}

```Hope that's of some use

Kind regards
Jonathan

---

### Post by CharlesA on 2011-10-23
> **capscrew said:**
> If it works, then great.  I've never tried this but here are my initial thoughts: The switch -M means don't create a home directory automatically, but then you manually crate one to nowhere.  If you didn't want one why run the -d switch at all.  Why create a shell (with -s) if you don't want one either.

Thought all users had to have a home directory and shell?

If you run the command without redirecting it to /dev/null, it adds the shell as /bin/sh. Of course that wouldn't work if the user doesn't have a password set, but better safe then sorry.

```
sudo useradd test1 -u 1002

```
```
test1:x:1002:1002::/home/test1:/bin/sh
```

---

### Post by RyanRahl on 2011-10-24
@erixnow That was out of left field, definitely something to think about. :guitar:

> Script looks nice and tidy! But did you know that the "function" keyword is unique to bash? Given that the default system shell changes from time to time, I'd suggest being conservative with this script. 
If you run your script with another implementation of the bourne shell (ie, the normal shell /bin/sh, which is currently 'dash'), it's incompatible?

Thanks, and I didn't know that. Is there a place where I can compare the syntax differences between the shell scripting languages? 

> If you run the command without redirecting it to /dev/null, it adds the shell as /bin/sh. Of course that wouldn't work if the user doesn't have a password set, but better safe then sorry.

Interesting point. I like the idea of using ```
-s /dev/null
```

I looked in the /etc/passwd file and most of the system users use  /bin/sh however there are some that use /bin/false and /sbin/nologin which are good and slightly better, respectively but neither as good as /dev/null.

---

