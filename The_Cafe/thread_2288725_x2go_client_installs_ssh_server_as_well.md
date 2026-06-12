---
title: "x2go client installs ssh server as well?"
date: 2015-07-29
forum: The Cafe
---

### Post by mr-woof on 2015-07-29
Hi all,

I've been playing around with X2go lately, I installed the server and the xfce desktop on a test ssh machine with no problems. I then installed the x2go client via the software centre on ubuntu mate, no problems I thought. I can connect and it works fine, but...

I'd forgotten what IP address the test server was on, so I ran a nmap scan of the network and found two ssh servers. The x2go client had installed ssh server on my laptop without me knowing, I didn't notice any tickboxes etc.

Anyone else come across this? Surely this is a bit naughty, as you could connect to ssh with your username and password on the laptop?

---

### Post by TheFu on 2015-07-29
X2go uses reverse ssh connections to make certain features work - file sharing, printing and perhaps remote audio come to mind.  

BTW - every Unix system I work on has openssh-server installed as a matter of routine. How else can I remote in to deal with any issues - like when the GUI locks up but the OS is just fine?  BTW, I don't allow passwords for ssh connections and always, always, always have fail2ban installed and working too.

On a Unix system, security is the responsibility of the admin. If you don't like it, you can disable the ssh server, but then you'll need to live with the repercussions.

---

### Post by mr-woof on 2015-07-30
Hi,

I think you've missed the point of what I'm trying to say, I appreciate servers needing ssh server installing for remote access but why does the client install it on a laptop?

---

### Post by TheFu on 2015-07-30
Sorry - I thought you were asking a question, so I tried to answer.  Was that a rhetorical question?

I'm sure the x2go people would love a patch to make everything work without needing the server-to-client ssh tunnel. Design decisions happen for all sorts of reasons. Some are brilliant and others are simply because the team had X number of days to solve an issue. Sometimes it is because code was inherited and for backwards compatibility will never be changed. 

We will probably never know the real answer.

---

