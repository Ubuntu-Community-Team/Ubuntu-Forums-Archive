---
title: "Document all Server Settings"
date: 2011-02-15
forum: Server Platforms
---

### Post by tadamadeit on 2011-02-15
Does anyone know a way to fully document any existing Ubuntu server and  all the setting into a printable format ? A piece of software or any  other means ? A script ?
This would be to have as a document to if needed to rebuild the server from nothing. Over and above a back up of the server. Every single configurable setting.

Thanks

---

### Post by wormyblackburny on 2011-02-15
Technically all of the files are already in "printable" format as most of the .conf files are simply textfiles. I would just pull up each .conf file and print them or better yet export a copy of them to a backup directory and ship it to a USB stick, then if u had to do a rebuild you could just copy the originals over the top of the conf files on the new build...

---

### Post by koenn on 2011-02-15
I've toyed with the idea of automatically generated system documentations (I'm a lazy sysadmin).

Here are some ideas
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

towards the bottom of that page, there's a script  that tries to wrap it all up and generate s set of text files that document pretty much the entire system.

---

### Post by tadamadeit on 2011-02-15
> **wormyblackburny said:**
> Technically all of the files are already in "printable" format as most of the .conf files are simply textfiles. I would just pull up each .conf file and print them or better yet export a copy of them to a backup directory and ship it to a USB stick, then if u had to do a rebuild you could just copy the originals over the top of the conf files on the new build...


I agree with your statement. It is that pulling up each file and print them. Trying to do a comparison of multiple servers to make sure they are all configured with consistency.
Most are already up and running. Need to get all this into a spreadsheet. I think some of the files needed are not all .conf ??

---

### Post by tadamadeit on 2011-02-15
> **koenn said:**
> I've toyed with the idea of automatically generated system documentations (I'm a lazy sysadmin).

Here are some ideas
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

towards the bottom of that page, there's a script  that tries to wrap it all up and generate s set of text files that document pretty much the entire system.


Thanks will check it out. Like many we all are lazy when it comes to documentation and assume the backup will be enough.  But I have seen outages that occurred after undocumented changes and with the backup failure the night before. ):P

---

