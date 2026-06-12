---
title: "sudo vs su"
date: 2011-07-19
forum: Security
---

### Post by orrymr on 2011-07-19
So, I'm not quite sure what the difference is? Is it that sudo allows you to "borrow" superuser privileges, whilst su allows you to actually log in as superuser?

Also, when I sudo [command] and get prompted for a password, after I input it, things work just fine, but if I su, and then get prompted for a password, I can't log in as superuser... Why is this?

---

### Post by androssofer on 2011-07-19
> **orrymr said:**
> So, I'm not quite sure what the difference is? Is it that sudo allows you to "borrow" superuser privileges, whilst su allows you to actually log in as superuser?

Also, when I sudo [command] and get prompted for a password, after I input it, things work just fine, but if I su, and then get prompted for a password, I can't log in as superuser... Why is this?

when u do "su" you switch user to 'root', so anything you run has root privileges... sudo is just for a single command. there isnt much different except with sudo ur less likely to give the wrong command root privileges as you need to specifically type sudo, however if u switch to 'root', as anything u run will have root privileges u might run sumthing by accident.. so i prefer sudo for tht reason.

also sudo will put anything you run in your command history, su will put it under root's command history.

---

### Post by haqking on 2011-07-19
su defaults to the superuser, or can be used to become another account

su <username>
[http://manpages.ubuntu.com/manpages/hardy/man1/su.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/su.1.html)

Sudo temporarily elevates privelege if user is in sudo group to carry out admin tasks.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Roasted on 2011-07-19
So, it's kind of like this?


Example 1 - Su

```
su
apt-get install audacity
```

versus Example 2 - Sudo

```
sudo apt-get install audacity
```

Su gives you a Fedora-feeling to it where you're in as root operating every command as root. Whereas Sudo is a "root" on a per-command basis.

Is that right?

---

### Post by Grenage on 2011-07-19
Just to make things ever more interesting, you can also use:
```
sudo -i
or
sudo -s
```
To gain a persistent root shell.

Sudo is generally safer, and it's what I use on most of my machines.

---

### Post by orrymr on 2011-07-19
When I try use su, however, I get an "Authentication failure" error...

---

### Post by Wim Sturkenboom on 2011-07-19
*su* logs you in as the root user. So you need to provide the root password.

And in (standard setup of) Ubuntu that does not work.

On a site note:
don't use '*su*' but use '*su -*'; in the first case root still has the user's environment, in the second case root has the root environment.

---

### Post by androssofer on 2011-07-19
> **orrymr said:**
> When I try use su, however, I get an "Authentication failure" error...

the root user password is usually different to your password. sudo is elevating ur username to have root power, so requires ur password, root (su) is a seperate user and has its own password. 

```
sudo passwd root
```

will allow you to change roots password to be the same as yours.. tho i would advise keeping it different from your own.

***note:** read this before changing the root password:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Grenage on 2011-07-19
> **orrymr said:**
> When I try use su, however, I get an "Authentication failure" error...

Because the root account is disabled in Ubuntu.

P.S: It is against forum policy to show a user how to enable the root account.

---

### Post by orrymr on 2011-07-19
> **Grenage said:**
> Just to make things ever more interesting, you can also use:
```
sudo -i
or
sudo -s
```To gain a persistent root shell.

Sudo is generally safer, and it's what I use on most of my machines.


And if I want to end my root session, do I simply use the command "exit"? 

This whole thing stems from a very simply script I'm trying to implement: 
```

#!/bin/bash
#script checks if logged in as superuser.

if [ id = "0" ]; then
    echo "Script run by superuser"
else
    echo "Script not run by superuser"
fi

```The name of the script is suScript, and whether or not I run ```
 ./suScript 
``` or ```
sudo ./suScript
``` I get the same result. I guess that would be as a result of su being a completely different user, and the use of "sudo" just elevating the current user to have root power, as androssofer put it.

---

### Post by Grenage on 2011-07-19
> **orrymr said:**
> And if I want to end my root session, do I simply use the command "exit"? 

This whole thing stems from a very simply script I'm trying to implement: 
```

#!/bin/bash
#script checks if logged in as superuser.

if [ id = "0" ]; then
    echo "Script run by superuser"
else
    echo "Script not run by superuser"
fi

```The name of the script is suScript, and whether or not I run ```
 ./suScript 
``` or ```
sudo ./suScript
``` I get the same result. I guess that would be as a result of su being a completely different user, and the use of "sudo" just elevating the current user to have root power, as androssofer put it.

Correct; you aren't running as root, merely elevated permissions.  The root account is disabled by default; it can be enabled, but as it's against forum rules (and not recommended), we can't mention how.

---

### Post by sisco311 on 2011-07-19
su and sudo are two setuid root applications. Both of them allow a user to run a command or start a shell as another user. 

If no user is specified, both of them default to root.

By default, sudo prompts for your user's password, while su prompts for the target user's password. In Ubuntu, the root account password is locked, hence you can't use su to become root.

`sudo -s', similar to `su', starts a root shell, but keeps some of your environment variables.

`sudo -i', similar to `su -', starts a root (login) shell with root's environment variables. (This one is the preferred method for starting a root shell.)

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see [post=6188826]unutbu's post[/post].

`sudo COMMAND', similar to `su -c "COMMAND"' runs a single command as root.

sudo *remembers* your password for a brief period of time, by default in Ubuntu for 15 minutes, so you don't have to re-enter it every time you invoke it, while su will prompt for a password each time is invoked by a non-root user.

This are the main differences and similarities, I can think of right now, between the default behavior of su and sudo.

Of course, you can customize sudo via the sudoers file. You can make it to prompt the users for the root password or for the target user's password. You can specify which environment variables you want to reset or keep. You can specify which users are allowed to run commands as another user with or without a password and much more...

---

### Post by doas777 on 2011-07-19
@op, the most pertinent differance is that su will not work on a default ubuntu system, because it disables the root account. NEVER ENABLE ROOT UNLESS YOU ARE SURE YOU KNOW WHAT YOU ARE DOING. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There are some important environment differances between escalation methods, including the location of '~'. check this out:

```

#----------normal----------------#
User@Lucid:~$ pwd
/home/User

#----------sudo -i --------------#
User@Lucid:~$ sudo -i
[sudo] password for User: 
root@Lucid:~# pwd
/root
root@Lucid:~# exit
logout

#----------sudo -s --------------#
User@Lucid:~$ sudo -s
root@Lucid:~# pwd
/home/User
root@Lucid:~# exit
exit

#----------su ------------------#
User@Lucid:~$  sudo passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

User@Lucid:~$ su
Password: 
root@Lucid:/home/User# pwd
/home/User
root@Lucid:/home/User# cd ~
root@Lucid:~# pwd
/root
root@Lucid:~# exit
exit

User@Lucid:~$ sudo passwd -l root
passwd: password expiry information changed.

```

---

### Post by psusi on 2011-07-19
> **Grenage said:**
> 
P.S: It is against forum policy to show a user how to enable the root account.

No it isn't; the instructions are provided on the wiki:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Both su and sudo run a command as another user ( defaults to root ).  That command may be a shell that will prompt you for more commands ( that will also be run as that user by virtue of the fact that the shell is ).  The main difference between the two is that su asks for the password of the user you are switching to, but sudo normally asks for YOUR password.  su defaults to running a shell if you do not specify another command to run as the other user, but sudo does not; to have it run a shell, use the -s switch.

Other differences/features include:

1)  su does not prompt for a password if you are root, allowing root to switch to other users without knowing their password

