---
title: "Setting up first Ubuntu Server"
date: 2013-09-13
forum: Server Platforms
---

### Post by grier-devon on 2013-09-13
Hi everyone, I got a new laptop and I want to take my old laptop and set it up as a server. I have never set up a server before and what I want to use it for is to run plex, use to back up all the other machines in the house and ssh into it when I am wanting to test some scripts I am learning how to use. I was wondering if there are any good guides on how to accomplish this to include how I just configure the server when installing. Thanks for any help.

---

### Post by LHammonds on 2013-09-16
If you are new to Linux, you might want to get familiar with it 1st in a safe environment to reduce hardware-specific hassles.  You can install it inside a virtual machine.  For example, if you are running MS Windows on your laptop, you can install Oracle VirtualBox and then create an Ubuntu VM inside.  This will allow you to take snapshots, try something out....then if it doesn't work or you want to go back a few steps, simply revert the snapshot.

Check my signature on [how I install an Ubuntu Server]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191") in a production environment and configure it for long-term use.

LHammonds

---

### Post by Lars Noodén on 2013-09-16
If you are wanting to back up the other machines in your house, you should definitely look at using [rsync](https://help.ubuntu.com/community/rsync).  It runs over SSH if you use it for backup or transfer between machines.  At its most simple, you can use it to transfer hierarchies of directories.  Getting more complex, you can use it for incremental backups.  

If you need a graphical interface for rsync to get started you can use grsync, but rsync itself is quite straight forward and easy to use, even if it is really flexible and powerful.  It's probably one of those programs people will still be using in 50 years, if there are still computers then.

---

### Post by TheFu on 2013-09-18
Running a server that isn't on the internet is easy.
Running a server that IS on the internet securely is difficult. Start to learn about the by checking out my signature.

The term "server" is overused.  It means almost nothing anymore since your smartphone can be a "server" too.  For Ubuntu, "server" to me means "without a GUI". If you intend to do that, then you'll need to be familiar with the shell.  During the installation, use the "server" installer and you will be asked what main services you'd like installed.  Choose the ssh one at a minimum.

Plex and ssh are not much load. I use xbmc, but suspect that plex is about the same.

Backups - there are 50-500 ways to backup different computers. The clients matter, since most people will have non-UNIX OSes to backup.  Everyone starts out using dump, then moves to rsync, then moves to some other tool, like duplicity or rdiff-backup. Enterprises have to handle Windows backups, which requires a different, more complex, tool-set, like backula. It takes a little time to figure each tool out.  

My sig has more on backups and techniques.

---

### Post by Lars Noodén on 2013-09-19
> **TheFu said:**
> My sig has more on backups and techniques.

In the future, you will change you signature.  At that time, someone looking at this thread for an answer won't find the right links.  If they are relevant to the original question, then please put them in the body of a post so they stick around over time.

---

