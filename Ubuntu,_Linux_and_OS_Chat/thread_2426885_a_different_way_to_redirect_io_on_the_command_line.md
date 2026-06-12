---
title: "a different way to redirect i/o on the command line"
date: 2019-09-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-09-15
the normal way to redirect input and output is like:
```

command arg1 arg2 < input-file > output-file

```

i often need to feed commands through other commands in such a way that normal redirect doesn't work.  this is usually because no shell is run to execute the next command (often for security reasons to avoid exploitation of the shell).  so i came my own way of redirection that works in a very different way that works with passing commands.  an example of the equivalent command as above is:
```

io input-file output-file command arg1 arg2

```

there are actually 14 such commands, 1 script and 13 aliases.  the script is named "eio" and is written in Python3.  the alias names are: "i", "o", "ei", "eo", "ie", "io", "oe","oi", (skipping "eio") "eoi", "ieo", "ioe", "oei", and "oie".  the order of the letters in the command name you are using determines the order you give the file names as arguments.  as you can guess, "i" means STDIN, "o" means STDOUT, and "e" means STDERR.  it then executes the command that follows 1, 2, or 3 file names.  if the name is "-", it just skips opening and redirecting that one.  if STDOUT and STDERR are given the same exact path name, it only opens the file once and duplicates the file descriptor so STDOUT and STDERR don't trip over each other.  you can also chain the redirect commands.  for example:
```

i input-file o output-file command arg1 arg2

```
there was going to be an alias for "e", but i already use that name to run my editor.  so far it is in the alpha development stage.  i plan to add more graceful and informative error handling.

---

