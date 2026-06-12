---
title: "[SOLVED] visudo syntax error?"
date: 2007-07-07
forum: Server Platforms
---

### Post by the music man on 2007-07-07
Hi, i'm trying to add this line to my sudoers file (with visudo of course):```
server ALL=(ALL) NOPASSWD: firestarter, proftpd, gproftpd
```
but i'm getting syntax error when i try to save it. When i delete the line, i can save the file without problems. I want to be able to admin the firewall and FTP server with the user 'server' without entering passwords all the time.  I checked it so many times with help of the sudoers man page but i couldn't find the mistake. I also tried it without the NOPASSWD: and the commands. What's wrong with the line?

---

### Post by Mr. C. on 2007-07-07
The syntax you want is this:

```
server  ALL = NOPASSWD: firestarter, proftpd, gproftpd
```

This says, user **server** can run on **ALL** hosts with **NOPASSWD** the commands **firestarter, proftpd, gproftpd**

Simplistically, the spec looks like:

```
*user* *host* **=** *commands*
```

and *commands* can have a *user-to-run-as* and optional *flags*, so it looks a bit like:

```
*user* *host* **=** **(***user-to-run-as***)** *flags***:** *commands*
```

and flag in your case is **NOPASSWD:**.  The *user-to-run-as* defaults to **root**, so it can be left out, but specifically it would look like :

```
server  ALL = (root) NOPASSWD: firestarter, proftpd, gproftpd
```

MrC

---

### Post by the music man on 2007-07-09
I solved the problem, i need to add the application paths to the line. Like this: ```
server ALL = NOPASSWD: /usr/sbin/firestarter, /usr/sbin/proftpd, /usr/sbin/gproftpd
```

---

### Post by the music man on 2007-07-10
Now another problem, i have this line in sudoers, but the NOPASSWD: tag doesn't work. When i do sudo firestarter or sudo proftpd or sudo gproftpd, it still asks for a password. Why? How do i fix this?

---

### Post by Mr. C. on 2007-07-10
Which user are you when you run the command ?

Show your commands and evidence.  Show which user you are with the "id" command.

MrC

---

### Post by the music man on 2007-07-11
> **Mr. C. said:**
> Which user are you when you run the command ?

Show your commands and evidence.  Show which user you are with the "id" command.

MrC
```

login as: server
server@192.168.2.101's password:
Linux server 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i586
*(...warranty messages...)*
Last login: Wed Jul 11 12:29:19 2007

server@server:~$ id
uid=1000(server) gid=1000(server) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),109(lpadmin),110(admin),1000(server)

server@server:~$ sudo firestarter
**Password:**

(firestarter:4600): Gtk-WARNING **: cannot open display:
server@server:~$

```

I get the gtk-warning because i did this through SSH with no gui. But that's not the problem, you can see that sudo asks for a password.
Here's the sudoers line again: ```
server ALL = NOPASSWD: /usr/sbin/firestarter, /usr/sbin/proftpd, /usr/sbin/gproftpd
```
I don't get syntax errors when i quit visudo.

---

### Post by Mr. C. on 2007-07-11
This may be an exact match issue with the command name.

Try the command's full path, as you specified it in the sudoers file.

For the GTK error, unset the DISPLAY environment variable to avoid the Gtk-WARNING.

```
unset DISPLAY
```

MrC

---

### Post by the music man on 2007-07-12
Still doesn't work :(
```
server@server:~$ id
uid=1000(server) gid=1000(server) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),109(lpadmin),110(admin),1000(server)
server@server:~$ sudo **/usr/sbin/firestarter**
**Password:**
/bin/sh: /usr/bin/esd: not found
Firewall started

```
:confused:

---

