---
title: "server upgrade crash + root passwd"
date: 2011-12-20
forum: Server Platforms
---

### Post by highspider on 2011-12-20
Maverick - to - Natty

I was "sudo do-release-upgrade" across ssh.  everything installed up to config files.  I was comparing deference's on config file ctrl+(D).  I did stupid mistake and exited with :ctrl+(c) instead of :q  --I think  

I went to the server.  And tried to boot. Oldest Kernel in grub works the best.

[COLOR=Red]FATAL /lib/modules/xxx-generic-pae/kernel/drivers/crypto/padlock=sha.ka
 no such device
[/COLOR]
NOTE:
THE FILE padlock=sha.ko does exist

disk drive for "/" not found or not ready
wait; - press "s" skip or "m" for manual triing M

I've reinstalled grub to master boot record via server cd
I've fixed root passwd via server cd
fstab has correct UUID's

NOTE:
   I can access the filesystem and no files seem encrypted

---

### Post by aeiah on 2011-12-21
i cant help with restoring your damaged install, but i thought id suggest in future that you use screen or tmux when performing operations that may take time. if you disconnect, the session will still carry on and you can reattach at a later point.

---

### Post by highspider on 2011-12-21
THANKS FOR REPLY 
This was the First time every upgrading on my First Server Every.   I will never use ssh again for thing type of operation.:( 

I Download the disk for Natty Server and I'm just going to try reinstalling when I get home.  If Its possible to do with out overwriting my website files and personal files.:(

If its not possible-  I'm going to pull the hard drive and plug it in to home system to copy all files I need then reinstall.:(

There maybe an easier fix but I don't know it! so this is "fastest" based on my limited knowledge.

[COLOR=Red]---EDIT added below text to my post [/COLOR]
[COLOR=Black]IF someone is reading trying fix there problem this is not a good solution just the one
I choose so please look for a better one for your error.

I used a ubuntu cd recovery mode to access the hard.
I wiped as many file permission off as I could. (gave files to normal user on that system)
```

cd /
chown -hR <commanuser> *
chrgp -hR <commanuser> *

```Pulled the server hard drive out of computer and put it on my home system
copied as many files as I could (over kill) just in case I forgot one 
just made sure mostly of my needed
1) my old config files    
2) my home folder files
3) my website data

doing new install and using old preferences configure files as needed.
No matter what I do I have backups now.




[/COLOR]

---

