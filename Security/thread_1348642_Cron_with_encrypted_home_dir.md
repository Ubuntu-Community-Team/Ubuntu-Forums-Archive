---
title: "Cron with encrypted home dir"
date: 2009-12-07
forum: Security
---

### Post by nyhm on 2009-12-07
**Does having an encrypted home dir (as provided in 9.10 by ecryptfs) impact user cron jobs? **

For example, if I add some nightly tasks to my user's crontab, how will cron react if my user is logged out?

Forgive me for not trial-and-erroring this before asking, but I am looking for some insight before committing to an encrypted home dir. Any insight greatly appreciated. (I'm an experienced Debian user, but brand new to Ubuntu.)

---

### Post by cdenley on 2009-12-07
> **nyhm said:**
> **Does having an encrypted home dir (as provided in 9.10 by ecryptfs) impact user cron jobs? **

For example, if I add some nightly tasks to my user's crontab, how will cron react if my user is logged out?

Forgive me for not trial-and-erroring this before asking, but I am looking for some insight before committing to an encrypted home dir. Any insight greatly appreciated. (I'm an experienced Debian user, but brand new to Ubuntu.)

I'm pretty sure there aren't any configuration files read in the user's home directory since the PATH variable isn't even set for cron jobs, and the cron tab isn't stored in the user's home directory, but in /var/spool/cron/crontabs/$USER, so I don't think it would be a problem. Unless, of course, your cron job uses commands which attempt to access the user's home directory.

---

### Post by nyhm on 2009-12-07
Thanks for the feedback cdenley. My cron scripts do, indeed, need to access my $HOME directory to function.

Under this use case, the script will only work if I leave my user logged in (with the home dir decrypted). If I log out (and Ubuntu is set up correctly to unmount my home dir), then the scripts cannot run properly. I'm not (yet) sure how cron itself will behave (log error perhaps).

Even if I do leave my user logged in, upon unexpected reboot/power-cycle, my cron scripts cannot function.

... I must evaluate whether this (generally useful) feature is compatible with my needs. Any further insight from the community on this type of use case is more than welcome.

---

### Post by cdenley on 2009-12-07
If your scripts need access to files, then those files will need to be accessible. There isn't really any way around it. Either put your files somewhere unencrypted, make sure the encrypted filesystem is mounted when needed, or expect it to fail when it isn't mounted and write your script to handle such a scenario. How your script fails when failing to read files depends entirely on the script. If any output is generated, it sends an e-mail by default, I believe, to the root user. You can have output sent to another user by setting the MAILTO variable.

---

### Post by nyhm on 2009-12-07
Thanks for comments cdenley. I should prefix all of my crontab entries with:

```
if [ -d $HOME/bin ] then ...
```This should work since the crontab file is *not* in the user's home (as mentioned earlier) and cron executes scripts in the user's context ($HOME should be set). If my bin directory exists, then it will run the script. As an else clause, I could echo "Warning: $HOME not mounted" which would be sent as email to root or MAILTO setting.

Is there a documented list of known pitfalls (failure cases) for using encrypted home dirs? For example, [this wiki article]("https://wiki.ubuntu.com/EncryptedHomeFolder") points out some issues.

---

### Post by Agent ME on 2009-12-07
You can move your ~/bin folder to be not encrypted. I can't remember the specifics, but it's the same method people use to make their ~/.ssh folder stay unecrypted so they can SSH in passwordless.

---

### Post by nyhm on 2009-12-07
Agent ME, thank you for the input. That's another good fail case: ssh'ing in using authorized_keys would need special, non-encrypted setup.

I could try to set up my bin directory like that, but my bin scripts operate on things within my home dir, so that doesn't solve the problem.

I'm thinking that, in general, I totally agree with the philosophy and theory of using an encrypted home dir, but the practice has too many pitfalls (at least for my particular use cases).

Now I just need an answer to [COLOR=Plum][removing encryption from the home dir]("http://ubuntuforums.org/showthread.php?t=1258294")[/COLOR]... (I think I'd be better off symlinking into the Private directory where needed)

---

