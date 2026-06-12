---
title: "Default Keyring"
date: 2008-09-08
forum: Security
---

### Post by rycharde on 2008-09-08
When I go to respond to an ad containing an e-mail address a message window comes up stating:
Enter Password for Default Keyring to unlock the application "evolution"
(/usr/bin/evolution) wants access to the default keyring but it is locked.

What is this?  And how do I gain access to the default keyring?
I am new to this system and am seriously considering going back to windows.

Can anyone help?

Thanks

---

### Post by rogeriopvl on 2008-09-08
That probably happens because you have the password to send email stored in the keyring (memorized). The keyring is the place where all you passwords are. Have you tried to insert your Ubuntu user password?

---

### Post by rycharde on 2008-09-09
I did want you suggested but I still get the Default window.
Any other suggestions?

Thanks

---

### Post by rogeriopvl on 2008-09-09
Then probably you have set a different password for the keyring. Delete the keyring, if you don't rely on it to remember any password.

---

### Post by rycharde on 2008-09-09
I'm computer illiterate, how do you delete the keyring?

Thanks

---

### Post by joshuachad on 2008-09-10
Hey Bro everything you need to do can be found here: [http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/")

This should set you straight.

Cheers

---

### Post by rycharde on 2008-09-10
I am still lost. I have the alphabetical directory of Linus Commands, but do not know how to use them.  Just got this Linux system and I am not well versed with computers.  I can open gnome through the System files, but can't change the existing password because I don't know what it is.  And I don't know how to delete the existing one.  I put in the rm info and the Alphabetical Directory came up, and I don't know what to do with it.

Help...

Thanks

---

### Post by The Cog on 2008-09-10
Can I suggest you use thunderbird instead? Since introducing this insitence on a password to a keyring that you might not want to store the password in and may not even actually exist, evolution has become practically unuseable.

---

### Post by cariboo on 2008-09-10
To find the file that stores your passwords. Go to Places-->Home Folder, then press Alt-h this will reveal the hidden files and directories in you home directory. Look for a directory called .gnupg, delete this directory, and things should be back to normal.

Jim

---

