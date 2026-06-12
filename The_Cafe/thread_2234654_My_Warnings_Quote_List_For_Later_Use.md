---
title: "My Warnings Quote List For Later Use"
date: 2014-07-15
forum: The Cafe
---

### Post by at_first_light on 2014-07-15
Just thought I'd make a thread where I can post warnings to quote when replying to other threads. If possible I will also include a few How To thread links relevant to the warning. The idea is to cover off background information that someone may not be aware of. I will post the warnings as replies to this thread.

**The layout I'll be using:**

[SIZE=4][COLOR=#ff0000]_**WARNING:**_[/COLOR][/SIZE]
The warning message goes here, and will normally be a bit longer than this example's is. Probably in the 2-4 lines range.

Related Threads:[COLOR=#ff0000]
[/COLOR][http://ubuntforums.org/how-to-do-somthing-relevant-the-warning]("http://ubuntforums.org")
[http://ubuntforums.org/how-to-do-somthing-else-relevant-the-warning]("http://ubuntforums.org")

**How it will look when used elsewhere:**

My response to the thread, and etc. More text and then the quote appears in the relevant section of the reply.

> **at_first_light said:**
> 
[SIZE=4][COLOR=#ff0000]_**WARNING:**_[/COLOR][/SIZE]
The warning message goes here, and will normally be a bit longer than this example's is. Probably in the 2-4 lines range.

Related Threads:[COLOR=#ff0000]
[/COLOR][http://ubuntforums.org/how-to-do-somthing-relevant-the-warning]("http://ubuntforums.org")
[http://ubuntforums.org/how-to-do-somthing-else-relevant-the-warning]("http://ubuntforums.org")


Then the post continues on, and eventually ends.

---

### Post by at_first_light on 2014-07-15
[SIZE=4][COLOR=#ff0000]_**WARNING:**_[/COLOR][/SIZE]
Before  engaging in any kind of partitioning be aware that if a failure occurs  you could loose access to all the data on the partitions involved, and  in a worst case scenario all data on the entire drive. It is good form  to back up your entire drive before doing any form of partitioning on  it. This means backing up your files, and operating systems in manner  that is restorable.

Related Threads:
[http://ubuntuforums.org/showthread.php?t=2234758](http://ubuntuforums.org/showthread.php?t=2234758)

[HTML]> **at_first_light said:**
> [SIZE=4][COLOR=#ff0000]_**WARNING:**_[/COLOR][/SIZE]
Before  engaging in any kind of partitioning be aware that if a failure occurs  you could loose access to all the data on the partitions involved, and  in a worst case scenario all data on the entire drive. It is good form  to back up your entire drive before doing any form of partitioning on  it. This means backing up your files, and operating systems in manner  that is restorable.

Related Threads:
[http://ubuntuforums.org/showthread.php?t=2234758](http://ubuntuforums.org/showthread.php?t=2234758)

[/HTML]

---

### Post by tgalati4 on 2014-07-15
_[SIZE=4][COLOR="#FF0000"]Warning:[/COLOR][/SIZE]_

Things are not as they appear.

---

### Post by QIII on 2014-07-15
[FONT=arial black]***[COLOR=#FF0000]WARNING:[/COLOR]***[/FONT]
If you don't know why aleady, you probably wouldn't understand if we tried to explain it.  
But go ahead if you don't trust us.  See what happens.
Don't say we didn't warn you.

---

### Post by bashiergui on 2014-07-16
[COLOR=#ff0000]Warning[/COLOR]

I posted a link to a detailed tutorial telling you how to do exactly what you're trying to do.
No one in the thread will actually read it.
A bunch of other people will respond with tangentially related comments.
Then one guy will ask you why you want to do what you want to do.
Then someone else will post the same link I did. But this time you'll click it, thus making him the hero of the thread.

---

### Post by PondPuppy on 2014-07-16
"I've never tried this myself, but"

```
sudo some-terrifying-shaky-commands
```

---

### Post by Habitual on 2014-07-18
[COLOR=#ff0000]Warning[/COLOR]:
When all else fails, do it the way your Mother told you.

---

### Post by at_first_light on 2014-07-19
> **Habitual said:**
> [COLOR=#ff0000]Warning[/COLOR]:
When all else fails, do it the way your Mother told you.

I want to +1 you so badly right now that I looked for a button.

---

### Post by cariboo on 2014-07-19
> **at_first_light said:**
> I want to +1 you so badly right now that I looked for a button.

How about just saying thank you?

---

### Post by at_first_light on 2014-07-19
> **cariboo907 said:**
> How about just saying thank you?

Use words, instead of trying to click an in-existent button that has an unclear meaning beyond showing some kind of positive reaction? Clearly you don't know me; I'm more of a push-a-pull-door kind of guy.

---

### Post by sudodus on 2014-07-19
[COLOR=#ff0000][SIZE=4]Warning[/SIZE][/COLOR]

Please never recommend using ***dd*** (particularly not for backup) unless you know that the user is experienced. ***dd*** is nicknamed 'disk destroyer' because it is very powerful and does what you tell it to do without questions. So if you tell it to overwrite your precious data files instead of backing them up, ***dd*** will be happy to overwrite them. A simple typing error can make the difference between success and catastrophe. I have seen too many threads here at the Ubuntu Forums, where people ask for help after destroying their data with a ***dd*** command.

-o-

It is a good idea to warn people, when helping them with potentially dangerous tasks, like you suggest backup before partitioning. And there are many backup tools and cloning tools, that have security checks and will ask questions.

1. See this link for ***backup tools*** (and maybe help editing it as suggested by [**[COLOR=#000000]livewirebt2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868820") in your thread [How To Backup And Restore A Hard Drive]("http://ubuntuforums.org/showthread.php?t=2234758&p=13075333#post13075333"))

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

2. You can use and recommend ***Clonezilla*** for safer cloning

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by at_first_light on 2014-07-19
@sudodus 

The backup process itself is safe, it's the restore process that can be dangerous if you specify the wrong location; this it is a problem for **_any and all_** backup/restore tools (including Clonezilla) when used under these circumstances. As discussed in [my guide]("http://ubuntuforums.org/showthread.php?t=2234758"), it's recommended that the user unplugs any storage devices that aren't needed during the restore process. I would also point out the location of a restore is not the only safety concern. The user is trusting this backup to **_work_**. Sector based backup tools like DD provide the best chance of a successful restore because they don't do anything extra to reduce the backup size. For example did you know that Clonezilla under certain circumstances will re-install grub2 rather than restore the MBR data included in the backup; kinda defeats the point of "cloning".

My guide covers an effective basic method of creating an **_exact copy_** of an **_entire drive_** that can easily be restored. Some file based tools leave out files that have unsupported attributes. Tar, and SquashFS Tools being examples of that. The only risky part of using DD is selecting the wrong location to restore, and this is true of any tool used to clone an entire drive. The only thing that could make DD safer would be a prompt saying, "Are you sure that's where you wish to restore to", and one can simulate this by simply double checking locations before doing a backup/restore. [My guide]("http://ubuntuforums.org/showthread.php?t=2234758") also advises users to unplug storage devices that aren't needed during the process.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) is for general backups; most of these tools **_cannot_** be used to clone a drive, and are file based which **_adds risk_**. The idea behind my post is that the user is new to this type of backup/restore which means they may not be familiar with disk types, bootloaders, or the backup requirements of different operating systems; a sector based tool **_had_** to be used.

[My guide]("http://ubuntuforums.org/showthread.php?t=2234758") is intended to help users avoid ending up in a bad situation. I've read several questions that involve partitioning, and none of them contained comments warning the OP that if anything goes wrong they're hooped. When dealing with beginners I think it is important to mention these things. I figure if I'm going to I should also offer up a solution. My guide is no more dangerous than their original postings about partitioning where the OP could loose data even if he/she selects the correct location for the partitioning alterations.

If people don't like my tutorial they are free to write a better one; I'd probably be the first person to read it as I'm always interested in better/different ways of doing things. :)

---

### Post by sudodus on 2014-07-20
I'm happy to have an open discussion on this matter. I'm trying to find the best way to help, so my post was not meant to tell anybody that your method is bad, only to explain the risks with dd, and what alternatives there are, particularly for beginners.  

> **at_first_light said:**
> @sudodus 
The backup process itself is safe,


> 13. In the terminal type "[COLOR=#0000ff]dd if=/dev/THEDEVICEYOUWANTTOCOPY of="/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img"[/COLOR] " In my case it will be "[COLOR=#0000ff]dd if=/dev/sdb of="/media/ubuntu/16bec086-64a0-4697-a55a-582a5ac6a56a/backup.img"[/COLOR] ". Press "[COLOR=#0000ff]enter[/COLOR]"   on your keyboard. The cursor will just sit there flashing, and when it   finishes it will display some stats. My hard drive was only 1GiB so it   took about 22 seconds, but if your drive is quite large then it may  take  a very long time.

What happens if you happen to type like this (and there is such a file)?

```
[COLOR=#0000ff][COLOR=#0000ff]dd [/COLOR][/COLOR][COLOR=#ff0000]o[/COLOR][COLOR=#0000ff][COLOR=#0000ff]f=/dev/sdb [/COLOR][/COLOR][COLOR=#ff0000]i[/COLOR][COLOR=#0000ff][COLOR=#0000ff]f="/media/ubuntu/16bec086-64a0-4697-a55a-582a5ac6a56a/backup.img[/COLOR][/COLOR]
```

O and I are neighbours on many keyboards, and typing errors can occur.

There are ways to make it safer, for example using redirection. You can also compress the backup by piping via gzip (faster) or xz (higher compression), and particularly if you zeroise the unused space in the partitions before the backup, it will reduce the size quite a lot. And selecting bs=4096 will make the process faster (I found the block size 4096 bytes optimal in many computers).

When booted from another drive and running with superuser privileges ***sudo -i*** or ***sudo -s***

...

```

mount /path-to-partition/ /mnt
cd /mnt/
[COLOR=#008000]dd if=/dev/zero bs=4096 > blank[/COLOR]
rm blank
cd
umount /mnt

```

```
[COLOR=#0000ff]dd if=/dev/THEDEVICEYOUWANTTOCOPY [/COLOR][COLOR=#008000]bs=4096 | gzip > [/COLOR][COLOR=#0000ff]/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img[/COLOR][COLOR=#008000].gz[/COLOR]
```
```
[COLOR=#0000ff]dd if=/dev/THEDEVICEYOUWANTTOCOPY [/COLOR][COLOR=#008000]bs=4096 | xz > [/COLOR][COLOR=#0000ff]/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img[/COLOR][COLOR=#008000].xz[/COLOR]
```

but

```
[COLOR=#0000ff]dd if=/dev/THEDEVICEYOUWANTTOCOPY [/COLOR][COLOR=#008000] > [/COLOR][COLOR=#0000ff]/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img[/COLOR]
```

is simpler and may be more attractive to a beginner, or whenever speed and or simplicity are more important than size.

> 
 it's the restore process that can be dangerous if you specify the wrong location; this it is a problem for **_any and all_** backup/restore tools (including Clonezilla) when used under these circumstances.

Compressed image files can be installed / restored with ***mkusb***, which is using dd under the hood, but makes the process much safer. See these links.

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If we make a corresponding tool for backup, which is using dd under the hood, but makes the process much safer, things would really improve :-)
> 
As discussed in [my guide]("http://ubuntuforums.org/showthread.php?t=2234758"), it's recommended that the user unplugs any storage devices that aren't needed during the restore process. I would also point out the location of a restore is not the only safety concern. The user is trusting this backup to **_work_**. Sector based backup tools like DD provide the best chance of a successful restore because they don't do anything extra to reduce the backup size. For example did you know that Clonezilla under certain circumstances will re-install grub2 rather than restore the MBR data included in the backup; kinda defeats the point of "cloning".

I also recommend that the user unplugs any storage devices that aren't needed during the or restore process. I would say during any process, where partitions are created or edited. Unfortunately many people are unwilling to unplug internal devices.

I will also repeat, it is important to tell people to ***test*** their backup. Otherwise they don't know, that it really works. Too many people trust their backup to work, but they don't check it. I would say they are lucky if it works, and the important family photos or important business documents should not depend on luck.
> 
My guide covers an effective basic method of creating an **_exact copy_** of an **_entire drive_** that can easily be restored. Some file based tools leave out files that have unsupported attributes. Tar, and SquashFS Tools being examples of that. The only risky part of using DD is selecting the wrong location to restore, and this is true of any tool used to clone an entire drive. The only thing that could make DD safer would be a prompt saying, "Are you sure that's where you wish to restore to", and one can simulate this by simply double checking locations before doing a backup/restore. [My guide]("http://ubuntuforums.org/showthread.php?t=2234758") also advises users to unplug storage devices that aren't needed during the process.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) is for general backups; most of these tools **_cannot_** be used to clone a drive, and are file based which **_adds risk_**. The idea behind my post is that the user is new to this type of backup/restore which means they may not be familiar with disk types, bootloaders, or the backup requirements of different operating systems; a sector based tool **_had_** to be used.

[My guide]("http://ubuntuforums.org/showthread.php?t=2234758") is intended to help users avoid ending up in a bad situation. I've read several questions that involve partitioning, and none of them contained comments warning the OP that if anything goes wrong they're hooped. When dealing with beginners I think it is important to mention these things. I figure if I'm going to I should also offer up a solution. My guide is no more dangerous than their original postings about partitioning where the OP could loose data even if he/she selects the correct location for the partitioning alterations.

If people don't like my tutorial they are free to write a better one; I'd probably be the first person to read it as I'm always interested in better/different ways of doing things. :)

There are many good things in your guide, and I wish you good luck with keeping it up to date and if possible improving it. I think we have the same intention, to "help [linux] users avoid ending up in a bad situation".

---

### Post by at_first_light on 2014-07-20
> **sudodus said:**
> my post was not meant to tell anybody that your method is bad
Don't worry, I didn't take it to be, and wouldn't have cared if it had been. Everyone has their preferred tools, and reasons for choosing them.

> **sudodus said:**
> it is important to tell people to ***test*** their backup. Otherwise they don't know, that it really works.
You are absolutely right, but as someone who doesn't usually test his (because I have many) this slipped my mind while writing the tutorial, it's certainly something that could be added.

> **sudodus said:**
> What happens if you happen to type like this (and there is such a file)?

```
[COLOR=#0000ff][COLOR=#0000ff]dd [/COLOR][/COLOR][COLOR=#ff0000]o[/COLOR][COLOR=#0000ff][COLOR=#0000ff]f=/dev/sdb [/COLOR][/COLOR][COLOR=#ff0000]i[/COLOR][COLOR=#0000ff][COLOR=#0000ff]f="/media/ubuntu/16bec086-64a0-4697-a55a-582a5ac6a56a/backup.img[/COLOR][/COLOR]
```
I'm not saying DD is perfect, because it isn't. Ideally a program would warn the user the file already exists, DD doesn't, and will overwrite the file. No program is perfect. I could definitely see adding a note about that in the tutorial.

> **sudodus said:**
> O and I are neighbours on many keyboards, and typing errors can occur.
Typing errors are a potential problem for any cli tool, just as clicking the wrong button is for gui apps. This goes back to double checking before actually doing anything.

> **sudodus said:**
> You can also compress the backup by piping via gzip (faster) or xz (higher compression), and particularly if you zeroise the unused space in the partitions before the backup, it will reduce the size quite a lot. And selecting bs=4096 will make the process faster (I found the block size 4096 bytes optimal in many computers).
I usually use gz myself, but sometimes xz. I aslo prefer doing partition based backups rather than the disk as a whole, but I wanted to keep the tutorial to the basics.

> **sudodus said:**
> Compressed image files can be installed / restored with ***mkusb***, which is using dd under the hood, but makes the process much safer.
The more options people have available to them the better. I remember a few years back (dealing with Windows) I had backups using several different programs, because I couldn't figure out which I liked best. The existing relevant posts I found about DD seemed a bit over-complicated for my purposes. I wrote a tutorial about using DD to fill a gap, but there are many methods users can use to make a backup. 

> **sudodus said:**
> I think we have the same intention, to "help [linux] users avoid ending up in a bad situation".
I'm sure we do. :)

---

