---
title: "rdiff-backup forced-command cannot execute script"
date: 2011-05-23
forum: Server Platforms
---

### Post by rfreytag on 2011-05-23
I am stuck.  I have read HOWTOs all over the place saying how to get rdiff-backup to use a public key with a 'command="(shell script name)"'.  The script then executes the client side version of rdiff-backup sudo'd which then safely backups up everything.  

I can do this using public-key authentication as root on the client with the forced command in the key on the client side.  But I just cannot get the forced-command in a script to work with rdiff-backup.  

BTW, I can get the forced-command to work with a script merely containing the 'ls' command.  

Totally baffled - as is apparently the folks at serverfault.com where I wrote this up in a lot of detail: [http://serverfault.com/questions/271518/rdiff-backup-fails-with-forced-command-but-works-through-shell](http://serverfault.com/questions/271518/rdiff-backup-fails-with-forced-command-but-works-through-shell)

I sure would appreciate some hint as to what I am missing.  Thanks! :)

---

