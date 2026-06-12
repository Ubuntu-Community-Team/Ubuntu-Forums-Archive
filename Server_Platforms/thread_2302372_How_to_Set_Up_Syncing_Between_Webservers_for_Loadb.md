---
title: "How to Set Up Syncing Between Webservers for Loadbalancing"
date: 2015-11-09
forum: Server Platforms
---

### Post by tehtotalpwnage on 2015-11-09
I have multiple computers lying around at home that I want to use as webservers that I can use for load balancing via NGINX. Based on what I've read though, I'd have to individually make changes to each system anytime I want to install/remove packages and do other tasks. Is there a way I can have the filesystems on these webservers be identical to each other or something along the lines of that so that if I made changes to one "master" client, the changes to propagate to the other servers? By changes, I mean package modifications and editing of webserver served files.

---

### Post by branau on 2015-11-09
I'm not sure if there are better ways to do this or not but you could set up rsync on a cron job to sync all the files between each system, and run it manually any time you make changes to the master. I use rsync to edit the code for my personal website on my computer and then push the changes live, the command looks like this:

```
rsync -vrutze ssh path/to/local/folder path/to/remote/folder:
```

^^ note the semicolon at the end of the remote destination. It's important, otherwise you end up making a copy of everything in another folder on the same machine.

The v option is for verbose output, so you can see what's going on, the r option is for recursive, so it grabs all the files and folders within whichever folder you've selected, the u only updates files if they already exist on the remote end, so you don't end up overwriting files that are more recent on the remote, the t retains the timestamps on them (not necessary, just something I like to have), and the e option specifies the protocol you'd like to use. I use ssh for security and convenience, because once you add the ssh keys to each system, you don't need to put in any passwords to gain remote access and it's still secure. I run this on my web server's root (/) so I get a full backup of my server stored on my local machine and then I make whatever changes I want and push it live with this command. Rsync is nice too because it compresses the information it sends, so it goes a little quicker and uses a little less bandwidth.

You could write up a quick script that would sync all of your servers instantly by running this command for each one, and then run it in reverse order (so remote machine listed first, then local machine, to get any new files on the remote machines), and set it up on a cron job to run it automatically however often you need. Again, I'm not sure this is the best solution in your particular case, so I'd suggest seeing what some of the other users who are more experienced than I am have to say before you jump on this but if no one else has anything to say, this isn't a bad choice either

---

### Post by Elizine on 2015-11-10
Hi,

You can sync two web servers with rsnyc - 
[http://www.tecmint.com/sync-two-apache-websites-using-rsync/](http://www.tecmint.com/sync-two-apache-websites-using-rsync/)

Hope this guide wil help you.

---

### Post by darkod on 2015-11-10
First, there needs to be a distinction between your web files (your code) and the OS.

For your code, you don't even need an automated process. It all depends how often you do changes and how you want to organize the sync. For example, even if you set an automated process each hour, you still might end up with files out of sync up to an hour depending when you do your change on one server. On the other hand, if you run rsync manually (or in a simple bash script), your files are synced right away after you did the change. And that is only a single command you need to run manually after you uploaded the modified files.

On the OS side, don't worry too much about the packages. You don't need for the servers to be 100% identical. Just the web files. I would prefer updating the OS manually on each machine, than using rsync for that (and you have to be careful not to sync machine specific files). There are even cases of updates doing damage to your server. With an automated process, all of them will sync that update without having a change to intervene. If you do manual update of one slave/backup web server, wait few weeks to see how it goes, and only then update the other, it is much safer.

You said we are talking about few machines, not hundreds. In such cases insisting on full automation can bring more problems than benefits, IMHO...

---

### Post by tehtotalpwnage on 2015-11-11
> **darkod said:**
> First, there needs to be a distinction between your web files (your code) and the OS.

For your code, you don't even need an automated process. It all depends how often you do changes and how you want to organize the sync. For example, even if you set an automated process each hour, you still might end up with files out of sync up to an hour depending when you do your change on one server. On the other hand, if you run rsync manually (or in a simple bash script), your files are synced right away after you did the change. And that is only a single command you need to run manually after you uploaded the modified files.

On the OS side, don't worry too much about the packages. You don't need for the servers to be 100% identical. Just the web files. I would prefer updating the OS manually on each machine, than using rsync for that (and you have to be careful not to sync machine specific files). There are even cases of updates doing damage to your server. With an automated process, all of them will sync that update without having a change to intervene. If you do manual update of one slave/backup web server, wait few weeks to see how it goes, and only then update the other, it is much safer.

You said we are talking about few machines, not hundreds. In such cases insisting on full automation can bring more problems than benefits, IMHO...

Ah, alright. I didn't realize that "exact copy" included machine specific configurations like IP configurations. I can probably write up a cron script. Thanks!

---

