---
title: "eCryptfs reasonably secure login passphrase VS sudo"
date: 2011-09-05
forum: Security
---

### Post by dan03557 on 2011-09-05
Hello there,
ecrypfs and the handy automount feature allows the user to use his login password to encrypt the */home/.ecryptfs/user/.ecryptfs/wrapped-passphrase* file, which in turn holds the key to decipher the rest of the user data. Right?(Am I missing something?) 

Therefore the user is expected to pick a file-encryption-wise passhprase as his login password. This would be all very good if the user had to enter his passphrase only at login. The problem is that thanks to the *sudo* way of granting admin privileges, the same passphrase is asked each time admins tasks are required (thus bugging the user to enter a long passphrase more frequently than he may be comfortable with. A shorter, more handy password would probably be more suitable for getting admin privileges).

[B]The user is thus left with the choice of either picking a less-than-secure passphrase for file-encryption, or having to enter a cumbersome password every time any admin task is at hand.

The question is: How can I separate the login and sudo password without getting rid of the sudo system altogether and activating the root account?[/B] (any possible workaround is welcome too)

thanks for the help.

---

### Post by bodhi.zazen on 2011-09-05
Easiest method is to not use ecryptfs to encrypt your entire home directory.

Just make a crypt within your home directory , you can do this with ecryptfs or you can use cryptkeeper, a graphical interface.

---

### Post by dan03557 on 2011-09-05
That is not exactly the solution I'm looking for, because I do care about the encryption of sensitive data usually placed in the home folder itself; such as .mozilla .kde .gnome, and so on.
 
Manually changing the location of each and everyone of these directories to be in the custom encrypted folder would be a pain(I'm sure it can be done), and you could always forget some data out of it, thus leaking user sensitive information.

---

### Post by Dave_L on 2011-09-05
I don't know of a good workaround.

But the frequency of entering the password for admin tasks can be reduced by (1) extending the sudo timeout and/or (2) launching a root shell (sudo -i) and initiating admin tasks from that shell.

---

### Post by Bachstelze on 2011-09-05
I get this behavior (prompted for a passphrase when using sudo) only on my server, where I do not encrypt my entire home directory for performance reasons. On my desktop system, where I do encrypt my home directory, I am never asked for a passphrase when I use sudo.

Do you encrypt your entire home director or not?

---

### Post by Dave_L on 2011-09-05
Bachstelze:

As far as I know, home directory encryption is independent of sudo.

If you don't get prompted for a password when using sudo, that must mean that your /etc/sudoers file contains the NOPASSWD parameter.  I guess that's another possible solution for dan03557.

---

### Post by Bachstelze on 2011-09-05
> **Dave_L said:**
> 
As far as I know, home directory encryption is independent of sudo.


Well, you are wrong. The PAM service for sudo includes common-auth, which calls the ecryptfs module. I know what I am talking about, thank you very much, and I can tell a passphrase prompt from a password prompt.

*EDIT*

```
firas@itsuki ~ % sudo echo foo
[sudo] password for firas: 
Encryption passphrase: 
foo
firas@itsuki ~ % 
```

There, it doesn't take a rocket scientist to figure out that it does ask for a passphrase.

---

### Post by Dave_L on 2011-09-05
Sorry, Bachstelze, I didn't mean to offend you.

---

### Post by dan03557 on 2011-09-05
> **Bachstelze said:**
> I get this behavior (prompted for a passphrase when using sudo) only on my server, where I do not encrypt my entire home directory for performance reasons. On my desktop system, where I do encrypt my home directory, I am never asked for a passphrase when I use sudo.

Do you encrypt your entire home director or not?

Yes, I do encrypt my home directory. 

So you say, I could set up my config files in ***/etc/pam.d*** so that the passprhase asked at (gdm)login to let me in the Desktop Envirorment and to decrypt my home dir is different from that which is asked when one uses sudo. 
How do you achieve that?

---

### Post by linis_australis on 2011-09-05
Why not just use sudo su for a root terminal then you don't have to type the whole passphrase in every time?

---

### Post by dan03557 on 2011-09-06
> **linis_australis said:**
> Why not just use sudo su for a root terminal then you don't have to type the whole passphrase in every time?

mmh I thought about that but, it's not the solution I'm looking for: the terminal would be always open, and the root shell always available. 

I'd rather use different passwords for login and decrypt home(same pass) and sudo access(different)... is there a way to do that?

---

### Post by Bachstelze on 2011-09-07
> **dan03557 said:**
> Yes, I do encrypt my home directory.

Is your home directory decrypted automatically at login, or do you decrypt it manually. As I understand it, PAM prompts for a passphrase when you have an ecryptfs directory AND it is not decrypted at the time you call sudo. At least that's what seems to happen for me.

---

