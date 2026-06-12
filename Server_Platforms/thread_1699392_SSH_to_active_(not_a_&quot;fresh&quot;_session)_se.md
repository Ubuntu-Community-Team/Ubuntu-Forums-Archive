---
title: "SSH to active (not a &quot;fresh&quot; session) server terminal"
date: 2011-03-03
forum: Server Platforms
---

### Post by fly-by-night on 2011-03-03
Hi,

I **ssh user@ip** to my server from Ubuntu Desktop (10.04.2 both) .  On the server I have wget going.  When I ssh to it **I want to reach the active wget terminal**, but only see a "fresh" terminal session.

Also when I start wget on the server from the client, I don't know how to reach that wget session on the server.  I see it's running with **top**, but can't control it.  I tried **jobs** with no success.

Anyone with a solution?

---

### Post by CharlesA on 2011-03-03
Each SSH session is a "new" session. Take a look at [screen]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/").

---

### Post by fly-by-night on 2011-03-03
The server is basically used for downloading files, nothing else. I thought I can ssh in to see how it's going.

I'll have look at screen, thank you.

---

### Post by Lars Noodén on 2011-03-04
Either [screen](http://jmcpherson.org/screen.html) or [tmux](http://manpages.ubuntu.com/manpages/maverick/en/man1/tmux.1.html) is what you want.  You can start a session, then detach /reattach as needed even log out in between.  Of the two, screen is more powerful, tmux is simpler.

---

### Post by BkkBonanza on 2011-03-04
One easy way to do this is to start the wget command as a background process (detached from the console). Then you can connect again later and monitor it. You run the command as normal but add a & on the end. It will return immediately but when you use the "**ps afx**" or **top** (or better yet **htop**) commands you will see it running still. 

You may want to pipe output to a file to be able to browse results. I used to do this with an input file list and output log file since wget can take it's target urls from a file. That way you can set up a batch of many files to get. And at any time login and use **less logfilename** to see status.

**Screen** is good too but a bit more work to get familiar with and learn to use effectively.

---

