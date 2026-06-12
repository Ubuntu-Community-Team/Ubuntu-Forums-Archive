---
title: "backing up Server automatically"
date: 2013-05-14
forum: Server Platforms
---

### Post by CatorAde on 2013-05-14
hi guys,

my web-hosting server is up and running and do its job nicely :)

the next task i want to perform is to have my server backup every 12 hours, does anyone know of any software that will do this? or how i would go about it?

many thanks

---

### Post by CharlesA on 2013-05-14
Rsync via ssh for the win.

---

### Post by SeijiSensei on 2013-05-14
Expanding a bit on Charles's correct but brief answer...

Suppose your website is on [www.example.com](www.example.com) and stored in /var/www. At home you have a computer with a directory called /backup into which you want to write copies of the remote files.  You can run:

```

cd /backup
sudo rsync -av www.example.com:/var/www .

```

That will create the directory /backup/www with copies of all the files and directories there.  You'll need to have root privileges on the remote machine.  The best method for setting that up is using public-key authentication in SSH so you don't need passwords.  One other option to avoid passwords is running rsync in daemon mode on the server.  Read the rsync man page ("man rsync" at the prompt) for details.

Eventually when you have your backup configured to your liking, you would put the commands into a script and run it from cron.

---

### Post by CharlesA on 2013-05-14
I have also found [this page]("http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html") to be very helpful, and the [man page]("http://linux.die.net/man/1/rsync") is worth a read if you want to get into some of the different options rsync offers.

---

