---
title: "Nautilus Actions Extra on Ubuntu 13.04"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by ezcomputersolutions on 2013-03-02
Hi guys!
I installed Ubuntu 13.04 yesterday and it is really great. It has fixed a lot of problems that I had with Unity, runs fast and all. The only problem that I have with it is Nautilus 3.6, now renamed Files. In Ubuntu 12.04 and 12.10 you could install "Nautilus Actions Extra" too add a lot of options that you find in Dolphin. Is there any way to add that functionality to Ubuntu 13.04? Thanks.

---

### Post by stinkeye on 2013-03-02
See [**_[COLOR="#B22222"]THIS[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2120433") thread 
in the **Ubuntu +1 (Raring Ringtail)** section.

---

### Post by ezcomputersolutions on 2013-03-02
> **stinkeye said:**
> See [**_[COLOR="#B22222"]THIS[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2120433") thread 
in the **Ubuntu +1 (Raring Ringtail)** section.

Thanks, however that doesn't help me because I added the PPA but it won't even install. I do ```
sudo apt-get install nautilus-actions-extra
``` and it just gives me a long list or errors. I guess it's because Nautilus isn't installed anymore. It's "Files". Is there another way to install it?

I followed the instructions on this page:
[http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html](http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html)

---

### Post by stinkeye on 2013-03-02
Yeah, I got the same error so I tried just installing the individual scripts from the nae ppa
to see if that worked.
[ATTACH=CONFIG]239657[/ATTACH]
They install but don't show.


So I just installed the **nautilus-open-terminal** package from the default universe ppa.
Need to make a bug report.

---

### Post by papibe on 2013-03-02
Thread moved to **Ubuntu +1 (Raring Ringtail)**.

---

### Post by ezcomputersolutions on 2013-03-02
Well not only a bug report, but we should try to get Canonical to put this in the default installation. Right now I am really looking at openSUSE 12.3, and Ubuntu 13.04. If we could get this working, then I will probably switch to Ubuntu 13.04.

---

### Post by stinkeye on 2013-03-02
> **ezcomputersolutions said:**
> Well not only a bug report, but we should try to get Canonical to put this in the default installation. Right now I am really looking at openSUSE 12.3, and Ubuntu 13.04. If we could get this working, then I will probably switch to Ubuntu 13.04.
It's probably got more to do with what the gnome developers vision for nautilus is, than Canonical.
Works in 12.04 and 12.10.

---

### Post by mc4man on 2013-03-02
If you take a look on the ppa the so-called raring packages were auto built on 11/17 & are the exact same as the quantal ones.
Putting aside any nautilus changes since then python-nautilus has changed so no way those packages will work as is in 13.04

Maybe they'll be redone as possible closer or at 13.04 release, no clue

edit: also possible even if redone still won't work. There are some ex. extensions in the new python-nautilus. Trying one as per  included  instructions results in same error seen with ppa ext.'s - 

ERROR:root:code for hash md5 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type md5
ERROR:root:code for hash sha1 was not found.
Traceback (most recent call last):
And so on...& on

All well over my head so don't know if the current python-nautilus is flawed or not

---

### Post by ezcomputersolutions on 2013-03-02
Ubuntu 13.04 is wonderful, but Nautilus 3.6 is way over simplified. If anybody knows any way to to get "nautilus-actions-extra" to work on Ubuntu 13.04 would be much appreciated. Or if not that specific package, something similar.

---

### Post by mc4man on 2013-03-02
> **ezcomputersolutions said:**
> Ubuntu 13.04 is wonderful, but Nautilus 3.6 is way over simplified. If anybody knows any way to to get "nautilus-actions-extra" to work on Ubuntu 13.04 would be much appreciated. Or if not that specific package, something similar.
That would depend on what you want out of nautilus-actions-extra.

I'm sure nautilus-actions can do some of them

---

### Post by ezcomputersolutions on 2013-03-02
> **mc4man said:**
> That would depend on what you want out of nautilus-actions-extra.

I'm sure nautilus-actions can do some of them

But the problem is, is that Gnome renamed Nautilus to "Files", so anything with the name nautilus won't install.

---

### Post by mc4man on 2013-03-03
> **ezcomputersolutions said:**
> But the problem is, is that Gnome renamed Nautilus to "Files", so anything with the name nautilus won't install.
Can't say I've seen that at all.
The name "Files" is quite unimportant, just a line (Name=) in the nautilus .desktop. Can be whatever one wishes (I use "File Manager" here.
The app is still nautilus, binary nautilus, ect.

If for ex. this doesn't install then you've some local issue(s)
sudo apt-get install nautilus-actions

---

