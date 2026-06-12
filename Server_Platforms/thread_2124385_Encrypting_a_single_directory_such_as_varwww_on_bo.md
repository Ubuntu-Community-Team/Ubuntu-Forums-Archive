---
title: "Encrypting a single directory such as /var/www on bootup.. Possible?"
date: 2013-03-10
forum: Server Platforms
---

### Post by kanadaguy on 2013-03-10
Hello I run a local lan server and I have sensitive customer info in the /var/www directory and wanted it encrtyped when the computer is turned off.  This way if the computer is physically stolen I don't have to worry about the private customer info.  Oh it also runs a sql database so I am guessing I would want to back that up too.. Not sure where that is located.  Anyhow is this even possible? I know you can encrypt the home folder and FDE but I am running this server and access it via ssh and the authorized keys file would be located on the encrypted partition so it will not be able to access it...

Any suggestions would HELP!  Thanks :)

---

### Post by agillator on 2013-03-11
Have you looked into Truecrypt ([http://www.truecrypt.org/)?](http://www.truecrypt.org/)?)

---

### Post by thnewguy on 2013-03-11
You probably want to make /var/www a separate partition and mount it using LUKS encryption. You will have to enter the password at each boot so that the partition will mount. And, yes, you should be backing up the www folder along with the database. Eventually the server will die or get hacked and you will want a backup on a second site.

---

