---
title: "problem following packaging new software directions."
date: 2013-02-18
forum: Ubuntu Application Development
---

### Post by pansz on 2013-02-18
Hello everyone, I want to pack and distribute some new software for ubuntu.

According to 

[http://developer.ubuntu.com/packaging/html/packaging-new-software.html]("http://developer.ubuntu.com/packaging/html/packaging-new-software.html")

the section "starting a package" it reads 

```
$ bzr dh-make hello 2.7 hello-2.7.tar.gz

```

however, dh-make is not a valid command of bzr.

I've tried
```
$ dh-make hello 2.7 hello-2.7.tar.gz

```

but dh-make is not a valid command it prompts dh_make instead.

when I try 
```
$ dh_make hello 2.7 hello-2.7.tar.gz

```

the help screen of dh_make prints and it seems that the command-line arguments are not accepted.

So, is this the correct document to go? is there any other document about how to create a .deb ?

---

### Post by pansz on 2013-02-18
[solved] need to install bzr plugins to complete the instructions.

---

