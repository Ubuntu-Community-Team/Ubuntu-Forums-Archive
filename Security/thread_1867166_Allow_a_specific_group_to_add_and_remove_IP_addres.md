---
title: "Allow a specific group to add and remove IP addresses."
date: 2011-10-22
forum: Security
---

### Post by peely on 2011-10-22
Hi,

I have a bash script which I would prefer to run as a user with low security as it is called remotely by another machine, however the script amongst other things needs to add and delete IP addresses.

If a non-root user executes something like "ip addr add 192.168.1.10/24 dev eth0" then the response is something like "RTNETLINK answers: Operation not permitted".

Is there a way I can authorise a group to have access to creating and deleting IP addresses?



Thanks,



Neil.

---

### Post by CharlesA on 2011-10-22
I guess you could always add that user to the sudoers file and have them only allowed to run that specific command.

---

### Post by peely on 2011-10-23
> **CharlesA said:**
> I guess you could always add that user to the sudoers file and have them only allowed to run that specific command.

The command is called from an automated task as part of a server to server failover, so I don't think I could do that with sudoers.

Thanks though.


Neil.

---

### Post by CharlesA on 2011-10-23
Ah ok.

Not sure how you'd get it to run properly without running it as root then.

---

### Post by Jonathan L on 2011-10-23
> **peely said:**
> 
I have a bash script which I would prefer to run as a user with low security as it is called remotely by another machine, however the script amongst other things needs to add and delete IP addresses.

If a non-root user executes something like "ip addr add 192.168.1.10/24 dev eth0" then the response is something like "RTNETLINK answers: Operation not permitted".

Is there a way I can authorise a group to have access to creating and deleting IP addresses?


Hi Neil

How about these?

_**Method 1, Root's crontab**_

If you can wait a minute for the command to execute, the easiest I can think of would be that the requsting machine puts a file in a particular location which is the request; that location is controlled by group privilege to the appropriate users.  Then root's crontab looks in that location for a legitimate request.

This is the drop directory
```
sudo mkdir /var/handover
sudo chmod 770 /var/handover
sudo chgrp handymen /var/handover
```Someone in group 'handymen' makes a file
```
echo 192.168.1.10/24 > /var/handover/please
```root's crontab does something like this every minute.  The awk is to pick out the first address/prefixlength line, and only allow well constructed lines
```
if [ -e /var/handover/please ]; then
  addr="`awk '/^[0-9]+\.[0-9+\.[0-9]+\.[0-9]+\/[0-9]+$/ {print $1; exit;}'' /var/handover/please`"
  if [ "$addr" != "" ]; then
    ip addr add $addr dev eth0
  fi
  rm -f /var/handover/please
fi
```_**Method 2, setuid-root program**_

You have a setuid program which does what you want.  Here, for example, is one in C which looks at a private file (though I hope it's obvious how you'd make it do "ip addr ...", and I might add that if you haven't done any C, this method is probably not for you.)

```
#include <stdio.h>
#include <unistd.h>

int
main(int argc, char *argv[]) {
    printf("uid=%d\n", getuid());
    execl("/bin/cat", "cat", "/etc/shadow", (const char *)NULL);
    err(1, "Exec failed");
}
```You compile and make the executable setuid-root with
```
make doit
```You'll see it behaves differently when you:
```
./doit
sudo ./doit
```Once you're satisfied the program does exactly what you want, you make it set uid root (so the executing image is owned by root), and executabel by the group who are allowed:
```
sudo chown root:handymen doit
sudo chmod u=rxs,g=x,o= doit

-r-s--x--- 1 root handymen 7250 2011-10-23 17:31 doit


```Now you can run it as a normal user but have super user privileges.  It's a bit like having a custom "sudo" which only does the exact command you want.  Be careful though with this kind of program, you might let yourself in for more trouble that you'd anticipate if it gets at all complex or lets in very much information from the user.

_**Method 3, change /bin/ip to setuid-root**_

Lastly, if you want something quick but dirty, you could change the ownership of /bin/ip to be setuid root and the group you want:
```
sudo chown root:handymen /bin/ip
sudo chmod u=rxs,g=x,o= /bin/ip
```This of course means no normal user could run 'ip', which they might reasonably want do to look at routes or the current IP addreses.  Not quite as dirty: you could make a copy of /bin/ip which you make setuid-root, group-execute, world-unreadable.



All in all, I'd recommend the crontab approach as it's much less prone to security problems.  Making safe setuid programs can be tricky, but nonetheless is the classic solution to the problem you describe.  I wouldn't change the permissions of anything from their standard ones except in extreme circumstances.

Hope that helps

Kind regards,
Jonathan

---

### Post by peely on 2011-10-28
Thanks all, especially Jonathan.

I came to terms with the fact I'd need a local process monitoring trigger files anyhow, due to other aspects of the process flow. I've implemented that and all is well.


Thanks,


Neil.

---

### Post by CharlesA on 2011-10-28
Glad you were able to figure it out. :)

---

