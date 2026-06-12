---
title: "How to run multiple terminals with AWS and PuTTy?"
date: 2021-04-09
forum: Server Platforms
---

### Post by forumate on 2021-04-09
Hello,

I installed a package and it has its own console. inside that console I need to run a command to start sync some information and it takes some time

how can I launch another terminal in parallel so that I can keep working on my server?

I connect to my Ubuntu 20.04 server from Windows via SSH with PuTTy (Server is on AWS EC2)

Thanks

---

### Post by TheFu on 2021-04-09
What is a "console"?  In the Unix world, it means something VERY, VERY, specific.  ssh isn't a console.

Is this a trick question?  Start another putty client?  This seems to be a putty question.  I can assure you it isn't a limit on the Ubuntu side.  I've seen systems with thousands of concurrent user logins over ssh.  

Or use a Linux workstation (or a small Linux virtual machine) and just ssh into the remote system as many times as you like using ssh.  Windows makes so many things that are trivial on Linux, hard. I commonly have multiple xterms connected via ssh to different and the same system daily, all day. Right now, I have 12 xterms connected to different systems. Some are to local servers, a few are thousands of miles away.

An example of things that Windows makes hard, but it easy on Unix:
 Do you save all the connection settings for each remote system in Putty because you don't want to remember odd DNS names or IPs?  
 On any Unix system, there is a ~/.ssh/config file which can be used to create aliases for any/all ssh connections that are used by **every** ssh-based tool.  It is just a text file, so trivial to edit, copy, backup, share.  No time wasted in a GUI point-click-type, Save; Repeat.
Much more efficient.
```
host joeb
 user u42956
 hostname joeb.dyndns.org
 port 2280

host joeb-r
 user root
 hostname joeb.dyndns.org
 port 2280

```
**ssh joeb-r** gets expanded for all ssh/scp/sftp/rsync and most backup tools into 
```
ssh -p 2280 -l root joeb.dyndns.org
```
**ssh joeb** gets expanded into
```
ssh -p 2280 -l u42956 joeb.dyndns.org
```
The hostname entry could be an IP address.

I don't use AWS, but ssh is ssh.  I've seen the long AWS DNS names.  I'd want my host-alias to be something short - say **aws-db1**

If you have 1 or 500 systems, it is easy.  Then you can use tools like Ansible to handle them in a similar way with 1 command.  Or your cssh (ClusterSSH) or create tiny bash scripts to do stuff if you don't want to use Ansible.  This is all very common.

Many people use **tmux** or **screen** for long running commands.  I just use what's called "job control", provided the first command isn't spewing junk to the ssh session.  If it does, then I'll use a batch tool like Task Spooler or 'batch' to run tasks in a queue.  If I need for things to happen at a specific time, then it is 'at' or cron to schedule when it will run.  Today, on one of my systems, the atq looks like this:
```
$ atq
2159    Fri Apr  9 13:58:00 2021 a thefu
2167    Sat Apr 10 06:28:00 2021 a thefu
2163    Fri Apr  9 17:58:00 2021 a thefu
2169    Sun Apr 11 19:58:00 2021 a thefu
2166    Fri Apr  9 19:58:00 2021 a thefu
2170    Sun Apr 11 21:58:00 2021 a thefu
2165    Fri Apr  9 19:58:00 2021 a thefu
2158    Fri Apr  9 12:58:00 2021 a thefu
2161    Fri Apr  9 15:58:00 2021 a thefu
2160    Fri Apr  9 14:58:00 2021 a thefu
2168    Sat Apr 10 19:58:00 2021 a thefu
2155    Fri Apr  9 09:58:00 2021 = thefu
2173    Sun Apr 11 18:58:00 2021 a thefu
2156    Fri Apr  9 10:58:00 2021 a thefu
2162    Fri Apr  9 16:58:00 2021 a thefu
2164    Fri Apr  9 18:58:00 2021 a thefu
2162    Fri Apr  9 16:58:00 2021 a thefu
2164    Fri Apr  9 18:58:00 2021 a thefu
2157    Fri Apr  9 11:58:00 2021 a thefu
```
One job is running now.  I can sort that output easily.  I have an alias 
```
$ ats
2155    Fri Apr  9 09:58:00 2021 = thefu
2156    Fri Apr  9 10:58:00 2021 a thefu
2157    Fri Apr  9 11:58:00 2021 a thefu
2158    Fri Apr  9 12:58:00 2021 a thefu
....
```
The sort is : ```
atq |sort -hk4 -k5
```

Job control is usually a chapter in any beginning Unix book.  It works exactly the same on Linux.  fg, bg, jobs, are the common shell built-in commands.   That means they are part of sh, ksh, bash, tcsh, csh, and probably fish, pash, zsh, too. Pick up a 25 yr old copy of Unix Power Tools [https://www.amazon.com/Power-Tools-Third-Shelley-Powers/dp/0596003307](https://www.amazon.com/Power-Tools-Third-Shelley-Powers/dp/0596003307) from a thrift bookstore for $0.50. The stuff inside there is still true, only it won't mention bash, since bash didn't exist.  Perhaps the newer version from 2002 has bash?  IDK.
The great thing about O'Reilly books is they make both reference titles (which are dry) and How-To titles which put many different tools together into solutions to help the mind start learning to think in the Unix way.
For example, here's a reference book full of facts and what options work for commands: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  It is a good book. I've used versions of it in my Linux classes.  However, it doesn't show how to solve a problem using 3+ simple commands to get a solution.  Learning to think the Linux way: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

Sorry if my assumptions about you being new to Linux aren't true.  Hopefully, someone else can find some use in my words above if they don't help you.  I find the "what to type" questions boring, but the "Why" questions much more interesting.  When I was new to Unix, it seemed there was a conspiracy to make things harder than necessary.  As I learned more and more, I came to the realization that they weren't all idiots. Actually, they were geniuses.  They build a system that was simple, elegant, and could run efficiently on almost any hardware in the world - and off the world too. Whenever something seems hard, I figure I've misunderstood something or asked a not-so-great question.  There is almost always a better way to accomplish my goal than what I believed was the answer.

---

### Post by LHammonds on 2021-04-10
If by console you mean something like starting an app and it consumes the console until completed but you want it running in the background, then you have several options available to you.

If you just want a fire-n-forget, then issue the app command using this command:
```
nohup myapp &
```
nohup means it will continue to run the app even if you lose your putty session or logout.  The ampersand at the end tells it to run in the background.

If you need to start the app but have the ability to get back into it and then get back out, then "screen" is a perfect utility for this.  Example:
```
screen -d -m -S MySessionName -t MyTitleName MyAppCommand
```

To list screen sessions, type:
```
screen -list
```

Reattach to a session typing something like this:
```
screen -r MySessionName
```

While inside the screen session and you want to push it back to the background, press this key sequence:
```
CTRL+a d
```
Pressing CTRL+a tells screen you want to do something with it, d says to detach.

**EDIT:** You could also just start another PuTTY session.  There's nothing to prevent you from having 10 PuTTY sessions at the same time and even for the same user.

LHammonds

---

