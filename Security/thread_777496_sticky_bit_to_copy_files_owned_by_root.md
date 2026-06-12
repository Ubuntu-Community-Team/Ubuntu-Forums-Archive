---
title: "sticky bit to copy files owned by root"
date: 2008-05-01
forum: Security
---

### Post by thnn on 2008-05-01
I've read and re-read discussions on the sticky bit - but I still seem to be using it wrong.

I'm managing a server where several team members are working on a project together. Without giving root access to this team members, I'd like to allow them to copy over a directory of files owned by root, permission are 700 on that directory.

our group is "stowdev"

my script is as follows:

```

#!/bin/bash
cp -r /path/to/rootowned .

```

I called it cp_rootowned and set permissions as follows:

```

-rwsr-xr-- 1 root    stowdev   58 2008-05-01 09:35 cp_rootowned

```

this doesn't work, it just says permission denied. If I add a whoami to that script it prints my username... I thought that sticky bit meant it would run as root?

Also, once I get the script to copy the files, I'll have to make the files owned by whoever ran the script - any tips?

thx!

---

### Post by movieman on 2008-05-01
Setuid is generally disabled by default for shell scripts. I'm not sure how to enabled it if you must do that.

---

### Post by The Cog on 2008-05-01
You can set the setuid bit on scripts, it's just that the kernel doesn't honour it. Security reasons, allegedly. It will honour it for comiled code though. A C program with a system() call will do the trick.

I thought the setuid bit and sticky bits were different. I'm not certain though.

---

### Post by thnn on 2008-05-01
thx for the replies. I'll just skip it for now, it's not a must-have. Just trying to explore and learn a little. I could well be wrong in calling it sticky bit...

---

### Post by movieman on 2008-05-02
> **The Cog said:**
> I thought the setuid bit and sticky bits were different. I'm not certain though.

Yes. One is an 's' and the other is a 't' :).

The sticky bit on executables used to keep them in memory to reduce startup time the next time they're run; I've no idea what it does these days.

---

### Post by lemming465 on 2008-05-02
This is a job for *sudo*

---

### Post by thnn on 2008-05-02
oh.. right of course, I can give the user sudo rights for just that script... shoulda thought of that

---

### Post by The Cog on 2008-05-02
> **movieman said:**
> Yes. One is an 's' and the other is a 't' :).

The sticky bit on executables used to keep them in memory to reduce startup time the next time they're run; I've no idea what it does these days.

I seem to remember that on a shared folder, it makes the contents files only delete-able by the owner even though the directory is world writeable. /tmp is an example.

---

### Post by stmurray on 2008-05-02
> **thnn said:**
> oh.. right of course, I can give the user sudo rights for just that script... shoulda thought of that

If you allow them to be able to sudo the script, make sure they can't edit (write to) it-- otherwise they can add whatever command they want in the script and it will run as root........the same may be true if they can delete the file and replace it with one of their choosing....

---

