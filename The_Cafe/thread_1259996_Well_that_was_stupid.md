---
title: "Well that was stupid"
date: 2009-09-07
forum: The Cafe
---

### Post by PurposeOfReason on 2009-09-07
I just finished some work and had a bunch of stuff left over on my desktop so I went to delete it. It is 11:36PM here so without thinking I go and do:

**Do not run, will delete all files and directories in working directory**
rm -rf * /home/shawn/Desktop

Now I'm sitting here trying to remember every file I had in my home folder and trying to think if it was important. :( Anything super important would also be on my server so I'm not that worried.

---

### Post by Bodsda on 2009-09-07
> **PurposeOfReason said:**
> I just finished some work and had a bunch of stuff left over on my desktop so I went to delete it. It is 11:36PM here so without thinking I go and do:

**Do not run, will delete all files and directories in working directory**
rm -rf * /home/shawn/Desktop

Now I'm sitting here trying to remember every file I had in my home folder and trying to think if it was important. :( Anything super important would also be on my server so I'm not that worried.

I did exactly the same thing not too long ago. Twas a sad day, but you may want to remove that command, it is, after all not something a new user would want to be running.

---

### Post by lisati on 2009-09-07
> **PurposeOfReason said:**
> I just finished some work and had a bunch of stuff left over on my desktop so I went to delete it. It is 11:36PM here so without thinking I go and do:

<potentially dangerous command snipped>

Now I'm sitting here trying to remember every file I had in my home folder and trying to think if it was important. :( Anything super important would also be on my server so I'm not that worried.

We feel your pain! I've done some things equally drastic in MS-DOS and Windows as well.

---

### Post by PurposeOfReason on 2009-09-07
> **Bodsda said:**
> I did exactly the same thing not too long ago. Twas a sad day, but you may want to remove that command, it is, after all not something a new user would want to be running.
Went ahead and flagged it. I'm not sure why anyone would run a command in a thread called "well that was stupid" but better safe than sorry I guess.

---

### Post by Bodsda on 2009-09-07
> **lisati said:**
> We feel your pain! I've done some things equally drastic in MS-DOS and Windows as well.
good old deltree :)

> **PurposeOfReason said:**
> Went ahead and flagged it. I'm not sure why anyone would run a command in a thread called "well that was stupid" but better safe than sorry I guess.
Not sure why anyone would rm their cwd but it happens :)

Having thought about this, I am now going to add a cd ~/safe to my terminal profile so that I start in an empty directory so that command would do nothing. Cheers :)

---

### Post by lisati on 2009-09-07
> **Bodsda said:**
> good old deltree :)

Done that on the Windows & program files directories a few times, usually as part of preparing for a fresh install using a copy of the installation files on the hard drive. 

The format command is a good one too. Managed to achieve an effect similar to that described by the OP once, thankfully nothing important lost.

---

### Post by Whiffle on 2009-09-07
I once lost a through m of my music collection that way (it got that far before I caught it and hit ctrl+c).  Twas a sad day indeed.

---

### Post by chessnerd on 2009-09-07
Yes, the terminal provides great power. But with great power, comes great responsibility. Sadly, we are not always 100% responsible... :(

I feel for you, man. I've run my fair share of stupid commands. Did a few just today when trying to transfer files between user accounts using the CLI. Mistyped one and, had it been sudo, I would have renamed my home directory and made it a hidden file. Don't know what that does, but I doubt it's good...

---

### Post by Bodsda on 2009-09-07
> **chessnerd said:**
> I would have renamed my home directory and made it a hidden file. Don't know what that does, but I doubt it's good...

It does nothing but precede the directory with a '.', its for file managers so that configuration files and things can be hidden from the normal view

---

### Post by chessnerd on 2009-09-07
> **Bodsda said:**
> It does nothing but precede the directory with a '.', its for file managers so that configuration files and things can be hidden from the normal view

It wouldn't have just hidden it, it would have been named /.fonts instead of /home.

---

### Post by PurposeOfReason on 2009-09-07
No harm there. You could just move it back and everything would be fine and dandy. Most mistakes that don't involve deleting or replacing can be fixed. In your case, you would have just lost everything in .fonts.

---

### Post by Bodsda on 2009-09-07
> **chessnerd said:**
> It wouldn't have just hidden it, it would have been named /.fonts instead of /home.

Nothing that a quick ```
mv -v /home/.fonts /home/chessnerd
```
Couldn't have fixed but I understand where you are coming from.

---

### Post by Exodist on 2009-09-07
> **PurposeOfReason said:**
> I just finished some work and had a bunch of stuff left over on my desktop so I went to delete it. It is 11:36PM here so without thinking I go and do:

**Do not run, will delete all files and directories in working directory**
rm -rf * /home/shawn/Desktop

Now I'm sitting here trying to remember every file I had in my home folder and trying to think if it was important. :( Anything super important would also be on my server so I'm not that worried.

ONLY run that when strange men in suites are at your front door!

---

### Post by Firestem4 on 2009-09-07
if rm -rf can become a problem for you alias it to rm -i or echo no, lol =)

