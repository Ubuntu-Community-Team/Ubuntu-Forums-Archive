---
title: "copying files from remote server. (naive question)"
date: 2019-12-18
forum: Server Platforms
---

### Post by bjngchn on 2019-12-18
Here is a very elementary question:  

How can I copy/move files from a server using command line?  

I logged in via ssh, and I see folders there. and I want to move those folders and files to my laptop. 

I know I have to use cp command, but I don't know how to name the server and my laptop.   

For example I want to move the whole /home directory on the server to my laptop. 
What would be the command, when I'm on the remote server?  

cp /home  /my-laptop ?  


Or do I need to go back to my laptop,  and  copy when I'm on the laptop directory?

  ...............  
We had a site there, but our webmaster just disappeared.. And I need to  copy files and remove all data on the server. 
Do you think all data we have would be under /home directory?   For example I  see directories like:  boot, dev, etc,  run, vmlinuz, lib64, tmp,.. 
Would they contain essential info as well, or are they only part of the system? 
 ........... 
My laptop is kubuntu, and the server is ubuntu.
   .... 
How can I open files on the server using  dolphin?  I tried , it failed. 
 .......... 
How can check sizes of directories and files?
  .. 
Should I do  some chmod'ding before  moving files?
   ..............
 Is there a simple command to erase all data? (I remember dd )

---

### Post by howefield on 2019-12-18
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by bjngchn on 2019-12-18
UPDATE:  

While using doplhin on the laptop, I was able to add the server as a network folder. BUT, I can't view most of the data, 
probably because of their chmod status? I see folder, I click on them, and /home direcory looks empty:
It shouldn't be.

Hope it doesn't become less visible now. This is an urgent matter.

---

### Post by TheFu on 2019-12-18
scp, sftp, rsync, 

scp uses the same input as the default shell prompt shows.
```
thefu@posc:/tmp$ 
thefu@hadar:/tmp$ 
```
so the scp command to copy a file from a remote system, hadar, in the /tmp/ directory to my local system, posc, would be:
 ```
scp  thefu@hadar:/tmp/testfile.mpg /tmp/ 
```

If the username on both systems is the same, it can be left off.
 ```
scp hadar:/tmp/testfile.mpg /tmp/ 
```
If you setup ssh-keys between the systems, none of those commands will require providing credentials. The ssh-keys will be used automatically.  To set that up, on the client machine, run 2 commands:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
That will solve ssh, scp, sftp, rsync, and 50+ other ssh-based connections.

All of these work just by installing ssh, fail2ban and rsync on both the systems.
```
sudo apt install ssh fail2ban rsync
```

---

### Post by TheFu on 2019-12-18
All the website command answer are, "it depends."

It depends on what the web hosting provider is, how they've setup things, is it a VPS or just a shared host?  Are there multiple different userids? Is the web-data userid different from the login userid you have?  

"It depends."  You'll need to know much more for any reasonable answer.

As usual, start from the beginning and work through a book like this: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) chapter by chapter.  Be certain you understand permissions for files and directories.

---

### Post by bjngchn on 2019-12-18
Thanks.

Still not clear enough.

Let's say I connect  via ssh and I see /home1  folder on the server's root directory.

And I decide to move home1 folder together with all its contents to  ~/Documents on my laptop.

Is this the command then?


scp  -r serveruser@host:/home1/      ~/Documents/


If so ,  I think this thing needs to be done while I'm on the laptop, not on the server, right?

......
How about the other way around: do the same while I'm on the server? (more complicated?)

---

### Post by TheFu on 2019-12-18
Try it? See what happens.

Also, this copies. It does not move.  If you want the files gone, do a copy first, then delete them after you are positive nothing will be lost.

For which side (client/server) the command needs to be run, that's up to you and connectivity.   Often, the server has public ssh connectivity, but a desktop wouldn't.

For recursive copies, I'd use rsync.  rsync has a --dry-run option if you don't want to actually copy stuff.

```
rsync -avz serveruser@host:/home1/ ~/Documents/
```
if you want lots and lots of feedback, use
 ```
rsync -avz --progress --stats      serveruser@host:/home1/     ~/Documents/
```
It should be obvious, but which files can be accessed on "host" by serveruser is completely limited to local directory and file permissions on that remote system.

BTW, if you have funny usernames, ugly remote-server-hosts/IP addresses or non-standard ssh ports, check into setting up a client-side ~/.ssh/config file to make those things automatically handled.  I've written about this here a few times.  The settings are documented in **man ssh_config**, but there are lots of simple examples on the web.

---

### Post by bjngchn on 2019-12-18
I can connect via SSH to   root@host (host here is an IP number). 

