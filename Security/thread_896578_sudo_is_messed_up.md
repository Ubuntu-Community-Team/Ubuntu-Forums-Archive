---
title: "sudo is messed up"
date: 2008-08-21
forum: Security
---

### Post by gkaragoulis on 2008-08-21
I just restarted my Ubuntu computer and when it came back up 'sudo' was screwed up.  What I mean by that, is when I type "sudo whoami" it returns a couple blank lines, and definitely not root.  'sudo su' doesn't work either, because it tries to make a blank home directory ('') and fails.

I tried to fix it any way I knew how, which included trying to "source" the /etc/passwd file (. /etc/passwd)  After throwing a bunch of bash errors, somehow that worked and now I can 'sudo whoami' and get root.  My question is, why does sourcing /etc/passwd work?  And is this the right way to fix the problem?  Is there a better way?

---

### Post by ggaaron on 2008-08-21
source runs selected file as a script - if you'd copy and paste it into the terminal it would be the same, so no it isn't a good way to do this (but you say it works which amazes me). I'd check /etc/passwd file for root line and ensure that it ends like this: :/root:/bin/bash, alternatively you can have some nasty things in root's .bashrc .bash_profile or .profile.

---

### Post by gkaragoulis on 2008-08-22
Yes, frankly I was amazed that sourcing /etc/passwd worked too!  I checked all the entries in it and they all look good.  This is one of those things that almost never happens, but every once in a while I will start the computer and sudo won't work.  I'm wondering if something in the 'init' sequence is out of order and so it doesn't load the information about root fully.  The same symptoms have happened to me for other accounts too, including my regular local account.  I'm very puzzled.

---

### Post by ggaaron on 2008-08-22
You must have hacked your system heavily, haven't you?=D It should work or not, it shouldn't work sometimes... Have you recently added/removed groups/users, edited sudoers file?

---

### Post by gkaragoulis on 2008-08-22
> Have you recently added/removed groups/users, edited sudoers file? 
Oh yeah I do that all the time.  I'm the network administrator for a software consulting company, so I do what's required.
> You must have hacked your system heavily, haven't you?
You got that right too, my most recent addition to the Linux environment was joining them to the existing Active Directory domain.  So I hacked the PAM directories a lot to allow domain users.  I even got my VMware Server installation to authenticate against the domain.  So you think that's what's causing this?  Sloppy hacking?

---

### Post by ggaaron on 2008-08-23
Probably something under the way messed things up. Can be hard to tell what was it now. You say that passwd file is good, I think that only one that also affects sudo is sudoers file edited by sudo visudo.

---

