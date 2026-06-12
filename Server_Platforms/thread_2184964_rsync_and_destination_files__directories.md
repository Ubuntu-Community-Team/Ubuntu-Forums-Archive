---
title: "rsync and destination files / directories"
date: 2013-10-31
forum: Server Platforms
---

### Post by alfirdaous on 2013-10-31
Hello everybody,

I am trying to do a rsync file transfer from a server to another one using the below command:

```

rsync -e 'ssh -p 2345' -vrR  /home/alfirdaous/www/BackUps/ USER2@IP:/home/USER2/Store/

```

Once going to server2 (destination), I should go as below:

```

$: cd /home/USER2/Store/
$: ls
$: home
$: ls
$: alfirdaous
$: ls
$: www
$: ls
$: Backups
$: ls
AND HERE I FOUND AL FILES
```

How can I transfer my files, so if I go to:

```

$: cd /home/USER2/Store/

```

I will all files without browsing the whole directories.

Thanks in advance

---

### Post by Lars Noodén on 2013-10-31
I think it might be -R which is messing things up.  That makes rysnc use relative paths and it does look like you are trying to give absolute paths.  Also, it is more common to use -a for transfers, it is a shortcut equivalent of -rlptgoD and will make a proper backup including of attributes when possible.

```
rsync -e 'ssh -p 2345' -va  /home/alfirdaous/www/BackUps/ USER2@IP:/home/USER2/Store/
```

See if that copies the files and directories the way you expected.

---

### Post by alfirdaous on 2013-10-31
Thx [**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643") it works great

---

### Post by SeijiSensei on 2013-11-01
I often run a test with "rsync -avn" to see the list of files it intends to transfer.  Also how you define the filespecs matters a lot.
For instance, "/path/to/something/*" as a source will take all the files from that directory but none of their antecedent paths.

---

### Post by alfirdaous on 2013-11-02
Thx [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") for the suggestion, I would use that

---

