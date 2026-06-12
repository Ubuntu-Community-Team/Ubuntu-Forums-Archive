---
title: "how to &quot;sudo ssh/rsync&quot; a remote host using a user's keyfiles?"
date: 2013-11-23
forum: Security
---

### Post by clearski on 2013-11-23
Hi, everyone.

I am trying to run a script as root using /etc/crontab. 

```
X Y  * * *   root    /some-path/script.sh
```

The first part of the script needs local root priviledges and runs fine.

The other half needs a regular user priviledges, but the job is run by user root in crontab and it fails.

Basically, the second part of the script is trying to access a remote directory using a regular user's credentials (keyfiles), not the root's ones. That is because the root doesn't have keyfiles on the local or on the remote host. The user **test** does have remote access to that host however, but only when ssh and rsync are run by user **test** (non sudo command).

So a command like

```
"ssh test@remotehost"
```

works just fine.

However, the script fails when it tries to execute these two commands:

```
sudo ssh -fnx4 -l test -i /home/test/.ssh/id_rsa.pub test@remotehost "mkdir /home/test/somedirectory"
```

This actually asks me the passphrase for the public key...

```
Enter passphrase for key '/home/test/.ssh/id_rsa.pub':
```

And there is no password for the public key...

The second command is this:

```
sudo rsync -avzl -e "ssh -l test" /home/test/Desktop/somefile test@remotehost:/home/test/somedirectory
```

And the output is "Permission denied (publickey).

Adding "-i /path/to/public_keyfile" leads to the same output as when using ssh:

```
Enter passphrase for key '/home/test/.ssh/id_rsa.pub':
```

Is it possible to make ssh and rsync login using another user credentials when they are started with root privileges by sudo?

Thank you.

---

### Post by CharlesA on 2013-11-24
Are you completely sure the key has no passphrase? It would just log you in if that was the case instead of prompting you to enter the passphrase.

---

### Post by clearski on 2013-11-24
Absolutely. I am connecting to that host a dozen of times a day and there is no password required, nor the keys were created using any password, nor the ssh server will accept any connection using a password.  I am wondering too what password does it ask for?

---

### Post by CharlesA on 2013-11-24
That's odd.

I've connected to other boxes via ssh using another user's credentials with no problem before.

You could try running ssh with -vvv and see what it spits out.

---

### Post by clearski on 2013-11-24
I'll give it a try later and post back the results.

Thank you.

---

### Post by Lars Noodén on 2013-11-24
> However, the script fails when it tries to execute these two commands:

```

sudo ssh -fnx4 -l test -i /home/test/.ssh/id_rsa.pub test@remotehost "mkdir /home/test/somedirectory"

```


There you're running ssh under sudo to no real gain.  If you are already running the script as root then sudo is redundant (unless used with -u).  But it alone should not cause the  line to fail.  What might cause it to fail is that you are using the public key (id_rsa.pub) where you should be using the private key (id_rsa)  The private key stays on the client and shouldn't leave.

> 
 The second command is this:
```

sudo rsync -avzl -e "ssh -l test" /home/test/Desktop/somefile test@remotehost:/home/test/somedirectory

```


That one might be for two reaons.  First,  you also have to specify the key inside the -e option unless it is already in the agent:

-e "ssh -l test -i /home/test/.ssh/id_rsa"

Second, again,  the client end uses id_rsa and not id_rsa.pub.  The public key (id_rsa.pub) is the only one that belongs on the server in authorized_keys.

---

### Post by clearski on 2013-11-24
> **Lars Noodén said:**
> There you're running ssh under sudo to no real gain.  

Indeed, in the script there is no sudo for these two commands, but I had to simulate the root perspective when running them separately, trying to find out what's wrong.

> **Lars Noodén said:**
> What might cause it to fail is that you are using the public key (id_rsa.pub) where you should be using the private key (id_rsa)  The private key stays on the client and shouldn't leave.

[COLOR=#b22222] ** Thank you, Sir! Thank you!**[/COLOR]

I spent a few good hours and I simply didn't realise that I so was stupid to use a public key to authenticate against the same key which was already on the server... :)

Dear everyone, don't do the same mistake. :)

The two commands are working just fine in the previous specified circumstances if they are used properly (as follows):

```
test@localhost:~$ **sudo rsync -azvl -e "ssh -l test -i /home/test/.ssh/id_rsa" /home/test/Desktop/test-backup test@remotehost:/home/test/backup/test1/**
sending incremental file list
test-backup

sent 1074265999 bytes  received 31 bytes  11613686.81 bytes/sec
total size is 1073741824  speedup is 1.00
```

and...

```
test@localhost:~$ **sudo ssh -fnx4 -l test -i /home/test/.ssh/id_rsa test@remotehost "mkdir /home/test/backup/IT-WORKS"**
```

I'll leave this thread open for a little more because I want to test the commands with the script, too. I think everything will be fine, but just to make sure... :)

:P

CharlesA, thank you, too for your time.

---

### Post by CharlesA on 2013-11-24
Wow, I totally missed that one. Nice job, Lars!

---

### Post by clearski on 2013-11-24
Testing the commands with the script & with crontab -> success.

Solved. :)

---

### Post by Lars Noodén on 2013-11-24
Glad it's working.

By the way, if you're working with a number of keys, it won't hurt to rename the files.  You can do that when the keys are created with "ssh-keygen -f" or after the fact by just renaming the files.  That can tell you at a glance what the keys are for when you see them in the directory.

Also, the very last data field in the public key is actually a comment and it is a good idea to put something descriptive there.  By default it ends up with an email address-like string, but it's better to replace that, at least on the public key you keep on your client.  Some graphical key management programs use that string to describe the key pair.

Both can help remind you of what the key is for.

---

### Post by clearski on 2013-11-24
Even different and explicit names cannot help in case I will try again to do something without thinking about it. It wasn't a naming issue, I knew what every key was for, I was so focused that I just didn't realize that I have to send the private key to the server. That won't happen again. :)

Thank you.

---

