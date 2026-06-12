---
title: "How do you find out whats running on the machine?"
date: 2008-10-12
forum: Server Platforms
---

### Post by effec on 2008-10-12
Windows has task manager, what does Ubuntu have?

I tried to install XAMPP yesterday , because I thought that nothing involving a LAMP server was on my machine. It seems as if was wrong. Here's what I got.
```
Starting XAMPP for Linux 1.6.8a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'Mars'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.
```

---

### Post by jordilin on 2008-10-12
Well, you can type ps ax or top. More info:
```
man ps
```
```
man top
```

---

### Post by howefield on 2008-10-12
Go to System menu, select Administration, then System Monitor.

Second tab from the left, Processes will tell you what's running.

---

### Post by jordilin on 2008-10-12
> **howefield said:**
> Go to System menu, select Administration, then System Monitor.

Second tab from the left, Processes will tell you what's running.

Yep, that maybe easier. I'm so used to the command line that sometimes I forget GUIs really exist :biggrin:

---

### Post by howefield on 2008-10-12
Glad you do, I'm learning something new every day, nice command that top.

:)

---

### Post by paris_alex on 2008-10-12
You'll also want to check out "System Monitor" for GNOME panel. Right click your GNOME panel, select "Add To Panel" and add "System Monitor". 

This would give something like the Windows Task Manager tray icon.

---

### Post by crazyness003 on 2008-10-12
Actually, the best one I've tired is called htop. You have to download it from the repos
```
sudo apt-get install htop
```You need to run as root (in super user), so be careful.
Then just type
```
htop
```To run. Its a CLI-like GUI in the terminal, but it takes very little resources like TOP but is extensive like the System Monitor. It takes a little to get used to, but its worth it.

---

### Post by Krupski on 2008-10-12
> **effec said:**
> Windows has task manager, what does Ubuntu have?

I tried to install XAMPP yesterday , because I thought that nothing involving a LAMP server was on my machine. It seems as if was wrong. Here's what I got.
```
Starting XAMPP for Linux 1.6.8a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'Mars'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.
```

The "ps" command is what you need.

"ps -A" lists all commands running. If you're looking for something in particular, pipe it through "grep" like this:

Example: see if the vsftpd daemon is running:

"ps -A | grep -i vsftpd"

The "-i" parameter for grep means "ignore case" so that "vsftpd" and VSFTPD will both be matched.

Hope this helps.

-- Roger

---

