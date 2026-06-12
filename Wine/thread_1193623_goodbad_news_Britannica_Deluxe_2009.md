---
title: "good/bad news Britannica Deluxe 2009"
date: 2009-06-21
forum: Wine
---

### Post by cigtoxdoc on 2009-06-21
Good news is that Britannica Deluxe 2009 installed and ran well under Ubuntu 9.04 and Wine 1.1.24.  My Son got Britannica for his birthday.  I installed program logged in as Dad.  When my Son logs in (as Son) and loads Wine, Wine cannot see Britannica.

I think the problem is that Ubuntu file permissions are keeping the Wine related from my Son's directory from seeing my "C: drive."

How do I fix this problem?

John

---

### Post by Dark Aspect on 2009-06-22
> **cigtoxdoc said:**
> Good news is that Britannica Deluxe 2009 installed and ran well under Ubuntu 9.04 and Wine 1.1.24.  My Son got Britannica for his birthday.  I installed program logged in as Dad.  When my Son logs in (as Son) and loads Wine, Wine cannot see Britannica.

I think the problem is that Ubuntu file permissions are keeping the Wine related from my Son's directory from seeing my "C: drive."

How do I fix this problem?

John

Wine stores data on virtual hard disk usually as .wine in the home folder. You have to enable hidden files and directory in Nautilus to see it. However, when you installed Britannica as the user dad, it installed like:

```
/home/dad/.wine/drive_c/Program Files/Britannica/and so on
```

Your Son's user has a different .wine directory that I am assuming looks like:

```
/home/son/.wine/
```

The fix would be to move your .wine folder from your user account to your son's user account or reinstall Britannica logged in as your son.

---

### Post by amont on 2010-10-27
> **cigtoxdoc said:**
> Good news is that Britannica Deluxe 2009 installed and ran well under Ubuntu 9.04 and Wine 1.1.24.  My Son got Britannica for his birthday.  I installed program logged in as Dad.  When my Son logs in (as Son) and loads Wine, Wine cannot see Britannica.
John

John,
I'm very interested in that question because I can't even install Britannica Deluxe (2007 in my case). Can you give me some more details about your PC environment? I meant, did you need to install previously Java JDK, Adobe Flash, Kubuntu... or just it works out of the DVD?

I run Ubuntu 10.04 and wine 1.2, in a laptop Toshiba, but I have tried Wine 1.2, and also OpenSuse 11.3 with KDE, and neither works. It hangs or give me an error.

Thanks for your time,
Toni

---

