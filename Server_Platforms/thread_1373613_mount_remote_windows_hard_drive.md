---
title: "mount remote windows hard drive"
date: 2010-01-05
forum: Server Platforms
---

### Post by joborohe on 2010-01-05
Alright,

this hard drive that I need to mount is on a windows machine, in a different town.

What would be the best approach for this?

---

### Post by litspliff on 2010-01-05
vpn/smb would be my approach, but there may be better ones.
this way it's encrypted.

---

### Post by HermanAB on 2010-01-06
Uhmmm, I'd use Cygwin and SSH.  The problem is that you would want a system that can easily re-establish a connection when it goes down and an ad-hoc VPN like you get with SSH/SCP is good for that.

---

### Post by joborohe on 2010-01-06
im not familiar with cygwin, how do we use it?

---

### Post by BkkBonanza on 2010-01-06
If you install the windows version of OpenSSH it will install just the cygwin dlls you need with it. Once you have OpenSSH installed on windows you can ssh to the machine from anywhere and use various methods to get to the files. 

Probably the nicest approach is to install "sshfs" on the Linux system. It allows you to mount a remote filesystem via ssh so it appears local.

Another simpler approach if you just need temporary access is to put 

ssh://user@win_pc_ip_name/path_to_files

into the nautilus address bar and it will let you browse and work with the remote files.

OpenSSH is a pretty quick/easy install onto Windows so this is likely the quickest most flexible way to get going.

There are a few variants for windows but I found this one very easy,

[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

---

