---
title: "Unable to execute .sh script"
date: 2010-05-13
forum: Server Platforms
---

### Post by simmerin on 2010-05-13
I have a Dell PowerEdge 2850 running Ubuntu 10.04 Server with SSH and Samba. My problem is that I am unable to execute my adduser.sh script which reads from a text file and adds users to the box and Samba. I have ran chmod a+x to make it executable and placed it in /usr/local/bin. 

When I run sudo adduser.sh I get "sudo: unable to execute /usr/local/bin/adduser.sh: No such file or directory".

When I run adduser.sh I get "-bash: /usr/local/bin/adduser.sh: /bin/bash^M: bad interpreter: No such file or directory
"
I have been using Kubuntu as my home workstation for some time now but am new to the Linux server environment and specifically shell scripting. I have managed Windows servers but since I was given the freedom to setup this server I chose Linux. Thanks for any and all help with this issue.

---

### Post by TheFuturian on 2010-05-13
Does sudo ./adduser.sh work?

---

### Post by simmerin on 2010-05-13
Negative it gives the "no such file or directory" error.

---

### Post by wojox on 2010-05-13
I think it's 

```
sudo sh adduser.sh
```

---

### Post by TheFuturian on 2010-05-13
If that don't work can you please supply the output of:-

```
ls -l /usr/local/bin/adduser.sh
```

---

### Post by simmerin on 2010-05-14
Ok so sudo sh adduser.sh worked, thanks to wojox, and the script executes but it erros out. The error I am getting is 
: not found 30:
: not found 33:
: not found 36:
adduser.sh: 94: Syntax error: "||" unexpected

Below is the sript and as you can see lines 30, 33, and 36 are blank lines so does bash not no how to handle these. Any help you all could offer on the line 94 error would be great as my scripting skills are rather primitive right now.

#!/bin/bash

# Script to add users to Linux and Samba
echo " "
echo "**************************************"
echo " This script takes a list of usernames, groups, and plaintext passwords from"
echo " a file named 'userlist' and located in the same directory as the script, and"
echo " from this file creates Linux and Samba users."
echo ""
echo " It can ONLY be run by root, and will fail if another user attempts to run it."
echo ""
echo " Values in 'userlist' must be separated by a single space character; also, the"
echo " last record (line) in that file must be empty. If it's not, the last user in"
echo " the list will not be added. Note that the script prints only the 1st 4 characters of"
echo " the user plaintext password, to avoid leaving the full password in Bash history. "
echo " For more security, simply comment that line out of the script."
echo ""
echo " The REQUIRED data order is: name group password UIN directory shell samba "
echo " Three lines of SAMPLE data: "
echo "******************************************"
echo "user1 smbgrp user1pass 501 /home/smbusers/user1 /bin/sh 1"
echo "user2 lnxgrp user2pass 521 /home/lnxusers/user2 /bin/sh 0"
echo "user3 lnxgrp user3pass 522 /home/lnxusers/user3 /bin/false 0"
echo "" # empty line!
echo "******************************************"
echo " where samba is '0' or '1'. If 'samba' is '1', then a Samba user and"
echo " password will also be created. "
echo ""
echo "**************************************"
echo ""

# Give ROOT user a chance to read info and make sure he/she wants to run script.
# Comment the line below, and uncomment the next line when you get tired of the pause.

#read -p "yes or no?" response
 response="yes"

if echo $response | grep "y" >/dev/null
then
echo ""
echo "Will continue"
echo ""
else
echo ""
echo "Bailing out!"
echo ""
exit 0
fi

# Check user -- must be root!

if [ $(id -u) -ne 0 ]; then
echo "**************************************"
echo "Only root may add a user to the system"
echo "**************************************"
exit 2
fi

# Users to be created.
new_users="userlist.txt"
echo Reading users from file $new_users
echo ""

# *****************************************************************
# Loop through user data
echo "*************************************"
cat ${new_users} | \
while read username group plainpass uin dir ushell samba; do
echo "**************************************"
echo ""
echo "User: $username Group: $group UID: $uin **"
echo "Pass: $plainpass " | head -c10
echo ""
#	make random salt for openssl
rand=$(cat /dev/urandom | tr -dc A-Za-z0-9 | head -c8)
#	encrypt via openssl using MD5 -- allows long passphrases, but no spaces in this script.
encpass=$(openssl passwd -1 -salt $rand $plainpass)
echo "Home: $dir Shell: $ushell Encrypted password: $encpass Samba?: $samba ***"
echo " "
# *****************************************************************
# Add groups as needed.
#
egrep "^$group" /etc/group >/dev/null
if [ $? -eq 0 ]; then
echo "Group $group exists, and does not need to be created!"
else
groupadd -g $uin $group
fi

# *****************************************************************
# Add matching Samba users.

useradd -m -p $encpass -u $uin -g $group -s $ushell -d $dir $username
[ $? -eq 0 ] && echo "User $username has been added to the system!" \
|| echo "Failed to add user $username!" \


if [ $samba -eq 1 ] ; then
(echo $plainpass; echo $plainpass) | smbpasswd -as $username
echo "User $username added to Samba"
else
echo "Not adding user $username to Samba"
fi
echo ""
echo "**************************************"

done

---

