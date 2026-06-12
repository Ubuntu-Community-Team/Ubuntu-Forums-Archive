---
title: "how to undo chmod -R 755"
date: 2008-07-27
forum: Server Platforms
---

### Post by RHAnthony on 2008-07-27
A backup script was accidentally run a few directories below where it should have.  the chmod -R 755 has affected about 20 website structures that shouldn't have been touched.

My curiosity now goes to, how can one undo such a change?
Is it at all possible?

Is there some way of outputting the current state of file attribs to a file, as say, a daily/weekly cron job?

The hope with that being that parsing that file, could restore the previous attribs and permissions should something like this happen again.

Anyone?

---

### Post by Keith Hedger on 2008-07-27
i dont think there is any way of automatically undoing what u did but for future reference u can use```
ls -l /path/to/folder 
``` to get a listing of files and folders and their current permissions

---

### Post by RHAnthony on 2008-07-27
I guess I should rephrase my desires for the cron thing.

I can ls -l to a file for the whole server if need be.
But, does anyone know of anything already made, or how one would go about making, a script to parse that info out, and use it to re-attrib all files?

I'm not so good with parsing it back out to something useable.

---

### Post by skunkbad on 2008-07-27
From what I've read, Linux has no undo. You will have to manually go in and change permissions for all of the files and directories that were changed. Chmod might be able to be run in interactive mode, and if it can, then this would have been a good time to have used it.

---

### Post by osx424242 on 2008-07-27
> **RHAnthony said:**
> I guess I should rephrase my desires for the cron thing.

I can ls -l to a file for the whole server if need be.
But, does anyone know of anything already made, or how one would go about making, a script to parse that info out, and use it to re-attrib all files?

I'm not so good with parsing it back out to something useable.

I think I know how to do this, although it's probably not the most efficient way.

(you could combine these steps, but I'm listing them separately for clarity)

awk '{print $1 " " $8}' < savefile.txt > step1.txt

(gives you just the 'rwxrwxrwx' and filename; depending on your system type and 'ls' options, you might need to use something other than fields 1 and 8 )

sed s/^[d-]//g < step1.txt > step2.txt

(strips the leading 'd' or '-'; maybe stick an 'l' inside the brackets ('[d-l]') if you have links, too)

sed s/rwx/7/g < step2.txt > step3.txt

(repeat for s/rw-/6/g, s/r-x/5/g, ... s/---/0/g.  This will give you switches for chmod.)

sed s/^/chmod\ /g < stepn.txt > steplast.txt

(sticks "chmod " at the beginning of each line; probably could've combined with the first step)

Now make 'steplast.txt' executable (chmod 500 steplast.txt) and run it.  It'll call 'chmod' a couple bazillion times (well, `find . -print | wc -l` times, actually ;) ) so it's probably not the most efficient way to do this, but it should get the job done.


That's a lot of steps, but if you stick them all in a script (and test it out pretty thoroughly!!) you should be able to make it work.


Now someone will come along and tell us that there's already a GUI tool in the repositories to do this ;)

---

### Post by Keith Hedger on 2008-08-03
This wont be of help now but I have done similar things so I created a small app to record/repair permissions so checkout: [http://code.google.com/p/perms/](http://code.google.com/p/perms/) for future use.

---

### Post by windependence on 2008-08-03
Do you have any backups before the problem? How would this happen with a backup? If your backups are changing your file permissions you should use something else. What if you had to restore? If you have 20 web sites you should have a good incremental backup and you would be up and running in less than an hour.

-Tim

---

