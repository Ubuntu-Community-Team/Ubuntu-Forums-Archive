---
title: "Restrict user to their home directory in ssh"
date: 2009-02-26
forum: Server Platforms
---

### Post by bemar on 2009-02-26
Hi @ all,

my target is to setup a ssh-ftp fileserver in my company.

So I've installed the server edition and the openssh server. All is running fine.

But now its time for the security part. How can I setup the system that no user can access to the root folder and its subdirectories and how can I setup that he can't see the other subdirectories in the home dir? If set chmod 750 the user can't login furthermore with ssh.

I've tried out "sudo chmod o-rw * /" which worked good at first view. The user will get the message "permission denied" if he wants to see the content of a root directory in example "/etc". But if the users knows the subdirectories in example "/etc/ssh" he can jump directly to this directory.

Is there a water proof solution?

Thx in forward

Ben

---

### Post by ajmorris on 2009-02-27
hi there,
you might like to look at restricting the user with 'rbash'. bodhi.zazen has a nice guide on his blog about it:

[http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/](http://blog.bodhizazen.net/linux/how-to-restrict-access-with-rbash/)

Hope that helps,

AJ

---

### Post by hyper_ch on 2009-02-28
I prefer mysecureshell. Very simple to setup.

---

### Post by upengan78 on 2009-08-25
> **hyper_ch said:**
> I prefer mysecureshell. Very simple to setup.

Hi,

does mysecureshell allow ssh ?

I would like to allow sftp and ssh both. If sftp can be chrooted that should be enough but want to allow ssh as well. 

Thanks!

---

### Post by scorp123 on 2009-08-25
> **bemar said:**
>  I've tried out "sudo chmod o-rw * /"  That's a great way of **_[COLOR="Red"]RUINING + HOSING[/COLOR]_** your installation!

**[COLOR="Red"]Never ever do this!![/COLOR]** Recursively changing the permissions system-wide is like cutting your head off because you can't find a comb ....

It will do more damage than good. Especially: It will change the permissions of files which were supposed to be readable system-wide and by everyone. There are tons and tons of system-essential files such as **/etc/passwd** which are supposed to be readable for everyone. 

In my opinion you just hosed your system with that command up there. You just did not notice anything yet. But don't worry, the next weird error message about the system being unable to read file xyz is not too far away.

Again: **Please don't run commands via "sudo" if you don't fully understand what why and how and what it will do what it does, OK?**

(Sorry if I sound like a d*ck (nope, I wasn't thinking of ducks ...) here but one can't stress this enough ... )

---

### Post by upengan78 on 2009-08-25
> **scorp123 said:**
> That's a great way of **_[COLOR=Red]RUINING + HOSING[/COLOR]_** your installation!

**[COLOR=Red]Never ever do this!![/COLOR]** Recursively changing the permissions system-wide is like cutting your head off because you can't find a comb ....

It will do more damage than good. Especially: It will change the permissions of files which were supposed to be readable system-wide and by everyone. There are tons and tons of system-essential files such as **/etc/passwd** which are supposed to be readable for everyone. 

In my opinion you just hosed your system with that command up there. You just did not notice anything yet. But don't worry, the next weird error message about the system being unable to read file xyz is not too far away.

Again: **Please don't run commands via "sudo" if you don't fully understand what why and how and what it will do what it does, OK?**

(Sorry if I sound like a d*ck (nope, I wasn't thinking of ducks ...) here but one can't stress this enough ... )

This is very correct. Some commands like these are very dangerous ( atleast on production systems)

While I was new to to systems, I had run chmod o-rx .* and working directory was / on solaris. I did this on solaris and was happy that this secured some of root's files in / ( / being home for root on solaris)...so happy that I went home. :)

Checking emails revealed me that my command messed up complete / :( ..Well, not only user's websites stopped working but no one could login (ssh) to the system because their home directory perms also got changed 

scorp123, has mentioned an important thing in his message, :)

Thanks

---

### Post by scorp123 on 2009-08-25
Addendum:

After you have reinstalled your system (which is only a question of time IMHO) you could consider access control lists maybe?

It's simple: 

I'd create a special mount point for the accounts of these guests, so that their accounts don't end up on **/home** like my own account but rather somewhere else, so I can set ACL's without risking to cause any side-effects on my own files. Let's call this mountpoint **/externals** .... So those guys would have their home directories not underneath **/home**, but rather underneath that directory. Voila, now you could add an ACL entry that forbids those users to go snooping around on **/home** where your account might be located.

What you could also do is this: You add your external SSH users to a user group, e.g. "guests". Then you set an ACL entry on all the stuff you don't want your "guests" to have access to, let's say stuff underneath these locations:
[LIST]
[*]/opt (some expensive commercial softwares I know always install themselves underneath /opt ... so it's a perfect candidate for blocking unwanted access to)
[*]/home
[*]/boot
[/LIST]

However, for the logins and what not to work I would be cautious with banning them from /etc or /var ... There is plenty of stuff in those locations that even a guest account needs access to if you want it to function properly.

ACL tutorial:

[https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)

---

### Post by scorp123 on 2009-08-25
Now that I've looked at the dates of the posting ... ](*,)

Sorry guys for accidentally bumping this ..... :lolflag:

---

### Post by delatun on 2009-10-13
Great post all, just what I'm looking for.

Yup, do NOT:
sudo [ $[ $RANDOM % 6 ] == 0 ] && rm -rf / || echo “You live”

Hahah, a bit of a Roulette for bash. Yum.

---

