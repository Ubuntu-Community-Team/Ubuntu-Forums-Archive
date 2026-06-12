---
title: "empty directory test via ssh"
date: 2023-03-21
forum: Ubuntu, Linux and OS Chat
---

### Post by awerik on 2023-03-21
Hello,
I'm trying to tweak a script for synchronizing files between servers.
At one point I need to check if a directory on server 2 is empty or has files to start or rsync.


I'm using the following code to test.



if [ "$(ssh root@meuIP ls -A /data/teste/transfer/ 2>/dev/null)" == "" ]; then echo "VAZIO"; else echo "CONTEM ARQUIVOS"; fi
Ele funciona como linha única direta no shell, mas quando coloco ele dentro do script ele não funciona.


CODE:
Declaration of variables bla bla



if [ "$(ssh $server2 ls -A $DIR_ 2>/dev/null)" == "" ]; then
rsync --dry-run --remove-source-files -avzrh "$SRV_PRD2":"$DIR_PRD2" "$DIR_PRD1"


EXIT:
root@server1:~# sh -x /data/teste/s5.sh
+ ssh root@ip ls -A /data/teste/transfer/
+ [  ==  ]
/data/teste/s5.sh: 35: [: unexpected operator
+ exit 0


Can you help me understand the error?


Thanks

---

### Post by TheFu on 2023-03-21
space needed on line 35?
expecting root remote access to work?  It is disabled on all official Ubuntu systems.  Learn to use sudo.

Does the exact command work from a shell?

BTW, hard to know which shell interpreter you are using when it isn't provided.

---

### Post by TheFu on 2023-03-21
If I wanted to test whether a directory existed on a foreign machine, I'd use a **test -d **command.

```
ssh istar ' [ -d /TV/Recordings ] && echo "Recordings dir exists" || echo "No Recordings exist" '
```
You could return 0 or non-zero results and check that in the $? variable to decide if continuing makes sense too.

If you like, you could have a .needs-processing file in the directory and check whether it exists or not.  When the directory is full, just **touch** that file to let the next script know. When processing finishes, remove the file.

---

