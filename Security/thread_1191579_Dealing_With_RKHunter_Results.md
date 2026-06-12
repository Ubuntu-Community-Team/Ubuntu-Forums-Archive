---
title: "Dealing With RKHunter Results"
date: 2009-06-19
forum: Security
---

### Post by JohnWesleyMethodist on 2009-06-19
Hello

 I am not a super Linux geek so I was thinking of ways to deal with these annoying files that RKHunter shows are suspect without having to do a whole lot of work or requiring a whole lot of knowledge.

 The thought came to me that if I could re-install these files and then update RKHunter, then they should no longer be a concern. This seemed like a good solution for a non-expert, or a good quick solution for anyone.

 I did re-install the one package that I could find from the list of suspect, but I can't find the others.

 My question for you all is whether or not this is a good way to deal with the problem and also if you can help me to figure out which package these suspect files belong to.

    /usr/sbin/unhide-linux26                                 [ Warning ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/adduser                                        [ Warning ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/groups                                          [ Warning ]
    /bin/which                                               [ Warning ]

 From that list I could find "unhide" in the Synaptic Package Manager but none of the others. I choose to reinstall "unhide."

 Thanks!

---

### Post by brian_p on 2009-06-19
> **JohnWesleyMethodist said:**
> 

 My question for you all is whether or not this is a good way to deal with the problem and also if you can help me to figure out which package these suspect files belong to.


A better way to deal with the problem without compromising security:

```
apt-get purge rkhunter
```

To find which package a file belongs to:

```
apt-cache search file_name
```

---

### Post by JohnWesleyMethodist on 2009-06-19
> **brian_p said:**
> A better way to deal with the problem without compromising security:

```
apt-get purge rkhunter
```

To find which package a file belongs to:

```
apt-cache search file_name
```

 I do thank you for the 2nd answer. As for the 1st answer, while that may be tempting considering how frustrating RKHunter is, I am hoping for a more supportive answer.

---

### Post by lovinglinux on 2009-06-19
Here is an example using one of your files with a warning.

First I try to discover the package which installs the file

```
dpkg -S /usr/sbin/adduser
```

Result: 

> adduser: /usr/sbin/adduser


Then I download the package to my download folder

```

cd ~/download
aptitude download adduser
```

Then I extract the package to a folder for itself

```
dpkg -x ./adduser_3.110ubuntu5_all.deb ./adduser
```

Then compare the file hashes

```
sha1sum ./adduser/usr/sbin/adduser /usr/sbin/adduser ; sha256sum ./adduser/usr/sbin/adduser /usr/sbin/adduser
```

I repeat the process for each file with warnings on rkhunter results. If all file hashes from the downloaded packages are the same as the corresponding  installed files, then I can run the command below to update rkhunter database with the hashes from my system:

```
sudo rkhunter --propupd
```

It is a little bit complicated, but it works just fine. The best way to avoid this trouble is to scan the system before and after EVERY update and software installation. That's what I do since I installed Jaunty from scratch.




*UKeywords: 649167 2009 june rkhunter hash warning package checksum*

---

### Post by brian_p on 2009-06-19
> **JohnWesleyMethodist said:**
> I do thank you for the 2nd answer. As for the 1st answer, while that may be tempting considering how frustrating RKHunter is, I am hoping for a more supportive answer.

Apologies. The apt-cache command I gave you is not very useful. As already said, dpkg -S is the command you want.

Regarding rkhunter and my perceived non-supportive answer: even when set up correctly its track record as a discoverer of root kits is less than sparkling. However, for reasons I do not quite understand it does appear to be a popular package and is often among the first things  be put on a new install.

---

### Post by lovinglinux on 2009-06-19
> **brian_p said:**
> Regarding rkhunter and my perceived non-supportive answer: even when set up correctly its track record as a discoverer of root kits is less than sparkling. However, for reasons I do not quite understand it does appear to be a popular package and is often among the first things  be put on a new install.

Maybe the same reason why people install Firestarter :)

Which tool would be better than rkhunter?

---

### Post by brian_p on 2009-06-19
> **lovinglinux said:**
> Maybe the same reason why people install Firestarter :)

You could be on to something there. :smile:

> Which tool would be better than rkhunter?

The common-sense package (which among other things advises not installing unknown software from dubious sources) would be a start. Unfortunately it is not available via aptitude or synaptic.

---

### Post by lovinglinux on 2009-06-19
> **brian_p said:**
> You could be on to something there. :smile:


The common-sense package (which among other things advises not installing unknown software from dubious sources) would be a start. Unfortunately it is not available via aptitude or synaptic.

Yep, common-sense works for me :)

---

### Post by JohnWesleyMethodist on 2009-07-02
Okay thanks for the info LovingLinux!

 I decided to post exactly how I am following your instructions just in case it helps someone else who reads this thread.

 #1 - In my /home/<username> folder I created a folder called "Downloads"
 #2 - I opened up terminal and typed: cd /home/<username>/Downloads
 #3 - I typed this command into Terminal: aptitude download <particular file>
 #4 - After it downloaded I went into that directory via the gui and right-clicked on the .deb file and chose "extract".
 #5 - I continued to extract additonal archives until I found a text file called: "md5sums".
 #6 - In the text file "md5sums" it shows the hash for each file and it's location.
 #7 - Using Terminal I type this command: "md5sum (example: cd /usr/sbin/unhide-posix)
 #8 - I confirm all numbers are the same.
 #9 - After all testing is completed successfully I run Sudo Rkhunter --propupd

 Sounds good?

---

### Post by bodhi.zazen on 2009-07-02
OSSEC is my preference.

---

### Post by lovinglinux on 2009-07-02
> **JohnWesleyMethodist said:**
> Okay thanks for the info LovingLinux!

 I decided to post exactly how I am following your instructions just in case it helps someone else who reads this thread.

 #1 - In my /home/<username> folder I created a folder called "Downloads"
 #2 - I opened up terminal and typed: cd /home/<username>/Downloads
 #3 - I typed this command into Terminal: aptitude download <particular file>
 #4 - After it downloaded I went into that directory via the gui and right-clicked on the .deb file and chose "extract".
 #5 - I continued to extract additonal archives until I found a text file called: "md5sums".
 #6 - In the text file "md5sums" it shows the hash for each file and it's location.
 #7 - Using Terminal I type this command: "md5sum (example: cd /usr/sbin/unhide-posix)
 #8 - I confirm all numbers are the same.
 #9 - After all testing is completed successfully I run Sudo Rkhunter --propupd

 Sounds good?

Yep, sounds good.

---

### Post by bodhi.zazen on 2009-07-02
Sounds like a pain.

OSSEC is much easier.

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Scroll past the fires posts on snort.

---

### Post by JohnWesleyMethodist on 2009-07-10
Hello Again!

 I have a problem checking the MD5 of hidden files now:

Ubuntu@Ubuntu-Laptop:~$ sudo dpkg -S /etc/.java/.systemPrefs/.system.lock
dpkg: /etc/.java/.systemPrefs/.system.lock not found.

 I tried renaming the files to see if that would help but no go:

Ubuntu@Ubuntu-Laptop:~$ sudo dpkg -S /etc/java/systemPrefs/system.lock
dpkg: /etc/java/systemPrefs/system.lock not found.

 Funny thing is I can find them with Nautilus but Terminal thinks they are not there.

 Uh oh... Just tried something. I typed sudo dpkg -S ls -a /etc/.java/.systemPrefs/.system.lock

 Now Terminal printed a load of stuff...

---

