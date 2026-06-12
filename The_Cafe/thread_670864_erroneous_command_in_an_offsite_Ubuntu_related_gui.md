---
title: "erroneous command in an offsite Ubuntu related guide"
date: 2008-01-17
forum: The Cafe
---

### Post by erfahren on 2008-01-17
I installed Xubuntu along side my existing Ubuntu Feisty install and went by [this guide](http://www.psychocats.net/ubuntu/mountlinux) to mount my Ubuntu /home partition in Xubuntu.

at the bottom of the guide it gives commands to set the permissions like:
```

sudo chown -R erfahren:erfahren /mnt/ubuntu_home
sudo chmod -R 755 /mnt/ubuntu_home

```
I noticed later that *every* file in my /home partition was set to be executable (because of the recursive part).

The result caused me some time and trouble to fix, but I admit that I should've researched more before running the command. I wasn't really too upset about it - I saw it as a "live and learn" type thing.

I'm a little annoyed now though because I tried contacting the author of the guide in a couple different ways to report the error but never receive a reply and the erroroneous code hasn't been changed. I'm not sure if my messages were just ignored or what.

The site is geared toward people new to Ubuntu (I often have directed new users to the site) so I think the instructions should be as accurate as possible, and I think the author truly strives for that.

for clarification I posted a [a question at linuxforums.org](http://www.linuxforums.org/forum/misc/112631-help-clarifying-directory-permissions-ext3-mounted-partitions.html) about it. I also looked more at the [tuxfiles page on /etc/fstab](http://www.tuxfiles.org/linuxhelp/fstab.html) and figured out that if there's a problem with reading/writing to the partition the permissions set in fstab could be, for example, something more like:
```

/dev/sda6      /mnt/ubuntu_home      ext3     rw,auto,user     0       0

```
I have it working now and my file permissions fixed for the most part but, again, I think the guide needs to be changed and am at wits end on how to notify the author. I'm posting here hoping the author will notice this post.

--- thanks

---

### Post by p_quarles on 2008-01-18
The instructions in that tutorial are completely correct, but were not meant to be applied to your /home folder. They are quite clearly intended to help you mount a data partition.

---

### Post by aysiu on 2008-01-18
> **p_quarles said:**
> The instructions in that tutorial are completely correct, but were not meant to be applied to your /home folder. They are quite clearly intended to help you mount a data partition.
I also thought that was clear, but I have amended the page with a warning now, anyway.

---

### Post by erfahren on 2008-01-18
> **p_quarles said:**
> The instructions in that tutorial are completely correct, but were not meant to be applied to your /home folder. They are quite clearly intended to help you mount a data partition.
I wasn't mounting my Ubuntu /home partition in Xubuntu to use it as Xubuntu's /home (I wasn't sharing it in other words) - I was mounting it to just be able to access it (I thought I explained that pretty well in my linuxforums.org post I had [*linked to*](http://www.linuxforums.org/forum/misc/112631-help-clarifying-directory-permissions-ext3-mounted-partitions.html) in my first post.)

Also, when researching it more afterwards I came across [this thread](http://ubuntuforums.org/showthread.php?t=332241) - where  two people just give it just as "chmod 777" and "chmod 755" (without setting it recursive) - (taurus did put it as "chmod -R 777" but that doesn't make it correct).

I admit that you all probably know more from the outset about all this than I do, *but* I did spend a few hours studying up on it and posted at linuxforums.org afterwards just to make sure I had it clear.

This is my point - irregardless of whether it's a *"data"* partition or not (whatever the common definition is for "data" - to me it means miscellaneous files a person saves) - those permissions set *every* existing file to be executable (recursively) - text files, images, videos, what-have-you. How can that be correct? 

...and if I'm wrong then I guess the person who replied to my post at linuxforums.org is mistaken about it as well (but I really don't think that's the case).

---

### Post by erfahren on 2008-01-19
I was a little annoyed about all this because I took time to research and "study up" a little to ensure that I knew what I was talking about before stating my case the first time. I felt like I was just "brushed off" (the novice *must* be wrong) without anyone in return taking time to take a serious look at what I was saying.

Well I went and studied some more and at this point I think I have a fairly good understanding on this. 

It seems like you guys wouldn't look past the fact that I did this on my /home partition (again, I wasn't mounting it to *share* it, just access it) - anyway, never mind all that.

Just for the sake of argument here, lets say I was mounting an existing ext3 partition I use for storage called: "place_where_i_keep_stuff". 

I'll go through this part real quick first: **(Note: this is not intended to be a HowTo.)**

I can run blkid to see its "name" (location), its filesystem type, and its [UUID](http://linux.byexamples.com/archives/321/fstab-with-uuid/).
```

erfahren@acer-ubuntu:~$ blkid
/dev/sda9: UUID="c9d266e5-3cba-496f-ab7a-7355d604b783" SEC_TYPE="ext2" TYPE="ext3" 

```
After I create the directory to mount it I can make the entry in /etc/fstab (I'm not using the UUID here):
```

/dev/sda9      /place_where_i_keep_stuff      ext3     defaults     0       0

```
After I "mount all", I change ownership of the directory (recursively) to me (by using the colon after my username the group will be changed to my login group as well):
```

sudo chown -R erfahren: /place_where_i_keep_stuff

```
I may need to get Nautilus to see the change in ownership ( [COLOR="navy"]ls -l /[/COLOR] ), and then should be able to access it.


[size="3"][color="blue"]I didn't use chmod there - I'll get into that now.[/color][/size]

[size="3"]The common default settings for regular files is usually **644**, and for directories it's usually **755** (they need to be set to be executable to open them).[/size] see: ["Setting the default file creation permissions : umask"](http://www.linuxforums.org/security/file_permissions.html)
r = 4
w = 2
x = 1

[size="3"][COLOR="blue"]So, if the files and directories were set at the defaults, and the command **"sudo chmod -R 755"** was ran on the mount point directory, the settings for the *directories* wouldn't change (they'd already be 755). The *only* thing that would be changing is *all of the regular files would be set to be executable for the user, group, and others*. - That's it.[/COLOR] 

What is the purpose of that? It's like "just throwing everything at it to see what sticks"!

Again, irregardless of what kind of partition it is, setting every file to be executable is not correct.[/size]


The directories and files *could* be done separately (and also reset if needed) with something like this:
(change the directories to 755)
```

sudo find /place_where_i_keep_stuff -type d -exec chmod 755 {} \;

```
(change files to 644)
```

sudo find /place_where_i_keep_stuff -type f -exec chmod 644 {} \;

```
(of course, if there were files that needed to be executable they'd need to be worked on separately, but this is being done on a *data* partition so that shouldn't be a problem).

BTW: Having regular files (like text files) set to execute wasn't noticeable for me in Xubuntu (using Thunar file manager) but when using Nautilus it definitely was.


If you wanted a few different users to have access to that storage partition they could be added to the same group (like "users") and then change ownership for the group like: 
```

sudo chown -R :users /place_where_i_keep_stuff

```


[size="3"]The only other thing is that if the storage partition is shared between two Linux distros the UID and GID could be a factor - [coffeecat goes into that on the post here](http://ubuntuforums.org/showthread.php?t=329999). You can get those from /etc/passwd - see [here](http://www.ahinc.com/linux101/users.htm).[/size]


Like I said, I think i have a fairly good understanding of all this, but if I'm mistaken about anything please let me know. - thanks
_

---

