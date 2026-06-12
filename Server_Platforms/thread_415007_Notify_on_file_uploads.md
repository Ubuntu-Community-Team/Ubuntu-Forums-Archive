---
title: "Notify on file uploads?"
date: 2007-04-20
forum: Server Platforms
---

### Post by gumbald on 2007-04-20
I've got an FTP server set up ready for people to upload some photos. When they put them there, I'll then resize the photos and dump them into a gallery. Is there a way of knowing when someone has uploaded (or even accessed the folder), so I know when I have to do something :)

I'm guessing there could be a log file already doing such, but where should I be looking, and can I get some kind of notification of changes rather than looking at the log file?

I'm using proftpd...

---

### Post by Jussi Kukkonen on 2007-04-20
proftpd may have a log file, but you could also use filesystem-level notifications: inotify (if the kernel supports it) or dnotify. See e.g. package *dnotify*.

---

### Post by gumbald on 2007-04-20
Looks complicated, and can't find any simple examples to prove me wrong :)

---

### Post by jtc on 2007-04-20
Are you familiar with writing shell-scripts? If so, then you could always have cron run a script, checking for new files, at regular intervals.

---

### Post by gumbald on 2007-04-20
Not hot on shell-scripts, so it would take me some time, but possible.

I've found the proftpd log file, which shows when files are created, is it possible to somehow know when this single file changes? :)

---

### Post by Jussi Kukkonen on 2007-04-20
> **gumbald said:**
> Looks complicated, and can't find any simple examples to prove me wrong :)

Ok... the dnotify package is described as follows: *"Execute a command when the contents of a directory change"*. After installing the package, you can look at the man page, where a trivial change to one of the examples gives you a command:
```
dnotify -C /path/to/ftp/dir -e script-to-run-on-file-creation
```
I don't think it can get much more simple. You haven't said what you'd like to happen when a file is created, but possibilities include popping a dialog (use zenity) or sending an email (use e.g. mail) or just about anything. 

The simplest option could be running the command from a terminal and leaving it visible: 
```
dnotify -C /path/to/ftp/dir -e echo file created
```
It'll print a line everytime there's a new file in the dir

---

### Post by gumbald on 2007-04-20
That's much simpler than I read, an explanation like that was what I needed :) Cheers! So I can get that to run on startup from a script? And then create a file on the desktop?

---

### Post by Jussi Kukkonen on 2007-04-20
You're welcome.
> So I can get that to run on startup from a script?
Yes. If you mean system startup, I believe /etc/rc.local would be a good place to put it. If you meant your user login, I guess you can add scipts in System->Preferences->Sessions

> And then create a file on the desktop?
Can you explain that?

---

### Post by gumbald on 2007-04-21
> **Jussi Kukkonen said:**
> 
Can you explain that?

I've managed to explain it to myself :) Thanks for the help.

---

