---
title: "Does rkhunter update itself?"
date: 2009-03-10
forum: Security
---

### Post by lovinglinux on 2009-03-10
Does rkhunter update itself?

I'm asking this because I'm starting to feel that using rkhunter is almost useless, at least regarding file changes.

I usually forget to run rkhunter before system updates, so I'm frequently presented with some warnings that I really don't know how to deal with. I already know the **--propupd** command option, but it comes with a warning itself:

> You can run this option to update the file information. This will clear the stored information about the files that rkhunter checks and then replace it with the current information from your system. There is a warning in the man page for rkhunter not to do this unless you are certain that your system has not been compromised.

So, finding out which files have been replaced by official updates or exploited is a complex task. I tried before, but was never 100% sure. For example, I have warnings now about the following files:

/usr/bin/curl 
/usr/bin/last   
/usr/bin/sudo 
/sbin/sulogin

Who knows which files could be already compromised when I used  **--propupd** before this report...

Is there a way to update rkhunter data not with information from my own system, but from a repository?

---

### Post by cmay on 2009-03-10
i do not know if this is any good advise but i think there is a distribution called backtrack that has a lot of security related programs on it. its a live dvd and i have one myself but i hardly ever used it since i really do not have any use for penetration testing. maybe you can use that to get a sort of "second opinion" 
anyway hope that someone can answer your question for you.

---

### Post by lovinglinux on 2009-03-10
Thanks for the tip. BackTrack looks really interesting. I will download it and try it.

---

### Post by slowth5 on 2009-03-10
Hi lovinglinux, I don't think there's a way to update rkhunter from a repository, but would you trust an rkhunter update from a repository?  
You've uncovered the limitations of any security utility; namely, whom should we trust and extreme dedication.  

I would trust myself before a repository.  I would run --propupd immediately after a clean install, assuming the installation cd were uncompromised. 

As for dedication, I would monitor each and every file I installed from that point forward, updating with --propupd along the way.  

You're quite right, ambivalence towards either trust or persistence  would render rkhunter, chkrootkit, or any other utility quite useless.  The question is are you concerned enough to do the job correctly?  There's no point in using these programs if you aren't dedicated.

---

### Post by lovinglinux on 2009-03-10
> **slowth5 said:**
> Hi lovinglinux, I don't think there's a way to update rkhunter from a repository, but would you trust an rkhunter update from a repository?  
You've uncovered the limitations of any security utility; namely, whom should we trust and extreme dedication.  

I would trust myself before a repository.  I would run --propupd immediately after a clean install, assuming the installation cd were uncompromised. 

As for dedication, I would monitor each and every file I installed from that point forward, updating with --propupd along the way.  

You're quite right, ambivalence towards either trust or persistence  would render rkhunter, chkrootkit, or any other utility quite useless.  The question is are you concerned enough to do the job correctly?  There's no point in using these programs if you aren't dedicated.

I could be dedicated, but I guess it is too late and I really don't want to do clean install right now.

---

### Post by slowth5 on 2009-03-10
I understand completely.  I'm very security conscious, but even I'm not dedicated enough to monitor every changed file on my system.  Then again, I'm not running a corporate server.

---

### Post by shad0w_crash on 2009-03-11
> **slowth5 said:**
> I understand completely.  I'm very security conscious, but even I'm not dedicated enough to monitor every changed file on my system.  Then again, I'm not running a corporate server.

If you're realy dedicated you could make a list of hashes of your files and compare those each weak.

Isn't there a hash available for the database of rkhunter? So you could verifie that the hashes to compere to are valid?

---

### Post by cryogen on 2009-03-12
> **lovinglinux said:**
> I usually forget to run rkhunter before system updates, so I'm frequently presented with some warnings that I really don't know how to deal with.
.....
So, finding out which files have been replaced by official updates or exploited is a complex task. I tried before, but was never 100% sure.

Personally I prefer ossec for monitoring changes but I do keep rkhunter around for additional verification.

What I've done is install version 1.3.4 from debian (beware: debian packages are not ubuntized so install with great caution) because using 1.3.4 allows --propupd to accept a file as an argument.  To check if binary on my systems match what's in the repositories I run something like this (for /usr/bin/sudo in hardy amd64):

```
cd ~

wget http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.4_amd64.deb

dpkg -x ./sudo_1.6.9p10-1ubuntu3.4_amd64.deb ./sudo

sha1sum ./sudo/usr/bin/sudo /usr/bin/sudo ; sha256sum ./sudo/usr/bin/sudo /usr/bin/sudo

```
which returns something like:

```
6917217548d9fea6b97629db7eb44fe4cfe89e23  ./sudo/usr/bin/sudo
6917217548d9fea6b97629db7eb44fe4cfe89e23  /usr/bin/sudo
7a4beec3419fa3db50cc4d2b06a433f72bda77119fd1b6fa5f21456740be9922  ./sudo/usr/bin/sudo
7a4beec3419fa3db50cc4d2b06a433f72bda77119fd1b6fa5f21456740be9922  /usr/bin/sudo
```
If the sums are equal, I assume the changes came from a package update and then run:
```

rkhunter --propupd /usr/bin/sudo

```
to update rkhunter.  Or for 1.3.2 just run --propupd after you've checked all the binaries in question.

