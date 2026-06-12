---
title: "SSH Login Script"
date: 2007-06-14
forum: Server Platforms
---

### Post by rennen01 on 2007-06-14
Does anyone have a script that can log into multiple SSH devices?

I am trying to pull configuration files and then tftp the config files to a remote tftp server on the same local network.

Any help would be great.

---

### Post by meatpan on 2007-06-14
Can you give a few more details about what you are trying to do?   Also, what do you mean by ssh device?  Are you trying to make a script to crawl across multiple machines via ssh?  If you are just trying to retrieve a file from each machine, you might want to investigate using the scp command instead (a relative of ssh, used for copying files).

For a task like this, consider using an ssh-agent.  This can save you the effort of typing in a password during each authentication phase.  Beware the risks of automatic authentication though ;)

---

### Post by craigp84 on 2007-06-14
Hi rennen01,

The preferred way to do this is via public key authentication as meatpan says above.

As a quick fix, here's an expect script (sudo apt-get install expect on the host you're running from) to ssh to a box, login via password authentication, then run a command and send output to stdout. You could call this from another script.

```

#!/usr/bin/env expect -f
#
# ssh-login.exp
# Craig Perry
# 19th Mar 2007
#
# Emulate an rsh in ssh, without pubkey authentication
#
# Usage:
#  ./ssh-login.exp <username> <password> <hostname> <command> [parameter1 [ parameter2 [ ... ]]]
#
set username [lrange $argv 0 0]
set password [lrange $argv 1 1]
set hostname [lrange $argv 2 2]
set command [lrange $argv 3 3]
set arguments [lrange $argv 4 9]

set timeout 60
match_max 1000

spawn ssh $username@$hostname $command $arguments

expect {
  "Are you sure you want to continue connecting (yes/no)? " {
    send -- "yes\r"
    expect "*?assword:*" {
      send -- "$password\r"
      send -- "\r"
    }
  }
  "*?assword:*" {
    send -- "$password\r"
    send -- "\r"
  }
}

expect eof

```

Hope this helps,

-c

---

### Post by rennen01 on 2007-06-14
Thanks for the responses.  For some clarification, the ssh devices are firewalls and the OSes on them do not have the ability to have anything installed besides an OS upgrade.  I am attempting to ssh into them from a Dapper Server, and then execute specific commands to tftp their configurations to another server.

I will take a look at the script above though and keep you posted.

---

### Post by craigp84 on 2007-06-15
Yeah you install expect on the dapper server, you don't need to touch the network devices.

-c

p.s. google for "rancid" Really Awesome Network ConfIg Differ

---

