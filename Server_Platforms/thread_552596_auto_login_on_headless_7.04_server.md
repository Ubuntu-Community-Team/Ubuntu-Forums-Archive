---
title: "auto login on headless 7.04 server"
date: 2007-09-16
forum: Server Platforms
---

### Post by neill on 2007-09-16
hi

i have a headless 7.04 server i use or backups (rsync over ssh from my main server)

every once in a while i need to reboot - dodgy electrics means i shut down on holidays for eg

the headless server has no keyboard and i want it to log in automatically on reboot

how can i do that ?

/neill

---

### Post by p_quarles on 2007-09-16
There are a couple different and basically unrelated things that could be meant by "log in automatically."

1) There's passwordless authentication using RSA/DSA encrypted keys.

2) It could also mean automatically opening a terminal+ssh session when you log in to the desktop.

To do the first, run the following command on the *desktop* computer (i.e., the one you want to log in from):
```
ssh-kegen -t rsa
```Choose the default key location. Leave the "passphrase" option blank (this is completely safe, unless you're doing this from a laptop that is at risk for theft).

Then:
```
ssh *your-user-name*@*server-static-IP-address* "cat >> ~/.ssh/authorized_keys" < ~/.ssh/id_rsa.pub
```To do the second, you'll need to write a bash script and add it to the list of startup programs.

Hope this helps.

---

### Post by neill on 2007-09-17
sorry for not being clear

when i use a desktop version of *buntu there are various ways i can avoid having to give a username and pw to arrive at the desktop automatically

when i use my server version and reboot i end up at a prompt asking for a login - then i enter my uname and pword and off we go

i want to automate the last bit - have the server login using my uname and pword automatically at reboot

does that make more sense ??

/neill

---

### Post by Wim Sturkenboom on 2007-09-17
Question: It's a headless server so why do you want to login?

I suggest that you setup ssh (telnet of it does not have to be secure) and use that to access your server remotely.

---

### Post by neill on 2007-09-17
can i ssh into a server that's not logged in ??

i have ssh setup and that's how i normally manage it - but only once it's logged on

i confess i'd never tried it otherwise

:oops:

---

### Post by p_quarles on 2007-09-17
> can i ssh into a server that's not logged in ??
Yes.

---

### Post by neill on 2007-09-17
> can i ssh into a server that's not logged in ?? .

> **p_quarles said:**
> Yes.

well that will ceratinly make life easier !!

:cool:

---

### Post by neill on 2007-09-18
it works !!!

thanks

---

### Post by Brazen on 2007-09-18
> **neill said:**
> it works !!!

thanks

Ha!  I'm coming late, but yeah when I read the first couple posts, I was like "why on earth would he want the console logged on?!"  As you realized you can, and should, use ssh from a workstation without the server console logged on.

---

