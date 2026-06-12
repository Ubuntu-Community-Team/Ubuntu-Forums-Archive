---
title: "Best approach to creating a basic Openbox back-up"
date: 2021-03-10
forum: Ubuntu/Debian BASED
---

### Post by deanr2 on 2021-03-10
[COLOR=#242729][FONT=Arial]I want to be able to quickly set up my personally configured Openbox installation (based on Crunchbang++) on future installations. I therefore need to create some kind of back-up. I want to avoid the command line.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've experimented with grsync, back-in-time and luckyBackup - all of which generally work fine and the amount of options is pretty impressive. But perhaps too much so...

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've begun to wonder if I actually need any such specific back-up tool because (correct me if I'm wrong) I would basically only need to restore the config files for Openbox, conky and tint2, my wallpapers, icons, themes and rofi themes (these, I know, are slightly more problematic as they are not stored in the home directory).

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I guess in essence my main questions are:

[/FONT][/COLOR]

[LIST=1]
[*]Can I simply just copy these files/folders to another location (USB formatted ext4, for example) and then copy and paste them back into a fresh install?
[*]Do I need to worry about file/folder permissions at all?
[*]Will something like midnight commander (or any standard file manager) do the job just as well? Should I be root? (I need root to copy rofi files, I know that.)
[*]Are there any other reasons I should really use one of the back-up utility tools instead of a file manager - given the fact that I actually need very few files for my back-up?
[/LIST]
[COLOR=#242729][FONT=Arial]
Much appreciated in advance for any help.[/FONT][/COLOR]

---

### Post by TheFu on 2021-03-10
The best backup tools don't have GUIs. That mandate severely limits your choices and adds complexity.
rsync/grsync isn't really much of a backup tool.  There are better options that are faster.

[LIST=1]
[*]a copy is not a backup. Changes over time matter.  Files can become corrupted over time. Backing up a file that got corrupted last month isn't exactly helpful, unless you have a backup from before the corruption happened.
[*]data is only 50% of the backup. Withotu the owner, group, permissions, ACLs, and xattrs - you won't be able to restore to a working system.
[*]No.
[*]Yes.
[/LIST]

---

### Post by deanr2 on 2021-03-11
> [COLOR=#000000]rsync/grsync isn't really much of a backup tool. There are better options that are faster.[/COLOR][COLOR=#000000]

That seems a rather controversial statement. I believe rsync is in fact the go-to command for backing up files. Any suggestions for something better then?

[/COLOR]> [COLOR=#000000]a copy is not a backup. Changes over time matter. Files can become corrupted over time. Backing up a file that got corrupted last month isn't exactly helpful, unless you have a backup from before the corruption happened.[/COLOR][COLOR=#000000]

Fair enough, but as stated, I basically just want my openbox config files and icon themes etc, not system files. Once set up, these will not be subject (any/much) change.

> 

3. No.
4. Yes. 

Not very helpful I'm afraid, but thanks anyway for taking the time to respond. 

Just so you know, as perhaps you're not familiar with the tool, but MC (midnight commander) actually copies files with permissions in tact.


[/COLOR]

---

### Post by TheFu on 2021-03-11
> **deanr2 said:**
> That seems a rather controversial statement. I believe rsync is in fact the go-to command for backing up files. Any suggestions for something better then?
rsync alone is not a backup. Other steps are required to make it into a backup tool.  There are multiple scripts that have been around 20+ years that do just that.  rsnapshot, rbackup for example.

But if you are going to do a backup, why not use a better, faster, tool, like rdiff-backup?  The command looks very much like an rsync command, but provides so much more capability and ease of use.  It captures changes not just in the data, but in the permissions.  It is highly storage efficient and can be used with non-Linux file systems since the file metadata is stored separately.  There are other tools which do these things too, but most don't have the proven track record or are terribly slow.

Backups requirements:
[LIST=1]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]

> **deanr2 said:**
> Fair enough, but as stated, I basically just want my openbox config files and icon themes etc, not system files. Once set up, these will not be subject (any/much) change.
It's your data.

> **deanr2 said:**
> Not very helpful I'm afraid, but thanks anyway for taking the time to respond. 
Simple questions were asked with little background provided. Simple answers seemed the best. If it isn't 100% automatic, it isn't a backup. Failures seldom happen when we are prepared. They wait until the worst possible time to occur.  With automatic, daily, versioned, backups, we are always prepared.

---

### Post by deanr2 on 2021-03-11
Thanks for the detailed response. 

I'll continue looking into it as well as checking out [COLOR=#000000]rdiff-backup.

Much appreciated.[/COLOR]

---

