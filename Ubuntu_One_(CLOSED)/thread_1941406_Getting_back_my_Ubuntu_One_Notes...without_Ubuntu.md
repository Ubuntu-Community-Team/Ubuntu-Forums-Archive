---
title: "Getting back my Ubuntu One Notes...without Ubuntu"
date: 2012-03-15
forum: Ubuntu One (CLOSED)
---

### Post by djwkd on 2012-03-15
Hi there,

A while ago, I uninstalled my Ubuntu due to the lack of support for predominantly Adobe applications, which I needed for my school work. However, I continued to use Ubuntu One Notes, as I preferred its interface over Google Docs. I used it mainly for keeping lyrics to songs I'd written available from anywhere, under the impression that it would, you know, stay...

Foolish me.

Fast forward a few months, and I go to one.ubuntu.com/notes, and I get a 404. Went to the Ubuntu One homepage to log on. No notes link. After googling, I found out that it was being taken offline on that day. First time I'd heard! Next time, UO - PLEASE give people a proper notice when they log in!

Anyway, I tried downloading the notes application for Android, but it keeps crashing on Sync, so I only have a couple of the notes (I have a lot on the service).

I installed Tomboy for Windows, but found that when I went into preferences, it set that synchronisation was "not configurable". Which is, you know, kind of irritating...

So, basically...how do I get all those notes back onto my computer? Is there -any- way to do it on Windows, or will I just have to re-install Ubuntu just to get that one app for 10 minutes?

Thanks,

Dom.

---

### Post by djwkd on 2012-03-15
Right...solved that problem by using version 1.6.0. Have entered the server into the box, and have authorised with UO, and have pressed save. Then, when it tries to sync. It says "synchronisation failed. See details below". I click the thing for details, and there is nothing...

---

### Post by Dragonbite on 2012-03-15
What about running a LiveCD and attaching the Ubuntu One to your account? Maybe you can copy the files or their content to something else like Google Docs.

---

### Post by duanedesign on 2012-03-20
Please try the following script that should provide you with the information regarding what note is causing the synchronization to fail.

Press Alt-F2, type "gnome-terminal", press "Enter" and run:

```
cd /tmp
wget
http://people.canonical.com/~roman.yepishev/us/tomboy-sync-validator.py
python tomboy-sync-validator.py
```

It should print something like this:

```
API ref is at https://one.ubuntu.com/notes/api/1.0/user/, querying...
Notes are at https://one.ubuntu.com/notes/api/1.0/op/, querying...
Current sync GUID: 0
Latest sync revision: 2
Found 5 notes
[1/5] "Start Here": OK
[2/5] "Ubuntu One": OK
[3/5] "Hello again!": OK
[4/5] "Using Links in Tomboy": OK
[5/5] "New Note 1": OK
```

However if there is an error it will print something like:
```
[1/5] "Start Here": ERROR
23d57ffb-a492-4ba1-adf4-72f0eb23b254: last-change-date-is-broken
(000)

https://one.ubuntu.com/notes/view/23d57ffb-a492-4ba1-adf4-72f0eb23b254
```

If the script is showing you that there are errors in the notes, please run the script again with --fix option:

```
python tomboy-sync-validator.py --fix

```
After the script finishes running, please try syncing the notes again.

---

