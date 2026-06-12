---
title: "Gnome Keyring - Whats the point?"
date: 2006-10-15
forum: The Cafe
---

### Post by chrismyers on 2006-10-15
Can anyone explain whats the point of the Gnome keyring?

I know its for security, but how far do we have to go?

I find that I log into my system & then I then have to type in my password  to access Network Manager (& Evolution, I believe).

Presumably, if someone had compromised my password to log on to my system, then they allready have access to my data?

Would it be possible to bypass Gnome Keyring & should I (or shouldn't I) even try?

Cheers :-k

---

### Post by Dr. Nick on 2006-10-15
Not sure what all keyring controls, but if I recall it can be used to store gpg keys. Basically with a gpg key you could make a "key" and encrypt all outgoing mail, for anyone to read that mail they would need that
key to unencrypt it.

I think thats correct and that Im not confusing 2 things here. 

Alot of people set their system to autologin so that cant always be trusted to much with keeping people out.

---

### Post by .t. on 2006-10-15
It stores passwords and the like, encrypted. It uses GPG, and so can do things like encrypt outgoing mail from Evolution. It also is used by the GNOME NetworkManager applet to store your network information. It's a centralised, secure, data store; I guess.

---

### Post by prizrak on 2006-10-15
The Gnome keyring is simply a way to hold encrypted passwords. No more no less. You can use your user password as the encryption key or you can choose a different one. The keyring is used by NM to encrypt your WAP key (as opposed to plain text), which is why you need the password. The new version of NM doesn't ask for a password.

---

### Post by .t. on 2006-10-15
It is more. It can be used to hold pretty much any encrypted text.

---

### Post by prizrak on 2006-10-15
> **.t. said:**
> It is more. It can be used to hold pretty much any encrypted text.

I'm not sure if that was the intent, but yeah my bad.

---

### Post by jdong on 2006-10-15
I think there's a way to get Gnome keyring to use PAM authentication, so that a login suffices as enough clearance to unlock the keyring.

---

### Post by zenwhen on 2006-10-15
> **jdong said:**
> I think there's a way to get Gnome keyring to use PAM authentication, so that a login suffices as enough clearance to unlock the keyring.

[http://ubuntuforums.org/showthread.php?t=187874&highlight=nm-applet+keyring](http://ubuntuforums.org/showthread.php?t=187874&highlight=nm-applet+keyring)

You are right. Here is how to get around it.

I made a checkinstall deb that has worked for me on a few systems. 

Install it like this:

```
wget http://zenwhen.com/webdav/pam-keyring_0.0.8-1_i386.deb
sudo dpkg -i pam-keyring_0.0.8-1_i386.deb
```

Then be sure do do these steps:

> **s31523 said:**
> cd /etc/pam.d
sudo gedit gdm
Mine looks like:
```
#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

```

IT IS VERY IMPORTANT TO ADD THE ABOVE LINES TO THE END OF THE GDM FILE

After that, reboot, and no password.  BIG Thanks Jon Nettleton for getting this out!

As I mentioned in the comments in gdm file, this relies on having the password of the default keyring the same as your login password.  ENJOY!

This worked for me and I dont ever see the password requests.

---

### Post by prizrak on 2006-10-16
> **jdong said:**
> I think there's a way to get Gnome keyring to use PAM authentication, so that a login suffices as enough clearance to unlock the keyring.

Yes it is possible (and I have followed the howto that zenwhen linked to). There are some issues however, if you do auto login it won't work and you will need to put the password in anyway. I think we need hardware based authentication options. Most new machines have card readers so it would be nice to just have some kind of a key residing on a flash card that will be used as both user authentication and keyring decryption (could hold more than one key too).

---

### Post by chrismyers on 2006-10-18
Thanks Gentlemen.

I hope Edgy has the latest version of Network Manager...

Either that, or I'll be installing it from source.   :D

---

