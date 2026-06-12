---
title: "Any idea about protection of configuration files ?"
date: 2007-11-11
forum: Server Platforms
---

### Post by davidcopper on 2007-11-11
Hi. I am developing a software, and have some configuration files that need to be protected. Is there anyway to prevent others reading the file contents, but allowing them to execute the files? 

Many thanks for any idea you may give.

---

### Post by bmathis on 2007-11-12
.

---

### Post by MJN on 2007-11-12
That's not going to work - if a file is to be executed then it must by definition also be readable, otherwise how do you load it into memory?
 
Mathew

---

### Post by eldragon on 2007-11-12
if you dont want people reading it, you will need to encrypt the data in it :)

---

### Post by k_grdn on 2007-11-12
Hi,

Sudo could be a possibility to allow users to run the program as another user but not read as themselves.

Regards,

k_grdn

---

### Post by davidcopper on 2007-11-12
Thanks for all your ideas. 

Setting the file permission to 001 will not work, as OS needs to read content of file into memory when executing.

Here are what I have known so far.

Configuration files are usually either shell scripts or text files.

For shell scripts, there is a encryption tool shc available. It embeds shell scripts into a C program and compiles it as binary.

For text files that are to be loaded by other programs, I can add an encryption/decryption function into those programs.

Any suggestions?

Thanks.

---

### Post by davidcopper on 2007-11-12
> **k_grdn said:**
> Hi,

Sudo could be a possibility to allow users to run the program as another user but not read as themselves.

Regards,

k_grdn

Hi. Sudo requires root password to run the program. If he knows the password, he will have permission to read the files. But thank you for your suggestion.

---

### Post by k_grdn on 2007-11-12
I was thinking of something like the following.....


%users    ALL=NOPASSWD: /usr/local/bin/script.sh 

.........to allow the users to execute the script.

Regards,

k_grdn

---

