---
title: "Preserve /home dir on reinstall"
date: 2008-08-01
forum: Server Platforms
---

### Post by TheFuzzy0ne on 2008-08-01
Hi everyone. I am running 8.04 server, and I need to do a fresh install, but I don't have anywhere to back up my /home dir, and the /home dir is in the root partition.

I recently reinstalled Kubuntu 8.04 and noticed that it actually had built in support for spotting a /home directory and preserving it. Does anyone know if the server edition of the installer also supports this?

Thanks.

Daz.

---

### Post by windependence on 2008-08-01
Most all installers will allow you to go into expert or advanced mode and tell it what to format and what not to. When I do an upgrade (which is usually an install) I only usually format / and /etc and leave everything else in place. Sometimes I have to reinstall or reconfig some apps but most times it's flawless. That being said, I would still back up your /home if you can to DVD or an external drive even.

-Tim

---

### Post by rahmath on 2008-08-01
Hi,

You said home dir is in the "/" filesystem, right? Then according to me, no way to keep the data in home dir and do a formatting on this "/" partition. If it was in a seperate filesystem, you can ask to format only the "/" and avoid the /home filesystem formatting, so that the installer will automatically take this /home as the home directory.

Then you have another option to do the fresh installation, but without formatting your "/" partition;


What you have to do is, just boot up your currently installed system with ubuntu installation cd-rom and proceed as usual up to the partitioning menu.

There you will be shown the current partition detail with no mount points mentioned but will be listing the size of it. select that partition and choose edit partition.

In the field of 'use as' in edit partition menu -- select ext3 (whatever of your choice, but it should be the same FS as the current installed system), and PLEASE DONT Tick in "Format the partition" check box. if you tick, then it will be formatted, other wise it won't sure, it wont.

then you can proceed the installation as usual... it will be fine...

NOTE: all of your system related files will be either deleted or over written by the system, no doubt in it...

I can guarantee you the following things about your data;
1. Any of your files or directories which is created in the following path will be remaining there safely

a. /lost+found
b. /media
c. /your own directory under "/" (for eg: /test)
d. /srv
e. /opt
f. /home/your-current-homedirectory
g. /home
h. /root
i. /mnt

here your files and directory means NOT your system related files, but the files and directories which you created manually...

ok...

Hope this will not only help you, but few others too...

awaiting comments...

---

### Post by TreeFinger on 2008-08-01
I'm confused on how you don't have anywhere to back the home dir to. If it is a server why not backup your home dir on one of your work stations?

---

### Post by TheFuzzy0ne on 2008-08-01
> **windependence said:**
> Most all installers will allow you to go into expert or advanced mode and tell it what to format and what not to. When I do an upgrade (which is usually an install) I only usually format / and /etc and leave everything else in place. Sometimes I have to reinstall or reconfig some apps but most times it's flawless. That being said, I would still back up your /home if you can to DVD or an external drive even.

-Tim

