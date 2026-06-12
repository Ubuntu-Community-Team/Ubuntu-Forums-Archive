---
title: "Virtualbox, unable to grant vboxusers group permissions"
date: 2012-03-19
forum: Virtualisation
---

### Post by Insomn1a on 2012-03-19
Ok,

Ive looked for a resolution to this issue and there are resolutions for local user accounts.

basically you have to add a user to the vboxusers group in order to give your virtualbox permissions to access the USB drives plugged into your computer. 

However, Im logged into a domain (ldap) account through ubuntu here at the office. It does not list this account in the users list. 

Has anyone ever ran into this issue before? and if so did you ever find a resolution to the problem? ):P

---

### Post by haqking on 2012-03-19
> **Insomn1a said:**
> Ok,

Ive looked for a resolution to this issue and there are resolutions for local user accounts.

basically you have to add a user to the vboxusers group in order to give your virtualbox permissions to access the USB drives plugged into your computer. 

However, Im logged into a domain (ldap) account through ubuntu here at the office. It does not list this account in the users list. 

Has anyone ever ran into this issue before? and if so did you ever find a resolution to the problem? ):P

just add your self to the group or create the group.

```
sudo usermod -a -G vboxusers <username>
```


log out and back in after

---

### Post by Insomn1a on 2012-03-19
> **haqking said:**
> just add your self to the group or create the group.

```
sudo usermod -a -G vboxusers <username>
```


log out and back in after

thank you for the quick reply, I'll try this and let you know. it gave me an error when trying to add the domain account before.


update: when adding the user account to the group using 

> sudo usermod -a -G vboxusers KTP\ghamlin

it does not return an error. After rebooting it still gives me the Virtualbox Error below.

[IMG]http://i52.photobucket.com/albums/g24/Irish_ScoDeagle/Screenshot-VirtualBox-Warning.png[/IMG]

---

### Post by haqking on 2012-03-19
> **Insomn1a said:**
> thank you for the quick reply, I'll try this and let you know. it gave me an error when trying to add the domain account before.

adding a domain account ?

you are adding your local login account into the vboxusers group running on your local machine where virtualbox is installed.

it is nothing to do with a domain or domain login credentials.

Cheers

---

### Post by Insomn1a on 2012-03-19
> **haqking said:**
> adding a domain account ?

you are adding your local login account into the vboxusers group running on your local machine where virtualbox is installed.

it is nothing to do with a domain or domain login credentials.

Cheers

the account im logging into is KTP\ghamlin

it is a domain user account that im currently using. this computer was added to the domain using Likewise-open. 

The only user account on this machine is the user account I plugged into the machine whenever I installed ubuntu on it. I dont currently use this user account as im logged into this machine using a domain account, which is not seen in the users list. What im curious about, is how I would add this domain account to the vbox user group whenever it is not visible as a user account to be added.

---

### Post by DWade on 2012-03-19
I want to thank you, I've been having the same problem

Could not find the User menu like in past verison with admistration choices in the top of the Gnome  screen.  I am not so sure I like unity.

---

### Post by Insomn1a on 2012-03-19
> **DWade said:**
> I want to thank you, I've been having the same problem

Could not find the User menu like in past verison with admistration choices in the top of the Gnome  screen.  I am not so sure I like unity.


Yea I havent switched to any of the newer versions of Ubuntu, still running 10.04 to keep the gnome 2.0 environment. I think you can select a different environment at the login screen for unity, but don't take my word for it.

---

