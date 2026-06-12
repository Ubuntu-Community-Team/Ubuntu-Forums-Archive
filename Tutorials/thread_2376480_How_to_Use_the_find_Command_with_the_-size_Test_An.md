---
title: "How to Use the find Command with the -size Test: An Explanation"
date: 2017-11-02
forum: Tutorials
---

### Post by John_Patrick_Mason on 2017-11-02
This thread is meant for those who are not quite familiar with the -size test of the find command, but still have some basic familiarity with how the find command works. The -size test of the find command can be deceptively simple. In its simplest form, the -size test with the find command, when typed, should look something like this:

```

find name_of_directory_that_will_be_searched -size (+/-)file_size

```

The first thing to keep in mind is that find will round up file sizes, though not always, as we shall see, before looking for any matching files or directories.
The other thing to keep in mind is that the rounding takes place **in the unit specified by the find command**.

Let's look at an example.

Suppose we have a directory with the following file sizes:

```

-rw-r--r-- 1 mason mason  26K May 27  2013 file1.txt
-rw-r--r-- 1 mason mason 1.3M Sep 20  2013 file2.txt
-rw-r--r-- 1 mason mason 155K Oct 28 20:33 file3.txt
-rw-r--r-- 1 mason mason 245K Nov 27  2016 file4.txt
-rw-r--r-- 1 mason mason 1.9M Jun 14  2014 file5.txt

```

If we were to type:

```

cd Documents
find . -size -2G

```

into a terminal, the find command would return the following results:

```

./file1.txt
./file2.txt
./file3.txt
./file4.txt
./file5.txt

```

which is what we would expect. Since we specifically asked find to give us files that were less than 2GB in size, hence the negative sign before 2G in the command above, find outputs files that are less than 2GB. Before we provide another example, we need to understand by how much the file sizes get rounded up to, before find searches for any matching files or directories. In the example above, since the rounding takes place in the unit specified by the find command, in this case -2**G**,  or gigabytes, file1.txt, file2.txt, file3.txt, file4.txt, and file5.txt get rounded up to 1GB, 1GB, 1GB, 1GB, and 1GB, respectively, and since all of those files, after rounding, are less than 2GB, find outputs all 5 of them.

Let's try another example.
Let's do the same thing, but with a smaller unit this time.
Let's type:

```

find . -size -2M

```

If we were to type the above command into the terminal, we would get:

```

./file1.txt
./file3.txt
./file4.txt

```

Why, though? Didn't we specifically ask find to give us files that were less than 2GB? Not quite. The reason has to do with how file sizes are rounded up to. Before getting processed by the find command in our second example, file1.txt, file2.txt, file3.txt, file4.txt, and file5.txt get rounded up to 1MB, 2MB, 1MB, 1MB, and 2MB, and since we just told the find command to search for files that are less than 2MB in size (after rounding), hence the negative sign before 2G, find will only output three files: file1.txt, file3.txt, and file4.txt. OK, but, technically, file2.txt and file5.txt are less than 2MB, so how do we get the find command to search for files that are less than 2MB? One way to accomplish such a task, is through the use of the logical operator -or or -o for short. If we were to type:

```

find . -size -2M -o -size 2M

```

find would output all files that are less than 2MB: file1.txt, file2.txt, file3.txt, file4.txt, and file5.txt. By adding the test "-o -size 2M", which is meant to mean: "search also for files that are equal to 2MB" (after rounding), file2.txt as well as file5.txt end up in the output.

Let's give one last example.
Suppose we were to type:

```

find . -size -200k

```

If we were to type the above command, find would give us two results: file1.txt and file3.txt. Since the unit of the find command is in kilobytes, *and* since the rounding is supposed to take place in the specified unit of the find command, and since the file sizes that in are in kilobytes in our directory don't have any decimal places: file1.txt and file3.txt are left intact and are not rounded up before getting processed by the find command, which means that find sees file1.txt as a 26KB file and file3.txt as a 155KB file. file4.txt is also left intact, since the rounding is in kilobytes and since the file doesn't have any decimal places. As for file2.txt and file5.txt, something interesting happens. Even though both files have decimal places, they do **not** get rounded up, since the rounding takes place in kilobytes and both files are in megabytes. Consequently, find sees file2.txt as a 1.3MB file and file5.txt as a 1.9MB file, and since we specifically asked for files that are less than 200KB (after rounding), both files don't show up in the output.

[B]Special use case:
[/B]
Typing:

```

find . -size -1k/M/G

```

with any unit, will always match empty files. The reason is that as soon as a file is 1 byte large, the file gets rounded up to the specified unit of the find command, either k, M, or G. The only way for that not to happen is for the file to be empty. So a 1 byte file will get rounded up to a 1KB file if we were to type:

```

find . -size -1k

```

Note to everybody else: Please feel free to correct any part of my post if you feel I've made a mistake.
Keep in mind that this is not a man page, it's not meant to be technical.

---

### Post by John_Patrick_Mason on 2017-11-03
I'm also open to feedback if anybody is willing to spare some of their time.

---

