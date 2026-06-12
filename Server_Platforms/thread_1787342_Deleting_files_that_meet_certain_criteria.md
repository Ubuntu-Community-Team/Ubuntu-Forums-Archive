---
title: "Deleting files that meet certain criteria"
date: 2011-06-21
forum: Server Platforms
---

### Post by Tumex on 2011-06-21
Hey there, hope you're doing great!

I'm here of course because I would like to know what would be the SSH command to issue if I need to delete certain files that meet certain criteria.

For instance, in this case, I simply have files that almost bear the same name but still have some very minor differences. They are logs.

Let me give you an example:
[B]L0619000.log
L0619001.log
L0619002.log
L0619003.log[/B]
L0619004.log

Those in bold are those I'd like to have removed, while the "L0619004.log" is obviously to be left intact.

Thank you very much for your help and have an awesome day! :popcorn:

---

### Post by falko on 2011-06-21
If the files that you want to delete are older than the other files, it is possible to do this time-based, like this:

```
for file in "$( /usr/bin/find /path/to/directory -type f -mtime +2 )"
do
  /bin/rm -f $file
done
```This would delete all files in /path/to/directory that are older than two days.

I suggest you take a look at the find man page:
```
man find
```

---

### Post by SeijiSensei on 2011-06-21
> L0619000.log
L0619001.log
L0619002.log
L0619003.log
L0619004.log


If you simply want to delete the files ending in 0-3 rather than an automated method like falko suggests, you can use this:

```
rm -f L*[0-3].log
```

That matches all files that begin with "L" and end with a number between zero and three.  It will leave the last file intact.

---

### Post by Tumex on 2011-06-24
> **SeijiSensei said:**
> If you simply want to delete the files ending in 0-3 rather than an automated method like falko suggests, you can use this:

```
rm -f L*[0-3].log
```That matches all files that begin with "L" and end with a number between zero and three.  It will leave the last file intact.
Thank you VERY much, this is exactly what I was looking for!

Have an awesome day! :guitar:

---

