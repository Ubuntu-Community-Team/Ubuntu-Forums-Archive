---
title: "Need some help with reading list of files inside the script"
date: 2012-06-03
forum: Server Platforms
---

### Post by legolas_w on 2012-06-03
The problem may look obvious to you, but it is puzzling. Any help is welcome. Now the problem:
I am trying to load list of files with a specific extension in a directory inside my script and use them. I wrote the following script

```

#!/bin/bash
dir="/home/lego/books"
for f in `"$dir"/*."ray"`; do 
fullname=$(basename "$f");
filename=${fullname%.*};
echo "$f";
echo "$fullname";
echo "$filename";
done

```

When I execute this script file (named sm.sh) I get the following error message:

```

./sm.sh: line 10: /home/lego/books/book1.ray: Permission denied

```

There are some files like book1.ray, book2.ray... in the directory which I need to feed into another script I am writing to process them. However I am stopped with this error.

---

### Post by SeijiSensei on 2012-06-03
> ./sm.sh: line 10: /home/lego/books/book1.ray: Permission denied

There's your answer right there. The script can't gain access to that file.  Does the user running the script have execute permissions to /home/lego/books and read permissions on /home/lego/books/book1.ray?

Please post the results of this:
```

cd /home
ls -l | grep lego

cd lego
ls -l

```

By default, Ubuntu users have read/write/list ("rwx") permissions on the /home/username directory, and everyone else has no permissions at all.  Depending on how the files in /home/lego/books were created, user lego may not have permissions to them even though the files are residing in his/her own directory.  (For example, you could run an installation script as root that creates /home/lego/books and its contents with root owning all the files and having exclusive permissions.)

---

### Post by SeijiSensei on 2012-06-04
You marked the thread as SOLVED, but you didn't tell us what the problem was.  Was it a permissions issue?

---

### Post by legolas_w on 2012-06-04
Thanks for the reply. I deleted all directories and created them again. I am not sure how the permissions changed to the point i did not have the read access but after copying them again it works fine.

---

