---
title: "How do I recreate the magic ubuntu does with ssh keys?"
date: 2010-04-03
forum: Server Platforms
---

### Post by nbv4 on 2010-04-03
I followed the steps to create a SSH key on my local machine, and then I copied them over to my remote machine. I can now connect to my server via the ssh command without needing to enter a password. This is great. I created a script that invokes a script on my remote machine, then copies that file over to my local machine. Basically a two liner. Here is that script:

```

#! /bin/bash

ssh server "/srv/app/make_db_dump";
scp server:/srv/app/dump .;

exit

```

Pretty simple, right? I click on Applications -> Accessories -> Terminal. Then I cd into the directory where that script lives, and then I execute the script via "./script_name". It all works fine. Yay.

Now I want to take it a step further by having this script run every 6 hours via a cron job. So I add this to my crontab:

```

* */6 * * * "/path/to/script"

```

But it doesn't work because Ubuntu does some kind of magic when you launch a terminal that loads the SSH keys so they are available to the scp and ssh commands. This magic is not preformed when the script is invoked from cron. What do I need to do to invoke this magic? I've tried adding the following to the top of my script (the one that gets invoked by cron):

```

ssh-add
eval $(ssh-agent)
eval $(gnome-keyring-daemon)

```

and a few others, but no matter what I try, nothing seems to get the keys loaded so that they are found by the ssh/scp command. What do I need to do? I imagine the magic has to be somewhere in my .bachrc file, but theres nothing there. It really sucks to have to remember to run my backup script manually every few hours.

---

### Post by KB1JWQ on 2010-04-03
You can pass the key location via ssh -i; man ssh for more info on this.

---

### Post by nbv4 on 2010-04-03
> **KB1JWQ said:**
> You can pass the key location via ssh -i; man ssh for more info on this.

It still doesn't work. Here is what my script looks like now:

```

#! /bin/bash

ssh -i ~/.ssh/id_rsa server "/srv/app/make_db_dump";
echo "after ssh";

scp -i ~/.ssh/id_rsa server:/srv/app/dump .;
echo "after scp";

exit

```

and it works fine when I run the script directly, but the cron job:

```

*/2 * * * * /path/to/myscript > /home/chris/err.log 2>&1

```

outputs this:

```

~$ cat err.log
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
after ssh
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
after scp

```

OK I think I just found the problem. I added "echo $USER" to the script, which outputs "chris" when I run from the command line, but when ran from cron, returns a blank line. This is very odd. I'm adding this crontab by typing "crontab -e" as the user "chris"

---

### Post by KiLaHuRtZ on 2010-04-03
You need to let cron know who it needs to run the script as...

```
*/2 * * * * [COLOR="Red"][USER][/COLOR] /path/to/myscript > /home/chris/err.log 2>&1
```

Replace [COLOR="Red"][USER][/COLOR] with the name of the user (i.e. you) that will run the script.  In short, root is trying to ssh to the other box to which the key/ssh on the remote machine will deny root since he is not the permissible user due to the fact root does not own/hold the private key.

---

### Post by nbv4 on 2010-04-03
> **KiLaHuRtZ said:**
> You need to let cron know who it needs to run the script as...

```
*/2 * * * * [COLOR="Red"][USER][/COLOR] /path/to/myscript > /home/chris/err.log 2>&1
```

Replace [COLOR="Red"][USER][/COLOR] with the name of the user (i.e. you) that will run the script.  In short, root is trying to ssh to the other box to which the key/ssh on the remote machine will deny root since he is not the permissible user due to the fact root does not own/hold the private key.

that just returns this:

/bin/sh: chris: not found

did you see my edit above? the crontab in question is my user's crontab, not root's...

---

### Post by KiLaHuRtZ on 2010-04-03
> **nbv4 said:**
> OK I think I just found the problem. I added "echo $USER" to the script, which outputs "chris" when I run from the command line, but when ran from cron, returns a blank line. This is very odd. I'm adding this crontab by typing "crontab -e" as the user "chris"

Ok, didn't see this before.  I thought you were editing '/etc/crontab'.

Try this...

```
#!/bin/bash

SHELL=/bin/bash
HOME=/home/chris

pushd $HOME

ssh server "/srv/app/make_db_dump"
scp server:/srv/app/dump .

popd

exit 0;
```

---

### Post by nbv4 on 2010-04-03
That just returns this:

```

~$ cat err.log
~ ~
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
after ssh
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
after scp
~

```

by the way, the permissions of my ~/.ssh/id_rsa is "-rw-------", if thats relevant

---

### Post by KB1JWQ on 2010-04-03
You need to strip the passphrase from the key for this to work. Or somehow hook into the running ssh-agent.

---

### Post by KiLaHuRtZ on 2010-04-03
Make a test script so we can see if it is having trouble reading you key and place that into your crontab file.

Script...

```
#!/bin/bash

# Echo some useful stuff.

echo "$USER" > /tmp/test
echo "$HOME" >> /tmp/test
echo "$SHELL" >> /tmp/test
echo "$PATH" >> /tmp/test

# See if we can read the key. -- DO NOT POST THIS IF IT CAN READ IT!!!!
                               # THIS IS YOUR PRIVATE KEY!!!!

cat /home/chris/.ssh/id_rsa >> /tmp/test

exit 0;
```

---

