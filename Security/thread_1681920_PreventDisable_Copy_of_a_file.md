---
title: "Prevent/Disable Copy of a file"
date: 2011-02-05
forum: Security
---

### Post by gnulab on 2011-02-05
Hi,

How do I prevent/disable a file from being copied?

I would want someone to be able to see the content of a directory, then open the relevant document, but just for viewing purpose. They cannot copy the file, either through copy + paste or File/Save As.

Is that possible under Ubuntu?

Henry

---

### Post by jbrown96 on 2011-02-05
If someone has read access to a file, he or she can copy it.

It's not possible with any system.

---

### Post by stlsaint on 2011-02-05
> **gnulab said:**
> Hi,

How do I prevent/disable a file from being copied?

I would want someone to be able to see the content of a directory, then open the relevant document, but just for viewing purpose. They cannot copy the file, either through copy + paste or File/Save As.

Is that possible under Ubuntu?

Henry

Im hoping you are trying to refer to some other procedure because if a user can view the contents how would you expect them not to be able to copy them? I mean you can remove the ctrl+c key bind but again if they can view it they can simply type it up somewhere else and have a copy of the file!

---

### Post by movieman on 2011-02-05
Only obvious solution I can see:

1. Make the files owned by a dummy user with no permission for others to access them.
2. Create some special program which would be setuid for the dummy user and only allow you to display the files, not copy the contents.
3. Remember that hiring some Chinese sweatshop workers on $0.50 an hour to retype the documents from screenshots is probably cheaper than breaking your security.

---

### Post by ljhffmn on 2011-02-05
Always remember that if a user can view the file all that that user need due is run the command:
```

cat /somedir/somefile > /someotherdir/someotherfilename 

```
And they have a copy.

Use proper security procedures and only share your files with people you trust.

You may want to take a look at gpg.

Good luck.

---

