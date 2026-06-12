---
title: "wine won't install battleground antietim"
date: 2011-02-26
forum: Wine
---

### Post by kapi on 2011-02-26
I've tried wine config and I've selected the .exe files and clicked wine option but keep getting this:

The file '/home/craig/new games/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.


any ideas please

---

### Post by davidmohammed on 2011-02-26
not sure what you mean by wine option

but

in a terminal type

chmod +x <exe file name>

or using just right click the exe and select properties - on the permissions tab click the "execute" checkbox.

---

### Post by lkjoel on 2011-02-26
> **kapi said:**
> I've tried wine config and I've selected the .exe files and clicked wine option but keep getting this:
 
The file '/home/craig/new games/setup.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit.
 
 
any ideas please
If you trust the download source, open up a Terminal (Applications->Accessories->Terminal) window.
Type in it:
```
sudo chmod 0555 /home/craig/new\ games/setup.exe

```
Then it should work.

---

### Post by kapi on 2011-02-26
Thanks will try it now

---

### Post by kapi on 2011-02-26
actually it's running from a cd, would I have to copy the contents of the cd to my home folder and then run the command?

---

### Post by lkjoel on 2011-02-26
> **kapi said:**
> actually it's running from a cd, would I have to copy the contents of the cd to my home folder and then run the command?
You don't need to.
My command will work anywhere on the hard drive.
```
sudo chmod 0555 /home/craig/new\ games/setup.exe 

```

---

### Post by kapi on 2011-02-26
You are a gentleman and a scholar, thanks so very much

---

### Post by kapi on 2011-02-26
well your commands work fine but the problem appears when the program wants to run, says there's a wine problem and I should check their web site

thanks for your help

---

### Post by lkjoel on 2011-02-26
> **kapi said:**
> well your commands work fine but the problem appears when the program wants to run, says there's a wine problem and I should check their web site

thanks for your help
Could you post a screen shot of it?

---

