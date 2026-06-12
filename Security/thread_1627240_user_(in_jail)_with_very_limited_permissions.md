---
title: "user (in jail) with very limited permissions"
date: 2010-11-21
forum: Security
---

### Post by arapaho on 2010-11-21
I want to have an account (beta user), on which:
[LIST=1]
[*]I can use the Internet and other programs
[*]without administrative rights
[*]without the right to install programs
[*]with a kind of sandbox for everything that is connected to the Internet, which means: everything that is associated with the web browser's processes and files that I save to hard disk I want to be separated from the rest of the system, so that whatever can catch up on this account will be locked in it, for example any (if at all) possible malicious scripts from Internet or whatever may be dangerous now or invented in the future. Sometimes, for example, I save the web page to disk with all it content.
[/LIST]

And in case someone cracked into this account I want make it in that way that he could not do any tricks to read or change passwords, or make any other changes to the system. The best would be if a password for that user might serve only to log in without having any other powers, and I would give that user an automatic login.

For now I created a beta user without administrative rights. I understand that the limiting rights of the user are associated with limiting rights to their home directory. There are also groups, and a user may be included or excluded. I excluded that user from admin group but I don't know what else I can limit and how.
When I give chmod 0644 for /home of this user he cannot run Firefox. When I give him 0740 he can run applications, so I assume the x attribute must be preserved.

This is a user without sudo rights, so when I type sudo apt-get update a message shows up correctly that this user doesn't belong to the sudoers group. But still it's not what I wanted. When the user runs Gufw and wants to change the settings to disable the firewall, a message shows up asking to type in a password of alpha user = primary user, which is that belonging to the sudoers group, the first / main user that I created during system installation. I wish that there was only the message that the beta user has no power to change anything, which means even completely remove the possibility of asking for sudo. 

In addition, I wish that this beta couldn't be able to change the permissions to its home directory, or go to see what is above. Because so far beta can change the file permissions for its /home, even without a sudo password. How can I do it? Do I need to create a kind of chroot jail for this user? 

I would like any changes to that user account could be made only after the user log off from beta account, and log in on alfa account and that beta could run only programs that ware installed by alpha. And that beta could read and write, but alfa could also read and write or remove, alter files on beta account. Basically, alfa account should be superior to beta account. Can do that?

Feel free to comment on any aspect of the above idea.

---

### Post by CharlesA on 2010-11-21
If they don't have Administrator access (ability to use sudo) then they cannot install programs or modify system files.

I don't think you need to chroot anything, just limit their access to their home directory.

