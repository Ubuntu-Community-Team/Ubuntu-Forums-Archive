---
title: "Need simple, insecure remote execution calls"
date: 2012-05-18
forum: Security
---

### Post by ticket on 2012-05-18
I have a LAN to which a mix of Linux and Windows (XP+) boxes will be attached. The LAN will not have internet access. I want to be able to write programs that can launch other programs on the other computers on the LAN without having to use login passwords.  E.g. the program code would be something like: 

```
system("SomeUtility remoteMachineId  remoteProgram.exe listOfProgramParams &");
```

Ideally the LAN setup / configuring of the computers should be very easy.

I have looked at SSH / Putty, but it appears I need to set up encryption keys and run an SSH agent, unless there is a way of configuring each machine to accept SSH commands without authentication and without using keys.

rexec also seems a candidate, but can it be set up to not require authentication?

Finally there is good old telnet. Can that be made to work?

---

### Post by CharlesA on 2012-05-18
Logins are there for a reason. If you make it so each machine can have programs launched without authentication, you are asking for trouble.

In any case SSH gets my vote.

---

### Post by Ms. Daisy on 2012-05-18
> **ticket said:**
> I have looked at SSH / Putty, but it appears I need to set up encryption keys and run an SSH agent, unless there is a way of configuring each machine to accept SSH commands without authentication and without using keys.
You don't have to configure ssh with keys, it's just a good idea.  But if you really wanted you could configure it with blank passwords & log in as root every time I suppose.

I guess follow the opposite of what this and its daughter wikis say:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by diesch on 2012-05-18
If you *really don't care about security* you can install  *openbsd-inetd* and use something like

```
6666 stream tcp nowait nobody /usr/sbin/tcpd /bin/bash
```in */etc/inetd.conf*.

That lets *everybody* run any Bash command line as user nobody on your box without authentication by writing it to port 6666/tcp, e.g. with

```
echo 'touch /tmp/foobar'| nc somebox.example.com 6666
```**Anyone**.  **Any Bash command line.  Without authentication**.

---

### Post by CharlesA on 2012-05-18
> **diesch said:**
> **Anyone**.  **Any Bash command line.  Without authentication**.

Thank you for the warning. :)

I would suggest ssh with a passphraseless key instead of alternative methods.

Having no authentication will lead to your system being owned.

---

### Post by HermanAB on 2012-05-20
Howdy,

Install Cygwin and OpenSSH Server on Windows.  Make a key without passphrase as suggested above.  Any other method is just looking for trouble and you will come to regret it.

---

### Post by ticket on 2012-05-21
Many thanks for the replies.

I did a bit more research and yes indeed, ssh (without a passphrase) is the best method.

I am assuming I can use Putty (from a windows box) in a command line the same way I can use the ssh command line from a linux box. Otherwise I
 guess I'll install cygwin on windows ...

---

### Post by CharlesA on 2012-05-21
> **ticket said:**
> 
I am assuming I can use Putty (from a windows box) in a command line the same way I can use the ssh command line from a linux box. Otherwise I
 guess I'll install cygwin on windows ...

You can use putty to use sftp or ssh itself, if you want to use rsync, you'd need cygwin.

---

