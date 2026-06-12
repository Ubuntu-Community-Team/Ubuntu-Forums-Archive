---
title: "Make system choose password from file"
date: 2015-01-22
forum: Security
---

### Post by skeetermcbee on 2015-01-22
I want to set up a virtual victim on a virtual network with virtual machines. I have 2 set up: one with a randomly generated "strong" password, and one without. I want to set up a third one that has a common password. For this, I want the system to access a file of the most common passwords, and change the only users password to that BEFORE the login prompt. Can somebody walk me through how to make the system change a user password from a file, and have it run at boot?

Thanks.

---

### Post by bashiergui on 2015-01-22
You would have to create a script which would run at startup. There are always numerous ways to do everything in Linux. Here's the way I did it:

1. Create a snapshot of your virtual machine. 

2. Create a text file of bad passwords with one password per line. For example```
password
123456
iloveyou
password123
```

3. Here's a script that will pick the last password in the file and change your standard user's password to that. Call it BadPasswords.sh or something.
```
#! /bin/bash

# ************RUN AT YOUR OWN RISK!!!!!!!!!*********
# This script will change the password of the user specified.
# It depends on the file BadPasswords.txt

# First get the new password from the bottom of a list of
# terrible passwords that you created.
tail -n 1 BadPasswords.txt > NewPassword.txt

# Then prepend username: before the password so it's in the 
# format chpasswd is expecting. Change username to the 
# actual name of your user.
echo -e "username:$(cat NewPassword.txt)" > NewPassword.txt

# Next change the password to this new password
cat NewPassword.txt | chpasswd

# Now put the new password at the beginning of your list so that 
# the next time the script runs it will use a different password.
# The sed line is buggy; it seems to delete the most recently used
# password sporadically, but I didn't care enough to debug it.
first=$(head -n 1 BadPasswords.txt)
last=$(tail -n 1 BadPasswords.txt)
sed -i -e "/$last/d" -e "/$first/ i\\
$last
" BadPasswords.txt
```I chose to do a (pretty lousy) bash script. I'm sure someone on this forum can do this bash script in one line. You can script it in any language you like.

4. I had to chmod the shell script to 777, I didn't bother testing if it would run as root without chmod.

5. Test the script **_on a virtual machine that you have a snapshot of_!!!! **You will run the script by typing ```
./BadPasswords.sh
``` I had to run it as root, otherwise it prompted me for the existing password. You might be able to run it as your user but I didn't bother trying to figure out how. To find out what your new password is you can do```
cat NewPassword.txt
``` 

6. Then set the script to run at startup. There are a bunch of ways to do this. I chose ```
crontab -e
```Then add a line like this ```
@reboot /home/username/BadPasswords.sh
```Use the path to your actual script, I can't know where you'll put it. _**Have a snapshot of the system with a password you know.**_

---

### Post by schragge on 2015-01-23
A simpler and more reliable sed expression would be
```
sed -i '$d;1i '"$last" BadPasswords.txt
```

---

### Post by skeetermcbee on 2015-02-01
Thank you both! These are brilliant!

---

### Post by wannabe user on 2015-02-06
Hi, I'll offer my approach.

```

#!/bin/bash


TARGET="sally"                                                                      #Target user
FILE="./passwords.ls"                                                             #File containing passwords
PASS=$(/usr/bin/head -1 $FILE | openssl passwd -1 -stdin)       #Password to use


/usr/sbin/usermod --pass="$PASS" $TARGET                            #Set password


sed -i '1 {h;d;}; $ {p; x;}' $FILE                                             #Cp 1st line, delete it, print EOF

```

I've extended it a bit to include some comments :p and to make it easy to change. It would also be very simple to take in an argument for say, the username. So basically you're setting the target user who should have their password changed, the file which contains the passwords like:
> 
passwordA
passwordB
passwordC


You're then using the head command with 1 line to pipe this into openssl for encryption, this may seem redundant as you have the password in plaintext, however it's the preferred way with usermod and normally you wouldn't have a file with the plaintext, but it makes it easier for you to see what the last password used was for testing.
Usermod command is used to set the password for the target, and then some sed to move the line to the bottom. 

What the sed is actually doing is:
[LIST]
[*]Select 1st line
[*]Copy it to 'hold space'
[*]Delete this line
[*]Go to the end of the file (last line)
[*]Print line and exchange contents of hold and pattern space (so you don't create duplicate lines)
[/LIST]
The '-i' option allows inline editing.

---