See here: [http://www.cyberciti.biz/faq/restrict-linux-users-to-their-home-directories-only/](http://www.cyberciti.biz/faq/restrict-linux-users-to-their-home-directories-only/)

EDIT: Instead of editing /etc/passwd directly, I suggest using usermod:

```
sudo usermod --shell /bin/rbash username
```

---

### Post by arapaho on 2010-11-21
> **CharlesA said:**
> Instead of editing /etc/passwd directly, I suggest using usermod:
After 
```
sudo usermod beta --shell /bin/rbash
```
beta is my beta user
I got this:
```
usermod: user '/bin/rbash' does not exist
```
And I don't know how to proceed further.

---

### Post by CharlesA on 2010-11-21
Huh. I wonder if it's specific to the server install.

Try this:

```
which rbash
```

---

### Post by arapaho on 2010-11-21
After 
```
which rbash
```
I got
```
/bin/rbash
```

In article you linked there is a comment:
"cp /bin/bash /bin/rbash 
will do the trick"
Should I do the same?

---

### Post by CharlesA on 2010-11-21
Oh I failed the syntax.

It should be this:

```
sudo usermod --shell /bin/rbash username
```

---

### Post by arapaho on 2010-11-21
It works. Now I get:
```
beta@betacomp:~$ cd home
rbash: cd: limited
beta@betacomp:~$
```

**Thank you, for this great idea.** But stepping further, I read
[http://www.serverschool.com/dedicated-servers/what-is-a-chroot-jail/](http://www.serverschool.com/dedicated-servers/what-is-a-chroot-jail/)
which indicates that if attacker can see root directories he/she may try to exploit it.

Is it possible if I don't run a server and don't use any ssh services? :confused:

I also read
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

"The following are some possible uses of chroots: 
Isolating insecure and unstable applications"
That's seems to me a great thing to do. And there is an example that I can run Firefox in chroot jail.
I wander where I could place this /chroot directory if I wanted make it for this beta user, because there is written about
```
mkdir /var/chroot
```

I'd appreciate any help or comment.

---

### Post by CharlesA on 2010-11-21
Don't really think you should bother with a chroot if you don't have ssh access.

If it's someone logging in locally, they could always boot off a livecd to get to the root of the drive.

EDIT: I guess you could chroot firefox, but I have no idea how you'd do it.

I'd just use AppArmor tbh.

---

### Post by arapaho on 2010-11-21
Thank you. Two more issues. 
1. If I'd like to mount another partition I only have to make this beta user an owner of this partition. Correct? 
I'm asking because now it is owned by alfa user and its mount point is in /media. Or will I have change mount point to /home/beta_user?
2. I have alfa user belonging to beta user's group and I set 760 permissions to beta home directory. But when I'm logged in as alfa user I still cannot write to this beta directory because permission is denied. Even when I added beta as a member of alfa group I can't write to beta. If I want alfa user to be able to read write to beta user's home because for example I want to copy there some program setting. I don't know what I should do about it. I want alfa user to be kind of superior to beta user concerning privileges.

---

### Post by CharlesA on 2010-11-21
1. You'd need sudo rights to mount a partition. I guess you could add the mount in fstab to get around that, but I'm not quite sure how well that would work.

2. You need execute permissions to enter a directory.

---

### Post by arapaho on 2010-11-21
> **CharlesA said:**
> 2. You need execute permissions to enter a directory.
You are right. I had made one mistake because I forgot to add -R attribute to chmod, which changes also files attributes within chmod'ed directory. Now everything is working correctly. I also removed beta from alfa groups.

CharlesA, I'm very grateful for your help. Thank you. As still a newbie linux user I'm amazed how easy (with your help ;)) and with no cost at all I can harden my system and make it a little bit more secure.

Anyway, I won't mark this topic as solved for now in case anyone else would like to add something.

---

### Post by bodhi.zazen on 2010-11-21
FYI it is rather trivial to break out of a restricted shell (rbash).

Use Apparmor, see my jailbash profile. 

See this post: [http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

### Post by arapaho on 2010-11-22
I just watched information about Chromium OS Security
[http://www.youtube.com/watch?v=A9WVmNfgjtQ](http://www.youtube.com/watch?v=A9WVmNfgjtQ)
He is taking about a sandbox for web browser and jails, so I thought it would be a good idea to do the same. I want to have a more secure system (or user account) for using browsers and applications, but I don't use ssh or other web services, I don't have a server. I don't now if it is necessary but if this could be achieved in a simple way I would do that.
Edit:
You wrote in Ubuntu Security basics: "Consider creating an account without sudo access for "daily use". So, I want that kind of account with limited privileges and additional security measures. It would be nice if there was a script that could create that kind of additional account for web browsing and running applications in a kind of sandbox. As far as I understand sandbox and chroot idea - I'm not sure I do with all aspects of it.
I was also inspired by an article about Jolicloud:
[http://www.readwriteweb.com/archives/jolicloud_relaunches_its_cloud_os_now_built_on_chrome.php](http://www.readwriteweb.com/archives/jolicloud_relaunches_its_cloud_os_now_built_on_chrome.php)
"Jolicloud can also create a cross between a Ubuntu Linux desktop and a Chrome OS desktop. Parts of Chrome OS, including each browser tab and plugin runns in its own chroot jail. What is to stop Jolicloud running a conventional environment Linux applications in their own chroot jail or perhaps in another LXC container, with a shared space for files. This will allow the security of Chrome OS for the Internet, and local Linux applications as well."

---

### Post by bodhi.zazen on 2010-11-22
> **arapaho said:**
> I just watched information about Chromium OS Security
[http://www.youtube.com/watch?v=A9WVmNfgjtQ](http://www.youtube.com/watch?v=A9WVmNfgjtQ)
He is taking about a sandbox for web browser and jails, so I thought it would be a good idea to do the same. I want to have a more secure system (or user account) for using browsers and applications, but I don't use ssh or other web services, I don't have a server. I don't now if it is necessary but if this could be achieved in a simple way I would do that.
Edit:
You wrote in Ubuntu Security basics: "Consider creating an account without sudo access for "daily use". So, I want that kind of account with limited privileges and additional security measures. It would be nice if there was a script that could create that kind of additional account for web browsing and running applications in a kind of sandbox. As far as I understand sandbox and chroot idea - I'm not sure I do with all aspects of it.
I was also inspired by an article about Jolicloud:
[http://www.readwriteweb.com/archives/jolicloud_relaunches_its_cloud_os_now_built_on_chrome.php](http://www.readwriteweb.com/archives/jolicloud_relaunches_its_cloud_os_now_built_on_chrome.php)
"Jolicloud can also create a cross between a Ubuntu Linux desktop and a Chrome OS desktop. Parts of Chrome OS, including each browser tab and plugin runns in its own chroot jail. What is to stop Jolicloud running a conventional environment Linux applications in their own chroot jail or perhaps in another LXC container, with a shared space for files. This will allow the security of Chrome OS for the Internet, and local Linux applications as well."

By default, Ubuntu uses Apparmor. I suggest you learn to use it and download or write a profile for all network aware applications.

Adding a user is fairly straight forward, not sure what you find so difficult about that. You can do it with a graphical interface or from the command line.

[https://help.ubuntu.com/10.04/serverguide/C/user-management.html](https://help.ubuntu.com/10.04/serverguide/C/user-management.html)

FYI to change a user's shell, you can use the command chsh

```
chsh user_name
```

You will need to use sudo or enter the user's password. I always use the full path to specify a shell.

Add the shell to /etc/shells

If needed, restricted shells are merely links
```
sudo ln -s /bin/bash /bin/rbash
sudo ln -s /bin/zsh /bin/rzsh
```

or a command line option, see man bash

---

### Post by arapaho on 2010-11-23
It looks like I can't avoid learning Apparmor :)

I've found an interesting distribution:
[http://qubes-os.org/Architecture.html](http://qubes-os.org/Architecture.html)
[http://www.geek.com/articles/chips/open-source-security-focused-qubes-os-hits-alpha-2010047/](http://www.geek.com/articles/chips/open-source-security-focused-qubes-os-hits-alpha-2010047/)
It's in alpha state, yet. Just a piece of info for those interested in security.

---

### Post by bodhi.zazen on 2010-11-23
> **arapaho said:**
> It looks like I can't avoid learning Apparmor :)

I've found an interesting distribution:
[http://qubes-os.org/Architecture.html](http://qubes-os.org/Architecture.html)
[http://www.geek.com/articles/chips/open-source-security-focused-qubes-os-hits-alpha-2010047/](http://www.geek.com/articles/chips/open-source-security-focused-qubes-os-hits-alpha-2010047/)
It's in alpha state, yet. Just a piece of info for those interested in security.

Apparmor is not *that* difficult to learn. An alternate would be to learn SELinux.

[http://danwalsh.livejournal.com/31146.html](http://danwalsh.livejournal.com/31146.html)

---

### Post by arapaho on 2011-03-23
Does it make sense to make an account (jail) with /bin/false and run Firefox on another account that is not administrative account as a user of this /bin/ false account? I guess this way running Firefox would be safer.
```
gksudo -w -u jail firefox
```
Would it prevent scripts from making bad things like sanding my data somewhere...
Would this restriction be as good as using Apparmor to restrict Firefox?

---

### Post by bodhi.zazen on 2011-03-23
> **arapaho said:**
> Would this restriction be as good as using Apparmor to restrict Firefox?

Absolutely not.

You have many posts on these forums and honestly you aer spinning your wheels.

I advise you either:

1. Learn apparmor. It is not that difficult.

2. Use Fedora + xguest. selinux / xguest works out of the box and thus is a viable option if you do not want to learn apparmor.

3. Use a virtual machine.

---

