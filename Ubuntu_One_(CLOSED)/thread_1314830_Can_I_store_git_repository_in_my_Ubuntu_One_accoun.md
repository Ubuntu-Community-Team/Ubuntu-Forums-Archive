---
title: "Can I store git repository in my Ubuntu One account?"
date: 2009-11-04
forum: Ubuntu One (CLOSED)
---

### Post by valfreixo on 2009-11-04
Is it possible to put my repository in my Ubuntu One? It would be nice to have my repository stored somewere safe.

Thank you

Vx

---

### Post by 5carby on 2009-11-05
I'd guess so, providing you get it all in one folder, and that folder doesn't exceed 2gb.

I'm not an expert though, and I'm probably wrong. :lolflag:

---

### Post by zoniq on 2010-04-30
Should work. I do the same with Dropbox.

---

### Post by joshuahoover on 2010-04-30
> **valfreixo said:**
> Is it possible to put my repository in my Ubuntu One? It would be nice to have my repository stored somewere safe.

Thank you

Vx

Yes you can. You can even store a bzr repository there if you want. :)

-Joshua

---

### Post by LeoMaheo on 2010-06-24
**[COLOR="Red"]Ubuntu One just messed up some Git repos of mine.[/COLOR]**

Here is what Ubuntu One did to my .git folder:
(The u1conflict files are Ubuntu One's conflict files?)

```

.git
|-- branches
|-- COMMIT_EDITMSG
|-- config
...
|-- [COLOR="red"]ORIG_HEAD[/COLOR]
|-- [COLOR="red"]ORIG_HEAD.u1conflict[/COLOR]
|-- packed-refs
`-- refs
    |-- heads
    |   |-- [COLOR="red"]master[/COLOR]
    |   |-- [COLOR="Red"]master.u1conflict[/COLOR]
    |   `-- old
    |-- remotes
    |   `-- origin
    |       |-- master
    |       `-- old
    |           `-- master
    `-- tags
        `-- old
            |-- delete
            `-- profile-and-bad-war

```

**And** lots of files in my currently checked out branch have been **reverted to earlier versions**, or messed up in some other manner (don't know yet).

I can fix this by renaming some files in the .git dir,
and revert changes done to the checked out files.

I wonder if a Git newbie would know how to do that
(understanding that Ubuntu One has messed up the repo,
and proceeding to rename files inside the .git dir),
or if, from his/her point of view, the repo is
destroyed forever?

I wonder if ``git gc'' would mess up my repo even more.

***

> **joshuahoover said:**
> Yes you can. You can even store a bzr repository there if you want. :)

-Joshua

Joshua did you mean a bare Git repo? Or a Git repo with checked-out-files? (I suppose a bare repo would work ... seemingly? better.)

For how long have you used Git and Ubuntu One without problems?

My problems appeared today, 2 - 3 weeks after starting
synchronizing my Git folders with Ubuntu One.

***

I have connected to Ubuntu One from only one computer.

(I've disconnected Ubuntu One for now.)

Kind regards, Magnus

---

### Post by LeoMaheo on 2010-06-24
Here are all files that Ubuntu One has reverted:

```

14:32:49 99 ~/me-dev/dezzi/jspwiki[master*]$ find . -type f -iname '*u1conflict'
./jspwiki/.gitignore.u1conflict
./jspwiki/.git/ORIG_HEAD.u1conflict
./jspwiki/.git/index.u1conflict
./jspwiki/svn-export/build.xml.u1conflict
./jspwiki/svn-export/src/com/ecyrd/jspwiki/providers/AbstractFileProvider.java.u1conflict
./jspwiki/svn-export/src/com/ecyrd/jspwiki/providers/ProviderException.java.u1conflict
./jspwiki/build.sh.u1conflict
./core/.git/config.u1conflict
./core/.git/index.u1conflict
./.git/config.u1conflict
./.git/ORIG_HEAD.u1conflict
./.git/refs/heads/master.u1conflict
./.git/index.u1conflict
./pom.xml.u1conflict
./.gitmodules.u1conflict
./dezzi-jspwiki-forum/pom.xml.u1conflict
./dezzi-jspwiki-forum/src/main/scala/com/dezzi/jspwiki/DezziForumPlugin_v0.java.u1conflict

```

(Don't know if this matters, but that's 17 reverted/messed-up files out of 2283 files.)

Ubuntu One should, from my
point of view, have reverted none of these files.

I don't understand with why
Ubuntu One came up with the idea to revert these files?
I've been modifying them on one computer only, and connected to
Ubuntu One from that computer only. It seems strange to me that 
Ubuntu One then can find conflicts and start reverting my files.

Regards, Magnus

---

### Post by klakin on 2011-09-15
I had the same trouble.  It is caused if you commit and push changes, then shut down the computer before the changes get uploaded.  (I wish Ubuntu would warn you and give an option to shut down after syncing)
To fix it DON'T DO ANYMORE COMMITS.  Fix the conflict files and you will be ok after that.

---

