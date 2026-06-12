---
title: "Encrypted home not unlocked when logging in over SSH"
date: 2009-11-20
forum: Security
---

### Post by FuturePilot on 2009-11-20
I have a computer setup with SSH and my home directory encrypted with ecryptfs. The problem is that if I don't log in locally on the machine first, when I log in over SSH it doesn't decrypt my home directory. I have to manually run "ecryptfs-mount-private" which gets really annoying after awhile. I don't use password authentication, only key based authentication. I'm not sure if that is connected to the problem at all. Is this normal behavior? Is there a way to make it decrypt my home directory when I log in over SSH?

---

### Post by kevdog on 2009-11-20
What is the command line you are running?  

Take a look at
/etc/sshrc
and
~/.ssh/rc

5.6.4. Arbitrary Actions with /etc/sshrc
When a user logs in, the normal Unix login system typically runs some shell scripts, such as /etc/profile. In addition, sshd runs the script /etc/sshrc for each SSH-based login. This feature lets the system administrator run special commands for SSH logins that don't occur for ordinary logins. For example, you can do some additional logging of SSH connections, print welcome messages for SSH users only, and set SSH-related environment variables. In all three, SSH1, SSH2, and OpenSSH, /etc/sshrc is processed by the Bourne shell ( /bin/sh) specifically, rather than the user's shell, so that it can run reliably for all accounts regardless of their various shells. It is run for logins (e.g., ssh my-host) and remote commands (ssh my-host /bin/who), just before the user's shell or command is invoked. It runs under the target account's uid, so it can't take privileged actions. If the script exits due to an error (say, a syntax error), the SSH session continues normally. Note that this file is run as input to the Bourne shell: sshd runs /bin/sh /etc/sshrc, not /bin/sh -c /etc/sshrc. This means that it can't be an arbitrary program; it must be a file containing Bourne-shell commands (and it doesn't need the execute mode bit set). /etc/sshrc operates machinewide: it is run for every incoming SSH connection. For more fine-grained control, each user may create the script ~/.ssh/rc to be run instead of /etc/sshrc. [Section 8.4, "The User rc File "] /etc/sshrc isn't executed if ~/.ssh/rc exists in the target account. Note that SSH rc files interact with X authentication. [Section 9.3.5.2, "xauth and the SSH rc files"]

---

### Post by FuturePilot on 2009-11-20
> **kevdog said:**
> What is the command line you are running?  
I'm just running 
```
ssh user@host -p secret-port
```

> Take a look at
/etc/sshrc
and
~/.ssh/rc

5.6.4. Arbitrary Actions with /etc/sshrc
When a user logs in, the normal Unix login system typically runs some shell scripts, such as /etc/profile. In addition, sshd runs the script /etc/sshrc for each SSH-based login. This feature lets the system administrator run special commands for SSH logins that don't occur for ordinary logins. For example, you can do some additional logging of SSH connections, print welcome messages for SSH users only, and set SSH-related environment variables. In all three, SSH1, SSH2, and OpenSSH, /etc/sshrc is processed by the Bourne shell ( /bin/sh) specifically, rather than the user's shell, so that it can run reliably for all accounts regardless of their various shells. It is run for logins (e.g., ssh my-host) and remote commands (ssh my-host /bin/who), just before the user's shell or command is invoked. It runs under the target account's uid, so it can't take privileged actions. If the script exits due to an error (say, a syntax error), the SSH session continues normally. Note that this file is run as input to the Bourne shell: sshd runs /bin/sh /etc/sshrc, not /bin/sh -c /etc/sshrc. This means that it can't be an arbitrary program; it must be a file containing Bourne-shell commands (and it doesn't need the execute mode bit set). /etc/sshrc operates machinewide: it is run for every incoming SSH connection. For more fine-grained control, each user may create the script ~/.ssh/rc to be run instead of /etc/sshrc. [Section 8.4, "The User rc File "] /etc/sshrc isn't executed if ~/.ssh/rc exists in the target account. Note that SSH rc files interact with X authentication. [Section 9.3.5.2, "xauth and the SSH rc files"]

Hmm that might work as a workaround. I noticed that if I use password authentication it automatically decrypts my home directory when I log in. But it doesn't if I use key based authentication. I wonder if this is a bug.

---

### Post by cariboo on 2009-11-20
Ssh can't read your keyfile because it's encrypted. move your key directory to an unencrypted portion of your home directory.

---

### Post by FuturePilot on 2009-11-20
> **cariboo907 said:**
> Ssh can't read your keyfile because it's encrypted. move your key directory to an unencrypted portion of your home directory.

Logging in isn't the problem. I've already moved authorized_keys to my unencrypted home directory so that it stays in plain text. I can login over SSH fine, it's just that it doesn't decrypt my home directory. After doing some more searching, it seems that what I want to happen isn't possible (as of now). [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/364015]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/364015"). I guess I can hack something together with /etc/sshrc or ~/.ssh/rc to make it a bit easier.

---

### Post by kerignell on 2009-12-06
> **FuturePilot said:**
>  I guess I can hack something together with /etc/sshrc or ~/.ssh/rc to make it a bit easier.

Would you care to share that hack?

I tried to place a ~/.ssh/rc after unmounting the encrypted ~/, with this code:
```

#!/bin/sh

ecryptfs-mount-private 
sleep 1
exit 0

```

That one wont work.. But the command works when invoked manually.


To those of you who where in the situation of not being able to login unless logged in locally:
This drove me nuts for a while =). Solved it by moving a copy of my authorized_keys to the unencrypted ~/.ssh/ as per these instructions, from [here]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427"):

```

$ /sbin/umount.ecryptfs_private
 $ cd $HOME
 $ chmod 700 .
 $ mkdir -m 700 .ssh
 $ chmod 500 .
 $ echo $YOUR_REAL_PUBLIC_KEY > .ssh/authorized_keys
 $ /sbin/mount.ecryptfs_private

```

Note, by $YOUR_REAL_PUBLIC_KEY he means the raw content of your id_rsa.pub/id_dsa.pub

---

### Post by FuturePilot on 2009-12-06
So here is what I ended up doing. Using ~/.ssh/rc didn't work because ecryptfs-mount-private doesn't like the way it's executed for some reason and gives this error
```
stty: standard input: Invalid argument
```

So I created ~/.zlogin (use ~/.bash_login for Bash) in my unencrypted home with the following:

```
if test -e $HOME/.ecryptfs/auto-mount; then
  mount | grep "$HOME type ecryptfs"
  if test $? != 0; then
    ecryptfs-mount-private
    cd $HOME
    source ~/.zshrc
  fi
fi
```

Now when I login and my encrypted home hasn't been mounted yet it automatically prompts me for my password. Of course if you use Bash change "source ~/.zshrc" to "source ~/.bashrc". Kind of hackish but it seems to work OK.

---

### Post by kerignell on 2009-12-07
Sweet success! Thank you very much.

For myself in the future, and other n00bs like me. After creating and saving that file you need to make sure its executable and owned by you (FuturePilot is very welcome to correct me if I am wrong!):

```

$ chown $user:$group ~/.bash_login 
$ chmod u+rwx ~/.bash_login 
$ ls -lah ~/.bash_login 
-rwxr--r-- 1 $user $group 174 Dec  7 17:29 /home/$user/.bash_login

```

Where $user and $group of course should be substituted by you and your group =)

---

### Post by VoyezScout on 2011-02-27
I know this is an already solved issue, but went into a nice workaround which may be useful to some other people.

Situation was that I could login using public keys into my remote machine but the home folder was not decrypted.
Trying to follow the options suggested, I observed that calling the ecryptfs-mount-private after the login did not make the personal settings load, and I needed to logout and relogin each time in order to get them loaded.

So, I prepared this small login script that forces a password login to decrypt the home folder but leaves the host prepared to do the next logins using the keys.

```
~$cat /usr/bin/ssh_decrypt
#!/bin/bash 

# disable private key
mv ~/.ssh/id_dsa ~/.ssh/id_dsa.sbak
# dummy login at the remote server to force password promt
ssh $1 exit
# put the private key back into its place
mv ~/.ssh/id_dsa.sbak ~/.ssh/id_dsa

# do the real login using the private key
ssh $@
```And it is used exactly as the usual ssh binary:

```
~$ssh_decrypt remote_user@remote_host remote_commands
```The only bad thing about it is that you need to leave the password login active in the remote host, with the associated possible security lacks.

However, I hope that someone will find it useful!

---