If the sums don't match, well...

The above procedure isn't too time consuming to do: I just did it in about 5 minutes including typing this.  I've noticed that it's pretty unusual for rkhunter to scream about changed binaries so I tend to pay attention when it does.  This procedure would be fairly easy to script, but it doesn't happen often enough that I've ever bothered to do it.

If you're paranoid you can calculate the sum on the downloaded binary on a different system, or even a different OS.  You can also check with different hash algorithms like whirlpool.

Again though, I just use rkhunter as a backup.  Like I said, I like ossec much better: the change detection is coupled with other things like login failures and network events so you can be much more confident about if you are or aren't compromised.

---

### Post by lovinglinux on 2009-03-12
> **cryogen said:**
> Personally I prefer ossec for monitoring changes but I do keep rkhunter around for additional verification.

What I've done is install version 1.3.4 from debian (beware: debian packages are not ubuntized so install with great caution) because using 1.3.4 allows --propupd to accept a file as an argument.  To check if binary on my systems match what's in the repositories I run something like this (for /usr/bin/sudo in hardy amd64):

```
cd ~

wget http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.4_amd64.deb

dpkg -x ./sudo_1.6.9p10-1ubuntu3.4_i386.deb ./sudo

sha1sum ./sudo/usr/bin/sudo /usr/bin/sudo ; sha256sum ./sudo/usr/bin/sudo /usr/bin/sudo

```
which returns something like:

```
6917217548d9fea6b97629db7eb44fe4cfe89e23  ./sudo/usr/bin/sudo
6917217548d9fea6b97629db7eb44fe4cfe89e23  /usr/bin/sudo
7a4beec3419fa3db50cc4d2b06a433f72bda77119fd1b6fa5f21456740be9922  ./sudo/usr/bin/sudo
7a4beec3419fa3db50cc4d2b06a433f72bda77119fd1b6fa5f21456740be9922  /usr/bin/sudo
```
If the sums are equal, I assume the changes came from a package update and then run:
```

rkhunter --propupd /usr/bin/sudo

```
to update rkhunter.  Or for 1.3.2 just run --propupd after you've checked all the binaries in question.

If the sums don't match, well...

The above procedure isn't too time consuming to do: I just did it in about 5 minutes including typing this.  I've noticed that it's pretty unusual for rkhunter to scream about changed binaries so I tend to pay attention when it does.  This procedure would be fairly easy to script, but it doesn't happen often enough that I've ever bothered to do it.

If you're paranoid you can calculate the sum on the downloaded binary on a different system, or even a different OS.  You can also check with different hash algorithms like whirlpool.

Again though, I just use rkhunter as a backup.  Like I said, I like ossec much better: the change detection is coupled with other things like login failures and network events so you can be much more confident about if you are or aren't compromised.

This is great. Thank you very much.

How do I know which versions I should download with wget? I know I can get the installed version from Synaptic, but is there a connection between the deb name and the Ubuntu version? I can only distinguish the architecture.

---

### Post by cryogen on 2009-03-12
> **lovinglinux said:**
> This is great. Thank you very much.

How do I know which versions I should download with wget? I know I can get the installed version from Synaptic, but is there a connection between the deb name and the Ubuntu version? I can only distinguish the architecture.

Honestly, I just looked it up online at packages.ubuntu.com. :oops: However you can look up which package provides the binary in question  (/usr/bin/sudo in this case) by using:

```
dpkg -S /usr/bin/sudo
```

which gives:

```
sudo: /usr/bin/sudo
```

Then the quick way is to download the package with aptitude (I don't like apt-get):
```

aptitude download sudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://us.archive.ubuntu.com hardy-updates/main sudo 1.6.9p10-1ubuntu3.4 [188kB]
Fetched 188kB in 1s (148kB/s)
```

which sticks the package in the current directory.  You can then run the extraction and verification procedure I posted.

---

### Post by lovinglinux on 2009-03-12
> **cryogen said:**
> Honestly, I just looked it up online at packages.ubuntu.com. :oops: However you can look up which package provides the binary in question  (/usr/bin/sudo in this case) by using:

```
dpkg -S /usr/bin/sudo
```

which gives:

```
sudo: /usr/bin/sudo
```

Then the quick way is to download the package with aptitude (I don't like apt-get):
```

aptitude download sudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://us.archive.ubuntu.com hardy-updates/main sudo 1.6.9p10-1ubuntu3.4 [188kB]
Fetched 188kB in 1s (148kB/s)
```

which sticks the package in the current directory.  You can then run the extraction and verification procedure I posted.

Awesome. That's much easier. Thank you very much again.

---

### Post by Arup on 2009-03-12
You need to do a sudo rkhunter --update and it updates all its files.

---

