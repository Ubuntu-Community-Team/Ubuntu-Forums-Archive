---
title: "Sync folder between Ubuntu &amp; Windows server"
date: 2010-03-15
forum: Server Platforms
---

### Post by LarsEriksson on 2010-03-15
I have one folder on a Windows server, and one folder on a Linux server, that i need to be "exactly" the same. Though live is not needed, a sync that runs for example every hour would suffice.

I have looked at rsync, but i cant figure out how to make it handle deleted / renamed files and folders.
Ie when i delete a file on <Ubuntu>, run the sync script, the file will appear in <Ubuntu> again.
Also the --delete flag wont work either, since it will delete the files on the destination before they have been able to sync.

This is how i do it now:
```
rsync -rltvuz $ubuntu $windows
rsync -rltvuz $windows $ubuntu
```

Is there any other way i can do this better?

---

### Post by DutchLoki on 2010-03-15
For that you can use the parameter: 

--delete	//delete files that don't exist on sender

I would suggest the following command to backup:

rsync --force --ignore-errors --delete --backup
--backup-dir=$BACKUPDIR -av"

A complete working script + howto is [here]("http://www.linuxjournal.com/article/8590?page=0,2"). I've used it myself some time back. 

John

---

### Post by Ghostbear121 on 2010-03-15
Yup I use this at work.  Our file server's running Samba and I have it syncing with a second computer every hour.

```

rsync --progress --stats --delete -avxzl <source dir> <destination dir>

```

Basically whatever changes happen on the samba server will be mirrored to the remote.

Don't run this on both of your computers though, because the first one that syncs will force the other to follow, right?  You need a specific 'master' and 'mirror', and you run this script on the master to push the changes out.

---

### Post by LarsEriksson on 2010-03-16
Hm as i said before, if i someone on the <Windows> server make a change in their version of the folder, and i run rsync with delete flag..  rsync -flags --delete <Ubuntu> <Windows>  all the changes in the folder that they have done on the <Windows> side will be lost.

What i want to accomplish is this. My company have 2 offices, one in Sweden, one in Estonia, and in between we have a rather slow internet connection(1.5Mbit upstream at the bottleneck).
And we have a folder that both companies need to work in, open files, edit files, remove files, add files, and it need to be the same on both sides all the time (hourly sync is sufficient).
Ie, add a file in <Windows> and it should appear in <Ubuntu> as well, change a file name in <Windows> and it should be changed in <Ubuntu> as well, delete a file.... and vice versa.


If i use the --delete flag, only one of the servers will be the "master", and changes on the other will be ignored, or have i misunderstood this completely?

ps, im not looking for a way to make backups, im looking for a way to have a two way sync between folders. ds

---

### Post by DutchLoki on 2010-03-16
Hey LarsEriksson, Now I understand, I mistunderstood your previous post. I don't thing Rsync is the way to go. 

As I see it (now ;)) Your want two working folders that are keept in sync by a hourly syncrhonisation. The problem with this is that you sooner or later run into synchronisations problems. E.g. In the past hour the same file is changed on both locations.

Rsync is OK for backups etc. But unison will do a better job. Rsync has some awesome capabilities, but it only syncs in one direction. Unison will do bi-directional synchronization, which is what you need.

[Unison home page]("http://www.cis.upenn.edu/~bcpierce/unison/")

Unison is easy on the end-user side because it doesn't need users to check out a file before editing it. 

Also its better to sync more often to lower the change on users working on a 'out-of-sync' file. Another benefit is that the amount syncd data is more spread over time. 


An even better alternative is subversion (when you don't want users editing files that are not in sync e.g. its been updated or is currently worked on). 

Subversion(svn) is a version control system, which work great in office like spaces in combination with a subversion client. On windows turtoise is very populair and easy to use. On linux I don't know because our linux users are all developers with svn integrated in their IDE's. 

a subversion client has a small learning curve on the end-users but does give a lot extra. e.g. the user can look at the edit history of a edited file and retreive an older version of this file if he likes to. 

let me know if this helps.

John

---

### Post by HermanAB on 2010-03-16
Hmm, the proper solution would be a NFS Distributed File System.  The Rsync way would be a kludge at best.

---

### Post by Jekshadow on 2010-03-16
Have you considered installing SSHFS on one of them and mounting the folder on the other as a local directory?

I recommend using this command:

```
sshfs -o cache=YES -o uid=<local uid> -o gid=<local gid> <remote username>@<remote server>:<remote path> <local path>
```

The caching might help with the bandwidth issue, and changes will be reflected nearly instantly in both offices.

---

### Post by LarsEriksson on 2010-03-17
I think unison will be the only real alternative, since people will need to use their normal windows explorer to handle files, not some kind of client that is needed for SVN.
And we need to make use of currently existing folders, so we cant really change the file system now either.

Hm how does the caching in sshfs work? Though i doubt this will be an option for us, due to the bad bandwith and pretty big files.

---

### Post by Zeosa on 2010-03-17
How about using a service such as dropbox?  They give you 2GB free and you can pay for more storage if you need it. They have clients for Linux, mac and windows. Local copies are stored/synced on all machines so lack of bandwidth doesn't come into play much (if at all)

---

### Post by DutchLoki on 2010-03-17
> **LarsEriksson said:**
> I think unison will be the only real alternative, since people will need to use their normal windows explorer to handle files, not some kind of client that is needed for SVN.
And we need to make use of currently existing folders, so we cant really change the file system now either.

Hm how does the caching in sshfs work? Though i doubt this will be an option for us, due to the bad bandwith and pretty big files.

Hey Larseriksson, the subversionclient I recommended is after installation merged with the windows explorer. So the user gets 'a few' extra function in windows explorer. 

Unison will do its work, the only problem you'll need to solve are the synchronization problems you'll get when concurrent editors are working on a file (these file will not be synchronized on that moment). Have you thought how you're going to solve this? 

I don't see how more than one user can succesfully work on the same file without locking mechanisme.

thinking about it, there are better choices than subversion: [a distributed version system]("http://en.wikipedia.org/wiki/Distributed_revision_control") (e.g. mercurial, monotone, darcx, git, etc.).

---

### Post by LarsEriksson on 2010-03-29
As it looks now, we will drop the sync-solutions all together. We have an option to change our internet from *DSL to Fiber now, 30/30Mbps, so i think we will just make use of our IPSECVPN and mount the folders "locally" for the clients, samba shares through logon.bat-files. I hope that will work out ok.

Thanks a lot for all the suggestions though, ive learned quite a bit about file syncing now :) If the new connection dont solve this, however, i will perhaps look theese things up again.

---

