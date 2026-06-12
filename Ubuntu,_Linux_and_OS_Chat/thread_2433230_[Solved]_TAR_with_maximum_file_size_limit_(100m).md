---
title: "[Solved] TAR with maximum file size limit (100m)"
date: 2019-12-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Alistair George on 2019-12-16
Hi Ive been trying to get my data off one drive and onto another using this command and variants;
sudo tar -cvpzf alsmain2018.tar.gz --exclude=alsmain2018.tar.gz --exclude-caches --one-file-system /media/alistair/USB450G/backintime/alsmain/ --exclude-from <(find /media/alistair/USB450G/backintime/alsmain/ -size +100M)

which results in:
tar: /dev/fd/63: No such file or directory
tar: Error is not recoverable: exiting now

Ive tried removing last directory backslash and if I run the command soley: sudo find /media/alistair/USB450G/backintime/alsmain/ -size +100M
find works as expected, finding files over 100m. Can anyone figure where its falling apart?

If I run command: sudo tar -cvpzf alsmain2018.tar.gz --exclude=alsmain2018.tar.gz --exclude-caches --one-file-system /media/alistair/USB450G/backintime/alsmain/
backup works no errors.

Thanks kindly, Al.

---

### Post by Alistair George on 2019-12-17
Well its solved - problem was with the SUDO command which effectively removes tar command directories from the current user directory. SUDO can still be used, but its contents must be delimited by ''

---

### Post by TheFu on 2019-12-17
I'd think the issue was due to the redirection effectively ending the sudo elevated privileges. That and the missing $() around the 'find' command.  Would be nice if the actual working command were posted for others.

tar is fine in the way a ZIP file is fine, say, for total amounts of storage under 500MB.  Tar was designed to work when 250MB was a huge amount of storage.

For backups, there are so many better tools.  back-in-time is fine. There are many others.

For moving files between systems rsync is the go-to tool. If you want to exclude larger files, rsync has an option for that.  --max-size=SIZE

Anyways, please mark this thread as _SOLVED_ using the **Thread Tools** button near the top. Helps people seeking answers and helps people wishing to provide answers not waste time.

---

### Post by Alistair George on 2019-12-17
Once I found the issue was redirection, I simply searched for and removed the larger files, then used this non-original command instead:
sudo tar -cvpz  --exclude-caches --exclude=alsmain2018.tar.gz --exclude=.CACHE/* --exclude=[Cc]ache* --one-file-system -f alsmain2018.tar.gz /media/alistair/USB450G/backintime/alsmain/

Suggested with Find:

sudo sh -c 'sudo tar -cvpzf alsmain2018.tar.gz --exclude=alsmain2018.tar.gz --exclude-caches --one-file-system /media/alistair/USB450G/backintime/alsmain/ --exclude-from <(find /media/alistair/USB450G/backintime/alsmain/ -size +100M)'

---

