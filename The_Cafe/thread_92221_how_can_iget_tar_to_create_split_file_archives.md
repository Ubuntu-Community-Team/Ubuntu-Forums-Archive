---
title: "how can iget tar to create split file archives"
date: 2005-11-19
forum: The Cafe
---

### Post by kakashi on 2005-11-19
i want to back up my hdd and store it. but the place i want to star it (xbox ) has a fat filesystem that does not allow file larger than 4 gb. how i can i backup my files in split archives. kind of like rar part files.

---

### Post by GeneralZod on 2005-11-19
I'm not sure if tar itself provides this capability, but 

```

man split
```

could help.

---

### Post by kakashi on 2005-11-19
oh thanks i used split to split the file but  can't figure out how to put in back togather.
any help.

---

### Post by PatrickMay16 on 2005-11-19
[QUOTE=kakashi]oh thanks i used split to split the file but  can't figure out how to put in back togather.
any help.[/QUOTE]
I'm not sure, but maybe the "join" command would do it? I looked at the manpage for "join", but I'm not entirely sure if it's the command you need.

Worth a try anyway, right?

---

### Post by GeneralZod on 2005-11-19
You can just use "cat"

```
man cat
```

Since the split filenames are in alphabetical order (and all beginning with <prefix>), I would imagine that

```

cat <prefix>* > outputfile

```

would work, but i don't know for sure! (Obviously <prefix> should be replaced by whatever you chose as your split file prefix).

My recommendation would be to try the above "cat" command and then take an md5sum of outputfile to see if it matches your original file.  Be careful, and don't delete the originals until you are sure that the split versions can easily be reassembled into the original file! :)

---

