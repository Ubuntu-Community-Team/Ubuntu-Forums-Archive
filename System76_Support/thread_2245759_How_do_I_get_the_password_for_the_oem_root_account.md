---
title: "How do I get the password for the oem root account"
date: 2014-09-25
forum: System76 Support
---

### Post by Bill_McConnell on 2014-09-25
I am a cuple of days into using my new System76 laptop.  It came with an oem account that I assume is root.  I opened a second account for myself, which works fine, but I would prefer not to have an account on the machine with root access that I cannot control.  Any suggestions how I can get a password for this account?  can I safely delete the account or at least change the password?  last question, am I correct in assuming that this is the root account?

Thaanks for any help.

Bill McConnell

---

### Post by Bill_McConnell on 2014-09-26
So a little bit of digging in "How to configure your computer as a server" provided the password.  I continue to be troubled by this account, because it has access to the extra drive, but the account that I created for myself does not.  I was going to change permissions on the drive, but it gives full access

---

### Post by sudodus on 2014-09-26
The standard procedure with OEM installs is to log into the OEM user and double-click the icon to activate the end user account '**Prepare for shipping to end user** icon on the desktop.'

That will also remove that OEM account. See this link

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

But I don't know if your computer was configured that way. It is always possible to remove an account, but before doing that, ***make sure that your own account can run sudo***. Otherwise you will not be able to maintain the operating system.

---

### Post by Bill_McConnell on 2014-09-26
Thanks, I think that explains it.  I did the first few steps, but did not understand the significance of the "Prepare for shipping to end user" icon.  I have set up a user account for myself, but would not be greatly set back if I lost it.

A somewhat related question: I am able to sign in as root from my account.  Should I establish a password for root, or is the password fr my account the protection?

---

### Post by sudodus on 2014-09-27
No, at least the Ubuntu desktop flavours (standard Ubuntu, Kubuntu, Lubuntu ...) are not designed for running as root. Instead the intention is to use ***sudo***. This is a method to increase the security: to use elevated (superuser) privileges only for the commands that need it.

Example: Command line update/upgrade to make the system up to date:

```
sudo apt-get update
sudo apt-get upgrade
```
or to get also a new kernel (if available)
```
sudo apt-get dist-upgrade
```

and ***gksudo*** for GUI applications

```
gksudo synaptic
```

---

