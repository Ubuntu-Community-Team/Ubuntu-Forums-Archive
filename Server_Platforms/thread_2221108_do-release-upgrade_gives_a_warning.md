---
title: "do-release-upgrade gives a warning"
date: 2014-04-30
forum: Server Platforms
---

### Post by m3rtijn on 2014-04-30
So the upgrade to 14.04 is finally done. It crashed, it hung, the kernel went in limbo, dpkg became corrupted. But in the end, I'm the one who fixed it all. Great.

One last (hopefully) thing:

```

$ do-release-upgrade
Checking for a new Ubuntu release
Ignoring unknown parameter "announce version"
No new release found

```

Why do I get that warning/error? I'm not getting it on my other servers...
Should I be worried about this warning? I guess I should, since I'm not getting it on other servers, but for now I'm noticing any other weird behaviour just yet...

---

### Post by bapoumba on 2014-04-30
Make sure you are on trusty and all up to date:
```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

In that case, if you are on trusty up to date, unless you force the upgrade to the development version 14.10, there is no new release.

---

### Post by m3rtijn on 2014-05-01
I can't find any lines in sources.list with anything other than trusty.

I just noticed, `apt-get update` also produces this warning:
```
$ sudo apt-get update
0% [Working]Ignoring unknown parameter "announce version"
Ignoring unknown parameter "announce version"
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
...
```
What could it mean?

/edit
Ooh, even ssh'ing to another server gives this warning:
```
$ ssh andromeda
Ignoring unknown parameter "announce version"
martijn@andromeda's password:
```

Is there some sort of generic system component that's being called and produces (or is capable of producing) this warning?

---

### Post by bapoumba on 2014-05-01
All I can find with this error is related to samba :
[https://answers.launchpad.net/ubuntu/+source/apt/+question/177652](https://answers.launchpad.net/ubuntu/+source/apt/+question/177652)
The solution was to purge samba (including conf files) and reinstall.

There are other unanswered threads here on the forums.

Please have a look at this page : [https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html](https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html)
and search for announce version. Does it ring a bell ? Not sure if the info is still relevant. Looking here [https://www.samba.org/~ab/output/](https://www.samba.org/~ab/output/) says 2008. There is also this one [http://www.ast.cam.ac.uk/~rgm/cirsi/samba/docs/man/smb.conf.html#announceversion](http://www.ast.cam.ac.uk/~rgm/cirsi/samba/docs/man/smb.conf.html#announceversion)

Going here [https://www.samba.org/samba/docs/man/manpages/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages/smb.conf.5.html)  from the main samba.org page does not show the same wording.

Just look for samba announce version in a search engine and see if you find anything helpful.

---

### Post by m3rtijn on 2014-05-01
Wow, that's it!

There was an entry in /etc/samba/smb.conf:
```
announce version = 6.0
```
I don't remember having added that, or I may have plucked it from an example config. In anycase, I removed this line, restarted smbd and nmbd, and the warnings are gone.

One thing though: why does this warning pop up when executing a command that has absolutely nothing to do with samba? Isn't that strange to say the least?

---

### Post by bapoumba on 2014-05-01
> **m3rtijn said:**
> Wow, that's it!

There was an entry in /etc/samba/smb.conf:
```
announce version = 6.0
```
I don't remember having added that, or I may have plucked it from an example config. In anycase, I removed this line, restarted smbd and nmbd, and the warnings are gone.

One thing though: why does this warning pop up when executing a command that has absolutely nothing to do with samba? Isn't that strange to say the least?

Glad to see you got it fixed! Please mark your thread as solved (under Thread Tools), thanks.

To answer you question, I have no idea, I'm not that familiar with samba and how it interacts with the system, and in particular if it talks to the package managers.
[http://ubuntuforums.org/showthread.php?t=1740312&p=11184373#post11184373](http://ubuntuforums.org/showthread.php?t=1740312&p=11184373#post11184373)
[http://oreilly.com/openbook/samba/book/appc_01.html](http://oreilly.com/openbook/samba/book/appc_01.html)
[https://www.samba.org/samba/docs/using_samba/ch07.html#samba2-CHP-7-TABLE-4](https://www.samba.org/samba/docs/using_samba/ch07.html#samba2-CHP-7-TABLE-4)

May be it was announcing itself in a way the package manager was unable to complete the upgrade due to some conflicts with version numbers ?

---

