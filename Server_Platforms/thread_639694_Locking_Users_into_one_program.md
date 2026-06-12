---
title: "Locking Users into one program"
date: 2007-12-13
forum: Server Platforms
---

### Post by linuxunil on 2007-12-13
I want to set a server up so that when a user logs in through ssh a program launches and they are only able to use that one program.

---

### Post by drummingpariah on 2007-12-13
> **linuxunil said:**
> I want to set a server up so that when a user logs in through ssh a program launches and they are only able to use that one program.

You could set up a limited user account and chmod +x the single program you want them to use, and nothing else.  Of course, it'd take awhile to test all the dependencies and folders that would require access.  I'm not sure that ssh has a function built-in for this.

---

### Post by HermanAB on 2007-12-13
Sudo can do that.

Read the sudoers man page.  Since Ubuntu already use sudo, this is the 'right' way to do it.

Cheers,

Herman

---

### Post by drummingpariah on 2007-12-13
> **HermanAB said:**
> Sudo can do that.

Read the sudoers man page.  Since Ubuntu already use sudo, this is the 'right' way to do it.

Cheers,

Herman

I thought it'd be nice and simple, I just wasn't sure exactly what app took care of that.  You can also customize ssh settings, but if this is a dedicated server, I'd say make separate user logins with only the permissions you want them to have.

---

### Post by cdenley on 2007-12-13
You can change that users shell to that program, or a script which launches that program.

```

sudo usermod -s /path/to/program username

```

---

### Post by HermanAB on 2007-12-13
Well, doing it with sudoers and gtksu *is* nice and simple.  Any other way would be more difficult.

---

### Post by cdenley on 2007-12-13
I think one of us misread the original post. From what I understand the user logs in through ssh terminal. As soon as logging in, a command-line program launches. The user should have no option to run anything but the program which started automatically. Setting a user up with sudo wouldn't restrict what they can run, unless they are attempting to run it with sudo, correct? Also, can sudo launch stuff automatically on login?

Are we talking about using sudo and ssh on a remote server, or sudo as an alternative to using an ssh server on the local machine to switch users?

---

### Post by HermanAB on 2007-12-13
With sudoers, you can specify *exactly* which programs a user is allowed to run.  If you list only one program for a group of users, then that is the only one they can run and they cannot do anything else.

It is all explained in the sudoers man page.

Cheers,

H.

---

### Post by linuxunil on 2007-12-13
Setting it up so that the user(s) can only sudo one program might work.  But more specifically what I'm doing is developing a MUD (multi user dungeon) for a class.  Since most MUDS use Telnet (and I don't like the idea of sending unencrypted passwords over it) I wanted to develop one using SSH.  Rather than develop it by directly implementing SSH I was going to use an SSH client and have the game client launch from the console.

---

### Post by HermanAB on 2007-12-13
That should work.  I am using sudo to limit certain user groups to very specific programs on military schtuff.  If it works for us, then it will work for you.

You can launch things in one line like this:
$ ssh [email]user@server.example.com[/email] programname

Cheers,

H.

---

