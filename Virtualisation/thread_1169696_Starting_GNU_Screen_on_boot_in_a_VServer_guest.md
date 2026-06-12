---
title: "Starting GNU Screen on boot in a VServer guest"
date: 2009-05-25
forum: Virtualisation
---

### Post by Soepstengel on 2009-05-25
Hello all,


I am running a Debian Lenny VServer host which has currently only one guest machine. The guest runs Ubuntu Intrepid and has the applications "HellaNZB" and "(GNU) Screen" installed. My goal is to start HellaNZB in a Screen session and set the owner of that to the user "administrator" everytime the guest starts. That way I don't have to manually SSH into to guest, open a Screen session and start HellaNZB.

I made a "/etc/init.d/hellanzb" script, chmodded it with "chmod +x /etc/init.d/hellanzb" and executed "update-rc.d /etc/init.d/hellanzb defaults" to make it start on boot. 

The contents of "/etc/init.d/hellanzb":
```
#!/bin/bash
#
### BEGIN INIT INFO
# Provides: hellanzb
# Required-Start: $network $local_fs $remote_fs $screen-cleanup $devpts $mountkernfs $udev $mountdevsubfs $tmpfs
# Required-Stop: 
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start daemon at boot time
# Description: Enable service provided by daemon.
### END INIT INFO


NAME=hellanzb
HELLAUSER=administrator

trap "" 1
export LANG=C

case "$1" in
  start)
    echo -ne "Starting $NAME"
    su -c '/usr/bin/screen -L -S $NAME -d -m hellanzb > /tmp/aaa 2> /tmp/bbb' $HELLAUSER
    echo "."
    ;;

  stop)
    killall hellanzb.py
    echo "."
    ;;

  reload)
    echo "."
    ;;

  reload-modules)
    echo "."
    ;;

  restart)
#    $0 reload-modules
    $0 stop
    $0 start
    ;;

  force-reload)
    $0 reload-modules
    ;;

  *)
    echo "Usage: /etc/init.d/$NAME start|stop|reload|reload-modules|force-reload|restart}"
    exit 1
    ;;
esac

exit 0
```

The line that is important is this line:
```
su -c '/usr/bin/screen -S $NAME -d -m hellanzb > /tmp/aaa 2> /tmp/bbb' $HELLAUSER
```

"/tmp/aaa" and "/tmp/bbb" will be replaced with "/dev/null", but this way I can see the output.

Also the following line is a bit ugly. I don't really know what is required and what not, so I probably added a bunch of things which can be removed:
```
# Required-Start: $network $local_fs $remote_fs $screen-cleanup $devpts $mountkernfs $udev $mountdevsubfs $tmpfs
```

The problem is is that it doesn't start and I don't know how to solve it. The contents of "/tmp/aaa" after the system is done booting:
```
Cannot access '/dev/pts/0': No such file or directory
```

So. The system boots and tries to start a Screen session. But, if I am correctly, screen reports that it cannot start a session because "/dev/pts/0" is not found. I figured this might be because "/dev" is not mounted yet, but adding "$devpts" to the requirements of the script didn't solve the problem.

When I manually execute the following command:
```
sudo /etc/init.d/hellanzb start
```

... in a SSH session when the guest is fully started the "/tmp/aaa" file looks like this:
```
Cannot open your terminal '/dev/pts/1' - please check.
```

The command "ls -l /dev/pts" gives the output:
```
root@guesttest:/tmp# ls -l /dev/pts                 
total 0
crw------- 1 root tty 136, 1 May 25 17:29 1

```

When I chmod "/dev/pts/1" so it is owned by the user "administrator" the script works perfectly. But since the contents of "/tmp/aaa" give an different error at boot this will not solve that problem.

I don't know what I am doing wrong or how I can solve this problem. If anyone can put me back in the right direction I would really appreciate it.

---

### Post by Soepstengel on 2009-05-29
* little bump *

---

### Post by Soepstengel on 2009-06-08
I still didn't manage to solve the problem, any ideas are more then welcome.

---

### Post by bodhi.zazen on 2009-06-08
Not sure why is not working for you.

It "works for me" on openvz, I just put a screen command in /etc/rc/local

> screen -s "test" -d -m

When I start the machine screen is running as expected.

Suggestions :

1. Is screen working in your guest ?

2. Can you start screen without ssh into the machine ? On openvz one simply

```
vzctrl exec 101 screen -s "test" -d -m
```

3. Why are you writing a fancy init script for a simple command such as screen ? Try just putting your screen line in rc.local. 

I mean your script seems to be a good one, but it is more complex then it needs to be, declaring variables and what not for what at the end of the day is a "one liner" (no offense).

At any rate, before putting the command in an init script, make sure it works from a terminal.


Hopefully one or another of the tips will lead to a solution.

---

### Post by Soepstengel on 2009-06-08
Thank you for your reply, it was very useful for me. I managed to almost solve the problem. I am not really an advanced user and I didn't knew about the /etc/rc.local file. Adding the following (same) line to the file makes a screen session at boot.

```
su -c '/usr/bin/screen -L -S hellanzb -d -m hellanzb > /dev/null 2> /dev/null' administrator
```

After the guest system has booted there is a screen session called "hellanzb" which is owned by the user "administrator". But when I try to enter it ("screen -R hellanzb") I get the following error:

