---
title: "Whoops! I've just given the entire filesystem full permissions"
date: 2011-02-14
forum: Security
---

### Post by michaell4 on 2011-02-14
Hi guys.

As the title says, I've just given ubuntu full filesystem permissions. I used the following command thinking it would change the permissions of the folder I was in.

sudo chmod -R 0777

Is there anyway of reverting the permissions without doing a full reinstall?

However saying that, i'm doing a full reinstall just incase.

Thanks.

Michael

---

### Post by ajgreeny on 2011-02-14
I suspect that was your only real option, as files in the root filesystem do not all have the same permissions, though you could have tried ```
sudo chmod -R 0755
```, but I think that would still have left you with problems.

For future reference, if you want to use that sort of command again, make sure you indicate a full pathway to the folder that you want to act upon.  However, as a general rule it is best not to change permissions of files and folders in the filesystem, but to use sudo to do what you wanted.

What were you wanting or needing to do?  It may be too late now in this case, but in future if you need to do something like you tried, there are probably other ways.

---

### Post by CandidMan on 2011-02-14
Could some variation of find be useful here? Something like:

```
find /  -type f -user root -exec chmod -v go=r {} \;
find / -type d -user root -exec chmod -v go=x {} \;
```Just used a variation of this to remove empty folders from Music/ . Worked like a charm :-)

---

### Post by ajgreeny on 2011-02-14
That might find the files and folders, but then what permissions do you change everything to?  Thats the main problem I think; there are lots of different permission permutations within the filesystem, and it is very difficult to know where to set things.

---

### Post by CandidMan on 2011-02-14
Fair point, I just thought I'd put it out there for anyone who didn't have reinstallation as an option or are determined not to reinstall.
Thinking about it now there are special blocks etc in /dev/
Potential nightmare

---

### Post by movieman on 2011-02-14
If you did that from the root directory (/) then a full reinstall will be faster than trying to fix it. If nothing else, you presumably lost the setuid and setgid bits so you'd need to find all of those and repair them.

---

### Post by The Cog on 2011-02-14
I don't think the command you posted would work, because it's missing the target file/directory name (though I daren't try it to be sure). I would expect an error message.

If it really did what you say, then I think your only option is to reinstall.

---

