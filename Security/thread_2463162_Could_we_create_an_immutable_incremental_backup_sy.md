---
title: "Could we create an immutable incremental backup system to protect against ransomware?"
date: 2021-06-05
forum: Security
---

### Post by Paddy Landau on 2021-06-05
In a world where ransomware has become clever enough to mess with backups, I was wondering how to create incremental backups, but make each increment immutable?

At the moment, I use two daily backup solutions: [SpiderOakONE]("https://spideroak.com/one/") for online (off-site) backups, and [rdiff-backup]("https://rdiff-backup.net/") for offline (on-site) backups. Both provide incremental backups, but neither provides an immutable option.

Obviously, I'd like a solution for Ubuntu, but if it were also available for Windows and Mac (so that I could recommend it to non-Linux users), that would be great.

Another factor would be ease of use. I'd find it too complex to have to start setting up servers and whatnot; it needs to be reasonably straightforward.

I found the heavily-advertised [Veeam]("https://www.veeam.com/"), which seems reasonably priced. But, as far as I can tell, Veeam is tailored specifically for cloud services rather than for personal computers, as well as needing  a complex set-up, so it's unsuitable.

What can you suggest?

---

### Post by CharlesA on 2021-06-05
I guess that all depends on your definition of "immutable." You could burn your backups to CD/DVD/Bluray and have it read only, but that's going to cost a bit and the storage space would be exponential as your data grew.

