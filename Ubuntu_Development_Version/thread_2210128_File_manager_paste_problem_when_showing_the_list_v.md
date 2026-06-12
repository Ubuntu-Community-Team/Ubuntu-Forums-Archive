---
title: "File manager paste problem when showing the list view"
date: 2014-03-09
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-09
In 12.04, I could right click paste into the folder with it set to displaying files-folders as lists.
This is the same behavior windows uses.

Now it will not do that, the file or folder remains highlighted and the paste can not be done.
So I must switch to tile view to paste and I hate that view.

Can others verify this?
Also I am using gnome.

---

### Post by Mateusz Stachowski on 2014-03-09
I don't have any problem with copying and pasting into folder while Nautilus is set to list view. I only run Unity.

Do you have this version of Nautilus.

> $ apt-cache policy nautilusnautilus:
  Zainstalowana: 1:3.10.1-0ubuntu7
  Kandyduj&#261;ca:   1:3.10.1-0ubuntu7
  Tabela wersji:
 *** 1:3.10.1-0ubuntu7 0
        500 [http://ftp.vectranet.pl/ubuntu/](http://ftp.vectranet.pl/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by sdowney717 on 2014-03-09
looks that way
```
scott@scott-P5QC:~$  apt-cache policy nautilus:
nautilus:
  Installed: 1:3.10.1-0ubuntu7
  Candidate: 1:3.10.1-0ubuntu7
  Version table:
 *** 1:3.10.1-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
scott@scott-P5QC:~$ 
```

I should boot into ubuntu and see what it does.

---

### Post by sdowney717 on 2014-03-09
for example, do a right click and it highlights a file or folder, so paste is of course not an option.
You can not unhighlight to paste.

I cant take a screenshot and show the menu when set to tile icons.

---

### Post by mc4man on 2014-03-09
nautilus no longer has any empty space to the far right of entries in list view so yes you'll need to find/use alternate means
switch to icon view
highlight new location > r. click > paste into folder
drag file to be pasted & drop on new location
drag file to be pasted & hover over new location, then drop after view switches
r. click on file to be copied or moved > copy to or move to option

Or use another file manager

---

### Post by Smask on 2014-03-11
Right-click on the folder name at the top of the window, in this case "home", select "paste into folder"

---

### Post by sdowney717 on 2014-03-11
paste is not an option there.
I right clicked copy on a file, then right clicked on home and no paste.

This was working in 12.04
I dont understand why it cant work now.

---

### Post by mc4man on 2014-03-11
> **sdowney717 said:**
> paste is not an option there.
I right clicked copy on a file, then right clicked on home and no paste.

This was working in 12.04
I dont understand why it cant work now.
The previous poster is clicking on a breadcrumb, you're clicking in Places

---

