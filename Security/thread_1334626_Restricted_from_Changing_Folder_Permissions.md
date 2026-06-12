---
title: "Restricted from Changing Folder Permissions"
date: 2009-11-22
forum: Security
---

### Post by Mandraix on 2009-11-22
I recently downloaded the Java programming language for home use, but I can't use any of the executable files due to permission settings on the folder. The options are all grayed out and I'm given the message: "You are not the owner, so you cannot change permissions." Opening the terminal and logging in as root doesn't affect it. I'm sure this is something simple, but I haven't been able to find an answer through my own searches. Thanks for reading.

Ubuntu 8.10 Intrepid

---

### Post by cariboo on 2009-11-22
You use sudo to change the ownership and permissions of a file or directory. The change ownership of a directory type:

```
sudo chown -R username:usergroup <directory name>
```

the -R is to change ownership recursively.

To change permissions:

```
sudo chmod -R 755 <directoryname>
```

---

### Post by Mandraix on 2009-11-23
> chmod: missing operand after `+xjdk-6u17-i586.bin'
Try `chmod --help' for more information.

The above is the error returned, I apologize if I'm having trouble with some simple little thing.

---