---

### Post by koshatnik on 2009-09-07
Don't you guys back up data at all?

---

### Post by PurposeOfReason on 2009-09-07
> **koshatnik said:**
> Don't you guys back up data at all?
Media and work only. Random stuff AKA anything in my home folder, never. I have over 4TB data counting backups so roughly 2TB worth of stuff that I back up. It can be a pain.

---

### Post by Johnsie on 2009-09-07
Does Linux not have an undelete function?

---

### Post by -grubby on 2009-09-07
> **Bodsda said:**
> but you may want to remove that command, it is, after all not something a new user would want to be running.

Did you miss the bold warning?

---

### Post by p_quarles on 2009-09-07
You were looking for:
```
rm -rf /home/shawn/Desktop/*
```

A wildcard by itself always matches every possible file. It's dangerous when used with any command.

---

### Post by azkehmm on 2009-09-07
> **koshatnik said:**
> Don't you guys back up data at all?

Backup is for pansies! Real men just cry a little, then start over again :)

---

### Post by zolookas on 2009-09-07
> **Johnsie said:**
> Does Linux not have an undelete function?
File recovery depends on filesystem. There are a few utilities on Linux. Google <filesystem_name> recovery or <filesystem_name> undelete.

---

### Post by ad_267 on 2009-09-07
I would boot into a LiveCD and started trying to recover stuff with something like Photorec. There's a page with some good tools here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

The annoying thing is often you lose file names, so if there's nothing very important lost it can be more hassle than it's worth.

I don't think Windows or Mac has an undelete either. Linux has a recycle bin just like Windows, but if you delete something using rm it's gone for good (well technically not but it's difficult to get back).

---

### Post by Johnsie on 2009-09-07
> Backup is for pansies! Real men just cry a little, then start over again 

:-) For home use yes... but for business use this can be a huge problem. Most users save all their documents in a 'My Documents' folder. On Ubuntu that folder is in the home folder. Those documents could have been monthly records, customer details, pricing schemes, scripts etc. Some of this can be crucial for the business to function, other files can be records that are legally required to be kept.

This is why at work I tell the users to always save documents on the network drive rather than 'my documents'. In most companies network drives are backed up regularly, but the desktops are only backed up when the user can be bothered backing stuff up (something that simply doesn't happen)

Users dont think, "What happens if my hard disk fails?",  they just keep on plodding away until it breaks and then expect the IT admins, or in my case the programmer, to pick up the pieces.

---

### Post by Eisenwinter on 2009-09-07
I once built a 32-bit Arch within my 64-bit Arch system (chroot environment).

Its directory was /opt/Arch32.

After I was done experimenting, I wanted to delete that system, so I did rm -rf /opt/Arch32 as root.

For an unknown reason, it was linked to my regular user's home folder.

You can probably figure out the rest of the story...

---

### Post by collinp on 2009-09-07
I once setup a test system in a VM to see what *****DO NOT RUN: **rm -rf / would do.

It was interesting.

---

### Post by Mariane on 2009-09-07
I thought when you were scripting the system remembered where it was. I wanted to go up in a directory and clear it. Let us say I was in: 

/home/myname/current

and I wanted to delete everything in

/home/myname/current/temp

I did (and this is also a stupid example and not something you should copy paste randomly):  

system 'cd temp';
system 'rm -rf *'; 

It did not have the same effect as typing these two successive commands in a terminal. It deleted everything in the current directory. Including the script. 

Mariane

---

