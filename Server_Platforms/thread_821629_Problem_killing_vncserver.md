---
title: "Problem killing vncserver"
date: 2008-06-07
forum: Server Platforms
---

### Post by melo1705 on 2008-06-07
Ok, Iam having some issues when trying to run $ tightvncserver -kill :1

It is giving me the following output:

Can't find file /home/user/.vnc/ubuntu-pc:1.pid
You'll have to kill the Xtightvnc process manually

If I manually run the following:

$ vncserver

It outputs the following and Iam able to connect from a remote location using :2

Found /usr/share/tightvnc-java for http connections.
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is ubuntu-pc:2

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/ubuntu-pc:2.log

But I have to run the $ vncserver manually for it to create the :2 session.

Still, I am not able to kill or connect using the :1 session.

Right now there is no VNC session open as I killed :2 and this is the output of some commands that I have read:

user@ubuntu-pc:~$ netstat -n | grep 590[0-9]
unix  3      [ ]         STREAM     CONNECTED     15909    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15908  

user@ubuntu-pc:~$ ps -ef | grep vnc
user     7004  6734  0 11:29 pts/0    00:00:00 grep vnc

user@ubuntu-pc:~$ ls -l ~/.vnc
total 20
-rw------- 1 user user    8 2008-06-07 02:41 passwd
-rw-r--r-- 1 user user 4062 2008-06-07 02:47 ubuntu-pc:1.log
-rw-r--r-- 1 user user 1978 2008-06-07 10:43 ubuntu-pc:2.log
-rwxr-xr-x 1 user user  135 2008-06-07 11:02 xstartup
-rw-r--r-- 1 user user  296 2008-06-07 11:02 xstartup.original

user@ubuntu-pc:~$ ps -e -f | grep -i vnc
user     7007  6734  0 11:31 pts/0    00:00:00 grep -i vnc

user@ubuntu-pc:~$ ps -ef | grep -i vnc
user     7009  6734  0 11:32 pts/0    00:00:00 grep -i vnc

I have give up trying to fix this by myself. So, any help will be greatly appreciated since Iam a noob in here.

Thanks in advanced.

---

### Post by harak on 2008-09-07
May be this is too late for you. I had the same problem for minute ago. By any chance have you installed "xinetd". Uninstall and reboot. You should be able to run vncserver :1 and kill it. May be there is some other way out but I am not much of an expert either.

---

### Post by harak on 2008-09-07
If you still get the error just delete the .vnc* folders. I also deleted .fluxbox files. I know Iam overdoing it. I am still to figure out which one exactly is giving me trouble

---

### Post by chuckyp on 2008-09-20
The problem is that the vnc server crashed and it no longer has a pid file in the ~/.vnc.  Even though there isn't a pid running it looks at the files in /tmp and thinks that there is a vncserver running on :1 because of the Xlock files.  Just delete all the files in /tmp ex:

```

$sudo rm -rf /tmp/*
$sudo rm -rf /tmp/.*

```

Then you should be able to start vncserver again. I've noticed that this behavior happens when you try to connect via a java browser when you are using tightvnc-java. It immediately crashes the vnc server.

---

