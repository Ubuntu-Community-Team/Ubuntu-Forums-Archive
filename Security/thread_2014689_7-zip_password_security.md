---
title: "7-zip password security"
date: 2012-07-02
forum: Security
---

### Post by bradhaack on 2012-07-02
Maybe I'm being too cautious, but the only way to encrypt a zip file with 7-zip is with the password on the command line (-ppassword) & this doesn't seem very secure.  Decrypting is better because you can leave it off & get a prompt.  I know the cmd is saved in bash history, anyplace else also?  Is there some way to make this invisible?  I'm probably being paranoid since this is personal desktop, but it just doesn't seem right.
The file manager uses p7zip (7z) and puts the password on the cmd line also.  I observed this by running ps when I unzipped a file.  Does this cmd get stashed in a log file somewhere?
I'm using 7-zip for compatibility with an android app, to have a few common, encrypted files on my phone & desktop.

ubuntu 10.04 LTS

---

### Post by Dave_L on 2012-07-02
The bash man page describes an environment variable HISTIGNORE ("A colon-separated list of patterns used to decide which command lines should be saved on the history list..."):

[http://manpages.ubuntu.com/manpages/lucid/en/man1/bash.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/bash.1.html)

-----

Another possibility is to write a wrapper script that prompts for the password (without echoing it) and then runs 7-zip. I don't think that commands executed within a script are stored in the history.

---

### Post by sudodus on 2012-07-02
Would it be possible to use ***gpg*** in your android system? Linux update keys are gpg-encrypted, so maybe gpg is part of android too, and available if you know how to use it.

---

### Post by sudodus on 2012-07-02
> **bradhaack said:**
> Maybe I'm being too cautious, but the only way to encrypt a zip file with 7-zip is with the password on the command line (-ppassword) & this doesn't seem very secure  ...

ubuntu 10.04 LTS

I got curious and checked. You need not enter the password like that. The following command works for me in Ubuntu 10.04 LTS.
```
7z a -mhe=on -p archive.7z ttt
```
where ttt is the directory to zip and encrypt. You are prompted to enter and verify the password without echo.

```
$ 7z a -mhe=on -p archive.7z ttt

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04
Scanning

Creating archive archive.7z


Enter password (will not be echoed) :
Verify password (will not be echoed) :

```

---

### Post by bradhaack on 2012-07-02
> **sudodus said:**
> I got curious and checked. You need not enter the password like that. The following command works for me in Ubuntu 10.04 LTS.
```
7z a -mhe=on -p archive.7z ttt
```
where ttt is the directory to zip and encrypt. You are prompted to enter and verify the password without echo.


Perfect, Based on my read of the man/info page that didn't occur to me that you didn't need the passwd after -p.
Thanks

---

