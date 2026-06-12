---
title: "execute post ssh login script"
date: 2008-06-28
forum: Security
---

### Post by cccccccc on 2008-06-28
hellou, i searched google almost 2 hours, but was not able to find a solution for this.
 i need to run exact script for each user who will connect to server via ssh. problem is, it can not be in .basrc (for bash for example). Reason is simple: it can be killed/changed... bud the script should be "hidden" and not visible to logged user.
 So how would I do that? Thanks and am very curious.

---

### Post by jpkotta on 2008-06-28
Run it from /etc/profile.

Read the INVOCATION section of the bash man page.  The shell you get from ssh is a login shell.

---

### Post by cccccccc on 2008-06-28
> **jpkotta said:**
> Run it from /etc/profile.

Read the INVOCATION section of the bash man page.  The shell you get from ssh is a login shell.

Thanks for help, but this almost I was searching for. In your man page, there was options --noprofile (calling directly for shell - I think this is feasible). So I can not use this for security reason, am I right? I thought that when using sftp I am also lost, but I find out, that /etc/bash.bashrc do the trick (althought it will run my secret script for all my console - neinnnn:()
can be --noprofile option called directly with ssh command?

---

### Post by brian_p on 2008-06-28
> **cccccccc said:**
> hellou, i searched google almost 2 hours, but was not able to find a solution for this.
 i need to run exact script for each user who will connect to server via ssh. problem is, it can not be in .basrc (for bash for example). Reason is simple: it can be killed/changed... bud the script should be "hidden" and not visible to logged user.
 So how would I do that? Thanks and am very curious.

Install sec. Visit the author's website and read the documentation there. Set up sec to monitor /var/log/auth.log and run your script.

---

### Post by ghostdog74 on 2008-06-28
check the [man page of sshd]("http://www.openbsd.org/cgi-bin/man.cgi?query=sshd"). you can use /.ssh/rc or using the example described under  AUTHORIZED_KEYS FILE FORMAT in the man page.

---

### Post by cccccccc on 2008-06-29
> **ghostdog74 said:**
> check the [man page of sshd]("http://www.openbsd.org/cgi-bin/man.cgi?query=sshd"). you can use /.ssh/rc or using the example described under  AUTHORIZED_KEYS FILE FORMAT in the man page.

thanks all. yes I found ssh/rc too, it doesn't cover sftp connections, very sad. but I will have a look at your second advice.
still, can anybody answer my question, if it is possible to make command like: ssh [email]user@server.com[/email] /bin/bash --noprofile --norc?  I saw it somewhere, but it doesn't work for me. if this doesn't work, I  could use /etc/bash.bashrc for certain user with if... condition (the monitored one)

---

