---
title: "sudo, sudo -s, sudo -i"
date: 2007-11-17
forum: Server Platforms
---

### Post by ToniVC1963 on 2007-11-17
Hi,

Sometimes, when I have to do many things as root I use "sudo -s" or even "sudo -i" to become root, instead of having to always precede all my commands with "sudo" (which I many times forget to do).

But now I read on the Community Ubuntu Documentation/RootSudo page ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)) the following:

> 
Logging in as another user
To login as another user.

NB [COLOR="Red"]Please don't use this to become root, please see the bottom of the page for some more information[/COLOR]. 

sudo -i -u username

...

Special notes on sudo and shells
[COLOR="Red"]None of the methods below are suggested or supported by the designers of Ubuntu.[/COLOR] 

Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root. 

To start a root shell (i.e. a command window where you can run root commands), starting root's environment and login scripts, use: 

sudo -i     (equivalent to sudo su - , gives you roots environment configuration)

To start a root shell, but keep the current shell's environment, use: 

sudo -s     (equivalent to sudo su)


My question is: why these methods are not suggested nor supported by the designers of Ubuntu? Is it due to security issues? If so, which ones? 

For example, what's the difference (security wise) of doing:

```
sudo command 1
sudo command 2
...
sudo command n
```

or doing:

```
sudo -s
command 1
command 2
...
command n
exit
```

or:

```
sudo -i
command 1
command 2
...
command n
exit
```

I think I understand the benefits (and drawbacks) of Ubuntu having the root account dissabled and the use of the sudo mechanism to do things as root. But still I have difficult to understand the security implications of sometimes using a root shell...

Thanks,

Toni

---

### Post by conjur3r on 2007-11-17
With power comes responsibility. I believe the main reason to prefixing your commands with sudo is that it reaffirms the user that the following will have (or could have) some system wide affect.  We all make mistakes and being able to make changes which could detriment the state of your system is more evident without any form of a reminder.

Also, sometimes people forget to log out of root mode which is a security threat.  If the user walks off and someone else comes by, they can do anything!  sudo times out after 15 minutes of inactivity which is customisable.

If you feel you are competant enough to use sudo -s or -i, then do so!  The advice not to use it is more directed towards the every day users who do not venture into the terminal and those who are not totally comfortable with issuing commands.  If you can fix your own problems with little direction, you'll be fine.

With the provided examples, there are no differences.  Effectively, they all run commands with root privileges and would have the same result.  However, when things are dependent on environmental variables, then the -s or -i difference is important.

---

### Post by Steveway on 2007-11-17
Imagine that some script/malware whatever you call it inserts a command into your open shell.
That script needs of course root access to do damage.
Now look again at your examples and see wich way is the best.
> **ToniVC1963 said:**
> Hi,

Sometimes, when I have to do many things as root I use "sudo -s" or even "sudo -i" to become root, instead of having to always precede all my commands with "sudo" (which I many times forget to do).

But now I read on the Community Ubuntu Documentation/RootSudo page ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)) the following:



My question is: why these methods are not suggested nor supported by the designers of Ubuntu? Is it due to security issues? If so, which ones? 

For example, what's the difference (security wise) of doing:

```
sudo command 1
sudo command 2
**evilscript**
...
sudo command n
```

or doing:

```
sudo -s
command 1
command 2
**evilscript **
...
command n
exit
```

or:

```
sudo -i
command 1
command 2
**evilscript**
...
command n
exit
```

I think I understand the benefits (and drawbacks) of Ubuntu having the root account dissabled and the use of the sudo mechanism to do things as root. But still I have difficult to understand the security implications of sometimes using a root shell...

Thanks,

Toni

---

### Post by ToniVC1963 on 2007-11-18
Thanks a lot conjur3r and Steveway. So I see that in fact there's little "technical" implications but some "practical" ones, mainly having to do with the responsibility of having the power of root all the time, while with sudo you must be constantly deciding for each command if you need root and specifically stating you want to run commands as root when needed. But in my experience I can say that sometimes, when doing heavy root duties, I end automatically writing "sudo" even with commands that wouldn't need it... so at the end maybe the problem is the same...

> **conjur3r said:**
> However, when things are dependent on environmental variables, then the -s or -i difference is important.

That's true, and I already was aware of it. That's what I meant to know when asking for differences between one method or the other.

> **Steveway said:**
> Imagine that some script/malware whatever you call it inserts a command into your open shell.
That script needs of course root access to do damage.
Now look again at your examples and see wich way is the best.

You are right. But this would also be possible to occur if the inadvertently inserted command is executed as root via sudo... I don't think it can only occur when using a root shell, but maybe I'm wrong. Anyway, this is exactly the kind of security issues I'm asking for: security threats that would be possible if using a root shell but NOT using the sudo escheme.

Thanks,

Toni

---

