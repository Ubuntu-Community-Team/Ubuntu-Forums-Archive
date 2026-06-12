---
title: "add samba users"
date: 2010-01-04
forum: Server Platforms
---

### Post by root1234 on 2010-01-04
Hi there.

I need to add 200 samba users and i am looking for a script to use to add the users with password with out typing each one .

Any help will be great

---

### Post by root1234 on 2010-01-05
Hi there.

Does anyone know how to import a text file with usernames and password for samba?

user1 password1

Thanks
root

---

### Post by root1234 on 2010-01-07
hi there.

I got this script from a friend but is not working 100% any help will be great.

Name.txt:
test1 it test123
test2 hr test234
 
#!/bin/bash
#
# Ensure that root is running the script.
##
NEW_USERS="/home/names.txt"
 
cat ${NEW_USERS} | \
while read USER GROUP SMBPASS ; do
** 
** groupadd ${GROUP} 2> /dev/null
** adduser ${USER} -g ${GROUP}
 
** (echo $SMBPASS; echo $SMBPASS) | passwd --stdin ${USER} > /dev/null
** echo Added user ${USER}
 
** smbpasswd -e ${USER} -w ${SMBPASS} > /dev/null
** (echo $SMBPASS; echo $SMBPASS) | smbpasswd -as ${USER}
** echo -e "${USER} = ${USER}" >> /etc/samba/smbusers
done

---

### Post by root1234 on 2010-01-07
Hi there.

I found a script that works for anyone that need it.

test file names.txt

#!/bin/bash

USERLIST="names.txt"

while read USER; do
PASS=$(tr -dc a-z-0-9 </dev/urandom | head -c6 )

# samba account
(echo $PASS ; echo $PASS )|smbpasswd -s -a $USER

# output so you can tell users their password
echo $USER $PASS; echo  ;

done < $USERLIST > "passwords.txt"

Root1234

---

