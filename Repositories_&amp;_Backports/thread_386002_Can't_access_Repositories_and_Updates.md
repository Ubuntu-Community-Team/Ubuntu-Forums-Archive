---
title: "Can't access Repositories and Updates"
date: 2007-03-16
forum: Repositories &amp; Backports
---

### Post by Spalatum on 2007-03-16
I get this error when i try to access the repositories or updates. The error ocures when I open the Synaptic Package Manager.

```
E: Malformed line 32 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```

Can someone please explain what do I need to do in order to fix this problem and try to make it newb-understandable because this is my day-2 under the Ubuntu Linux OS.

Thanks in advance.

---

### Post by bapoumba on 2007-03-16
Hello, this means that your repository list has two errors on lines 2 and 32.
Please open a terminal (> Accessories > Terminal), enter the following command and paste in here the complete output:
```
cat /etc/apt/sources.list
```
We'll have a look at it and tell you how to fix it.

---

### Post by Kateikyoushi on 2007-03-16
You can find breezy 5.1, dapper 6.06 and edgy 6.1 sources.lists here. [LINK]("http://www.psychocats.net/ubuntu/sources")

---

### Post by Spalatum on 2007-03-17
I did what you said and I got this in the terminal.

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://archive.ubuntu.com/ubuntu/ edgy

```

What must I do now?

---

### Post by bapoumba on 2007-03-17
In addition to the link Kateikyoushi gave you, you can also read the following:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

I do not see obvious errors line 2 and 32 (except it's a duplicate), may be some hidden character.

You can edit the file with:
```
sudo nano -B /etc/apt/sources.list
```
nano is a small text editor you use in a terminal.

[COLOR="Red"]Remove[/COLOR] what is in red and [COLOR="Green"]add[/COLOR] what is in green:
> **Spalatum said:**
> 
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe [COLOR="Green"]multiverse[/COLOR]

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe [COLOR="Green"]multiverse[/COLOR]

[COLOR="Red"]## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy universe[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe [COLOR="Green"]multiverse[/COLOR]
[COLOR="Red"]# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://archive.ubuntu.com/ubuntu/ edgy
deb http://archive.ubuntu.com/ubuntu/ edgy[/COLOR]

```

Then save the file with CTRL-O (same name, hit <enter>) and exit with CTRL-X. Run:
```
sudo aptitude update
```
and paste any error in here.

---

### Post by Spalatum on 2007-03-17
I have already read both of those links you two gave me. I did what you told me to do and i got this error afterwards:

```
sky@blackbox:~$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
```

---

### Post by Kateikyoushi on 2007-03-17
I noticed that in your first post already, what's interesting that I've never seen that error and I do not even have anything in that directory.

Anyway list the content of it for us.
```
cat /etc/apt/sources.list.d/edgy-universe.list
```

---

### Post by bapoumba on 2007-03-17
In addition, line 2 is a blank line (and the error on line 32 is not there anymore after you removed it). So try to remove the blank line n°2 in your source.list and run **sudo aptitude update** again.
Use nano the same way as the previous time.

I cannot find the relevant link right now, but I have already came across some "hidden" characters of some sort in source.list giving these kind of errors. Removing line 32 and not line 2 was (and I apologize for it) a test to see if that could be the case here again. I have no explanation, though.

---

### Post by Spalatum on 2007-03-17
@ Kateikyoushi:

This is what I get after applying that code:

```
sky@blackbox:~$ cat /etc/apt/sources.list.d/edgy-universe.list
# automatically added by gnome-app-install on 2007-03-15 19:47:53.982023
deb http://archive.ubuntu.com/ubuntu/ edgy

```

@ bapoumba:

So I have followed your instructions and the **source.list** looks like this now.
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://si.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse


```

The blank line 2 was removed. After that ...

```
sky@blackbox:~$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.

```

I got the same error again. I don't know, maybe I did something wrong.
By the way, you do not need to apologize for that because you are the one helping me remember ;).

---

### Post by Kateikyoushi on 2007-03-17
You got the same error because the problem is not in your sources.list but the other file what you see in the error message. I am currently trying to find out the function of that file, before I recommend something.

---

### Post by bapoumba on 2007-03-17
@ Spalatum: so my guess was not accurate (you did it correctly), then follow Kateikyoushi's suggestions :)

---

### Post by Kateikyoushi on 2007-03-17
Out of curiousity, Bapoumba do you have that file in your installation ? I don't have anyhting in that directory and upgraded from dapper to feisty.

Anyway seems apt-get does not make difference between the two files so I recommend to try to comment the problematic line by putting a hashmark (#) at the beginning of the second line.

```
sudo nano /etc/apt/sources.list.d/edgy-universe.list
```

Then save it and try to update again.

---

### Post by bapoumba on 2007-03-17
> **Kateikyoushi said:**
> Out of curiousity, Bapoumba do you have that file in your installation ? I don't have anyhting in that directory and upgraded from dapper to feisty.
This is exactly what I was looking at. This directory is empty.
May be rename the file with an _old extension all together ? There is a bug in feisty:
[https://launchpad.net/ubuntu/+source/gnome-app-install/+bug/87965]("https://launchpad.net/ubuntu/+source/gnome-app-install/+bug/87965")

> **Kateikyoushi said:**
> 
Anyway seems apt-get does not make difference between the two files so I recommend to try to comment the problematic line by putting a hashmark (#) at the beginning of the second line.

```
sudo nano /etc/apt/sources.list.d/edgy-universe.list
```

Then save it and try to update again.
Or comment the line out ;)

---

### Post by Spalatum on 2007-03-17
Thanks allot. Putting the # in front of the 2nd line  fixed the problem. The repositories and the updates now work "out of the box".

Thanks to both of you for taking your time. :cool:

---

### Post by bapoumba on 2007-03-17
You're welcome, Spalatum, and many thanks to Kateikyoushi :)

---

### Post by the79bomb on 2007-03-24
I had this same problem.  It's not a problem with /etc/apt/sources.list but rather with the file   /etc/apt/sources.list.d/edgy-universe-list  edit the latter file and remove line 2.

In my case line 2 was redundant anyway as the same command was on line 4 also with a different switch.

after you edit the file run #sudo aptitude update
to update the changes

---

