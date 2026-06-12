---
title: "Simultaneous Commands"
date: 2007-08-23
forum: The Cafe
---

### Post by Gwasanaethau on 2007-08-23
Hi y'all. This is probably the wrong forum, but here goes anyway! I'm in the middle of writing a backup script for my documents, and I want to archive four folders at once. Of course I could just do:
```
tar -czvf Folder1.tar.gz Folder1
tar -czvf Folder2.tar.gz Folder2
tar -czvf Folder3.tar.gz Folder3
tar -czvf Folder4.tar.gz Folder4
```
but that's boring and will only archive each one in sequence. Is there any way to get all four to start 'tarring' simultaneously and then make the shell wait until all four archives are finished before taking a new command?
```
tar -czvf Folder1.tar.gz Folder1 &
tar -czvf Folder2.tar.gz Folder2 &
tar -czvf Folder3.tar.gz Folder3 &
tar -czvf Folder4.tar.gz Folder4
```
…won't work if any of the first three folders take longer to archive than the last one does.

---

### Post by Gwasanaethau on 2007-08-23
For those of you who might be wondering, I think I've figured it out:
```
tar -czvf Folder1.tar.gz Folder1 &
ARCHIVE1=$!
tar -czvf Folder2.tar.gz Folder2 &
ARCHIVE2=$!
tar -czvf Folder3.tar.gz Folder3 &
ARCHIVE3=$!
tar -czvf Folder4.tar.gz Folder4 &
ARCHIVE4=$!
wait $ARCHIVE1 $ARCHIVE2 $ARCHIVE3 $ARCHIVE4
```

---

### Post by rolando2424 on 2007-08-23
Wouldn't 

tar -czvf Folder1.tar.gz Folder1 && tar -czvf Folder2.tar.gz Folder2 && tar -czvf Folder3.tar.gz Folder3 && tar -czvf Folder4.tar.gz Folder4

work?

---

### Post by pelle.k on 2007-08-23
Since i think bash is fun (and confusing at times...), i'll drop in an alternative for you to experiment with :)

```
archives="folder1 folder2 folder3 folder4"
for name in $archives
do
tar -czvf "$name.tar.gz" "$name" &
pid="$pid $!"
done

wait $pid
```

This way you will only have to adjust your variable content. You could of course automate it even further if you wanted to.

---

### Post by rolando2424 on 2007-08-23
> **pelle.k said:**
> Since i think bash is fun (and confusing at times...), i'll drop in an alternative for you to experiment with :)

```
archives="folder1 folder2 folder3 folder4"
for name in $archives
do
tar -czvf "$name.tar.gz" "$name" &
pid="$pid $!"
done

wait $pid
```

This way you will only have to adjust your variable content. You could of course automate it even further if you wanted to.

What? No indent? :lolflag:

If the names change, wouldn't it be better to put a "read" in the beggining of the file, so that it could (I think) be piped with a command like "find -mtime 1" (finds every file modified in the last 24 hours) with a command like "find -mtime 1 | backup.sh"?

---

### Post by Gwasanaethau on 2007-08-24
> **rolando2424 said:**
> Wouldn't 

tar -czvf Folder1.tar.gz Folder1 && tar -czvf Folder2.tar.gz Folder2 && tar -czvf Folder3.tar.gz Folder3 && tar -czvf Folder4.tar.gz Folder4

work?
That's what I thought originally, but it seemed to do weird things (like executing any shell scripts stored in the folders). Couldn't figure that out.
> **pelle.k said:**
> Since i think bash is fun (and confusing at times...), i'll drop in an alternative for you to experiment with :)

```
archives="folder1 folder2 folder3 folder4"
for name in $archives
do
tar -czvf "$name.tar.gz" "$name" &
pid="$pid $!"
done

wait $pid
```

This way you will only have to adjust your variable content. You could of course automate it even further if you wanted to.

Wouldn't that still just archive each folder one after another (with each iteration of the 'for loop'?

No, my mistake - not using my eyes as usual. That would make more sense. Looks cooler too!

---