```
Cannot open your terminal '/dev/pts/2' - please check.
```

"ls -l /dev/pts/2" shows:

```
crw------- 1 root tty 136, 2 Jun  8 20:51 /dev/pts/2
```

When I change the owner of "/dev/pts/2" to "administrator" I can enter the screen session without any problem but after a system restart I get the same error. Is there an easy way to solve this?


Now the answers to your suggestions, it might not be relative to the new problem anymore, but it might understand things better (?).

> 1. Is screen working in your guest ?
Yes, screen is working without a problem.

> 2. Can you start screen without ssh into the machine ? On openvz one simply (...)
Yes, that also worked. I moved my lazy *** from the chair to the VServer host machine and used "vserver guesttest exec (...)" to execute the "screen" command.

> 3. Why are you writing a fancy init script for a simple command such as screen ? Try just putting your screen line in rc.local.
Well, I didn't knew about the /etc/rc.local file (i'm not completely new to linux/ubuntu, but I am new to start-up scripts/sessions/etc), but I knew about daemons and thought that would be the best way to make it start on boot.

Besides the little rights problem it works now, thank you for that. If you have any idea on how I can solve the "new" problem I would be very thankful.

---

### Post by bodhi.zazen on 2009-06-08
Hack it :)

in /etc/rc.local change the permissions (right after your screen command)

su -c screen .....
chown ...

exit 0

---

### Post by Soepstengel on 2009-06-08
> **bodhi.zazen said:**
> Hack it :)

in /etc/rc.local change the permissions (right after your screen command)

su -c screen .....
chown ...

exit 0

How evil, lol. But unfortunately that doesn't work. The log shows this:

```
chown: cannot access `/dev/pts/2': No such file or directory
```

It exists when the guest is fully booted, so I guess that "/dev/pts" is not yet available when "/etc/rc.local" is executed? I might be wrong, don't know anything about that but that would be my best guess.

The error is the same error as I get in my "daemon solution", so i'm back where I started. Any idea's?

---

### Post by bodhi.zazen on 2009-06-08
Let the guest boot

then run /ect/rc.local

(you run it like any other program , just put /etc/rc.local in the terminal).

If it works, you clearly need a sleep

sleep 10
su - screen ....
chown ...

---

### Post by Soepstengel on 2009-06-09
> **bodhi.zazen said:**
> Let the guest boot

then run /ect/rc.local

(you run it like any other program , just put /etc/rc.local in the terminal).

If it works, you clearly need a sleep

sleep 10
su - screen ....
chown ...

Thank you for your reply, but sleep didn't helped me. My /etc/rc.local file contains these three lines:

```
sleep 10
su -c '/usr/bin/screen -L -S hellanzb -d -m hellanzb > /dev/null 2> /dev/null' administrator
chown administrator:administrator /dev/pts/2
```

When booted the log shows this error:

```
chown: cannot access `/dev/pts/2': No such file or directory
```

Screen is started and a session is made, but I cannot access it. I get this error:

```
Cannot open your terminal '/dev/pts/2' - please check.
```

When I executed "/etc/rc.local" manually it runs without any error and afterwards I am able to access screen ("screen -r hellanzb") and I see hellanzb running fine. It starts without a problem, I just cannot access it because I ("administrator") don't have enough rights to access it. The sleep didn't helped, unfortunately.

I really appreciate your help, I wouldn't have come this far on my own. If it's hopeless (me or doing this in vserver) just tell me, any idea's are always welcome.

---

### Post by Soepstengel on 2009-06-09
By the way, is there any later stadium to run a command?

Maybe I am thinking wrong, but if I can execute the command "chown administrator:administrator /dev/pts/2" at the very last point then /dev/pts/2 should be available. Or not?

---

### Post by bodhi.zazen on 2009-06-09
It will slow your boot time, try moving your sleep between the screen command and the chown command.

If that fails, try increasing the sleep time.

/etc/rc/local is, in theory, supposed to run last in the boot scripts.

The other option is to simply put your commands into a ssh key

with ssh keys you can force commands.

See :

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

for an example of how it works. Simply start the screen session with a key.

---

### Post by Soepstengel on 2009-06-09
Moving the sleep command didn't worked. Increasing it to a 120 second sleep also didn't solve the problem.

I'm going to set up key based SSH authentication and read your blog entry tomorrow, it's time for some sleep now.

---

### Post by Soepstengel on 2009-06-12
Thank you very much, it works perfectly now :D

---

### Post by bodhi.zazen on 2009-06-12
> **Soepstengel said:**
> Thank you very much, it works perfectly now :D

Awesome :)

For the benefit of others would mind confirming your solution (I assume it was a ssh key ?)

---

### Post by Soepstengel on 2009-06-12
> **bodhi.zazen said:**
> Awesome :)

For the benefit of others would mind confirming your solution (I assume it was a ssh key ?)

Ofcourse, sorry I forgot about that. As previously said moving the sleep command in the /etc/rc.local file didn't worked so I enabled key based authentication in the SSHd configuration file and moved my key (I already had one) to the VServer Guest. I modified it and added the command (to chown the rights) to it. That did the trick. When I SSH into the VServer guest I can enter the screen session correctly without any problem.

Thank you for your help and I hope this will help other people as well.

---

### Post by bodhi.zazen on 2009-06-12
Thank you :)

ssh keys FTW

---

