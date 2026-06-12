---
title: "recommend encryption solution?"
date: 2009-03-08
forum: Security
---

### Post by pmooney78 on 2009-03-08
I'd like to hide some of my sensitive data from prying eyes. I'm more concerned about my roommate than the NSA, although my roommate is fairly computer-literate.

What I'd really like is to have an entire encrypted partition. I've got enough free space on my hard drive to carve off another slice. I'd prefer not to have it auto-mount when I log on, and I'd like to be about to mount/unmount it easily. I don't want to have to recompile the kernel or do anything too funky configuration-wise. 

All of the information I've found searching so far is over my head. Any suggestions?

---

### Post by Dr Small on 2009-03-08
Have you tried TrueCrypt?

---

### Post by blueshiftoverwatch on 2009-03-08
> **Dr Small said:**
> Have you tried TrueCrypt?
A friend told me about that program. How does it compare to other similar programs for Linux?

---

### Post by pmooney78 on 2009-03-08
Haven't tried anything yet ... looking at TrueCrypt right now. Seems easy enough, and people seem to say good things about it ...

---

### Post by Dr Small on 2009-03-08
> **blueshiftoverwatch said:**
> A friend told me about that program. How does it compare to other similar programs for Linux?
I've only ever used it a few times, but it has worked for me just fine. As far as comparing, I'm not the encryption expert. hyper_ch or kevdog could probably answer that better. It has a GUI and is simple to use, but beyond that, I don't know.

---

### Post by pmooney78 on 2009-03-08
Thanks, Doc. Looks a lot like PGPdisk, which I used to use a trillion years ago on my Mac. Familiar interface is a plus ... I'll give it a try.

---

### Post by Tubes6al4v on 2009-03-09
I wonder if it would auto mount the drive on recovery mode as well. Then he could access it without a username/password. I tend to go for full disk encryption. It is easy, and I don't have to think about where anything is, everything is encrypted.

---

### Post by pmooney78 on 2009-03-09
I tried downloading TrueCrypt tonight -- I get a tar.gz file that, when I unzip it, contains a file that doesn't seem to do anything. It claims to be a shell script, but when I double-click it, VLC player tries to open it. Trying to run it in a bash shell doesn't do anything, either, even if I sudo chmod +x the file. 

Changing the file name so it ends in .deb and trying to install it with GDebi doesn't work, either. 

Any suggestions?

---

### Post by rzrgenesys187 on 2009-03-09
Go to this page: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php).  There is a select box close to the bottom that allows you to download a deb file for ubuntu.  Click where it says "Select a Linux Distribution and hardware platform"

---

### Post by pmooney78 on 2009-03-09
> **rzrgenesys187 said:**
> Go to this page: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php).  There is a select box close to the bottom that allows you to download a deb file for ubuntu.  Click where it says "Select a Linux Distribution and hardware platform"

That's what I've been trying to do ... it gives me the file I don't know what to do with.

---

### Post by hyper_ch on 2009-03-09
download the tar.gz file, extract it, then it will create a True Crypt folder and in there you'll have a file:  truecrypt-xxxx-setup-ubuntu-x86

make it executable: chmod 0755 truecrypt-6.0a-setup-ubuntu-x86

install it: sudo ./truecrypt-6.0a-setup-ubuntu-x86

Then it should create an entry in the menu

---

### Post by pmooney78 on 2009-03-10
> **hyper_ch said:**
> download the tar.gz file, extract it, then it will create a True Crypt folder and in there you'll have a file:  truecrypt-xxxx-setup-ubuntu-x86

make it executable: chmod 0755 truecrypt-6.0a-setup-ubuntu-x86

install it: sudo ./truecrypt-6.0a-setup-ubuntu-x86

Then it should create an entry in the menu

Perfect! It's installing now. 

I finally figured out what the source of the problem was: I download almost everything from the Internet onto an external hard drive ... which is formatted as NTFS, and the default permissions mapping in /etc/fstab marks everything on the drive non-executable. Of course, it's not possible to change permissions on an NTFS volume ... solved the problem by copying it to my home directory and following the instructions from there. (D'oh!)

Since I have your ear, I'd like to ask two quick questions about the advice you gave, if you have a moment:

1. Is there a difference between "sudo chmod 0755 <something>" and "sudo chmod 755 (with no leading zero) <something>"? What does the fourth octal digit mean, anyway?

2. I see people advising to type "./ <some executable file>" all the time. Isn't ./ just "this folder"? Why not just type the name of the executable file?

OK, that's four questions, I admit.

Thank you in advance for any info.

---

### Post by hyper_ch on 2009-03-10
don't ask me about the difference between 0xxx and xxx. I know there is one but can't explain it to you.

If you just issue
```

command

```
then it will look in environment path variable but not in the according directory. That's why you need to specify it with "./" (this directory).

It's different if you assign a program first:
```

sh file.sh

```
then "sh" will be looked up in the enviroment variable and "file.sh" is just a parameter to be added to the "sh" command.

---

### Post by pmooney78 on 2009-03-11
Thank you, very helpful! I've been banging my head against that for a while now ...

---

