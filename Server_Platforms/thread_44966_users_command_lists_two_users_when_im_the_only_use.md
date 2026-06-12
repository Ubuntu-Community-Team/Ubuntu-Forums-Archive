---
title: "users command lists two users when im the only user of the system"
date: 2005-06-28
forum: Server Platforms
---

### Post by sal on 2005-06-28
06-28-05
just a quick question:
when i go to the terminal and issue the command: users

it lists my user name twice as if there are two users loged on at once.

it looks like this:
username username (where username would be my name)
is this normal? if not what could it mean and how could i check it out and find out whats going on and fix it?

thanks in advance

---

### Post by fdoving on 2005-06-28
That is normal.
When ever you execute a terminal program with a login shell it is considerd a login by the system. You could try to open more terminals and issue the command again.

- Frode

---

### Post by sal on 2005-06-28
06-28-05
thanks for the fast response on this one.
i've been a windows user for years and have played with linux for about a year now, but, after hearing about ubuntu, i switched over to it with a dualboot set up. 
at first i was switching btwn. windows and ubuntu every hour, but now i've been in ubuntu for a week strait and can't think of a reason to go into windows yet.
i just wanted to make sure everything was on the up and up after i issued the users command and saw myself listed twice.

it's funny, in only the one week that i have used only linux, when doing some thing on the system, i find myself thinking, "why can't (such and such) be this easy in windows?"

thanks for the help.

---

### Post by NixMonk on 2005-06-30
I would recommend to use the `who` command over `users`

output of /usr/bin/who
username  :0           Jun 20 08:12
username  pts/0        Jun 28 08:37 (:0.0)
username  pts/1        Jun 28 11:42 (:0.0)
username  pts/2        Jun 28 14:40 (:0.0)

Here you can see the user 'username' is logged into the system and has one session open with 3  pseudo-terminal sessions open. Normally a pts session is just another terminal window open. One thing to note is the :0.0 this tells you that all these sessions are local to the system. If someone is logged in via ssh remotely you will see something similar to:

username  pts/0        Jun 28 08:37 ( 10.0.0.10 )

It may show the hostname in place of the IP address if DNS can perform reverse lookup.

---

### Post by ArBaDaCarBa on 2005-06-30
And even better, 'w' tells you so much more than 'users' or 'who'...

---

### Post by sal on 2005-06-30
thanks for all the help on it.
the who an w commands are going into my head as i write this.

---

