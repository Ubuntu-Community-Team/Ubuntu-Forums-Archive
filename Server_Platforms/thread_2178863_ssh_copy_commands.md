---
title: "ssh copy commands"
date: 2013-10-05
forum: Server Platforms
---

### Post by remo2 on 2013-10-05
What is the command mode when i want copy a file remote.txt  to home directory?
By what command / how  to change to home.txt?
What is the command copy a fileeasy .txt from my notebook to server  a home directory folder as ´´an important´´ by easy2.txt file name?

---

### Post by steeldriver on 2013-10-05
```
scp remotehost:/path/to/remote/filename /path/to/local/newname
```

or to keep the same name and just copy remote 'file' to 'local' directory

```
scp remotehost:/path/to/remote/file /path/to/local/
```

e.g. to copy remote 'file' to the local current directory

```
scp remotehost:/path/to/remote/file **.**
```

To copy a whole directory recursively

```
scp **-r** remotehost:/path/to/remote/dir/ /path/to/local/dir/
```

I don't know what you mean by ``an important``

---

### Post by nerdtron on 2013-10-05
In addition to above, you can also use rsync:
Advantages:
1. Can resume interrupted copying.
2. Can show the progress of copying.
3. Same security as scp
4. Can update files on the destination.

I haven't used scp for a long time. 
Issue the commands on you notebook.
Here's the syntax, same as scp with extra options:
From remote.txt to your home directory (and change it to home.txt)
```
rsync -avh --progress username@serverIPAddress:/path/to/remote.txt /home/username/home.txt
```

From your notebook to the server and rename the file at the same time:
```
rsync -avh --progress /path/to/fileeasy.txt username@serverIPAddress:/path/to/homedirectory/easy2.txt
```

Be sure that the folders exists on the destination before you do the copying.
You can also make -avh into -avrh to copy whole folders and contents recursively.

---

### Post by remo2 on 2013-10-06
by impotrant i meant name of  folder just wanna now how to coppy from notebook to some folder *x*

---

