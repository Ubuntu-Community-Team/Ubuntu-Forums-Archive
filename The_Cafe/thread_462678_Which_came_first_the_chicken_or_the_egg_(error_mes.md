---
title: "Which came first: the chicken or the egg? (error message)"
date: 2007-06-02
forum: The Cafe
---

### Post by Atreus12 on 2007-06-02
I had an error when booting up, due to a botched mount(or something). Anway, the error didn't get saved to /var/log, but I wrote it out by hand, it was too good to pass up.

```

filesystem (and not swap or ufs or something else), the superblock is corrupt, and you might try running e2fsck with an alternate superblock:

e2fsck -b 8193 <device>

/dev/hda6: clean 294/256512 files, 2056/512064 blocks

fsck died with exit status 8

*filesystem check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable. Please repair the filesystem manually

*A maintance shell will now be started

Control -D will terminate this shell and resume system boot

bash: no job control in this shell
bash: groups: command not found
bash: less pipe: command not found

The program 'apt-get' is currently not installed.
You can install it by typing: apt-get install apt

```

---

### Post by Kingsley on 2007-06-02
Lol

---

### Post by R3linquish3r on 2007-06-02
hahaha. interesting.

---

### Post by guitarmaniac on 2007-06-03
LMAO, did you try it? Somehow I think it wouldnt work;)

---

### Post by Lucifiel on 2007-06-03
ROFL... 
> 
apt-get install apt

That's classic! :D

---

### Post by 23meg on 2007-06-03
[http://www.bash.org/?766211](http://www.bash.org/?766211)

---

### Post by H.E. Pennypacker on 2007-06-03
> The program 'apt-get' is currently not installed.
You can install it by typing: apt-get install apt

LOL.  Thanks for sharing.

---

### Post by FuturePilot on 2007-06-03
Absolutely priceless. Lol. That made my day.
:lolflag:

---

### Post by shijirou on 2007-06-03
OMG... lol! How'd you get rid of the error then? I'd like to know. XD

---

### Post by Feba on 2007-06-03
Lmfao. Catch22s in computers are wonderful. Reminds me of the time I couldn't install drivers because they wanted to run in X, and I couldn't run X because it wanted graphics card drivers. 

I have to say, "apt-get install apt" is better than "No keyboard detected. Press any key to continue" though.

---

### Post by Atreus12 on 2007-06-03
> **shijirou said:**
> OMG... lol! How'd you get rid of the error then? I'd like to know. XD

I had edited my fstab, and forgot to add a remount option. After fixing the fstab, everything is fine. :)

I think what happened (I am not an expert in linux by any means) is that it mounted the file system, scanned it, had an error, unmounted it, and then didn't have much of a shell left. The maintance shell it started had no commands that actually worked.

---

### Post by JC_510 on 2007-06-03
Hahaha, nice one. :D

Glad you got it fixed up ok.

---

### Post by happy-and-lost on 2007-06-03
Hehe, I've seen that a few times before. Mostly when Windows crashes causing my ext3 drives to be uncleanly dismounted by Ext2Ifs. Almost as good as:

**Keyboard Failure: Press F11 To Continue**

---

### Post by Feba on 2007-06-04
Just for fun, to see what would happen if you apt-get remove apt:

> WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 33.6MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 


---

### Post by Lucifiel on 2007-06-04
Btw, this thread was so funny that I refused to pass up the opportunity of setting it as my signature on another forum.

---

### Post by Ozor Mox on 2007-06-04
I saw this a while ago when my hard drive somehow corrupted itself and needed to be repaired by that scanning utility. The scan failed, and it kicked me into the recovery shell or whatever it's called asking me to run it manually there, where I guess no applications work and the error message appeared.

Same message, apt-get not installed, install using sudo apt-get install apt. Heh, silly!

---

