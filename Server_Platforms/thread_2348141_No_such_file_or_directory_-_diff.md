---
title: "No such file or directory - diff"
date: 2017-01-01
forum: Server Platforms
---

### Post by sed_faster on 2017-01-01
I run diff program to detect difference between disk on ubuntu server. When I ran command diff between disk I received this report:

```

diff: /patho/to/file.php: No such file or directory

```

I use this parameter on program diff
```

diff -ryq fileone filetwo

```

What this report means?
thanks

---

### Post by SoftwareExplorer on 2017-05-23
This is a guess, but here it goes.

I was getting the same error.

The core reason was that diff was throwing the error when it came across a symlink. Instead of comparing the path that the symlink pointed to, it was trying to compare the contents of the symlinked file (but the link was broken, so it was throwing a "No such file or directory" error.)

If you have a new enough version of diff (see [https://unix.stackexchange.com/a/128089/7816](https://unix.stackexchange.com/a/128089/7816)), then you can give it the '--no-dereference' option to have it compare the paths that the symlinks point to instead of the content of the files (that may or may not be present) that those paths point to.

---

