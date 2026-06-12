---
title: "Ubuntu only requires first 8 chars of password!!"
date: 2007-06-29
forum: Server Platforms
---

### Post by Cheese Sandwich on 2007-06-29
I thought I was being extra careful in using a strong 13 character password, turns out just typing the first 8 will get you in the door!

:eek: :!:

---

### Post by Cheese Sandwich on 2007-06-29
...more specifically, it's the xubuntu desktop (installed on ubuntu server) login & SSH login that only require the first 8. Webmin, however, requires the entire thing.

---

### Post by Cheese Sandwich on 2007-06-29
Hmm, I had set my 13-char password through webmin. Now, trying again to set my 13-char password via "passwd" on the command line, that seems to do the trick (i.e. now logging on to SSH requires the entire 13 chars).

---

### Post by Cheese Sandwich on 2007-06-29
Aha!

It is a webmin issue. I just went in to webmin, & created a new user called "dummy". I set dummy's password to "0123456789".

I then attempted to log into the machine through SSH as dummy. For the password, I typed "01234567" - and it let me in!

---

### Post by Cheese Sandwich on 2007-06-29
Filed a bug report under webmin at sourceforge.

---

### Post by yabbadabbadont on 2007-06-29
I believe this actually has to do with the shadow package.  You need to change the encryption method that is used for storing passwords as the default method only allows up to 8 characters.  Unfortunately, I don't remember how to change it.  I just remember having to do it quite a while ago.

---

### Post by Cheese Sandwich on 2007-06-29
> **yabbadabbadont said:**
> I believe this actually has to do with the shadow package.  You need to change the encryption method that is used for storing passwords as the default method only allows up to 8 characters.  Unfortunately, I don't remember how to change it.  I just remember having to do it quite a while ago.

Webmin should at least warn when the entered password exceeds the max, then...

---

### Post by yabbadabbadont on 2007-06-29
> **Cheese Sandwich said:**
> Webmin should at least warn when the entered password exceeds the max, then...

They probably figure that since passwd won't warn you, they don't need to either.  ;)

---

### Post by yabbadabbadont on 2007-06-29
Actually, after doing some google searches, it might be that the default pam configuration needs to be changed.  See the following for some relevant information: [http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html](http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html)

---

### Post by Cheese Sandwich on 2007-06-29
> **yabbadabbadont said:**
> Actually, after doing some google searches, it might be that the default pam configuration needs to be changed.  See the following for some relevant information: [http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html](http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html)

Hmm, there is a "PAM Authentication" area in Webmin, where it lists PAM "services":

Service 	Description
atd 	
chfn 	Change finger information
chsh 	Change shell
common-account 	
common-auth 	
common-password 	
common-session 	
cron 	Scheduled commands daemon
cupsys 	CUPS printing
gdm 	Gnome X login
gdm-autologin 	
login 	Local or remote login
other 	Other services
passwd 	Password change
ppp 	PPP daemon login
samba 	Samba Windows file server
ssh 	SSH Login
su 	Switch user
sudo 	Limited root command execution
webmin 	Webmin web server
xscreensaver 	Screen saver

...and in "common-password", I see this, for example:

Password change steps
PAM module 	Description 	Failure level 	Parameters 	Move
pam_unix.so 	Old Unix password authentication 	Required 	nullok obscure min=4 max=8 md5

You are probably right...

---

### Post by Cheese Sandwich on 2007-07-02
My webmin bug report was closed & here's the response:

> 
This will happen if Webmin uses classic Unix DES encryption for passwords,
which only takes the first 8 characters into account.
To use MD5 encryption, do the following :

1) Install the MD5 or Digest::MD5 perl module. On Ubuntu, this is in the
libmd5-perl package.
2) In Webmin, go to the Users and Groups module, click on Module Config
and change the 'Password encryption method' to 'MD5'.
3) Change the password again for a user.

---

