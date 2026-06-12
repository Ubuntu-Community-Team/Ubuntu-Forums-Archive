---
title: "Trouble Switching to Process, Appears to be Running on Another User"
date: 2013-06-24
forum: Server Platforms
---

### Post by MrCherno on 2013-06-24
Hey, I'm connected to a server running Ubuntu 11.10 via SSH, and I'm having trouble switching to a running process. I'm logged in as the root user. When I run the ps command, I get around three processes, but when I run the ps -U root command, I get about 20, with the one I need to switch to listed. I'm running Screen and a Java application, and I can't seem to access either of them when I log in to SSH again. How can I switch to that user/process? Thanks for any help. :D

---

### Post by The Cog on 2013-06-24
You can't "switch to" a process. 
The best you can do is reattach to a screen session, which the command
```
screen -r
```
should do.

If that's not what you mean, I think I need more explanation as to exactly what you are trying to do.

---

### Post by MrCherno on 2013-06-24
Thanks a lot, that seemed to have worked!

Only thing is, when I run screen -r (which gives me two screens), and attach an ID, then run it again, it says that both are now attached. If I kill one of them by hitting Ctrl-a k, only then does it switch to the running Java app. Is there a way to switch to it without killing all screens except for the one that it's running on? Thanks again. :)

---

### Post by The Cog on 2013-06-25
If you are only running one java process, then I think you should only need one screen process running. "screen -r" will reattach to an in-attached screen instance, but won't capture another screen instance that is already connected to by another console. See "man screen" for details, but "screen -d -R" might be what you are looking for. This is an extract from the manual:```
       -d -r   Reattach a session and if necessary detach it first.

       -d -R   Reattach a session and if necessary detach or even create it first.

       -d -RR  Reattach a session and if necessary detach or create it. Use the first session if more than one session is available.

       -D -r   Reattach a session. If necessary detach and logout remotely first.

       -D -R   Attach here and now. In detail this means: If a session is running, then reattach. If necessary detach and logout remotely first.  If it was not running create it and notify the
               user. This is the author's favorite.

       -D -RR  Attach here and now. Whatever that means, just do it.

            Note: It is always a good idea to check the status of your sessions by means of "screen -list".

```
I was sure there was a way to have multiple consoled attached to the same screen session (for doing demos in the classroom etc.) but I can't find that in the man pages now. Still, as you see above, you can forcibly disconnect the old console when connecting from a new one.

Or maybe I'm not understanding what your problem is now. Please explain further if that's the case.

---

### Post by MrCherno on 2013-06-25
screen -D -RR seems to be the only command that switches to Java app. When I run screen -r (if I'm in the Java app I run Ctrl-a c to create a new screen window first) I get this:

There are screens on:
     20757.ttyp0.tracnode    (06/24/13 18:46:00)     (Attached)
     17346.ttyp0.tracnode    (06/24/13 13:06:36)     (Attached)
There is no screen to be resumed.



I guess one of them is the screen running the Java app and one is the screen running the command line I used to run screen -r? They're both attached by how can I switch between them? If I run screen -r 20757 for example, it tells me that it doesn't exist:

There is no screen to be resumed matching 20757.

---

### Post by The Cog on 2013-06-25
No, it tells you there is no screen to be resumed. Meaning they are already attached to. You need to forcibly detach the current console from screen in order to take it over. This should do it:
```
screen -D -r 20757
```
or 
```
screen -D -r 17346
```

---

### Post by MrCherno on 2013-06-25
That seems to work. :)

Is there a way to check which screen you're currently in? Detaching the current console closes the SSH window, so I'd like to avoid that by switching to a screen that isn't the current one.

---

### Post by The Cog on 2013-06-26
Not that I know of. I never use more than one screen instance. 

You know you can create as many sessions as you want within one screen session? ^A-c creates a new prompt within screen. ^A-n and ^A-p jump to the next and previous sessions. You can even have screen do split windows with a prompt in each window.

---

### Post by MrCherno on 2013-06-26
Hey, thanks a lot for your help! I had two screen instances running (even though I didn't want to), so I killed one of them and all is well.
When I log in via SSH I just type

```
screen -list
```

and it gives me single screen instance, with its PID, and then I resume it by typing

```
screen -r [PID]
```

and that seems to work wonderfully! Thanks again for your help! :D

---

