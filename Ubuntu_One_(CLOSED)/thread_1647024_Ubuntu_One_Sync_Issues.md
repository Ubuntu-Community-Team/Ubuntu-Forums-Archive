---
title: "Ubuntu One Sync Issues"
date: 2010-12-16
forum: Ubuntu One (CLOSED)
---

### Post by siddarthkaki on 2010-12-16
Recently, I have been having some issues with Ubuntu One. I am running Ubuntu 10.10 Maverick. For some reason, Nautilus tells me that Ubuntu's default Videos folder (there is data in this folder) is synced on Ubuntu One when it is not. I have checked on the Ubuntu One website, and the site says the Videos folder is not synced (Ubuntu One's website does not show the Videos folder under "my synced folders"). When I attempt to uncheck the sync option in Nautilus, the loader next to it spins endlessly, or Nautilus gives me an error that it can not sync the folder. Does anyone have a solution to this? Thank you in advance.

---

### Post by Akavashi on 2010-12-16
Have you by any chance tried the steps from this post  [[COLOR="Red"]here?[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8146023&postcount=2")

Try logging out/restarting after you purge UbuntuOne.

---

### Post by duanedesign on 2010-12-18
> **siddarthkaki said:**
> Recently, I have been having some issues with Ubuntu One. I am running Ubuntu 10.10 Maverick. For some reason, Nautilus tells me that Ubuntu's default Videos folder (there is data in this folder) is synced on Ubuntu One when it is not. I have checked on the Ubuntu One website, and the site says the Videos folder is not synced (Ubuntu One's website does not show the Videos folder under "my synced folders"). When I attempt to uncheck the sync option in Nautilus, the loader next to it spins endlessly, or Nautilus gives me an error that it can not sync the folder. Does anyone have a solution to this? Thank you in advance.

To see a list of User Defined Folders(UDF) open a Terminal (Applications -> Accessories -> Terminal) and run this command. Do you see the Videos folder listed?

```
u1sdtool --list-folders
```

---

### Post by siddarthkaki on 2010-12-25
> **duanedesign said:**
> To see a list of User Defined Folders(UDF) open a Terminal (Applications -> Accessories -> Terminal) and run this command. Do you see the Videos folder listed?

```
u1sdtool --list-folders
```

Sorry for the late reply.

Yes, the Videos folder is listed.

---

