---
title: "How secure are the default file permissions?"
date: 2010-02-05
forum: Security
---

### Post by dogdo on 2010-02-05
Hi 

What do the default file permissions in ubuntu 9.10 protect/deny access to?

---

### Post by bodhi.zazen on 2010-02-05
That is a broad question.

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by dogdo on 2010-02-06
Well ok but i found those links throughly confusing :confused:

Just please tell me how 'safe' is a default install of a new user out of the box in terms of file permissions?

---

### Post by amac777 on 2010-02-06
By default, all users on your system will be able to see and read (but not write to) the files in other user's home folders.

---

### Post by dogdo on 2010-02-06
> **amac777 said:**
> By default, all users on your system will be able to see and read (but not write to) the files in other user's home folders.

If write access is not allowed then is it safe to assume that execute access is denied as well? 

Also with physical access with a live cd or with the hard drive in another computer is the only way to protect your files is with encryption?

---

### Post by movieman on 2010-02-06
> **dogdo said:**
> Also with physical access with a live cd or with the hard drive in another computer is the only way to protect your files is with encryption?

Yes.

---

### Post by amac777 on 2010-02-06
> **dogdo said:**
> If write access is not allowed then is it safe to assume that execute access is denied as well? 

Yes, that is correct. Execute access for other users is denied by default.

---

### Post by rookcifer on 2010-02-06
> **dogdo said:**
> Well ok but i found those links throughly confusing :confused:

Just please tell me how 'safe' is a default install of a new user out of the box in terms of file permissions?

Do some reading on [umask]("http://www.topbits.com/umask.html"), as I think it is what you are asking about. I believe Ubuntu, like most every distro, uses a default umask of 022.  This means any newly created file will not be able to execute own it's own -- that is, it can't do anything without your permission.

---

### Post by dogdo on 2010-02-07
> **rookcifer said:**
> Do some reading on [umask]("http://www.topbits.com/umask.html"), as I think it is what you are asking about. I believe Ubuntu, like most every distro, uses a default umask of 022.  This means any newly created file will not be able to execute own it's own -- that is, it can't do anything without your permission.

Ok i read that link but yeah its way confusing for me...sigh

In any case this is what i think your saying: by default only files that i put in my home folder are executable and only files that i give perimission via sudo can execute system wide changes. Am i off the mark here?

---

### Post by rookcifer on 2010-02-07
> **dogdo said:**
> Ok i read that link but yeah its way confusing for me...sigh

In any case this is what i think your saying: by default only files that i put in my home folder are executable and only files that i give perimission via sudo can execute system wide changes. Am i off the mark here?

Only files you explicitly give execute permission to in your /home folder are executable.  So, in other words, you must make the file executable (chmod +x).  This will stop some malicious file you download from executing itself (unless, of course, you are tricked into making it executable and running it).

---

### Post by dogdo on 2010-02-08
> **rookcifer said:**
> Only files you explicitly give execute permission to in your /home folder are executable.  So, in other words, you must make the file executable (chmod +x).  This will stop some malicious file you download from executing itself (unless, of course, you are tricked into making it executable and running it).

So files in my home folder are executable by default but files that attempt to interact with the operating system files must be manually made as execute?

---

### Post by Agent ME on 2010-02-09
Files in your home folder by default aren't executable, unless you specifically set them that way.

By default, most of your files are readable by other users on the system. Folders that hold application preferences (like your Firefox history and passwords) are generally set to be private to your user (other users don't have read permissions to them).

File permissions mean nothing if an attacker inserts a Live cd into your computer and boots up their own operating system install. Only file or disk encryption can help you there.

---

### Post by dogdo on 2010-02-09
I have my home folder encrypted with encfs which im told uses 128 bit AES. The password consists of 9 upper/lower cases letters, numbers and symbols-how difficult would it be to brute force this?

---

