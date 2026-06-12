---
title: "Preventing user from accessing command line"
date: 2011-05-08
forum: Security
---

### Post by madengineer on 2011-05-08
I'm trying to set up an unprivileged user on some field systems running 11.04 with the standard Gnome shell (rather than Unity), and ideally that user would not have access to the command line. The user can log in through GDM (but not the text consoles) with no password, so I need to provide the absolute minimum of privileges; basically the user should only be able to run one program.

I've already set the /desktop/gnome/lockdown/disable_command_line key with gconf-editor for that user, which successfully disabled the "Run Command" dialog. Unfortunately, even though the description of the key in gconf-editor says "prevents the user from accessing the terminal...", the terminal emulator is still accessible from the Applications menu, and I haven't been able to find a good way of disabling the terminal or removing it from the menu. The only thing that occurs to me is an ugly hack: replace the gnome-terminal binary with another that checks to make sure the user is not the unprivileged one and then starts gnome-terminal. Does anyone know the "right" way of doing this?

---

### Post by papibe on 2011-05-08
I would play a little with the permissions. I thought of something like this:
```
$ cd /usr/bin

$ ls -l gnome-terminal
-rwxr-xr-x 1 root root 263868 2010-09-16 03:20 gnome-terminal

$ sudo chown root:admin gnome-terminal

$ sudo chmod 750 gnome-terminal

$ ls -l gnome-terminal
-rwxr-x--- 1 root admin 263868 2010-09-16 03:20 gnome-terminal



```

That way only members of the admin group (initially just you) will be able to run gnome-terminal.

I hope it helps.

---

### Post by Lars Noodén on 2011-05-09
One step in that direction would be to try setting the user shell to **/bin/false**

---

### Post by karthick87 on 2011-05-10
> **lars noodén said:**
> one step in that direction would be to try setting the user shell to **/bin/false**

+1

---

### Post by dargaud on 2011-05-10
In the past (text-only linux) the main way to restrict the user to a simple program was to put it as the shell in /etc/passwd, but nowadays I don't know how that'd fly.

---

### Post by Lars Noodén on 2011-05-10
> **dargaud said:**
> ... nowadays I don't know how that'd fly.

```
usermod -s /bin/false *user*
```

Works as far as I can tell.

---

