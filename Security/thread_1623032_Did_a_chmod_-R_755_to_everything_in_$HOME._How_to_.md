---
title: "Did a chmod -R 755 to everything in $HOME. How to come back ?"
date: 2010-11-16
forum: Security
---

### Post by sheoly on 2010-11-16
Hello,

Everything's in the title :

I did a chmod -R 755 to everything in $HOME.
That was a really idiot manipulation because all the files (even not exe files) can now be executed.

Thanks!

---

### Post by Vaphell on 2010-11-16
try something like this

```
find ~ -type f -exec chmod -x {} \;
```
= find all files (-type f) in your homedir (~) and clear executable bit (chmod -x) on them ({} stands for the name of a matching item). Read about find and chmod to know what your options are (**find --help**, **chmod --help**), it's a very useful knowledge. Especially find is good to be friends with, you can do a lot with it :)

probably it's not the best idea to run the command on the whole home dir (find ~), as it will affect also true executable files you may have in various places (custom scripts, wine programs, ...). You can fine tune the find command to be more specific (for example ~/Music instead of ~, add some additional conditions on file names, etc). Do some research and test it on some dummy set of files to be sure you know what should happen.

---

### Post by Rubi1200 on 2010-11-16
No disrespect intended to Vaphell, but I have something better:

To change permissions back to the defaults:
```
find ~ -type d -exec chmod 0755 '{}' +;
find ~ -type f -exec chmod 0644 '{}' +;
```Then, to set permissions for the home directory:
```
chmod 0700 ~
```[http://ubuntuforums.org/showpost.php?p=10028718&postcount=2](http://ubuntuforums.org/showpost.php?p=10028718&postcount=2)

You can then check by using ```
ls -ld ~
```and what you should see is that the permissions for the home directory are drwx.

---

### Post by Vaphell on 2010-11-16
no offense taken, there is more than 1 way to skin a cat :-) i focused mainly on +x issue and i simply dislike running recursive, broad scope commands because way too often they cause as much trouble as the problem they fix. Resetting permissions to default is easy but is not the end if you happen to have a lot of executables that need to have their +x restored. I wanted to point that out and encourage OP to learn few handy tricks in the process :)

---

### Post by sisco311 on 2010-11-16
Running **chmod -x** on a file with 0755 permissions is the same as running **chmod 0644**, so there is nothing wrong with that. 

I would use the **-exec command '{}' +** syntax, which runs the command on the selected files, but the command line is built by appending each selected file name at the end; the total number of invocations of the command will be much less than the number of matched  files. 

> **Vaphell said:**
> Resetting permissions to default is easy but is not the end if you happen to have a lot of executables that need to have their +x restored.

That shouldn't be a big issue for one who keeps their files organized (i.e. all executables in ~/bin or ~/.bin). 

Of course, wine could be problematic, yeh, Windows filesystem hierarchy... :P

---

### Post by The Cog on 2010-11-17
> **sisco311 said:**
> I would use the **-exec command '{}' +** syntax, which runs the command on the selected files, but the command line is built by appending each selected file name at the end; the total number of invocations of the command will be much less than the number of matched  files.
Thank you. I didn't know about the + version.

---

### Post by jdong on 2010-11-17
This is one reason why you should consider the chmod symbolic name syntax as opposed to an octal permissions mode. Namely, the capital X specifier would've done a better job at doing what you presumably wanted to do.

See the description in the chmod manpage: [http://manpages.ubuntu.com/manpages/maverick/en/man1/chmod.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/chmod.1.html)

---

