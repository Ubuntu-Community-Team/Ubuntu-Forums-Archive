---
title: "Encryption Password Mixup"
date: 2009-05-04
forum: Security
---

### Post by ItsJweed on 2009-05-04
Hey,

I've had Ubuntu installed for a while with full-disk encryption with LUKS and LVM and I've used an obscenely strong password. (>80 characters totally random) It's worked out great and I had it memorized to the point where my hands would type it in without me even thinking about it. Unfortunately for some reason my muscle memory shifted and now I am one character short when entering the password. I'm pretty sure I know where the missing character is in the sequence but I'm not sure what it is.

I could manually type in the password and try every character for the missing key but that could take upwards of an hour and a half. What is worse is that I feel like each time I type it in wrong I risk getting even more confused.

Is there anyway I could automate the password guessing? I know this question probably sounds suspicious, but I know the password is one of ~180 possible passwords. Is there anyway to do this?

Regards,
J

PS. - Yes, I am a complete moron for allowing myself to get into this position. Feel free to berate me.

---

### Post by HermanAB on 2009-05-04
Howdy,

You can use an 'Expect' script.

The name Expect comes from 'send this, expect that'.  It is meant to drive test systems, which is exactly what you want to do.

---

### Post by rileinc on 2009-05-04
...and I thought I was overzealous with a 30 character passphrase for my encrypted LVM!

Just curious, how long does it take you to type all 80+ characters of passphrase?

---

### Post by ItsJweed on 2009-05-04
> **rileinc said:**
> ...and I thought I was overzealous with a 30 character passphrase for my encrypted LVM!

Just curious, how long does it take you to type all 80+ characters of passphrase?

Around 15 seconds. I figure if I'm going to bother encrypting I might as well use a password that could never be brute-forced. (Though I've been realizing lately it's not really necessary...)

---

### Post by nobodysbusiness on 2009-05-04
I've used the Python library "pexpect" to automate various things. It's pretty easy. Do you know any Python?

---

### Post by HermanAB on 2009-05-05
It would be about 5 liner in Bash with Expect.

---

### Post by ItsJweed on 2009-05-09
> **HermanAB said:**
> It would be about 5 liner in Bash with Expect.

I've tried coding it with expect and had issues. Here is my code...

```
#!/usr/bin/expect
set first "firstpartiknow "
set last " nextpartiknow"


foreach line {a b c d e f g h i j k l m n o p q r s t u v w x y z A B C D E F G H I J K L M N O P Q R S T U V W X Y Z , . / < > ? ; \' : \" \[ \] \{ \} \\ - _ = + \| 1 2 3 4 5 6 7 8 9 0 \` ~ ! \@ # \$ % ^ \& * \( \) } { 


puts "$line....."
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt

expect "Enter LUKS passphrase: "
send "$first$line$last\n"
expect "Enter LUKS passphrase: "
send "$first$line$last\n"
expect "Enter LUKS passphrase: "
send "$first$line$last\n"
expect "Command failed: No key available with this passphrase."
}

```

It doesn't seem to be working. Here is some sample output...

> security@Security:~$ sudo ./breakcrypt.sh 
[sudo] password for security: 
a.....
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: firstpariknow a nextpartiknow


Enter LUKS passphrase: firstpariknow a nextpartiknow

Enter LUKS passphrase: b.....
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: 
Enter LUKS passphrase: 
Enter LUKS passphrase: firstpartiknow b nextpartiknow

Command failed: No key available with this passphrase.

c.....
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: 
Enter LUKS passphrase: 
Enter LUKS passphrase: firstpartiknow c nextpartiknow

Command failed: No key available with this passphrase.

d.....
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: firstpartiknow d nextpartiknow


Enter LUKS passphrase: firstpartiknow d nextpartiknow

Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

e.....
spawn cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: 
Enter LUKS passphrase: firstpartiknow e nextpartiknow


It seems like it catches some of the text but not all.



I don't know python, although I've bean meaning to learn...

---

### Post by HermanAB on 2009-05-09
Here is a script that can change LUKS passwords.  Maybe you can use that for inspiration:

```
#! /bin/bash
echo Change the password of a LUKS device
echo Example: luks-password /dev/sdc1 oldpass newpass

# Do the password juggle
# The /tmp directory is a RAM disk
echo -n "$2">/tmp/oldpass
echo -n "$3">/tmp/newpass

# Add the new password, then remove the old one
cryptsetup -d /tmp/oldpass luksAddKey "$1" /tmp/newpass
cryptsetup -d /tmp/newpass luksRemoveKey "$1" /tmp/oldpass

# Remove the files even though it is a RAM disk - still a good idea
rm /tmp/oldpass
rm /tmp/newpass

echo Done

```

---

