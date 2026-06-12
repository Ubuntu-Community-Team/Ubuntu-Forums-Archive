---
title: "ubuntu one does not connect"
date: 2010-04-04
forum: Ubuntu One (CLOSED)
---

### Post by andrea000 on 2010-04-04
u1 takes 5 or more times of starting and restarting to connect
then after it connects and i try to upload five 1.8 MB files
they all come back with u1conflict on them.I was thinking that
bug was fixed over a year ago or something like that and the
slow connect time and u1conflict that was fixed also and it 
worked great.So could anybody tell me a fast way to fix this
as i love the idea of ubuntu one i just don't think it is ready
to be in main use at this time.I am going to go drop box intill
ubuntu 10.04 comes out maybe it's not ubuntu one it may just will
not work good with 9.10?I am not complaining and have the upmost
respect for the developers of the ubuntu 1 project i am just
saying the obvious.

---

### Post by Addiction2Code on 2010-04-04
I have never experienced the problem you say you are encountering. I am using Ubuntu 9.10 (64bit) and the pre-installed version runs fine. You may want to make sure that you are not somehow connected more than once. If you are not using Ubuntu 9.10, or haven't done updates, do them or uninstall the Ubuntu One package and re-install it based on the instructions found on their website "[https://one.ubuntu.com/support/installation/]("https://one.ubuntu.com/support/installation/")" I hope this helps, although I am not an expert, it would probably help more if you posted detailed information about the build of Ubuntu you are using.

---

### Post by andrea000 on 2010-04-05
Thank you i am using ubuntu 9.10 32 bit with every update
the only thing that is different about mine is i had the 
firefox bookmarks sync installed but i took that off and
there is no difference.

---

### Post by joshuahoover on 2010-04-05
> **andrea000 said:**
> u1 takes 5 or more times of starting and restarting to connect
then after it connects and i try to upload five 1.8 MB files
they all come back with u1conflict on them.I was thinking that
bug was fixed over a year ago or something like that and the
slow connect time and u1conflict that was fixed also and it 
worked great.So could anybody tell me a fast way to fix this
as i love the idea of ubuntu one i just don't think it is ready
to be in main use at this time.I am going to go drop box intill
ubuntu 10.04 comes out maybe it's not ubuntu one it may just will
not work good with 9.10?I am not complaining and have the upmost
respect for the developers of the ubuntu 1 project i am just
saying the obvious.

Very strange. I'm sorry this problem has started occurring for you. If at all possible can you do the following to provide us with good debug info?

[LIST=1]
[*]Open (or create  if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf 
[*]Add the following 2 lines to this file  and save: 
[main] 
 log_level = DEBUG 
 
[*]Restart the  Ubuntu One client 
[*]Copy  files into your ~/Ubuntu One folder
[*]Right-click on the Ubuntu One client and select "Report a Problem" to file a new bug
[*]Attach  ~/.cache/ubuntuone/log/syncdaemon.log to the bug report
[/LIST]
Thank you,

Joshua

---

