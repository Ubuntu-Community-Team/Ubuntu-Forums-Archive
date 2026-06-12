---
title: "Random, LONG delays when using ssh"
date: 2012-04-03
forum: Security
---

### Post by ladasky on 2012-04-03
This isn't a security issue per se, but it seems like all the people who understand ssh are to be found in this forum, so here I am.

I am running GROMACS 4.5.4, a package for molecular simulations.  It is one of Ubuntu's supported packages.  I have two nearly-identical computers, AMD six-core machines both running Ubuntu 11.10 x86_64.

GROMACS has a multiprocessing-aware version (also on Ubuntu's supported software list) which uses Open MPI to communicate between CPU's.  I have been using the multi-CPU version of GROMACS on a single machine for a while now.  I'm trying to harness the second machine as well over Ethernet.  In other words, I'm trying to set up a little cluster.

According to the Open MPI documentation, I need a working ssh connection between my master machine and slave machines.  So I have installed the openssh-server package on my slave machine.  I followed the directions _[here]("http://randomusefulnotes.blogspot.com/2010/12/setting-up-mpi-cluster-on-ubuntu.html")_ to set up the public encryption key.  

Once I got everything set up, I tried running GROMACS-mpi once, but it crashed.  So I figured that I should just go back to basics, and simply test whether my ssh connection was working.

I can log in to the slave machine from the shell using ssh, but I see three problems.  Actually, two of these may just be two manifestations of the same problem.  Both involve random, LONG delays.  

1) After I type a few commands, suddenly the cursor just freezes.  It can do this while I'm in the middle of typing a command.  If I'm patient, the text that I typed right as the cursor froze will eventually appear -- but I might have to wait as long as three to five MINUTES.

2) I also receive frequent timeouts when I log off of ssh, and then try to log back in.

3) Finally, I am still being asked for my password on each repeated login.  I thought that the SSH public key exchange was supposed to bypass the password prompt?

I'm doing this at home on my LAN.  Both of my machines are sitting behind a firewall-enabled router.  Local network traffic is absolutely quiet.  All other functions on these two machines, including web browsing, etc. continue to function absolutely normally while these hangups occur.  I have tried using ssh from the master computer, both while logged on locally to the slave computer and while not logged on.  It doesn't seem to make a difference.  None of the directories on either machine are encrypted, which I understand from _[this post]("https://rohieb.wordpress.com/2010/10/09/84/")_ can cause issues when trying to access a public key.

I suspect that one of these long delays probably also occurred when I tried to use GROMACS-mpi, and that it caused my crash.

Any suggestions?  Thanks!  :confused:

---

### Post by ladasky on 2012-04-03
Well, I solved one of my problems...

> **ladasky said:**
> I am still being asked for my password on each repeated login.  I thought that the SSH public key exchange was supposed to bypass the password prompt?

It turns out I copied the master machine's PRIVATE key (id_dsa) to the authorized_hosts file of the slave machine rather than its PUBLIC key (id_dsa.pub).  The names were just too similar and I missed the fact that I didn't include the .pub extension.

I'm still having a problem with long delays, though.  In fact I've now seem that the hanging can occur when the slave machine is sending me text, not just when I'm typing.

---

### Post by ladasky on 2012-04-05
Anyone?

Well, I also tried the General Help forum.  I'm getting more views there.  If anyone reads this and has some insight, I'm continuing the discussion _[here]("http://ubuntuforums.org/showthread.php?t=1952330")_.

Thanks.

---

