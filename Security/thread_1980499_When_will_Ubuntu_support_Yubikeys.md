---
title: "When will Ubuntu support Yubikeys?"
date: 2012-05-15
forum: Security
---

### Post by JarG0n on 2012-05-15
When will Ubuntu support Yubikeys from Yubico.com for end user logins?  This is 2 factor authentication.

---

### Post by Soul-Sing on 2012-05-15
ubuntu supports this.
- yubikey-personalization
- libykpers-1-1 or higher

its in the repositories.
```
sudo ykpersonalize -ofixed=cccccccccccc -a00000000000000000000000000000000 -2

```
fixed: m:
uid: h:000000000000
key: h:00000000000000000000000000000000
acc_code: h:000000000000
ticket_flags: APPEND_CR
config_flags: STATIC_TICKET|STRONG_PW1|STRONG_PW2|MAN_UPDATE|OATH_FIXED_MODHEX1|OATH_FIXED_MODHEX2|OATH_FIXED_MODHEX

Commit? (y/n) [n]: y

hold key between 3-5 sec. conf. 2/

---

### Post by JarG0n on 2012-05-15
> **leoquant said:**
> ubuntu supports this.

I don't see an option to login to the workstation using Yubikeys though.

---

### Post by Soul-Sing on 2012-05-15
> **JarG0n said:**
> I don't see an option to login to the workstation using Yubikeys though.

can be done.10.4 system
```
sudo -i
```
```
apt-get install libpam0g-dev build-essential libykpers-1-1 yubikey-personalization
```
[http://www.securixlive.com/yubipam/download.php](http://www.securixlive.com/yubipam/download.php)

```
cd /usr/local/src
wget http://www.securixlive.com/download/yubipam/YubiPAM-1.0.4.tar.gz
```

```
tar xf YubiPAM-1.0.4.tar.gz 
cd YubiPAM-1.0.4
./configure
make install
```

```
addgroup yubiauth
touch /etc/yubikey
chgrp yubiauth /etc/yubikey /sbin/yk_chkpwd
chmod g+rw /etc/yubikey 
chmod g+s /sbin/yk_chkpwd
```
exit

```
dd if=/dev/urandom count=16 bs=1 2>/dev/null | od -x | tr -d ' ' | sed -n 's/^0000000//p'

```

```
sudo ykpersonalize -a<AES key> -ofixed=ccccccbbltfi
```

faillure/error add. this one:
```
sudo rmmod usbhid
sudo modprobe usbhid quirks=0x1050:0x0010:0x04
sudo ykpersonalize -a<AES sleutel> -ofixed=ccccccbbltfi
sudo rmmod usbhid
sudo modprobe usbhid
```


```
sudo ykpasswd -a --user yourname -k <AES sleutel> -o <press Yubikey for Token>
```
```
ykvalidate --user yourname <press Yubikey for Token>
```

```
sudo gedit /etc/pam.d/common-auth
```

```
auth sufficient pam_yubikey.so
```
save this and reboot.

this is an experimental set-up/for a test system.

---

### Post by JarG0n on 2012-05-15
wow, thanks!

---

### Post by Anderen2 on 2013-04-11
Quite a bump, but this thread is at the top of the search, and the walkthrough posted by Soul-Sing does not work anymore, atleast not for me. So heres a different way to do this (This is working as of Ubuntu 12.04 LTS):

Get all needed dependencies (libykclient-dev libykpers-1-dev libyubikey-dev libpam0g-dev )
```
sudo apt-get install libykclient-dev libykpers-1-dev libyubikey-dev libpam0g-dev
```

Download, extract and install pam_yubico-2.13 (Go to yubico-pam.googlecode.com to get the latest version)
```
wget http://yubico-pam.googlecode.com/files/pam_yubico-2.13.tar.gz
tar -zxvf ./pam_yubico-2.13.tar.gz
cd pam_yubico-2.13
./configure
sudo make check install
```

Copy over the files required for PAM
```
sudo cp /usr/local/lib/security/pam_yubico.so /lib/security/
```

Create user files
```
mkdir ~/.yubico
nano ~/.yubico/.authorized_yubikeys
```

In here, type in your username, and yubikey token ID(s) in the format:
<user name>:<yubikey token ID>:<yubikey token ID 2>: &#8230;.
ex. anderen2:ccccccqwerty
or. anderen2:ccccccqwerty:ccccccasdfgh:cccccczxcvbn (if you have multiple yubikeys)

The token ID is the first 12 characters in your OTP (One Time Password)
Multiple user support is done by making another .yubikey folder and a authorized_yubikeys file in the other users home folder

After this, you just have to enable the Yubikey PAM module to be used on the login screen
```
sudo nano /etc/pam.d/common-auth
```
In this file, add the line "auth required pam_yubico.so id=16 debug" at the top of the file. (You may remove the debug flag after testing it)

Reboot or logout and you should now be able to use two-factor signin with first a yubikey and then a password.
If you get a fallback to simple graphics, you've done something wrong in the /etc/pam.d folder. Remove the changes and it will boot as normal again. 

Good luck :)
- Anderen2

---

### Post by sif519 on 2013-05-08
the default authorization file is "[COLOR=#000000][FONT=Ubuntu Mono]authorized_yubikeys" not ".[/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]authorized_yubikeys" i do believe this can be set through the [/COLOR][/FONT][COLOR=#333333][FONT=Consolas]authfile[/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000] flag [/COLOR][/FONT]

---

### Post by Leslie Dorner on 2013-05-08
I got 2 questions:

1. Does this work on Ubuntu 13.04 64 bit? Has anyone tested it yet? If so, then what were the results and the problems?

2. How do I get my Yubikey token ID OTPs? I have two of them. These instructions don't show me how to get them.

Thanks.

---

### Post by Leslie Dorner on 2013-05-08
My Administrator account has an encrypted /home folder. Is this still going to work on Ubuntu 13.04 with an encrypted /home folder or not? Did anyone try that out? I don't want to get myself locked out again.

If someone could try this out on their bare-metal installation, then I would appreciate your reply. Thanks.

---

### Post by tijn_tux on 2013-06-05
> **sif519 said:**
> the default authorization file is "[COLOR=#000000][FONT=Ubuntu Mono]authorized_yubikeys" not ".[/FONT][/COLOR][FONT=Ubuntu Mono][COLOR=#000000]authorized_yubikeys" i do believe this can be set through the [/COLOR][/FONT][COLOR=#333333][FONT=Consolas]authfile[/FONT][/COLOR][FONT=Ubuntu Mono][COLOR=#000000] flag [/COLOR][/FONT]

Nice :) I had already locked myself out ;)

How and where can i check/set the authfile flag?

---

### Post by Welly Wu on 2013-08-24
These instructions don't work with an encrypted /home partition. I installed Ubuntu 12.04.3 LTS 64 bit with full-disk encryption and an encrypted /home partition. I was wondering if I moved the location of the authorized-yubikeys to my /root partition in /root/.yubico, then would this work with the Ubuntu Unity Greeter for two-factor authentication? I can get everything else to work, but I can't log into Ubuntu Unity with an encrypted /home partition. How do I fix this problem?

---

### Post by Welly Wu on 2013-08-24
Yubico does not recommend an encrypted /home partition while using two-factor authentication with their Yubikeys. I guess this issue is laid to rest.

---

