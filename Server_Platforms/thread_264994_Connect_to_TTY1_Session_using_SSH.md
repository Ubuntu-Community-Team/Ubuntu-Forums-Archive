---
title: "Connect to TTY1 Session using SSH"
date: 2006-09-25
forum: Server Platforms
---

### Post by tuxthepenguin on 2006-09-25
I have Ubuntu 6.06.1 Server setup on a computer and have SSH enabled. I use the server for various things but mainly as a Bittorrent server. X is not installed and will never be installed. Not enough RAM or CPU power.

Currently the way I am using the server is that I use virtual sessions (TTY1, TTY2, TTY3, etc) for different tasks. 

For example on TTY1 I have btdownloadcurses running, downloading a particular torrent file. Samething for TTY2 and TTY3.

What I would like to do is when I am away from the server I want to be able to connect (Using SSH or something) to these particular active TTY sessions.

ALSO -Currently when I connect using SSH and start a particular task, for example I start a torrent download using btdownloadcurses, if I were to close out that SSH session any and all task I have running in it are closed too.

How can I connect (Using SSH or something) to existing TTY sessions to view those sessions just as if I were standing in front of the computer? AND be able to close out the SSH session and not have the task end with the session too? 

I've litereally spent hours googling but cant come up with anything.
Any help would be greatly appreciated.

Thanks

---

### Post by tuxthepenguin on 2006-09-25
Well I just found something that will work.

Screen

screen -S tty1

This creates the session. Afterwards startup which program I'm working with (btdownloadcurses).

On another machine to connect all I have to do is ssh in. then to connect to the tty1 session I issue these commands.

screen -d tty1

This detaches the session where its not bound to a screen

Next I do

screen -r tty1
I should now be able to view the session remotely exactly as if I was standing at it.

Well not sure if I was correct on all the wording or not but it works the way I want. Just thought I would share it with everyone else.

---

