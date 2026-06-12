---
title: "Conflicts"
date: 2009-05-29
forum: Ubuntu One (CLOSED)
---

### Post by FuturePilot on 2009-05-29
So originally I had dumped a number of files and directories into the My Files directory. Something like
```
Ubuntu One
|
|-My Files
    |
    |-file1
    |-file2
    |-dir1
    |-dir2
    ...
```

I decided this was too messy so I created a new directory under My Files and moved all those files and directories into the new directory I created. It looks something like this
```
Ubuntu One
|
|-My Files
    |
    |-new dir
        |
        |-file1
        |-file2
        |-dir1
        |-dir2
        ...
```
Now the problem is that when my laptop went to sync up with the changes it seemed to have gotten confused. All of the files are still under the My Files directory with ".conflict" appended to them. In the new directory I created, there is an identical set of files only they are empty and have ".partial" appended to them. The client is no longer syncing, so it's kind of stuck in this state. Is this a bug? Is there anything I can do to give it a little kick and make it re-sync or something?

---

### Post by joshuablount on 2009-06-18
Hi! Yes, this seems like a bug to me. 

I just attempted a similar thing (shuffling around some folders to see how it would work) with the most recent client, and I seem to be getting the correct results (folders move around, no .conflict files, web ui reflects the changes, etc)

Have you gotten any further with this? Sorry no one has responded in a while, we're still getting used to having a section of the forums for Ubuntu One stuff :)

---

### Post by helbent forleder on 2009-10-13
I just had the same problem 2 days ago, so it looks like it hasn't been resolved.

---

### Post by joshuahoover on 2009-10-15
> **helbent forleder said:**
> I just had the same problem 2 days ago, so it looks like it hasn't been resolved.

Hi, I'm sorry to hear the .u1conflict files are still occuring for you. This can happen for a number of reasons. If you can file a bug report by right-clicking on the Ubuntu One applet in your task bar and selecting "Report a Problem", we'll be able to better help you there. Also, for this bug we'll likely need you to attach ~/.cache/ubuntuone/log/syncdaemon.log to the bug report. Note that attaching syncdaemon.log will show filenames you are attempting to sync with Ubuntu One. If you do not want this to be public, please mark the bug as private and this bug report will only be available to you and the Ubuntu One team.

Thank you,

Joshua

---