And I see home1 directory under root directory.  

Then I exit and try from my laptop directory this command:

    scp -r root@host:home1   ~/Documents

  I'm asked the pw needed for ssh.  I type it, and it says, 
no such file or directory.  So it looks like  home1 was not named correctly.   

So although mmy username is root when I ssh, maybe it is something else, when I'm a user on the server?  

home1 directory appears as:

   loft123:/home1#  


when I'm logged in via ssh on the terminal.

Am I supposed to use loft123 as user (instead of root), when doing scp?

---

### Post by TheFu on 2019-12-18
```
scp -r root@host:home1 ~/Documents
```
is not the same as
```
 scp -r root@host:/home1 ~/Documents
```

Simple typo or do you need to review the difference between relative and absolute paths?  Again, with scp you can probably copy+paste the bash prompt to have the correct remote information.

>  Am I supposed to use loft123 as user (instead of root), when doing scp? 
How can anyone else know that answer?  It depends.  If you want to retain all permissions, owner+group, then you need to do things very differently from the client-side.

Allowing remote root direct access, especially with a password is asking to get hacked.  Use ssh-keys, please, please, please.

---

### Post by bjngchn on 2019-12-18
Hacking is not possible. Also I will just copy files and kill the server. (erase all data, etc..).
 Also I modify  keywords .

  I did :   whoami   on while on the server.   it said : root.  

And I  had typed the correct version;  with : / 

still it didn't work.  
................. 
I add the root directory of the server as a Network Folder , on dolphin.
  it is added. I see main directories. But I can't see their contents.  
Maybe I should do chmod -r 777  *  first.  Noone would know I did it. until I copy all files ..

---

### Post by bjngchn on 2019-12-18
Ok, it works with -r   , but only the  home1 folder, but NOT its contents are copied. 

How can I make sure I get all its contents as well?

I will do chmod, if it helps.

---

### Post by bjngchn on 2019-12-18
Ok, to help you in solving this mystery and fixing this problem I wll give some info.

Sometimes I can't see contents of the root folder of the server, instead see:  


root@loft12345:~# dir
README_DE  README_EN  e2fsck-static_1.45.3-4ubuntu2_amd64.deb 


So I do:  

chroot /mnt/

I don;'t know what this means, but it is like deencrypting something???


Then it becomes: 


loft112345:/# dir
... bin  boot  dev  etc  home ....

So you see the change.  Not only I can see folders now, but also, 
root@ part disappeared. 

..................
Now, when I try to use scp, AND, when trying to view this server as network folder on dolphin, 
something may be hidden because of chmod? or encryption? ..

............
Anyway, one way of copying will be enough. but nothing works so far, because contents of directories are not 
visible in all methods. If I could do sudo on the remote server, while I'm on local server, this could fix this problem, I think.

---

### Post by bjngchn on 2019-12-18
By the way I can't edit this post to fix minor typos, ..the browser freezes. local server --->local laptop

---

### Post by SeijiSensei on 2019-12-18
I'd use
```

cd ~/Documents
rsync -avz root@server/home1/ . 
```
The "." represents the current directory. This will create the directory ~/Documents/home1 on the local machine and recursively copy the content of /home1 from the server.