### Post by KiLaHuRtZ on 2010-04-04
Wait,.. you have a phase phrase on it?  If so that's your problem.  You have to make a key without a phase phrase.  When you create they key, when it asks for one, just hit enter.

---

### Post by KB1JWQ on 2010-04-04
The above script won't help. The issue is that the key is passphrase protected.

---

### Post by nbv4 on 2010-04-04
I'm 99% sure the key is not passphrase protected. Like I said, I can run the script from the terminal and it works fine without asking for any passwords to be entered.

---

### Post by KiLaHuRtZ on 2010-04-04
Ok then, try my test script suggestion.  I think something is messed up in the environment that cron is attempting to run the script in.

---

### Post by KB1JWQ on 2010-04-04
I've said this. Alternately he can hook the ssh-agent process. :-)

---

### Post by nbv4 on 2010-04-04
I added "cat /home/chris/.ssh/id_rsa" at the top, and it prints out this:

```

~$ cat err.log
~ ~
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,A7F6B957A1A54BCE

ZYS/WQG2DATBjle0qOq+8HbEQV8geH/Q3SEOyVOmZ65qqtq2ZaADYqd3x5t1pJFT
[snip]
bOOvwzDSrV36k8zORG8tf7dUWK6LEUd2aQ0CIuzbHf5XyQh2M0L3zw==
-----END RSA PRIVATE KEY-----
Permission denied, please try again.

Permission denied, please try again.

Permission denied (publickey,password).

after ssh
0.dump: No such file or directory
after scp
~

```

---

### Post by KiLaHuRtZ on 2010-04-04
Ok, is the user the same on the remote machine?  Try replacing "server" with "user@server".  Where the user is that on the remote machine.

---

### Post by nbv4 on 2010-04-04
> **KiLaHuRtZ said:**
> Ok, is the user the same on the remote machine?  Try replacing "server" with "user@server".  Where the user is that on the remote machine.

"server" is from ~/.ssh/config, changing to [email]user@domain.com[/email] has the same result.

echo "$USER"
echo "$HOME"
echo "$SHELL"
echo "$PATH"

returns this:


/home/chris
/bin/bash
/usr/bin:/bin

$USER seems to be blank. I tried manually setting it to 'chris', but it had no effect.

---

### Post by KB1JWQ on 2010-04-04
I suspect a passphrase. The creds to unlock it are stored with your login keystore.

---

### Post by nbv4 on 2010-04-04
> **KB1JWQ said:**
> I suspect a passphrase. The creds to unlock it are stored with your login keystore.

do you know of a foolproof way to verify this?

---

### Post by KiLaHuRtZ on 2010-04-04
On the remote machine, run this.  See who cron is attempting to login as.

```
sudo cat /var/log/auth.log | grep sshd | grep Failed
```

---

### Post by nbv4 on 2010-04-04
> **KiLaHuRtZ said:**
> On the remote machine, run this.  See who cron is attempting to login as.

```
sudo cat /var/log/auth.log | grep sshd | grep Failed
```

```

Apr  4 00:12:22 linode sshd[21253]: Failed password for chris from 173.88.x.x port 53743 ssh2
Apr  4 00:14:24 linode sshd[21295]: Failed password for chris from 173.88.x.x port 53844 ssh2
Apr  4 00:16:23 linode sshd[21583]: Failed password for chris from 173.88.x.x port 47979 ssh2
Apr  4 00:18:21 linode sshd[21628]: Failed password for chris from 173.88.x.x port 48091 ssh2
```

which all looks correct.

---

### Post by KiLaHuRtZ on 2010-04-04
If it is logging in as the correct user.  Then KB1JWQ has to be right.

> **KB1JWQ said:**
> I suspect a passphrase. The creds to unlock it are stored with your login keystore.

---

### Post by KiLaHuRtZ on 2010-04-04
> **nbv4 said:**
> ```

Apr  4 00:12:22 linode sshd[21253]: Failed [COLOR="Red"]password[/COLOR] for chris from 173.88.x.x port 53743 ssh2
Apr  4 00:14:24 linode sshd[21295]: Failed [COLOR="Red"]password[/COLOR] for chris from 173.88.x.x port 53844 ssh2
Apr  4 00:16:23 linode sshd[21583]: Failed [COLOR="Red"]password[/COLOR] for chris from 173.88.x.x port 47979 ssh2
Apr  4 00:18:21 linode sshd[21628]: Failed [COLOR="Red"]password[/COLOR] for chris from 173.88.x.x port 48091 ssh2
```

which all looks correct.

KB1JWQ, is right, you have a pass phrase on it!

---

### Post by nbv4 on 2010-04-04
> **KiLaHuRtZ said:**
> KB1JWQ, is right, you have a pass phrase on it!

then how is it not asking me for a password when I run "ssh server" or "scp server:file ."? If theres a passphrase, then theres gotta be something thats supplying the passphrase successfully when I accesses it from within the shell...

```

$ ssh server
Linux linode 2.6.31.5-linode21 #1 SMP Mon Oct 26 18:17:01 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
No mail.
Last login: Sat Apr  3 16:37:55 2010 from cpe-173-88-x-x.columbus.res.rr.com
1 00:29:12 chris@server ~ $ 

```

edit: whats a "login keystore."? How do I access it from within a cron script?

---

### Post by KiLaHuRtZ on 2010-04-04
> **KB1JWQ said:**
> ...are stored with your login keystore.

:)

---

