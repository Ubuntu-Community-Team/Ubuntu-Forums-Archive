---
title: "&quot;sudo ssh-add&quot; won't work"
date: 2008-06-30
forum: Security
---

### Post by jam1492 on 2008-06-30
Hello,

After installing xubuntu (hardy) the command

sudo ssh-add 

generates the following error message

sudo: unable to resolve host asus

followed by the error message

Could not open a connection to your authentication agent

I tried the following command suggested on another post:

sudo exec ssh-agent bash

but it generated the error message:

sudo: unable to resolve host asus
sudo: ecec: command not found

All of the commands above work fine without sudo and using sudo -i followed by exec ssh-agent bash I can get ssh-add working using su. 

Does anyone have any suggestions for fixing sudo ssh-add?

Thanks very much.

Alex

---

### Post by HalPomeranz on 2008-06-30
See this thread:  [http://ubuntuforums.org/showthread.php?t=807171](http://ubuntuforums.org/showthread.php?t=807171)

---

### Post by jam1492 on 2008-06-30
Thanks for the link. The links refer to one of three error messages:

sudo: unable to resolve host asus

I've now fixed that.

Unfortunately, the other error message seems to be the key:

"Could not open a connection to your authentication agent"

and I don't know how to fix this.

I've installed xubuntu (hardy) on two laptops and get this error on both immediately following installation (and adding private keys). 

Without "sudo" the ssh-add works fine and I never had problems with this previously.

Is this a new security measure or could it be a small bug that found its way into the new version.

Any suggestions?

Thanks very much.

Alex

---

### Post by HalPomeranz on 2008-06-30
Then you do:

```

sudo ssh-agent bash
ssh-add

```

That'll put you into a root shell ("sudo ssh-agent bash") and load your key into the ssh-agent process ("ssh-add").

The real question here is why are you doing this as root?  What exactly are you trying to accomplish with all of this?

---

### Post by jam1492 on 2008-06-30
I use rsync as root over ssh to syncronize my work between office, desktop, and laptop. Without being able to do this on a new computer, I cannot use it for work because I would end up with different file versions on different computers.

In principle, I shouldn't do this as root. But there is a mess of permission settings and a couple of users and doing it as user would not work (some files and directories would be left out -- and I am not sure which). 

Regarding your suggestion. I agree that I can run ssh-add when logged in as root (sudo -i or sudo ssh-agent bash). However, if do this and then run

sudo ssh 

it doesn't remember my pass-phrase and re-prompts me.  The scripts that I use to rsync uses sudo. I could change these all to run directly as root without sudo, but that would move me further away from the use of sudo.

Is it a new security policy on ubuntu not to allow "sudo ssh-add". If so, it may be a great default, but as with all defaults it seems to me that there ought to be some way for to undo it, no matter how un-advisable.

Thanks again very much.

Alex

---

### Post by HalPomeranz on 2008-06-30
OK, I'm now understanding what you're trying to do.  Try this:

1) Add "env_keep=SSH_AUTH_SOCK" to your Defaults in /etc/sudoers.  So you would run "sudo visudo" and change your Defaults line to look something like:

```

Defaults	!lecture,tty_tickets,!fqdn,env_keep=SSH_AUTH_SOCK

```

The above is based on the Defaults line from my Hardy system.  Yours may look slightly different.

2) Use "ssh-add" to add keys to your keyring as your normal user ID (no need for sudo at this stage).

3) Execute your "sudo rsync ..." (or "sudo ssh ..." or whatever) and it should get the keys from your normal ssh-agent process and not prompt you for your passphrase.

What's going on here is that SSH_AUTH_SOCK is the environment variable that tells SSH processes (or rsync running over SSH) how to communicate with the ssh-agent process and get keys.  sudo normally suppresses environment variables like this when you run a command like rsync via sudo, but the env_keep setting tells sudo to propagate this variable into the environment of the process you're running.

I suspect that if things were working for you on earlier releases of Ubuntu it was because the sudo program in the default package was compiled with env_reset option turned off by default.  But it's most definitely turned on in my Hardy system at least:

```

$ **sudo sudo -V**
Sudo version 1.6.9p10

*[... lots of output not shown ...]*
Reset the environment to a default set of variables    <--- means env_reset set by default
*[... more output not shown ...]*

```

---

### Post by jam1492 on 2008-07-01
Thank you so much!  This did the trick.

Alex

---

