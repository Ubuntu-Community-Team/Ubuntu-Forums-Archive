---
title: "access to the keyring, password"
date: 2010-09-03
forum: Security
---

### Post by jacopo1981 on 2010-09-03
I would like to use a wireless network, I type in the correct password but suddenly a new window pops up saying:
'an application wants to access to the keyring 'Vorgabe', but its is locked
password:'

But I don't know what password it's talking about

I went to Password and Encryption keys, there are two folders 
'password: vorgabe' 
'Password: login'

What am I supposed to do?

I have just installed UBUNTU (in germany), everything is new, so while answering try to be very didactic, please.

---

### Post by akoskm on 2010-09-03
> **jacopo1981 said:**
> I would like to use a wireless network, I type in the correct password but suddenly a new window pops up saying:
'an application wants to access to the keyring 'Vorgabe', but its is locked
password:'

But I don't know what password it's talking about

I went to Password and Encryption keys, there are two folders 
'password: vorgabe' 
'Password: login'

What am I supposed to do?

I have just installed UBUNTU (in germany), everything is new, so while answering try to be very didactic, please.

Hi!
Go to Application > Accessories > Passwords and Encryption Keys.
According to your description there are two folders, vorgabe and login.
Open them and search for something like: *Network secret for .....*. Once you found the entry for your wireless network just right click to the entry and Delete it.

ps.:Have you tried to type your root password when the dialog comes up?

---

### Post by jacopo1981 on 2010-09-03
they look like folders but when you open them they contain only this

'name : vorgabe
created :'

'name: login
created :'

yes i tried with my root password but did not work out

---

### Post by akoskm on 2010-09-03
> **jacopo1981 said:**
> they look like folders but when you open them they contain only this

'name : vorgabe
created :'

'name: login
created :'

yes i tried with my root password but did not work out

You don't need to open it, expand the node to see the entries.
[http://imagebin.org/112557]("http://imagebin.org/112557")

---

### Post by jacopo1981 on 2010-09-03
there is no 'plus' unfortunately.

---

### Post by akoskm on 2010-09-03
> **jacopo1981 said:**
> there is no 'plus' unfortunately.

Have you tried just deleting the whole folder?
If it wont work, delete the keyring profiles in your *~/.gnome2/keyrings* directory.

---

### Post by jacopo1981 on 2010-09-03
I managed to delete the two folders but nw there is another windows

'an application wants to creat a new keyring called 'defaults' choose the password you want to use for it'

Personally I hate passwords How can I get rid of his new request?
where can I find Gnome?

sorry about so many questions

---

### Post by akoskm on 2010-09-03
> **jacopo1981 said:**
> I managed to delete the two folders but nw there is another windows

'an application wants to creat a new keyring called 'defaults' choose the password you want to use for it'

Personally I hate passwords How can I get rid of his new request?
where can I find Gnome?

sorry about so many questions

Okay, choose a password for your default keyring and that's all.
The point is this keyring application is that the passwords used by your Gnome applications are stored (& encrypted !) by this single application, so once you log in you just type your password for the default keyring and voila all passwords are unlocked.
Personally - I hate passwords too, but this approach is still better then leaving the applications to store them in plain-human readable- text files.

ps.:Is there any way to switch off this keyring manager completely? I have no idea. Maybe it's possible but "not recommended".

---

### Post by OpSecShellshock on 2010-09-03
The password you create on the initial installation of Ubuntu is used for both logging on to a desktop session and unlocking the keyring. However, they are two distinct processes. When the keyring prompt comes up for certain things (such as accessing a wireless network) you just put in the same password that you use to log on to your computer. This is separate from whatever password is required in order to connect to the wireless AP, and should only have to be done once I think.

---

### Post by akoskm on 2010-09-03
> **OpSecShellshock said:**
> The password you create on the initial installation of Ubuntu is used for both logging on to a desktop session and unlocking the keyring. However, they are two distinct processes. When the keyring prompt comes up for certain things (such as accessing a wireless network) you just put in the same password that you use to log on to your computer. This is separate from whatever password is required in order to connect to the wireless AP, and should only have to be done once I think.

On this way, it would be very comfortable. However I need to unlock my keyring every time when I log in, and connecting to our wireless network.

---

### Post by David Batty on 2010-09-03
Try editing your wireless connection settings by ticking the box that says "available to all users" once that has been done you shouldn't have to enter the password every time to connect.

---

### Post by Tootler on 2010-09-17
> **David Batty said:**
> Try editing your wireless connection settings by ticking the box that says "available to all users" once that has been done you shouldn't have to enter the password every time to connect.

I have been having the same problem and that worked for me.

Thanks :p

---

