---
title: "Read Only Mounts"
date: 2008-08-30
forum: Server Platforms
---

### Post by MONK_DUCK on 2008-08-30
Hi All,

I have a need to be able to setup bind mounts that are read only within a single FS e.g.

/store/system/template1

is bound to other systems

/store/system/company1/template
/store/system/company2/template
/store/system/company3/template

For many long and boring reasons it needs to be located within each of the company folders.  The other problem is the interface to update files within this template is the same user as will have access to the company directories.  Hence my need for a read only link.  My first thought was to try use symlinks however this has caused a few problems.

What I was hoping to do was this:-


mount --bind /store/system/template1 /store/system/company1/template

mount -o remount,ro /store/system/company1/template

However this appears to make the WHOLE /store read only, even though I thought it would only effect the template folder within company1! :(

Is this expected and if we is there a way around this????

I am running Ubuntu 8.04 Server, although could possibly run 8.10.

---

### Post by MONK_DUCK on 2008-08-30
I have just tested this on 8.10 with this setup

/store/test1/test
/store/test2/test

mount --bind -o ro /store/test1/test /store/test2/test

The bind works as when I make a file in test1/test I can see it in test2/test.

However I am still able to change the file even though when I run mount it states:-

/store/test1/test on /store/test2/test type none (ro,bind)


Looking [http://kernelnewbies.org/LinuxChanges]("http://kernelnewbies.org/LinuxChanges") it suggests this should work in this version as uname -a states 2.6.26-5

---

### Post by MONK_DUCK on 2008-08-31
By the looks of it, it is supposed to work however I don't seem to be the only one with this problem.

[http://lwn.net/Articles/281157/](http://lwn.net/Articles/281157/)

There is a possible work around however it is not perfect.

[http://www.linuxquestions.org/questions/linux-general-1/mount-bind-read-only-478154/#post3264534](http://www.linuxquestions.org/questions/linux-general-1/mount-bind-read-only-478154/#post3264534)

---

