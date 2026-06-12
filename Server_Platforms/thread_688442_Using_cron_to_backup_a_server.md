---
title: "Using cron to backup a server"
date: 2008-02-05
forum: Server Platforms
---

### Post by jmidgley on 2008-02-05
Hi

I'm hoping to get some pointers to backup some folders on my server. I'm backing up to a HDD attached to an NSLU2. I've mounted a share on the NSLU2 using mount -t smbfs //slug/share /here/there -o username=xxx,password=yyy. I have in mind a running a script every day that goes something like:

for files in directory where datestamp is later than somefile do
copy file to /here/there
end
touch somefile
#the idea being to only backup files modified or added since the last backup

But I'm not familiar enough with scripting to write it from scratch. I'm not too concerned with compression (most of the stuff is compressed in some way already). I wasn't thinking of using tar, either - I'm quite happy to basically replicate  the file structure on the machine.

Any thoughts?

Many thanks
John

---

### Post by freebeer on 2008-02-05
you might want to look into **rsync**.  It's a great program for this sort of thing and it'll only copy files that have changed (and then only the part that has changed, if I've read the docs properly).  ;)

---

