---
title: "screen issue and ssh permissions and so on :)"
date: 2007-07-01
forum: Server Platforms
---

### Post by Luca.es on 2007-07-01
Hello!
Picture this:

I created a user. That user chown's -R a directory. The homedir is set to that folder. proftpd is set to limit the user to the home directory. So far so good.

This user runs a script file as so:

#!/bin/sh
screen -r user -X quit
echo blabla
screen -dmS user ./the_application

The user is set to run this script. (that has to be like that in my case).

Now the problem:

when root I "su" to the user

But when I want to resume the screen session I get:

Cannot open your terminal '/dev/pts/0' - please check.

However when I login with a new session SSH server it works.

Question 1: How can I access the screen session with su user? I know that the permissions of dev pts 0 can be changed. How do I do this?
I was told that tty group has permissions on this. Could I make "root" member of tty and that would solve it?

Another problem is I dont want that users can SSH to the server! I thought about limiting SSH access to root only. 

Or what would be the cleanest way to do this?

---

