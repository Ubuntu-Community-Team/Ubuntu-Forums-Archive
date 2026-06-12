---
title: "Few small-business IT questions"
date: 2009-01-16
forum: Security
---

### Post by dongle07 on 2009-01-16
First off, sorry if this is the wrong forum to post these questions &#8211; feel free to move the thread if appropriate.

So far I've talked to some people and done some googling and come up with TrueCrypt and Alfresco as potential solutions for security and DM/KM. Backup is still iffy. Budget is flexible but preferably under $1k (we already have a ThinkServer with Ubuntu server on it).

OUR TEAM AND EQUIPMENT
We currently have 7 people. Each person has their own Lenovo laptop running Windows with the full MS Office suite.

For the rest of the team, the backup and security technology should be as transparent as possible.

DOCUMENT/KNOWLEDGE MANAGEMENT
We have 5 years of institutional knowledge and documents. We need a way to keep track of and access documents such as past reports, past year data, templates for documents, contracts, current reports that are being collaborated on and so on over the internet. We also need to have some way of managing information such as process and implementation information, internal info regarding network and building access, client billing histories, etc. Is a wiki the best solution to knowledge management? Are there any that integrate with a document management system?

BACKUP
Currently, we are backing up our computers by dragging the 'My Documents' folder to separate directories on a 1TB external hard-drive. This is obviously problematic because the drive is not secured, physical access is required, there is little versioning with backups, and there is no redundancy should the drive crash/get lost/etc. [I had nothing to do with this policy; yes I realize it is hilarious]

We'd like to have some sort of version-controlled network available backup. Something kind of like Dropbox, or a periodic svn commit (not ideal since there should be GUI-based file retrieval and it should be able to be paused easily in case bandwidth is needed elsewhere). rdiff-backup could probably work as well but it's probably too difficult for analysts to get their files back once they've been backed up.

SECURITY
Most of our documents do not need to be particularly secure. We do, however, store demographic and contact information for thousands of our clients' customers in some of our files. It is, predictably, of utmost importance that we start storing these files in a secure manner.

These files are in a few different formats, from raw data dumps from our surveying tool, CSVs, XLS, etc. Sometimes we need to share these files with clients. They can be too large for email &#8211; sometimes in the 100s of MB.

What is a good method for securely storing these files locally?
How should we send these files to clients?
What's a good password policy &#8211; one internal + one for clients; one for each member + one for clients, etc.

Thanks for any help or useful links.

&#8211; Jon

---

### Post by hyper_ch on 2009-01-16
can't help you much with the document / knowledge management... however if you use a linux server and samba server then you can map it just as a network drive from the windows clients...

if you just need to backup the files then use rsync and hardlinks to create regular snapshot-style backups. With LUKS/dm-crypt you will have it encrypted and with a keyfiled stored on the encrypted server it can be auto-unlocked by the server.
So basically you'd do a daily backup. rsync will just backup the altered file and with hardlinking you just create inodes to the previous files that were unchanged and hence a backup does not take a lot more space than the sum of all documents that were altered on that day plus a few inodes more.

with regard to security use full disk encryption, make very tight rules for external (internet) access.. probably best to use vpn for "normal" access and ssh for "shell/scp" access.

you could use mysecureshell to created chrooted ssh accounts into which clients could then login. each one could not leave his home folder and if you want to make files available, create an account, set shell to mysecureshell and copy the according files into his home folder. He could then use a SCP/SFTP client to access it (free: [http://www.winscp.com](http://www.winscp.com))

---

### Post by dongle07 on 2009-01-19
Oh, that's great advice! Thanks!

---

### Post by HermanAB on 2009-01-19
For document management I'd suggest Opendocman: [http://www.opendocman.com/](http://www.opendocman.com/)

For backup, you can use either FTP or Rsync.  The advantage of FTP is that you don't need to install anything on Windows, it has FTP already:
[http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)

If you want to use rsync, then you need to install Cygwin on each PC, which would be painful, but it may work better in the long run, since rsync only transfers things that are different.

With Opendocman, you could give large clients a login and share files using a web browser.  If you use Opendocman for all documents, then that will take care of most of your backup problem too, since all the docs will be on a single server, not on on ten separate PCs.

Cheers,

Herman

---

### Post by kevdog on 2009-01-20
I prefer unison to rsync.  Unison runs rsync down below.  It also allows for 2 way synchronization (or 1 way) if you need this feature.  Its also well maintained.  Unison can also run on both windows and linux and mac.  I don't think you need cygwin installed on the windows machine, however it can be run in this manner if that is what your prefer.

---

### Post by pdtpatrick on 2009-01-20
I like unison as well.

---

