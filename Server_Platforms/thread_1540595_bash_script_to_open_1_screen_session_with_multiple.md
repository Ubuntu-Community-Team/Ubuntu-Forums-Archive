---
title: "bash script to open 1 screen session with multiple windows?"
date: 2010-07-28
forum: Server Platforms
---

### Post by skidz on 2010-07-28
Hi all

I am trying to write a bash script to open 1 screen session with multiple windows... each one running a different service. Is this possible? I tried several things, and I can start up multiple sessions really easy.. but not 1 session with multiple windows... 

I want this so I can attach to that session and quickly move between the different windows.

Thanks in advance.

---

### Post by DaithiF on 2010-07-28
Hi,
yes you can do this.  an example would be:
```

# start screen in detached mode (-d -m), and give it a session name ('bilbo') to avoid
# confusion when communicating with this session later as we add commands
screen -d -m -S bilbo
# run a command in the current screen window (edit some file for example)
screen -S bilbo -X exec vim /some/file
# create a new window, and run a command in that window:
# there are 2 ways of doing this:
# 1. this runs a command in the new window, without a parent shell.  so once the process ends the screen window also ends
screen -S bilbo -X screen tail -f /var/log/messages

# 2. this creates a screen window, runs a shell, and then runs a command in that shell.  
#   once the command ends, the shell (& screen window) remain running
screen -S bilbo -X screen
screen -S bilbo -X exec tail -f /var/log/messages

```when you want to attach to this screen session, 
```
screen -r bilbo

```hope this helps

---

### Post by skidz on 2010-07-28
Thanks a bunch.. but.. 

#2 does not work :(

It will open up several screen windows, but never executes anything..

I did figure out though that I could do this

screen -d -m -S bilbo

screen -S bilbo -p 0 -X stuff "screen -S bilbo -X screen nano /somefile"
screen -S bilbo -p 0 -X eval "stuff ^M"
screen -S bilbo -p 0 -X stuff "screen -S bilbo -X screen nano /somefile"
screen -S bilbo -p 0 -X eval "stuff ^M"
screen -S bilbo -p 0 -X stuff "screen -S bilbo -X screen nano /somefile"
screen -S bilbo -p 0 -X eval "stuff ^M"

screen -r bilbo

---

### Post by DaithiF on 2010-07-28
Hi,
sorry, #2 will work if you supply the -p parameter to tell screen which window to run the command in (this is necessary when in detached mode, otherwise screen doesn't know which window is 'active').  I missed this first because I was actually attached to the target screen process in another terminal (to observe the commands I was sending being executed).  So I wasn't really in detached mode, and so the -p wasn't required.

so:
```
screen -d -m -S bilbo
screen -S bilbo -p 0 -X exec nano /somefile
```

---

### Post by skidz on 2010-07-28
Thanks a bunch :).. I will give it a try...

---

