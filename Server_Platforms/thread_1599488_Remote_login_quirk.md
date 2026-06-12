---
title: "Remote login quirk"
date: 2010-10-17
forum: Server Platforms
---

### Post by river226 on 2010-10-17
Hi, my friend has a Ubuntu server he set up, and we tried to create multiple accounts so other friends and i can log in remotely on our own accounts, problem is that i can't gain access to these created accounts on a remote system, while i can gain access to my friends main account on the same system, i know the accounts are there, and my friend is able to log into the account, while i can't even switch from within his account.
any help?

also i apologize if this is the wrong category for this question.

---

### Post by craigp84 on 2010-10-18
Keyboard mapping on your end is set to something other than the correct one for your keyboard?

E.g. you think you're typing @ in the password but really sending '

Try typing out the password on the cmdline to see.

If it's your friend who's got a mixed up keyboard map that's something to keep in mind.

---

### Post by rouben on 2010-10-18
Not sure why the passwords don't work (typo?), but you can use SSH keys instead of passwords to log in.

If you want to troubleshoot, ask your friend to check /var/log/auth.log on his machine. Here's how to do it: [https://help.ubuntu.com/community/LinuxLogFiles#Authorization%20Log](https://help.ubuntu.com/community/LinuxLogFiles#Authorization%20Log)

[LIST=1]
[*]Run ssh-keygen on your machine, and type in a password of your choice. You can also just hit enter, but that means that when you log on to your friend's machine, ssh won't ask you for a password.
[*]This will generate both a private and a public key. They will be stored in ~/.ssh/id_rsa (private key) and ~/.ssh/id_rsa.pub (public key). The private key **MUST** stay on your machine and be adequately protected. With this private key file, and the password you set up in step 1 (if you did) anyone will be able to log in as you to machines that are set up to log in with your ssh key.
[*]Finally, set up your friend's machine (you'll have to ask him to do that). Simply add the contents of the public key file (~.ssh/id_rsa.pub) into ~/.ssh/authorized_keys on your friend's computer (the file should be chmod 600 and the ~/.ssh/ directory should be chmod 700). If the file ~/.ssh/authorized_keys doesn't exist under your account on his machine, then 
[/LIST]
This is very watered down. If you want to understand how this private/public key stuff works, check out this page: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

