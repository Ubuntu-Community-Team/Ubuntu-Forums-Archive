---
title: "Super Newb in training!"
date: 2016-03-01
forum: Server Platforms
---

### Post by joe199 on 2016-03-01
Alrighty so this is my very first experience with any form of Linux based system... I could use some help with a couple things!

I'm attempting to run an rsps from a vps as a learning environment for java coding. I just got java installed on the server, it's a standard vps from bluehost with cPanel... it is the jdk7 & jre7 installs

Now i'm looking for the proper way to convert my batch file I used to run the server from a windows computer to properly run in the new Linux environment. I'm not too sure of the differences between the 2 systems would be for the separate operations but this is the batch file edited in Notepad++

@title Star Server
@echo off
"C:\Program Files\Java\jre7\bin\java" -XX:-OmitStackTraceInFastThrow -Xms1024m -Xmx1024m -server -cp bin;lib/log4j-1.2.16.jar;lib/mysql-connector-java-5.1.18-bin.jar;lib/netty-3.5.2.Final.jar;lib/FileStore.jar com.rs.Launcher
pause

Any help converting this so i may use the new one as a command in Putty through SSH connection to start the server would be epic!
Thanks for the spoon feeding in advance!

---

### Post by Bucky Ball on 2016-03-01
*Thread moved to **Server Platforms**.*

Although you're new, people will take that into account and you'll have a much better chance of support here.

---

### Post by houstonbofh on 2016-03-02
The "@" are commands run that you may not need.

"@title" changes the window title.  This is a bit more work in Linux then you may want to do...
[http://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title](http://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title)

"@echo off" suppresses screen messages.  Again, you may not want to do this...
[http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-@echo-off-alternative-for-a-shell-script-780842/](http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-@echo-off-alternative-for-a-shell-script-780842/)

Then just change you java path.


This may work.
```

/usr/bin/java -XX:-OmitStackTraceInFastThrow -Xms1024m -Xmx1024m -server -cp bin;lib/log4j-1.2.16.jar;lib/mysql-connector-java-5.1.18-bin.jar;lib/netty-3.5.2.Final.jar;lib/FileStore.jar com.rs.Launcher 2>&1 >/dev/null

```

---

### Post by joe199 on 2016-03-04
Thank you bucky, and i'll try that houston

---

