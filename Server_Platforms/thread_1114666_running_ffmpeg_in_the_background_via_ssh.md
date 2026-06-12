---
title: "running ffmpeg in the background via ssh"
date: 2009-04-03
forum: Server Platforms
---

### Post by fatnic388 on 2009-04-03
Hi all.

I'm trying to convert an avi to dvd using ffmpeg. I have a headless server which I'm trying to do the converting on and running the commands from my laptop via SSH. I'd like to be able to tell the server to start converting and then disconnect without cancelling the command.

I've tried putting an & after the command but the process runs as normal and is still interrupted when the terminal is closed.  

Any ideas how I can run the command then disconnect?

---

### Post by squaregoldfish on 2009-04-03
The easiest way is to add 'nohup' to the front of your command. This tells the process to ignore any hangup signal (which gets sent when the parent shell is terminated).

```
nohup <command> &
```

By default, the console output gets dumped into a text file called nohup.out. This is handy for seeing what the command did while you weren't looking, but if ffmpeg spouts a lot of stuff you may not want to do this for disk space reasons (a very verbose program can easily pump out a gigabyte of console info). You can either adjust ffmpeg's behaviour or nohup's, but you'll have to check the man pages there.

There is an alternative that someone posted on here a while back, but I can't remember it. I may have a quick look for it if I get bored :)

Steve.

---

### Post by vpsville on 2009-04-03
I suggest you install 'screen'.  Its a wonderful app that will let you keep a session going after you log off.  You can then connect again later and resume the session.  You can run a lot of different sessions at the same time too.

---

### Post by fatnic388 on 2009-04-03
I gave *nohups* a go and it works. Running *jobs* showed that the process was running in the background OK. However, once I logged out then logged back in the job doesn't show up any more. How can I tell which background tasks are still running?

---

### Post by squaregoldfish on 2009-04-03
As far as I know, the jobs command tells you what's going on in your current session. Since ffmpeg has been started in a different session, you won't be able to see its details. You'll probably have to rely on top or ps.

As mentioned by vpsville, screen sounds like a more user-friendly solution for you. Might be worth checking it out.

Steve.

---

