---
title: "[SOLVED] aclexec directive in hosts.allow"
date: 2008-01-25
forum: Server Platforms
---

### Post by calraith on 2008-01-25
Has anyone here ever successfully used the aclexec directive in hosts.allow? I can't get it to deny any connections, even if I have the following in /etc/hosts.allow:
```
sshd : ALL : aclexec /path/to/script-that-only-exits-1
```I suppose I could have the script cat /bin/false > /dev/null, then killall -9 kittens before exit 1 if anyone reckons aclexec might finally get the hint after that? ;)

Anyway, according to the man page for hosts_options:
>        aclexec shell_command
              Execute,  in  a  child  process, the specified shell command, after performing the %<letter> expansions
              described in the hosts_access(5) manual page.  The command is executed with stdin,  stdout  and  stderr
              connected to the null device, so that it won't mess up the conversation with the client host. Example:

                 smtp : ALL : aclexec checkdnsbl %a

              executes,  in  a  background child process, the shell command "checkdnsbl %a" after replacing %a by the
              address of the remote host.

              The connection will be allowed or refused depending on whether the command returns a true or false exit
              status.
I know sshd is successfully querying hosts.allow and hosts.deny, because I can explicitly deny myself connectivity when I enter my IP address manually to test.  I also know that aclexec is successfully spawning its intended script, since I can include "echo 'something' >/tmp/logfile" within the target script and then view the expected output after an attempted connection to ssh.  It's just that aclexec seems to ignore exit code completely.  So as far as I can tell, I'm using the correct syntax.  Ain't I?

---

### Post by calraith on 2008-01-25
Well, apparently, as of tcpd version 7.6, aclexec doesn't conform to the documentation if it's called within hosts.allow.  Not sure whether this is a bug or not, but moving the directive to hosts.deny solved my problem.

When called from hosts.allow, aclexec will successfully spawn whatever process you intend, but it assumes "pass" regardless of the exit code dumped by said process.  Even if this odd behavior is a bug, it does encourage an admin to be more logical with his hosts.* directives. For instance, say you have a directive in hosts.allow such as the following:
```
ALL : ALL : aclexec scriptname %a
```Once that executes, regardless of exit 0 or exit 1, hosts.deny never gets parsed.  This is because aclexec passes either "allow" or "deny," with no further checks performed for the specified service.  You could deny or twist 127.0.0.1 in hosts.deny, but 127.0.0.1 would still be able to connect as soon as aclexec gets evaluated in hosts.allow. It's probably best to put any aclexec directives at the bottom of hosts.deny anyway.

---

### Post by calraith on 2008-02-08
Just for posterity, and since I couldn't find another checkdnsbl appropriate for aclexec in a Google search, I'm attaching my checkdnsbl script to this post.  Go nuts with it.

---

