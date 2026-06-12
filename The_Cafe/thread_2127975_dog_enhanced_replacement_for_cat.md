---
title: "dog: enhanced replacement for cat"
date: 2013-03-21
forum: The Cafe
---

### Post by sgy on 2013-03-21
I recently learned about the dog command, but I can't find it anywhere.

Could someone help me find it?

Thanks.

---

### Post by pfeiffep on 2013-03-21
try this[ site]("http://mydevelopedworld.wordpress.com/tag/dog-command/")

---

### Post by sgy on 2013-03-21
Thanks.  The command is working well for me now, but I don't know how to install the man page.

```

sgy@computer:~$ man dog
No manual entry for dog
See 'man 7 undocumented' for help when manual pages are not available.

```

I would love to have that working properly.

---

### Post by cariboo on 2013-03-22
The only dog package available in the Ubuntu repositories is for Hardy (8.04), you can download and install it manually, and then:

```
man dog
```

works correctly.

---

### Post by sgy on 2013-03-22
I can get man dog to work when I install the binary with the Software Center, as was suggested.

In my case, however, I need to build the package from source.  I have done this, and the dog command is working, but I still don't know enough to get the man page working as well.

Also, I don't have root privelages on the system.  So, I can only install to my home directory.

Thanks.

---

### Post by sgy on 2013-03-24
To install the man page manually to a home directory first download dog.1.gz from the following site.

[http://manpages.ubuntu.com/manpages/hardy/en/man1/dog.1.html](http://manpages.ubuntu.com/manpages/hardy/en/man1/dog.1.html)

Make a few directories in your home directory so that you have ~/local/man/man1/, and move dog.1.gz there.

Now, just add ~/local/man to MANPATH by putting this line in .bashrc.

```
export MANPATH="$HOME/local/man/":$MANPATH
```

Now man dog will work properly.

---

### Post by prodigy_ on 2013-03-24
Enhanced, eh? Well... matter of taste, I guess. I wouldn't replace my old trusty **cat** with a weird command that partially emulates **tr** and **wget ... | grep**.

---

