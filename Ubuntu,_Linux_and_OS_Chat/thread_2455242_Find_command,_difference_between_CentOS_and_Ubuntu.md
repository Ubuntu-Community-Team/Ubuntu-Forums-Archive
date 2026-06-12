---
title: "Find command, difference between CentOS and Ubuntu"
date: 2020-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by mishabou on 2020-12-15
Hi all,

I notice some strange behavior when using the Find command under CentOS, compare to Ubuntu, and was wondering if this is normal.

Let say i have folder **A**, it contains several files as well as other folders, **B, C and D**

In CentOS:
-If i do a ***Find*** in A, it lists all folders/files from A and drill down the hierarchy, B, C, D, etc...
-If i do a ***Find *.mov***, it only list the .mov files in folder A, but won't drill down the hierarchy, is this normal in CentOS

Thanks

---

### Post by guiverc on 2020-12-15
I've not noticed differences between a CentOS server, or any Debian and/or Ubuntu boxes.

There maybe differences due to age of software (my old CentOS is an older *10 year* support release), and it'll have much older version of GNU `findutils` than is found in my current Lubuntu box (*hirsute*), but that's to me is expected and only relates to age of software (just like an older release of Debian/Ubuntu may have differences to my current *hirsute* Ubuntu).

I would be explicit in options used, so any environment differences in user setups are avoided (eg. I'd use `-name`rather than letting it be implied like you did)

---

### Post by TheFu on 2020-12-15
```
find *.mov
```
isn't really a valid 'find' command.

**find** assumes the first option is a directory.  If you want to find all files that end in "mov" from the current directory down, use:
```
find . -type f -iname \*mov 
```
Use either the manpage or explainshell.com for help understanding the command and valid options.

There are easier front-ends for searching.  **recoll** is an example. I use it to find files and to search inside all sorts of files. Good metadata makes for good file searching. similarly, bad metadata can make for terrible results.

As for differences for any commands, the versions are changing all the time on each system.  Check the version on each system.  This is also why the manpage for each command on a system is so important. The manpage is for the exact version of the command on the system.

---

### Post by mishabou on 2020-12-15
[QUOTE=
 If you want to find all files that end in "mov" from the current directory down, use:
```
find . -type f -iname \*mov 
```
[/QUOTE]

why do i need to put a backslash (\) before *mov ?

wouldn't this work: find . -type f -iname "*.mov"

Thanks

---

### Post by TheFu on 2020-12-15
```
find . -type f -iname "*.mov"
```
has extra, needed characters.

The pattern *mov is functionally the same as *.mov  The '.' means "any single character", but the '*' means "any number of characters."  So having both is wasted. It s a regex pattern, not an MS-DOS limited pattern.  On Unix, there are no extensions, unlike Windows/DOS.  Learn about regex: [https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)  nothing magical about that link, just seemed like a simple intro.

"*mov"
   vs
\*mov
are the same, just fewer characters.  Admins want to save keystrokes.  That is all. 2 extra characters in a command?  Very wasteful. ;)  We need to prevent the shell expansion of the *, so 'find' gets it unmolested.  That's all.

---

### Post by mishabou on 2020-12-15
Thank you, very helpful info!

---