2)  sudo can be configured to allow specific users to only execute specific commands

3)  sudo is configured by default to not prompt for your password on repeated invocations ( in the same terminal ) within a few minute time period

4)  sudo can be configured not to bother prompting for your password at all, though this is not recommended

---

### Post by Grenage on 2011-07-19
> **psusi said:**
> No it isn't; the instructions are provided on the wiki:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Interesting; has that changed reasonably recently? I was sure it was so.

---

### Post by sisco311 on 2011-07-19
> **Grenage said:**
> Interesting; has that changed reasonably recently?

No, the policy is the same, although it was reworded about a year ago: 

[thread=1486138]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by orrymr on 2011-07-19
but then, regarding my script, when I sudo -i, and cd into the directory where I saved my suScript file, and run the script I get the following output: ```


root@orrymr-desktop:/home/orrymr/Documents/shellStuff# ./suScript
Script not run by superuser


```

When logged in as root, when I issue the command "id" I get the following output : ```

root@orrymr-desktop:~# id
uid=0(root) gid=0(root) groups=0(root)

```

I would have thought that, according to my script, the line "Script run by superuser" would be echoed out.

---

### Post by sisco311 on 2011-07-19
> **orrymr said:**
> but then, regarding my script, when I sudo -i, and cd into the directory where I saved my suScript file, and run the script I get the following output: ```


root@orrymr-desktop:/home/orrymr/Documents/shellStuff# ./suScript
Script not run by superuser


```

When logged in as root, when I issue the command "id" I get the following output : ```

root@orrymr-desktop:~# id
uid=0(root) gid=0(root) groups=0(root)

```

I would have thought that, according to my script, the line "Script run by superuser" would be echoed out.

[ id = "0" ] is always false. The string `id' is not `0' ;)

You probably want something like:
```

if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi
```

Or, in bash, you can use the EUID variable:
```
if (( $EUID == 0 ))
then
    echo "root"
else
    :
fi
```

---

### Post by orrymr on 2011-07-19
Awesome - that did the trick. Thanks!

---

### Post by raja.genupula on 2011-07-19
thanks for this info , to all of you 

but actually everytime i use 
sudo for all kind of root work

---

### Post by sisco311 on 2011-07-19
> **orrymr said:**
> Awesome - that did the trick. Thanks!

You're welcome! Don't forget to mark this thread as [SOLVED].

---

### Post by Grenage on 2011-07-19
> **sisco311 said:**
> No, the policy is the same, although it was reworded about a year ago: 

[thread=1486138]Forum policy on log-in-as-root tutorials[/thread]

Ah peachy, thank you. :)

---

### Post by doas777 on 2011-07-19
> **Grenage said:**
> Ah peachy, thank you. :)
Yeah, I got yelled at about that one some years ago, so now I just type stuff in all caps and include a link to the rootsudo doc, just to be on the safe side.
It was primarilly one mod that gave away most infractions for that issue, and I haven't seen them around lately.

---

### Post by Grenage on 2011-07-19
> **doas777 said:**
> Yeah, I got yelled at about that one some years ago, so now I just type stuff in all caps and include a link to the rootsudo doc, just to be on the safe side.
It was primarilly one mod that gave away most infractions for that issue, and I haven't seen them around lately.

Aye, that was the only reason I mentioned it; I was sure I'd seen that happen before.

---

### Post by wkulecz on 2011-07-21
I don't have anything to add about Ubuntu sudo vs. su, but in the old days, RMS and others considered su to be evil because it gave control of the machine to a cabal of users who had the root password and were members of the wheel group(as in big wheel :) ).

Its largely academic now that we all pretty much own our own machines.  As far as I know Ubuntu has never had the wheel group.

---

