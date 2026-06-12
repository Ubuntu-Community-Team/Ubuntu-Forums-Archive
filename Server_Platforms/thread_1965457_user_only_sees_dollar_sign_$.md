---
title: "user only sees dollar sign $"
date: 2012-04-25
forum: Server Platforms
---

### Post by ZenMasta on 2012-04-25
When I'm logged in as root my cli looks like this

root@ve:~# cd /home
root@ve:/home#


But if I su robbieb all I see is $ and it doesn't matter what folder I seem to be in. This is inconvenient for me because I prefer to be reminded which folder I am in.

su robbieb

$ cd /home
$ ls
html.zip  robbieb  testy
$

How can I change this?

---

### Post by rubylaser on 2012-04-25
You just need to make a .bash_profile and add a PS1 configuration option.  Here's what mine looks like.

```
export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
```
To implement this, you can just copy and paste this.

```
cd
echo "export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '" > .bash_profile
source .bash_profile
```

Your prompt would show up like this.
```
Rubylasers-MacBook-Pro ~/Downloads:
```

---

### Post by ZenMasta on 2012-04-26
This did not work for me

root@ve:/home/robbieb# su robbieb
$ cd
echo "export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '" > .bash_profile
source .bash_profile$ $
sh: source: not found
$ export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]:

now no matter which dir I'm in it looks like this

\[\e]0;\u@\h: \w\a\]\u@\h:\w$

---

### Post by rubylaser on 2012-04-26
This does work fine, I'm guessing that you had an error in your copying and pasting or you didn't understand what I meant.  Here's an example of me setting this up on an Ubuntu 10.04 Server that had no .bash_profile file previously.
```

root@svr-cc-mysql:~# cd
root@svr-cc-mysql:~# echo "export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '" > .bash_profile
root@svr-cc-mysql:~# source .bash_profile
**svr-cc-mysql ~:** cat .bash_profile 
export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '

```

Here are longer directions that will accomplish the same thing.  You need to change directories to your user's home directory.
```
cd
```
Remove any .bash_profile files that are wrong at this point.
```
rm .bash_profile
```
Then, you need to create a .bash_profile file.
```
touch .bash_profile
```
Open the file for editing.
```
nano .bash_profile
```
Then, you need to add this to the file.
```
export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
```
Finally, use this .bash_profile
```
source .bash_profile
```

---

### Post by azzamite on 2012-04-26
> **ZenMasta said:**
> This did not work for me
\[\e]0;\u@\h: \w\a\]\u@\h:\w$

Make sure your (default) shell is bash and not sh

```
me@server:~$ export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
server ~: sh
\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]:
```

And BTW, my system (bash) reads .bashrc and .profile... there is a copy of them in /etc/skel/, they have a line similar to the suggested by rubylaser.

---

### Post by ZenMasta on 2012-04-26
Whats the difference between bash and sh?

That must be the problem since when I do it on my non root user it says sh: source: not found

```
\[\e]0;\u@\h: \w\a\]\u@\h:\w$ source .bash_profile
sh: source: not found
\[\e]0;\u@\h: \w\a\]\u@\h:\w$
```

how do I switch to bash and sh and back etc.

---

### Post by ZenMasta on 2012-04-26
so after a touch of research I attempted to change shell

vi /etc/passwd
changed

    robbiebx:1001:1001::/home/robbieb:/bin/sh

c) change from /bin/sh to /bin/bash

so now my cli looks a little more normal..

```
robbieb@ve:~$ cd html
robbieb@ve:~/html$ cd app
robbieb@ve:~/html/app$ cd design
robbieb@ve:~/html/app/design$
```

Thanks much :)

---

### Post by rubylaser on 2012-04-26
Glad you got it figured out :)

Please mark the thread as solved via the Thread tools at the top of the page.

---

