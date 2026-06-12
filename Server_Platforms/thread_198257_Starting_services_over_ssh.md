---
title: "Starting services over ssh"
date: 2006-06-16
forum: Server Platforms
---

### Post by vigleik on 2006-06-16
This may be a stupid question (I hope it is) but when I ssh in to a server and start a program there, the program dies when I log out of my ssh shell. Is there a way to avoid that? Surely people ssh into their servers to start services all the time, without those services stopping as soon as they're done.

I have a box running mythtv which doesn't have its own mouse and keyboard, and it's a pain to connect those just to open up a shell and restart mythbackend (for example). And I'm too lazy to set up everything I might possibly want to do through the remote.

Vigleik

---

### Post by x64Jimbo on 2006-06-16
All you have to do is add an ampersand after the service's name. For instance, if you were starting the "foobard" daemon, you would type:
User@Machine$ foobard &
Give that a shot. If that doesn't work, try starting the daemon as root:
User@Machine$ sudo su
Password:
root@Machine$ foobard &
root@Machine$ exit
User@Machine$ exit

---

### Post by vigleik on 2006-06-16
My experience is that this doens't work.
user@machineA$ssh machineB
user@machineB's password:
user@machineB$foobar &
(at this point foobar starts, and everything is dandy)
user@machineB$exit 
(at this point foobar stops, which is what I want to avoid)
user@machineA$exit

---

### Post by Ixzat on 2006-06-17
If there isnt a init script for starting the daemon you want, an ugly way of doing could be to run it inside a screen session like this:

screen -s mythbackend
/path/to/mythbackend &

then press "ctrl+a" then "d" to disconnect from the screen session.

to connect to the session again just type screen -r mythbackend

---

### Post by linuchsan on 2006-06-17
you have to run nohup and the ampersand.

---

### Post by vigleik on 2006-06-17
[QUOTE=linuchsan]you have to run nohup and the ampersand.[/QUOTE]

Thanks, nohup sounds like just what I need. I think Ixzat's method works too, but this looks cleaner. I'll test it the next time my mythtv box hiccups, for now I want to just leave it alone....

Vigleik

---