rsync is very powerful but you have to be careful with syntax when specific the source and target directories. By using a trailing slash in the source specification I include both the directory /home1 and all the contents it contains.  Without the slash it will only copy the directory entry for /home1. See the examples section of the extensive manual page for rsync (type "[man rsync]("https://linux.die.net/man/1/rsync")" at a prompt).

When first starting out with rsync, I strongly endorse the use of the --dry-run parameter that TheFu mentioned.  Run the command above with --dry-run on the end first to see what will be transferred.
```
rsync -avz root@server:/home1/ . --dry-run
```

---

### Post by TheFu on 2019-12-18
>  I don;'t know what this means, but it is like deencrypting something???
Typing random commands like chroot isn't helpful.  In this case it harms your goal.  Do not type commands you don't fully understand, especially as root.  chroot is a command for a very special purpose and has nothing at all to do when anything we were trying to accomplish in this thread.  chroot is probably mentioned in less than 0.5% of the threads in these forums.

You need to safely exit out of that environment type **exit;** over and over and over until all the chroot layers are done.

**~/** and **/** are NOT the same places.  Again, I'll ask if you need to review absolute paths and relative paths?

And NEVER type **chmod -r 777**.  It always does more harm than good, IMHO.  Plus it has the wrong option.

Instead of typing **dir**, please use **ls -la**   dir shouldn't even work on Linux.

Unrelated: The newest versions of chrome and chromium browsers had a bug that has been reported earlier today. That could be causing the browser issues. I don't know if you are impacted or not.  I patched last Saturday and don't have the issue.  Firefox is not impacted, at least the version from last Saturday morning is not.

If ssh works, then scp should work. If the connection is as root, then only some really stupid permissions would prevent root from having access to the files ... or using chroot.  Again, I would use rsync to accomplish what you are trying to do.  I've provided the command in post #7.  rsync must be installed on both sides, but it works over ssh.  scp is fine for a few files.  rsync is designed for entire directory structures.

Minor typos matter here.  I assume what you type is actually what you typed. Cannot do anything else, right?

I'm afraid we aren't communicating well. I'm so sorry for my failure.  Hopefully, someone else will come along to help who can understand better than I've been able and proves better guidance.

---

### Post by bjngchn on 2019-12-18
Thanks to all. 

Still it doesn't work.


But scp works for all directories except the home1 directory of the server (it is the  home directory from the installation) (and anything under that directory).
Anything under home1 directory of the server can't be seen by scp and dolphin-network-folder.

Even chmod 777 doesn't seem to help (am I doing i correctly)? chmod 777 -R  /home1/


NOW I SUSPECT this happens because the home directory is encrypted. 
Any other possible explanation?

Pulling doesn't work. so maybe pushing can ?? If so, how?

---

### Post by bjngchn on 2019-12-18
Why I used chroot /mnt/

because,, sometimes when I login with ssh, I don;t see actual files and instead login in
RECOVERY MODE (why?:  have no idea), and this command fixes the problem. 
It was suggested by the hosting company. 


But it seems to be obvious now, that this  problem is related to some difference between the home directory of the server, and other directories.
Only explanation I can imagine is: encryption. I use encrypted kubuntu in the laptop, and probably our server also has encrypted home directory at least. 

,

---

### Post by TheFu on 2019-12-18
A web server at a hosting provider wouldn't use home directory encryption. That would break ... uh ... serving web pages.
It is something else.  

ssh, scp, rsync are pretty basic things.  Sorta just work.  When they don't, NONE of them work.  Try everything without root?

---

### Post by aljames2 on 2019-12-18
May not help in your case but the find command is useful to identify all directory permissions (or file permission, -type f) from a particular point and down the tree from there.

```
[COLOR=#333333][FONT=UbuntuMono]sudo find /path/to/someDirectory -type d -print0[/FONT][/COLOR]
```

A study of file & directory permission may be in order to get a handle on it.  The -R can be risky on chmod as it changes recursively all folders & files down the tree from the directory you reference in the command.  You don&#8217;t want your files at 0777, you rarely want directories with 0777.  More normal for directories to allow only the owner read/write access is 0755.  Of course, you don&#8217;t want to be messing with root system directory or file permissions from their defaults.

[https://help.ubuntu.com/community/FilePermissions#Recursive_chmod_using_find.2C_pipemill.2C_and_sudo](https://help.ubuntu.com/community/FilePermissions#Recursive_chmod_using_find.2C_pipemill.2C_and_sudo)

---

### Post by The Cog on 2019-12-19
Can you post the output of the command **mount | grep /dev** for us (run on the server)? This may help us understand what's going on.

Also, use the file manager on your PC, type Ctrl-L and enter the location **root@server/** . This should let you browse the server directories and maybe better understand the structure.

---

### Post by bjngchn on 2019-12-23
Sorry for late reply.. 

This is the result of the command when the server  is in recovery mode.

# mount | grep /dev 
none on /dev type devtmpfs (rw,relatime,size=16193384k,nr_inodes=4048346,mode=755)
none on /dev/pts type devpts (rw,relatime,mode=600,ptmxmode=000)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
/dev/md2 on /mnt type ext4 (rw,relatime,data=ordered)
/dev/md0 on /mnt/boot type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)
none on /mnt/dev type devtmpfs (rw,relatime,size=16193384k,nr_inodes=4048346,mode=755)

And this one is after  I  get out of recovery mode by  typing chroot /mnt/

 mount | grep /dev
/dev/md2 on / type ext4 (rw,errors=remount-ro,usrquota)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/md0 on /boot type ext2 (rw)



I can't control whether it is recovery mode or not (and whatever it means), except that if it is in recovery mode and I'm on the server
I can use chroot /mnt/ to exit that mode.

---

### Post by TheFu on 2019-12-25
> **bjngchn said:**
>  I can't control whether it is recovery mode or not (and whatever it means), except that if it is in recovery mode and I'm on the server
I can use chroot /mnt/ to exit that mode.

That isn't what a chroot does. Chroot is one of the commands that really should be understood before **any** use.  The manpage for it is the best source of information about it.

```
man chroot
```

---

