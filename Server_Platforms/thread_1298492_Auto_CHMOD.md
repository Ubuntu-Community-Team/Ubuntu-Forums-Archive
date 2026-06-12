---
title: "Auto CHMOD"
date: 2009-10-22
forum: Server Platforms
---

### Post by m3bik on 2009-10-22
I have a web and ftp server set up on my ubuntu box. Every time I upload a file via ftp however, I have to CHMOD the file to any readable value. For example, when uploading a .html file and trying to access it via the web, I get a Forbidden error. If I CHMOD the file to 644, it works just fine. Is there anyway I can set the server to automatically CHMOD the files for me or something? I mean, doing this myself isn't that big of a deal, but if there's a fix, it'd be great!

---

### Post by bab1 on 2009-10-23
> **m3bik said:**
> I have a web and ftp server set up on my ubuntu box. Every time I upload a file via ftp however, I have to CHMOD the file to any readable value. For example, when uploading a .html file and trying to access it via the web, I get a Forbidden error. If I CHMOD the file to 644, it works just fine. Is there anyway I can set the server to automatically CHMOD the files for me or something? I mean, doing this myself isn't that big of a deal, but if there's a fix, it'd be great!

Use the sticky bit.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

---

### Post by m3bik on 2009-10-23
While that looks like it might be what I need...but no tutorials seem to be doing me any good.

Everything I find just explains the permission settings in chmod and I've found mentioning about sticky group or user, but nothing  that is helping in any way, shape, or form. ????


:confused:

---

### Post by bab1 on 2009-10-23
> **m3bik said:**
> While that looks like it might be what I need...but no tutorials seem to be doing me any good.

Everything I find just explains the permission settings in chmod and I've found mentioning about sticky group or user, but nothing  that is helping in any way, shape, or form. ????


:confused:

Before going into what SETUID and SETGID bits are, maybe we should backup a bit and look at what permissions and ownership of the directory in question.

[QUOTE=m3bik]I have a web and ftp server set up on my ubuntu box. Every time I upload a file via ftp however...[/QUOTE]

When you upload a file, who are you logged in as?  Where in the filesystem are you uploading to?  Provide us with the output of ```
ls -l
``` for the directory and the files in that directory.  This is  my web directory for example.  ```
drw-r--r-- 6 bruce bruce    4.0K 2009-10-22 10:06 public_html
```and the file(s) in that directory are```
-rw-r--r-- 1 bruce bruce      14K 2009-10-07 23:23 index.html
-rw-r--r-- 1 bruce bruce    5.1K 2009-10-21 23:42 index.html.1

```

This is just a guess, as I can't see the file structure or the ownership of the directory, but I believe that the owner:group is not what you think it is.

The default umask is set to 022 (chmod 644).  If you are logged in and create a file the perms should be 644 already.  Are you moving files that you do not own (using sudo) or could the files be in a directory that does not have unix (posix) file perms (i.e. vfat or some such)?

The SETUID and SETGID bits force the ownership to the owner or group of the directory and stop deletion by anyone but the owner (and root of course).

Lots to think about, but I need to see what you have before I can advise you on what to do.

---