Unfortunately, I am very low on drive space. :(

I think your method would only work if the /home directory was on a separate partition. The reason I asked is that the Kubuntu CD actually saw the home dir, but deleted a few others, such as /bin/ /tmp/ /var/ etc, and then copied a load of fresh files back in. I think I should be able to do this if I mount the drive externally, and delete these directories manually, and of course tell the installer not to format the drive.

I have problems doing it like this before, however, but I hadn't deleted any directories, and the installer was moaning about not being able to copy a file over the existing one, and wouldn't let me continue.

I read about the "preserve home" functionality on a Web site somewhere, and wasn't sure if it had been implemented or not, so I tested it out. Damned if I can remember where I read it, though...

Thanks for your response.

---

### Post by TheFuzzy0ne on 2008-08-01
> **TreeFinger said:**
> I'm confused on how you don't have anywhere to back the home dir to. If it is a server why not backup your home dir on one of your work stations?

Quite simply because my 200 or so GB of /home data on my server will not fit on my 40GB desktop drive, no matter how much squeezing I do.

My server is not entirely shared content, in fact, part of the reason I want to do my fresh installation is because I can't configure it correctly to use ISPConfig, as I would like to have a few Web sites which are accessible externally. The rest of the server works as a file server for my PC, the wife's PC, and my laptop. We have lots of media that we share between our PCs, such as DVD backups, music, photos etc...

---

### Post by TheFuzzy0ne on 2008-08-01
> **rahmath said:**
> Hi,

You said home dir is in the "/" filesystem, right? Then according to me, no way to keep the data in home dir and do a formatting on this "/" partition. If it was in a seperate filesystem, you can ask to format only the "/" and avoid the /home filesystem formatting, so that the installer will automatically take this /home as the home directory.

...

awaiting comments...

Thanks for your response. It's similar to something I did previously (see above), but the installer started whining about certain files that it couldn't overwrite, or something of that elk.

I guess I have nothing to lose by trying it again. As long as I don't format the drive, all should be well, although it does get tiresome getting half way through an install, only to have to start over again. However, keeping people informed _is_ a worthy cause, so I think I will try it.

If only I could remember where that article on the Web was that actually listed the directories that we removed completely. I don't want to risk deleting everything other than the /home directory, in case I end up having to do more work than necessary in getting everything working again. With that said, as I'm not upgrading, I'm just reinstalling, the /home directory (in theory) should be fairly portable, and shouldn't cause me any grief.

Not being able to find that article is really going to bug me now. I was looking into methods of keeping the home directory without backing it up, as I didn't have the space for my Desktop PC either, and I came across it. I must have searched about 20 different search terms, but I can't remember what they were. I won't stop until I find it! (Or until 10 minutes have passed...)

---

### Post by TheFuzzy0ne on 2008-08-01
Fudgesticles! I was about to look that page up on my laptop, but since I updated Linux last night and shut it down, it now dumps me at the grub CLI, and I don't have any boot options... I blame the Laptop, not Ubuntu.

---

### Post by TreeFinger on 2008-08-01
If this server is a file server, can't you burn the /home directory to a cd/dvd from one of your workstations?

Not sure if you can burn straight over network or do the files need to be local?

---

### Post by dca on 2008-08-01
When I used to have spare time and try testing out new GNU/Linux distro releases that's how my boxes were partitioned.  /home would be separate from everything else.  The only caveat to that (by the way, it's easier this way than dual,tri,quad-whatever booting) is I would kill 'X' or switch to other terminal and make sure I deleted all '.' hidden files from my /home/username directory before rebooting w/ my fresh new flavor of the week Linux.  By doing that you can load up the installer and format everything except /home...  Most distro(s) give you the option to not format and use it as new /home for new install.

---

### Post by TheFuzzy0ne on 2008-08-01
> **dca said:**
> When I used to have spare time and try testing out new GNU/Linux distro releases that's how my boxes were partitioned.  /home would be separate from everything else.  The only caveat to that (by the way, it's easier this way than dual,tri,quad-whatever booting) is I would kill 'X' or switch to other terminal and make sure I deleted all '.' hidden files from my /home/username directory before rebooting w/ my fresh new flavor of the week Linux.  By doing that you can load up the installer and format everything except /home...  Most distro(s) give you the option to not format and use it as new /home for new install.

I agree. However, I hate seeing space go to waste. I've had a similar partitioning scheme to that before, but as I am not David Blaine, I could not be certain how much space I would actually use on the filesystem, and therefore either made partitions too big, or too small. I love software, and I am always installing new stuff to test out, to find which flavour of a certain kind of application suits me better.

I think I might re-partition the the drives so that /home is on another disk (which means I will need to do some serious data shuffling and probably ditch a lot of it), and I might look into LVM. LVM to me is scary, as I'm not sure how it works, and what would happen if one of the drives failed. I'm guessing it's not like RAID 0, where is one of the drives fails, the other is about as useful as a wheelchair with pedals. Also, I'm not entirely sure if I would be able to access the drives independantly if it ever came to it, as well as the fact I know slightly less about LVM as the average house fly, and I don't know how easy it is to set it up, and to break it, and if there is any performance loss.

---

### Post by TheFuzzy0ne on 2008-08-01
> **TreeFinger said:**
> If this server is a file server, can't you burn the /home directory to a cd/dvd from one of your workstations?

