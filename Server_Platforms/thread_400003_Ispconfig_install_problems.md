---
title: "Ispconfig install problems"
date: 2007-04-03
forum: Server Platforms
---

### Post by M0rThden on 2007-04-03
I just now finished the tutorial i got from the ispconfig website. Everything there got installed fine and isnt returning any errors. I copied ispconfig onto the hard drive and when i try to install it, it claims i dont have access. Im trying it as root and it still wont give me access.

Whats the chmod code for unlocking it. I thought chmod 666 was supposed to give me access but i dont think its working...

here is some code...

```
root@poweredge:/home/administrator/ispconfig# ./setup
bash: ./setup: Permission denied
root@poweredge:/home/administrator/ispconfig# chmod 666 ./setup
root@poweredge:/home/administrator/ispconfig# ./setup
bash: ./setup: Permission denied
```

---

### Post by huygens on 2007-04-03
you are looking for chmod 777 ;-) but it is probably really unsafe.

explanation:
basically, chmod use 3 octal digits.
1: executable
2: writable
4: readable

So 6 means 4+2 which is writable, readable but not executable.
7 4+2+1 is writable, readable and executable

So now you have 3 digits. The first one is for the owner of the file, the second one is for any one belonging to the group of the file, the third one is for everyone.
So if you are the owner of a file, you might want to set: chmod 700 myfile
so only you can read/write/execute the file, people from the group and others cannot.

there is much more to say, but I would recommend 'man chmod' :-)
for example, you can write: chmod u+x myfile to simply add executable rights to the file for the owner :-)

---

