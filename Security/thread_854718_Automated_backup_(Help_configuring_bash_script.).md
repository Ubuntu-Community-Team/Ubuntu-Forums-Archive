---
title: "Automated backup (Help configuring bash script.)"
date: 2008-07-09
forum: Security
---

### Post by Aleksandersen on 2008-07-09
I want to automate a backup process using rsync, ssh, and compression. (At least I believe these are the best tools.) 

I am going to explain how I picture this system, and I hope someone will find the time to help me with this. I guess this needs to be setup as a bash script that will be run daily from /etc/cron.daily/. 

I do not want to take a backup copy of every files on my system. But rather, I would like to create a text file listing files and directories that should be backed up. I imagine one path per line. For example: 
/etc/apt/sources.list 
/home/daniel/.lynxrc 

The local copy ought not need to be transmitted to the backup location if the local file has not been modified. (I presume this is where rsync come in handy.) Secondly, the remote copy should be compressed. (.gz for single files and .tar.gz for directories.) 

The first backup location is not always available, it is an USB hard drive located at /media/terabyte/ when it is available. The script should check whether the device is mounted (it is if the directory exist) before continuing with making the backup. The second location is an Apache server from a service provider available trough SSH, for secure file transfers. 

I really hope someone will help me make this system. Thanks in advance!

---

### Post by HalPomeranz on 2008-07-10
I don't have time to answer your post in full, but you might be able to get some ideas for your system from this posting:  [http://ubuntuforums.org/showpost.php?p=4980160&postcount=4](http://ubuntuforums.org/showpost.php?p=4980160&postcount=4)

Some quick comments:

-- My script in the above posting dumps the entire file system except for certain directories that are kept in an "exclude file".  If you want your script to dump specific directories that are list in a file, you could do something like:

```

rsync -aH `cat /path/to/filename` desthost:/backup/dir/

```

In the above example, "/path/to/filename" would be the the name of the file containing the list of directories you want to dump.

-- In general rsync will not automatically gzip and/or tar files for you.  rsync is designed to make copies of a file system in some other location, not to make archives.

---