Using DVDs works out very expensive, in both time and cash. 200GB of data would require over 40 DVDs (or 286 CDs), which is more than I can afford for a while to come. Also, at about 15-20 minutes per DVD (assuming they all burn correctly), that's 10-13.5 hours of burning discs (just under 12 hours burning CDs) and that doesn't take into account anything else such as disc changes and making cups of coffee. Then I'd have to copy it all back again. :lolflag:

So the short answer to your question is "Yes, but I don't have the time or money". :)

> **TreeFinger said:**
> 
Not sure if you can burn straight over network or do the files need to be local?


Yes you can burn straight over a network, but I think it might be slower(?) and there's more chance of data corruption on the optical media if the connection drops or bottlenecks for whatever reason. Unlikely, sure, but burning from HDD is certainly more reliable IMHO.

---

### Post by rahmath on 2008-08-02
i will get back to u soon... with the exact solution for ur problem. Right now i am testing out that solution...

---

### Post by rahmath on 2008-08-02
Well, you have the solution. You can preserve the contents of /home, and have a fresh installation. So let me start here...

What you have to do is, boot with the Ubuntu installation CD. once the Keyboard selection screen comes in, go to the console by pressing Ctrl+Alt+F2. Now you are in console. 

Now you have to mount your "/" of your present installation. for that, you have to be root,

so type 
$ sudo -i

now you are root.
then mount the exact "/" partition to /mnt
eg;
# mount /dev/sda1 /mnt (make sure about your "/" partition address)

Then delete the directory structures, which you need a complete fresh one.
For eg; while testing i deleted the following dirs with following commands

# rm -rf /mnt/bin
# rm -rf /mnt/dev
# rm -rf /mnt/etc
# rm -rf /mnt/initrd
# rm -rf /mnt/lib
# rm -rf /mnt/opt
# rm -rf /mnt/usr
# rm -rf /mnt/var
# rm -rf /mnt/sbin

Note: You can whatever dir's which you want, and also you can delete whatever the dirs which you need (but whic are all the dir's not affected by this installation process is already mentioned in the previous post)

Now unmount your prtition by;
# umount /mnt

Now switch back to your Graphical Installation screen (Ctrl+Alt+F7 mmmm.... i forgot, may be F8, anyway try it)

Then proceed with the installation. When you reach the partition screen, keep in mind about the instruction which is mentioned in my previous post.

Thats all!!!

This will work for you. 

Hope you will give me atleast 10 thanks :):lolflag:

:)

---

### Post by TheFuzzy0ne on 2008-09-09
> **rahmath said:**
> Hi,

You said home dir is in the "/" filesystem, right? Then according to me, no way to keep the data in home dir and do a formatting on this "/" partition. If it was in a seperate filesystem, you can ask to format only the "/" and avoid the /home filesystem formatting, so that the installer will automatically take this /home as the home directory.

Then you have another option to do the fresh installation, but without formatting your "/" partition;


What you have to do is, just boot up your currently installed system with ubuntu installation cd-rom and proceed as usual up to the partitioning menu.

There you will be shown the current partition detail with no mount points mentioned but will be listing the size of it. select that partition and choose edit partition.

In the field of 'use as' in edit partition menu -- select ext3 (whatever of your choice, but it should be the same FS as the current installed system), and PLEASE DONT Tick in "Format the partition" check box. if you tick, then it will be formatted, other wise it won't sure, it wont.

then you can proceed the installation as usual... it will be fine...

NOTE: all of your system related files will be either deleted or over written by the system, no doubt in it...

I can guarantee you the following things about your data;
1. Any of your files or directories which is created in the following path will be remaining there safely

a. /lost+found
b. /media
c. /your own directory under "/" (for eg: /test)
d. /srv
e. /opt
f. /home/your-current-homedirectory
g. /home
h. /root
i. /mnt

here your files and directory means NOT your system related files, but the files and directories which you created manually...

ok...

Hope this will not only help you, but few others too...

awaiting comments...

Hi. Sorry for my delayed reply, I got very busy and completely forgot about this post. I can confirm that both Kubuntu/Ubuntu Desktop and Ubuntu server both now check for directories such as /bin and delete them before reinstalling the system files, and leaving your home directory alone. Result!

---

