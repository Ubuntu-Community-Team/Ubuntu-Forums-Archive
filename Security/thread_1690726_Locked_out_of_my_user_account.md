---
title: "Locked out of my user account"
date: 2011-02-18
forum: Security
---

### Post by Am Elder on 2011-02-18
Hello,

My rsa passphrase seems to be locking me out of one of the accounts on my notebook running Ubuntu Maverick.

I have an administrator account and an every-day account on this computer.  In my 'desktop user' account, I recently created an rsa key in order to contribute to an open source project on GitHub.  Following the directions on GitHub for [generating SSH keys]("http://help.github.com/linux-key-setup/"), and [working with SSH key passphrases]("http://help.github.com/working-with-key-passphrases/"), I saved the key to /home/username/.ssh.  This is not the first time I created an rsa key on this account.  On my first reboot, a second log-in dialog popped up after I entered my account password, asking for my rsa passphrase.  However, it does not accept the passphrase I give it.  Instead, it returns me to the log-in screen.  So, I cannot log in to my main day-to-day account on this computer.

I spent time learning the passphrase when I created it and even wrote it down for safety, intending to destroy it after using it successfully a few more times, so I'm fairly sure I'm entering the passphrase I created for the key.

Some packages installed on this computer: gnome-keyring, libgnome-keyring0, libpam-gnome-keyring, openssh-client.

The last time I created an rsa key for github, I did not encounter this passphrase dialog.  Why am I shut out of this account, and what can I do to gain access to it again?

I would really appreciate any help.

---

### Post by cariboo on 2011-02-18
Probably the easiest way to to solve the problem is to log in as root:

```
sudo -i
```

then remove /home/username/.ssh/id_rsa and id_rsa.pub, and start over.

---

### Post by Am Elder on 2011-02-19
Thank you cariboo907. That didn't fix the problem: after moving the key pair, I still can't log in.  However, root access let me troubleshoot a bit.  I still need help though.

I've looked in .xsession-errors, and found the following error:
```
/etc/gdm/Xsession: Beginning session setup...
/home/daily/.profile: 29: function: not found
Initializing new SSH agent...
succeeded
Identity added: /home/daily/.ssh/id_rsa (/home/daily/.ssh/id_rsa)
/home/daily/.profile: 37: Syntax error: "}" unexpected
```The relevant portion of my .profile is:
```

28.  # start the ssh-agent
29.   function start_agent {
30.      echo "Initializing new SSH agent..."
31.      # spawn ssh-agent
32.      ssh-agent | sed 's/^echo/#echo/' > "$SSH_ENV"
33.      echo succeeded
34.      chmod 600 "$SSH_ENV"
35.      . "$SSH_ENV" > /dev/null
36.      ssh-add
37.  }
```So, correct me if I'm wrong, but I guess something is happening like: the shell isn't recognizing the function declaration, it's not reading the rest of line 29, and so not recognizing the closing bracket.

But how do I fix it?

[edit]I tried commenting out lines 29 and 37 of .profile, and that didn't work.[/edit]

---

### Post by Am Elder on 2011-02-19
Commenting out another function declaration further down as well, allowed me to log into my account.  I'm marking this as solved, because I'm in now.  But there are a whole host of new xsession errors that have popped up.  I'm going to the #ubuntu irc channel for help.

---

