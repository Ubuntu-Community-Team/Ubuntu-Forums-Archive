---
title: "gksu or gksudo"
date: 2010-01-18
forum: The Cafe
---

### Post by mick222 on 2010-01-18
I've noticed in some posts people using gksu to open gedit or another gui program as root. I always use gksudo i thought su was for changing user as root and sudo was for open as root am i wrong.

---

### Post by The Toxic Mite on 2010-01-18
[http://en.wikipedia.org/wiki/su_(Unix)]("http://en.wikipedia.org/wiki/su_%28Unix") (copy+paste)
[http://en.wikipedia.org/wiki/sudo](http://en.wikipedia.org/wiki/sudo)

:)

---

### Post by snowpine on 2010-01-18
> **mick222 said:**
> I've noticed in some posts people using gksu to open gedit or another gui program as root. I always use gksudo i thought su was for changing user as root and sudo was for open as root am i wrong.

gksu and gksudo are identical (in Ubuntu anyway).

---

### Post by Psumi on 2010-01-18
gksu/do is also dependant on GNOME dependencies, even though it's just a gtk app.

---

### Post by The Toxic Mite on 2010-01-18
> **Psumi said:**
> gksu/do is also dependant on GNOME dependencies, even though it's just a gtk app.

I didn't know that O_O

---

### Post by Psumi on 2010-01-18
> **The Toxic Mite said:**
> I didn't know that O_O

At least in ubuntu it is. try it on the mini.iso next time after you install xfce4. You'll see that it pulls gnome dependencies even with no-install-recommends.

---

### Post by sisco311 on 2010-01-18
gksu is a GUI frontend for su & sudo. gksudo is simply a symbolic link to gksu. By default, in Ubuntu it's used as a frontend for sudo, but you can use it as frontend for su, by changing the authentication mode in gksu-properties.

Both sudo and su allows a permitted user to execute a command as the superuser or another user.

Both are [suid]("http://en.wikipedia.org/wiki/Setuid") programs.

[http://en.allexperts.com/q/Unix-Linux-OS-1064/real-effective-user-id.htm]("http://en.allexperts.com/q/Unix-Linux-OS-1064/real-effective-user-id.htm")

---

### Post by Xbehave on 2010-01-18
Sudo is for giving a user a some of another user (e.g roots) abilities.
Su (substitute user) is for running a command as another user (e.g root)

In ubuntu sudo is used as su, because it lets you run any command as root, the only difference is the password for su is roots and the password for sudo is your (by default, as sudo can be configured to ask for another password)

Normally with su, you launch as shell (like sudo -i) whereas with sudo you normally run a single command (su -c), but both are almost identical for a gui program (because you always launch a command)

---

### Post by The Toxic Mite on 2010-01-18
BTW:

How come, when you're running a terminal as yourself, the $ sign is at the end of the prompt, but when you're running as root, there's a # sign at the end??

I'm still pretty new to *nix lol

---

### Post by Xbehave on 2010-01-18
> **Psumi said:**
> At least in ubuntu it is. try it on the mini.iso next time after you install xfce4. You'll see that it pulls gnome dependencies even with no-install-recommends. 
Cry me a river, are you going to bring this up everywhere? You never did explain what was so vital about having a "pure xfce" install yet you couldn't be bothered to recompile gksu without gnome enhancements or reimplement the relevant gnome libs yourself.

---

### Post by CharlesA on 2010-01-18
> **The Toxic Mite said:**
> BTW:

How come, when you're running a terminal as yourself, the $ sign is at the end of the prompt, but when you're running as root, there's a # sign at the end??

I'm still pretty new to *nix lol

Lets you know that you are in a child shell (or root shell, not sure which).

---

### Post by mick222 on 2010-01-18
> Sudo is for giving a user a some of another user (e.g roots) abilities.
Su (substitute user) is for running a command as another user (e.g roo

Thx I think i understand now so in ubuntu it doesn't really matter whether you use su or sudo, but in other linux os's su makes you root until you exit the terminal. and sudo just executes the command as root.

---

### Post by Xbehave on 2010-01-18
> **The Toxic Mite said:**
> How come, when you're running a terminal as yourself, the $ sign is at the end of the prompt, but when you're running as root, there's a # sign at the end??
That's a convenient (but not full proof) way to tell, basically if your $PS1 environmental variable, contains a \$ it will be substituted according to those rules (\u will be subbed for your username anyway which is probably an easier way to tell)

---

### Post by CharlesA on 2010-01-18
> **Xbehave said:**
> That's a convenient (but not full proof) way to tell, basically if your $PS1 environmental variable, contains a \$ it will be substituted according to those rules (\u will be subbed for your username anyway which is probably an easier way to tell)

Thanks for the info.

---

### Post by sisco311 on 2010-01-18
> **mick222 said:**
> Thx I think i understand now so in ubuntu it doesn't really matter whether you use su or sudo, but in other linux os's su makes you root until you exit the terminal. and sudo just executes the command as root.

_By default_, su starts a root shell, while sudo, _by default_, runs a single command as root.

su prompts for the target user's password, while sudo, by default, prompts for the invoking user's password.

For more details read the man pages:
```
man su
man sudo
```

---

### Post by cariboo on 2010-01-18
> **mick222 said:**
> Thx I think i understand now so in ubuntu it doesn't really matter whether you use su or sudo, but in other linux os's su makes you root until you exit the terminal. and sudo just executes the command as root.

Su stands for switch user, so you can use it to switch to any other user on you computer, not only root. If you thave three users on your system:

[list]
[*]Tom
[*]Dick
[*]Harry
[/list]

you can switch to any one of them using su eg:

```
su Harry
```

will ask you for Harry's password, you can then run as Harry. The same for Tom and Dick.

---

### Post by alexfish on 2010-01-18
I use gksudo nautilus to change prefs

---

### Post by Marvin666 on 2010-01-18
That symbol is a warning, it's what you'll turn your hard drive into if you're not careful (hash).

---

### Post by mick222 on 2010-01-18
> Su stands for switch user, so you can use it to switch to any other user on you computer, not only root. If you thave three users on your system:

    * Tom
    * Dick
    * Harry


 Yes thats what i thought . The reason I asked this question was a while ago i tried to use sudo to open firefox "forgot to out the gk" and mucked it up a bit . I know that in suse or  fedora  if you use su you can change user or become root just wondered hat the difference was when their is no root user.I think this has bee answered thx everybody.

---

### Post by sisco311 on 2010-01-18
> **mick222 said:**
> Yes thats what i thought . The reason I asked this question was a while ago i tried to use sudo to open firefox "forgot to out the gk" and mucked it up a bit . 


[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

By default, sudo doesn't reset the HOME environment variable. Some applications (like firefox) use this variable to identify the user's home directory. So, if you use sudo to run this applications (mostly GUI apps), you may end up with files owned by root in your home directory.

gksu is designed for GUI apps and resets the HOME variable.

You can also use *sudo -i command* or manually reset the variable *sudo HOME=/root command*.



> **mick222 said:**
> 
I know that in suse or  fedora  if you use su you can change user or become root just wondered hat the difference was when their is no root user.I think this has bee answered thx everybody.

There is a root user in Ubuntu, but the root user's password is locked. That's why you can't directly login as root or su to root.

---