You could also back up to tape and then set the tape as read only via the switch ([https://www.ibm.com/docs/en/ts3500-tape-library?topic=media-setting-write-protect-switch-lto-tape-cartrige](https://www.ibm.com/docs/en/ts3500-tape-library?topic=media-setting-write-protect-switch-lto-tape-cartrige)). However, tape drives and media are expensive for larger capacities (even used) since you'd need an auto loader so backups won't be a total pain in the butt.

If you want an immutable backup where you can't delete data from the backup, you can look into using borgbackup with the --append-only flag set at creation (see here: [https://borgbackup.readthedocs.io/en/stable/usage/init.html](https://borgbackup.readthedocs.io/en/stable/usage/init.html)).

Otherwise, keep your backups offline (or unmounted) until the backup job actually needs to run, then mount the drive, run the backup, and the unmount the drive.

However, both of these options are moot if your system is compromised and the ransomware encrypts the mounted file systems, so the only protection there is to do a weekly/monthly backup and keep that drive disconnected.

---

### Post by Paddy Landau on 2021-06-05
> **CharlesA said:**
> … burn your backups to CD/DVD/Bluray…
Unfortunately, the backups are almost 90Gb now, and of course it will only grow with time!
> **CharlesA said:**
> … back up to tape … are expensive for larger capacities
This would be a problem!
> **CharlesA said:**
> … look into using borgbackup
I hadn't heard of this. I'll check it out.
> **CharlesA said:**
> … keep your backups offline (or unmounted) until the backup job actually needs to run, then mount the drive, run the backup, and the unmount the drive.
I do this already, including a couple of older backup drives (which I rotate), so I have up to three weeks going back (although three weeks is rather a lot to lose).
> **CharlesA said:**
> … both of these options are moot if your system is compromised and the ransomware encrypts the mounted file systems…
Indeed so.

Thanks for your suggestions. I think that an online service, such as SpiderOakONE but with immutability as an option,would be best — ransomware couldn't affect it from my machine. I've submitted a request to SpiderOakONE for an option for immutability, but as they can't even implement 2FA for logins, I'm not holding my breath.

I'll read up on Borg.

---

### Post by scorp123 on 2021-06-05
> **Paddy Landau said:**
> ... I was wondering how to create incremental backups, but make each increment immutable?

As was already mentioned: You'd need to write to CD-R / DVD-R / Bluray BD-R disks, they can be written once but not overwritten.


> **Paddy Landau said:**
>  I found the heavily-advertised [Veeam]("https://www.veeam.com/"), which seems reasonably priced. But, as far as I can tell, Veeam is tailored specifically for cloud services rather than for personal computers, as well as needing  a complex set-up, so it's unsuitable. 

I've used an older release of this in the past:
[https://www.veeam.com/virtual-machine-backup-solution-free.html]("https://www.veeam.com/virtual-machine-backup-solution-free.html")

It will create a bootable DVD-R / BD-R (... depends on your disk recorder, of course ...) from your installed OS. If your OS installation gets hosed you boot off that CD / DVD / BD and get your system back. It didn't really strike me as being "complex"??

---

### Post by scorp123 on 2021-06-05
> **Paddy Landau said:**
>  Unfortunately, the backups are almost 90Gb now, and of course it will only grow with time! 

Why should that be a problem?
[https://en.wikipedia.org/wiki/Blu-ray_Disc_recordable]("https://en.wikipedia.org/wiki/Blu-ray_Disc_recordable")

BD-R XL can hold up to 128 GB per disk. And a quick search on Amazon shows that USB BD-R drives that can handle such disks cost about 80$ to 90$. Not exactly expensive.

Me personally? I often use USB3 disks that I only attach when I need them. 4 TB and larger capacity drives are very very cheap these days and good enough.


> **Paddy Landau said:**
>  Re: tape ... This would be a problem! 

At one of my previous jobs we had 2 x StorageTek SL500 tape libraries ... 
[https://sunstarco.com/oracle/tape/sl500/]("https://sunstarco.com/oracle/tape/sl500/")

And we made a backup of everything. Really everything. Totally worth it.

But yeah ... expensive :D

---

### Post by CharlesA on 2021-06-05
> **Paddy Landau said:**
> Unfortunately, the backups are almost 90Gb now, and of course it will only grow with time!

This would be a problem!

Tell me about it.  I've been backing up about 2TB of "essential" data to multiple hard drives for the last few years. Granted, this doesn't grow as quickly as my media and games do, but large data sets can be a pain to backup.

The rest of my data set (media, games, etc) totals to about 50TB or so and that gets backed up to a second NAS with secondary backups going to external hard drives.

I could move to tape, but the cost of the drive in addition to the cost of media makes it a bit of a wash. If I wanted to get a LTO5 drive, those are relatively "cheap" (at least compared to LTO 6 and 7 drives). But each tape would only hold 1.5TB of data, so I couldn't even fit my "essential" backup set on a single tape, so I'd need multiple tapes to back everything up.

---

### Post by TheFu on 2021-06-05
Would mounting the target backup storage as read-only work?  Just remount it rw for the backups, but ro for all other times.

With the rdiff-backups, are you pruning the oldest versions?  Something like this?
```
$rdiffb --remove-older-than $days --force $target
```

---

### Post by rbmorse on 2021-06-05
For Windows, take a look at Macrium Reflect ver 8.  It should do the things for which you are looking.

---

### Post by Paddy Landau on 2021-06-05
> **scorp123 said:**
> I've used an older release of this in the past:
…
It will create a bootable DVD-R / BD-R (... depends on your disk recorder, of course ...) from your installed OS. If your OS installation gets hosed you boot off that CD / DVD / BD and get your system back. It didn't really strike me as being "complex"??
OK. The advertising on the Veeam website shows something rather different. Maybe it's changed? Or maybe its advertising is targeted to a different market?
> **scorp123 said:**
> Why should that be a problem? …
Woah… I didn't realise how much storage those disc could hold!
Yes, that's an idea, then.
> **scorp123 said:**
> I often use USB3 disks that I only attach when I need them. 4 TB and larger capacity drives are very very cheap these days and good enough.
That's pretty much what I do as well, attach them only when needed.
> **TheFu said:**
> Would mounting the target backup storage as read-only work?  Just remount it rw for the backups, but ro for all other times.
Yes, I do that. Read-write while writing the backups, and read-only other times. Of course, clever enough ransomware would simply change read-only to read-write; simple enough if it has the right access. Or, it could wait until I back up, and then start its encryption process. I believe that some ransomware already does this.
> **TheFu said:**
> With the rdiff-backups, are you pruning the oldest versions?
At the moment, yes, I do that. Otherwise storage would grow immense. With immutable incremental backups, of course, I'd have to accept having larger drives with corresponding increase in costs.

Ideally, an online (off-site) backup, like the one that I use, would offer an immutable option, which would simplify everything as well as keeping costs down.
> **rbmorse said:**
> For Windows, take a look at Macrium Reflect ver 8.  It should do the things for which you are looking.
Thank you for the suggestion. I'll check it out.

---

### Post by scorp123 on 2021-06-05
> **Paddy Landau said:**
> OK. The advertising on the Veeam website shows something rather different ...

Follow the link I provided. If you just visit their main web site without specifically searching for their free ("free" as in free beer) personal backup product, chances are they will only show you their expensive corporate stuff...

---

### Post by TheFu on 2021-06-05
The other solution is to have a backup server that "pulls" the backups. Then the client wouldn't be able to access any of the backup storage.  rdiff-backup supports "pulling".  If you want more security, setup an alternate userid that is equivalent to root just for backup needs.  Then lock that account down so it can only run the commands necessary for the backups.  This is how github works from the CLI with ssh-keys.  Each userid can only run 1 program on the connection - "git". No shells. Nothing else. Just git.  For backups, probably want to run 
[LIST=1]
[*] pre-backup script, 
[*] backup script and
[*] post-backup script.
[/LIST]
Use the authorized_keys file with restrictions on the client allowed to connect using specific keys, each to run a specific command.  Look for **command=** in the sshd manpage.
The old tcp-wrappers files work for limiting by IP and/or userid, but limiting the commands can only happen in the ssh configs.

I hope you aren't doing versioned backups of media files.  That will make backups balloon.  Also restricting what gets backed up to just the stuff that is necessary to put everything back pre-backup, can save 4-10G, easy.  I don't backup the OS, for example.  I just get the settings, lists of installed packages, and the data.  For programs that are installed outside APT, I place those under /usr/local/  which does get backed up like all the HOME directories do.

But the key is to "pull" the backups, never "push" them.  Just be certain that your backup server isn't nice to undesired network locations.

---

### Post by rbmorse on 2021-06-05
> **Paddy Landau said:**
> With immutable incremental backups, of course, I'd have to accept having larger drives with corresponding increase in costs.


Your immutable backup store doesn't have to be literally immutable.  It just needs to be protected against any unauthorized alterations or deletions in the backup store. 

Some smart person could probably work out a scheme using access groups and ACLs that would do that, but still permit periodic pruning of the backup store to control disk consumption. Something like files in this directory are read-only except to the application rdiff-backup running on machine [some unique identifier] under user who is a member of [special backup group].  

Macrium Reflect for Windows does something similar, except I think it uses an application daemon to monitor accesses to the backup store and blocks write attempts and certain other file operations from all but from  the application itself.  Don't know how effective it is. The automatic pruning routine is very effective and efficient and I haven't had the need to interfere with what Reflect thinks best.

---

### Post by TheFu on 2021-06-05
If a higher level directory is locked down, say 
root:root 0700, 
then only root will be able to have access below there, regardless of the permissions, owners, ACLs in any subdirectories.

There are lots of ways to ensure backups aren't tampered.  Use Encrypted storage and parity files.  Tools like duplicity have a checksum for each file, which would almost prove that the backup hadn't been tampered with.  There are cryptographic signature tools, like openssl which can be used as a pipe-filter for encrypting any data that goes through the filter.  gpg can work the same, if stronger methods are necessary.

Or use a file as a block device, mounted with a loop, and lay down a file system inside it, then place the backups into that file system. When complete, umount the loop device, create a sha256sum for for the block-file or a gpg signature of it.  Keep that signature with the block file.

Almost everything on Unix-like OSes are files, so we can treat them however we actually like, as needed.  That goes for whole disks, disk partitions or regular files - we can treat each like the other, when it is convenient.

---

### Post by Paddy Landau on 2021-06-08
Thank you for all of your replies. It looks as though creating this sort of backup requires good technical knowledge, and maybe a remote server that I personally look after!
> **scorp123 said:**
> Follow the link I provided.
Thanks, that worked.
> **TheFu said:**
> The other solution is to have a backup server that "pulls" the backups. … the key is to "pull" the backups, never "push" them.
That's a clever idea that I hadn't thought of. I'll have to learn a lot more about this method before trying to implement it.
> **TheFu said:**
> I hope you aren't doing versioned backups of media files.
Indeed, no I don't!
> **TheFu said:**
> I don't backup the OS, for example. …
No, I back up only the data including settings.
> **TheFu said:**
> If a higher level directory is locked down, … only root will be able to have access below there…
Now, that's a great idea! I'll see if I can implement this, because it would possibly be the simplest solution.

Thank you again, everyone!

---

### Post by TheFu on 2021-06-08
> **Paddy Landau said:**
>  Now, that's a great idea! I'll see if I can implement this, because it would possibly be the simplest solution.

We have to assume the client machines are completely cracked. Never trust the client. It does dangerous things. It has internet access.  This is why only "pull"ed backups can fight malware/cryptoware.

And it should be clear that using any networked storage that is accessible by clients, besides read-only mounts, won't work. If the client can mount storage read-write, then the malware can change all those backup files.

There are lots of subtle choices with backups that improve the security and convenience.

BTW, rdiff-backup works with "pull"ed backups just fine.  The SOURCE directories are just on the other system with the TARGET directories local to the backup server.
```
$ sudo   rdiff-backup 
        --exclude-special-files \
        --include /usr/local --include /etc --include /home  --include /root \
        --exclude '**'   backup5492@{remote-machine}::/ \ 
        /Backups/{remote-machine}
```
where:
[LIST]
[*] Backups are run from a backup server via root's crontab (the sudo above not needed), just for initial work,
[*] connect to a random account, say backup5492, on the remote system and
[*] "pull"ed  specific included directories, excluding everything else (wouldn't hurt to clean up junk in HOME directories nightly and to exclude .Trash and cache directories in HOMEs.
[*] Random account is a _root-equiv_ with ssh-keys from the backup server installed just for that system, only allowed to run 3 commands:  pre-backup, backup, post-backup scripts and only from the backup server.
[*] The account keys are in the ~/.ssh/config of the root account on the backup server - might as well make the backup5492 username the default for the aliased connections to the system so we don't need to know or add to the script anything but the correct ssh-alias for the host.  manpage for ssh_config has all the possible settings in ~/.ssh/config, but in general, we'll need something like this:
```
host spam-[COLOR="#00FF00"]backup[/COLOR]
  user backup5492 
  hostname 172.22.22.81
  port 22
  IdentityFile ~/.ssh/id_ed25519-[COLOR="#00FF00"]backup[/COLOR]

```
Tie the host alias to the different key file for the pre/post and backup allowed commands. On the other side, the backup5492 authorized_keys file will need 3 entries with *command=* limits. Ref authorized_keys manpage for more details.
[/LIST]
Subtle things.

---

### Post by david504 on 2021-06-08
chmod 000 should work.

But ransomeware should not be an issue, if it is, then there is something else not correct. I have noticed system.d has bugs in it that Redhat fixed for themselves but didn't share that with the other distros. Be aware of this as I removed system.d from my commercial hosting servers because of this critical bug.

---

