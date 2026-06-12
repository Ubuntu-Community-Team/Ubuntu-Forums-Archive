---
title: "Autologin to 9.10 Server"
date: 2009-12-23
forum: Server Platforms
---

### Post by mertz on 2009-12-23
Now, I know there's been a million topics like this before, but none of the solutions I've found have worked for me, so here we go ... 

I have an old laptop on which I have a small commandline app that launches automatically on login. 
I have installed Ubuntu 9.10 Server on it, mostly because Ubuntu is the distro I am most comfortable with, and the Server edition because it doesn't have a GUI.

But I can't get the server to automatically log in. How can I get it to do that?

There are no security risks, because in the end the laptop will be used  as a prop for some LARPing mates of mine. 

So basically, what it should do is:
1. Boot up
2. Log in automatically
3. Launch the CLI application on login
4. ???
5. Make me rich! Or something like that.

Can anyone help?

---

### Post by cdenley on 2009-12-23
I believe if you want a user to login automatically, you can edit /etc/event.d/tty1 and change the last line to:
```

exec /bin/login -f username

```

Then, you can set the user's shell to a custom script/application, or you can configure their shell to start your application on login. What should happen then the application finishes executing. Drop to a shell or terminate session?

---

### Post by mertz on 2009-12-23
I looked into that approach. But when I do vi /etc/event.d/tty1 it's empty. There's nothing in there.
Should I just add the line, to the file and save it there?

---

### Post by cdenley on 2009-12-23
> **mertz said:**
> I looked into that approach. But when I do vi /etc/event.d/tty1 it's empty. There's nothing in there.
Should I just add the line, to the file and save it there?

It looks like it may have been moved to /etc/init/tty1.conf in 9.10.

---

### Post by mertz on 2009-12-23
Hi,

First off; I missed the last question you had. When the app finishes it should just drop to terminal.

However, I tried editing /etc/init/tty1.conf, where I commented out the existing last line, and instead added your suggestion.
When I rebooted the server it locks on:
* Setting up console font and keymap...

... and doesn't go any further. So something seems off or wrong?

---

### Post by cdenley on 2009-12-23
Did you replace "username" with the appropriate username? What is the user's shell? What happens when you execute this?
```

sudo /bin/login -f username

```

---

### Post by mertz on 2009-12-23
Yes, I did replace username with the actual username. In this case "guest".
Regarding the other two questions I am unsure what you mean ... ie. the user's shell? 

Also, you want me to try and just execute the /bin/login -f guest?

---

### Post by cdenley on 2009-12-23
> **mertz said:**
> Yes, I did replace username with the actual username. In this case "guest".
Regarding the other two questions I am unsure what you mean ... ie. the user's shell? 

Also, you want me to try and just execute the /bin/login -f guest?

Is there actually a user "guest"? If there is a user, then "/bin/login -f guest" should start a terminal session as the user and execute the user's shell (usually /bin/bash), whether it be executed in the terminal or by upstart via tty1.conf.
```

getent passwd guest

```

---

### Post by lumix on 2009-12-23
Similar results here.  So the question is, whence cometh the original invocation of the "login" command?  Should we not make our edits there?

---

### Post by cdenley on 2009-12-23
I tested it for myself, and indeed it didn't work as expected, so I booted a livecd and checked to see how it was done on there. I was close.
```

exec /bin/login -f guest </dev/tty1 > /dev/tty1 2>&1

```

Assuming the user uses bash as their terminal, simply add whatever command you wish to run to the end of the user's .bashrc file.

---

### Post by mertz on 2009-12-23
Briiliant. It works now.

---

### Post by Raistlin355 on 2012-05-29
I realized this is an old post but I felt it nessesary to report that this still works in 12.04.

---

### Post by LHammonds on 2012-05-29
Yes, it is definitely an ancient thread.   However, I would have suggested to use crontab and schedule a script to run and make use of the "screen" command.  Specifically using the "-d" and "-m" option to start a new, detached screen session.  This is what I do for my headless Minecraft server.

Anytime I need to jump onto the console, I login and type **screen -r** to access the screen session, then press **CTRL+A** and then **d** to detach and let the screen session continue running...and then logout.

LHammonds

---

### Post by Raistlin355 on 2012-05-29
> **LHammonds said:**
> Yes, it is definitely an ancient thread.   However, I would have suggested to use crontab and schedule a script to run and make use of the "screen" command.  Specifically using the "-d" and "-m" option to start a new, detached screen session.  This is what I do for my headless Minecraft server.

Anytime I need to jump onto the console, I login and type **screen -r** to access the screen session, then press **CTRL+A** and then **d** to detach and let the screen session continue running...and then logout.

LHammonds

wouldn't you have to be logged in for cron to work?

---

