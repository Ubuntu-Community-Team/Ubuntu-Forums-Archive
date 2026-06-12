---
title: "How to securely edit files on the server using FileZilla"
date: 2019-01-01
forum: Security
---

### Post by sstacker on 2019-01-01
I have an AWS EC2 instance running Ubuntu 18 with Apache2. Now I need to use FileZilla to edit files on the server's /var/www folder. The user provided by AWS if you use Ubuntu is called ubuntu, and that's the user I am connecting to FileZilla with. Currently I cannot edit any files on the server using FileZilla because permission is denied. What commands do I need to run in order to be able to add, move, delete files on the /var/www folder and that it will still be secured? I know it's something with chown and chmod, but I don't know which exactly.
Also, if I do change permissions while using FileZilla, do I need to change these permissions everytime I use FileZilla, and then revert it back to a secured state? Or I can have it permanent?

---

### Post by TheFu on 2019-01-01
File permissions are the cornerstone for all Unix system security.  Changing them for convenience, especially on a system connected to the internet is not a good idea. A common way "bad people" hack online blogs is due to incorrect file permissions.  There are over 2 million wordpress blogs running today, now, that have been hacked.

The safe way to edit system files on any Linux is to ssh into the machine, then use **sudoedit**.  You can specify any editor you like, assuming it is installed on the remote system.

For editing non-system files, the file permissions control which userid or groups are allowed that capability.  There's not single answer and I don't think filezilla or any other file transfer program is the solution to this problem.  Files in the /var/www/ directory structure have different permissions and ownership for security reasons.  There are techniques to make modifying those files more convenient, but a good understanding of file and directory permissions along with Unix groups is required.  There isn't any shortcut to gaining that knowledge.  You have to learn it.  Find a tutorial, follow it, then after you've mastered that, setup 3 new userids, 3 new groups, then mix and match which userids are in and not in each group.  Now, create some temporary directories + files in /tmp/ for each userid, and try every possible combination of the permissions until the understanding becomes clear.  Something should "click" in your mind.  For example, see when 711 on a file is exactly what you want or 710.  Same for directories.  Sometimes we need 704.  It just depends and only you can decide whether a 4, 5, 7 or 1 permission for the owner, group or other segments is workable.

There is also ACL permissions, but these raise an entire new set of issues.  In 25 yrs, I've needed to use ACLs twice because normal Unix permissions didn't work.

BTW, you do not **need** to use filezilla.  You may _want_ to use it, but it definitely is not any requirement.  People remotely administrate Linux systems world-wide without using filezilla daily.  I just hope it is using sftp for the transfers and not some other protocol with effectively -1 security.

---

### Post by sstacker on 2019-01-01
Thank you, I understand what you say, but maybe I can also study doing trial and error, as I need now, especially learning from someone with experience like you.
This is a good opportunity to study because I probably messed up some permissions right now when I allowed FileZilla to edit files on my machine.
Yes, I can SSH, it's just more convenient for me to use FileZilla, and it does use sftp.
Assuming I currently _CAN_ edit files using FileZilla, and I want to learn what I did in order to allow it to do so, what steps do I need to take? How can I tell what operations I did in order to make FileZilla be able to edit the files on /var/www? Let's say I want to revert it back to the beginning state, what do I need to do to make my server secured again?
And this is what I meant by "doing it everytime" - I don't mind to allow FileZilla edit files as long as it's temporary - every time I come to edit files, I give FileZilla the required permissions, then revert it back to a secured state - would love to know from you(An experienced person) how to do it, and also how to fix what I already did. I'm a complete novice

---

### Post by The Cog on 2019-01-01
I would suggest you do as TheFu says. 
Ultimately, learning to use an editor in ssh will be quicker than all the messing around with file permissions, which comes with the risk of a mistake leaving files open to hacking. 

A possible alternative if you are doing a lot of really heavy editing that you feel can't be reasonably done without a GUI editor is to use ssh commands to copy the original file to /home/ubuntu and use filezilla to copy from there, edit, filezilla back there, and then copy from /home/ubuntu to /var/www. This still comes with the possibility of copying with the wrong file ownership and permissions back into var/www though, so I do not recommend it.

Really, the most convenient thing is to learn to use an editor on the server through ssh.

---

### Post by TheFu on 2019-01-01
If it was a trivial issue, I'd tell you the chmod/chown command to run, but because I know ZERO about this system, I cannot.  All you said was apache, which doesn't say anything about the needed permissions that apache might be serving and that assumes there isn't a webapp or proxy or other very commonly used web tools.

Sorry.

Also, I'm probably not an expert on the specific webapp you are using.  Some need specific directories with 755 and others need 750.  Files might need to be 644 or 640 or 440.  And if the webapp is poorly designed, 1 directory might need 777 permissions. The last would indicated a lazy developer who doesn't care anything about security - or more likely - doesn't understand permissions sufficiently.

With all that said, for a production website, I'd probably handle deployments using either git or rsync and in the script, I'd force the permissions to be correct. That would make it reproducible and consistent. 

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a fairly comprehensive guide which happens to include a chapter on users, groups, and permissions. No-hassle download in multiple languages.

So, this simple question doesn't have a one-size-fits-all answer.  Sorry.

---

### Post by sstacker on 2019-01-02
Thanks,  I will try to use the SSH more now.
But, to be specific, now that I already changed permissions to allow FileZilla to edit files, how to bring it back to a secured state if:
-my user is called "ubuntu". 
-apache user and group are called www-data.
What permissions do I need to set on each? what chown and chmod commands do I need to run if I want it to be secured again?

---

### Post by TheFu on 2019-01-02
> **sstacker said:**
>  
What permissions do I need to set on each? what chown and chmod commands do I need to run if I want it to be secured again?

This simple question doesn't have a one-size-fits-all answer. Sorry.   It depends on the purpose, webapp, and how apache is configured.  That's the entire point I've been trying to make.

If you want commands, the only ones I could possibly suggest are 
```
sudo chown -R root:www-data /var/www
sudo chmod -R g+rX /var/www
```

But I doubt that is what you want.

---

