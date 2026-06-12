---
title: "/usr/bin/env: bash: Permission denied"
date: 2013-05-14
forum: Server Platforms
---

### Post by amolredhat on 2013-05-14
I not able to recollect, that what I did in .bashrc file in the server, after re-logging in the server. Not a Single was not working. Commands like ls, cat, and vi was
 not working on the server. I was Getting Error: Command not found. 

I have manage to fix from below steps:-

1)Edited .bashrc file in home pasted below text in the file

PATH=$PATH:/home/amol/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
export PATH

2) After reloading .bashrc from command --> source ~/.bashrc   Comands started working. 

But  whenever i loggin in the server. I get below error:-


Last login: Tue May 14 10:33:46 2013 from 14.140.90.22
/usr/bin/env: bash: Permission denied
/usr/bin/env: bash: Permission denied
/usr/bin/env: bash: Permission denied
/usr/bin/env: bash: Permission denied
/usr/bin/env: bash: Permission denied
-bash: tar: command not found
-bash: grep: command not found
-bash: cat: command not found

I have searched in Google, But not getting exact solution. 

OS:- Ubuntu 10.04 (64 bit)

Below is .bashrc file 

[http://paste.ubuntu.com/5664287/](http://paste.ubuntu.com/5664287/)

Please Help.

---

### Post by PowerBarry43 on 2013-05-14
Hi there

I think I see your problem.. at the end of the .bashrc file you set the $PATH 4 separate times causing it to be a mess. to see what I mean run:

```
/bin/echo $PATH
```

to fix this delete lines 102-120 and add 

```

PATH=$PATH:/home/amol/bin:/home/amol/.rvm/bin
export PATH

```

to edit run

```
/usr/bin/vi ~/.bashrc
```

or if you don't like vi..

```
/usr/bin/nano ~/.bashrc
```

Barry

---

