---
title: "Accidently rm'd my.conf"
date: 2009-03-07
forum: Server Platforms
---

### Post by Godd on 2009-03-07
I went to go set up the my.cnf for MySQL and I accidentally rm'd it. 

DOH! Don't ask me how I can miss-type vim as rm. 

And I went to try to reinstall it and nothing seems to do the trick.

Then I tried purging it, but it won't allow it to happen due to the lack of the .cnf file. :/

So, what other means can I use to remove MySQL **entirely** as to allow a CLEAN install without my.cnf.

Oh, and I am in the process of making a Trashbin script. :]

---

### Post by drubin on 2009-03-07
```

sudo invoke-rc.d mysql stop
sudo aptitude remove mysql-server 
```

That should work... but if you are just looking for a standard my.cnf file that might be easier to locate :)

---

### Post by drubin on 2009-03-07
This might also work.
```
sudo dpkg-reconfigure mysql-server-5.0
```
[Source]("http://ubuntuforums.org/showpost.php?p=6342696&postcount=4")

---

### Post by Godd on 2009-03-07
Ha, I tried those and they're both stopped by errors.

Fixed it though.

I installed MySQL common after a purge then installed MySQL server on top of that.

I don't quite know how that worked but none the less it did.

---

