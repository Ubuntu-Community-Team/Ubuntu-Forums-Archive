---
title: "Firefox and &quot;failure to initialize ... security component&quot;"
date: 2008-06-04
forum: Security
---

### Post by tiggerntatie on 2008-06-04
This afternoon I booted up the laptop with Hardy and when I launched Firefox I get this popup first: 

*Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.*

The consequences of this are that attempting to hit a https site kills Firefox instantly.

Renaming ~/.mozilla fixes the problem but I lose all bookmarks, etc., so I am not crazy about that. What should I delete inside ~/.mozilla?

---

### Post by kamaji792 on 2008-06-06
If all you are worried about is the book marks.  Hunt around in the ~/mozilla directory for a bookmarks.html file (I guess ~/.mozilla/Profiles/zxcvbbnn.default/bookmarks.html).  Then copy the file from your old profile into your new working profile.

I'm a bit vague about the full path because I'm basing it on a Windows install of Firefox but I am sure the bookmark.html file is the one you want.

I guess you will also loose any add-on's but they do not take long to re-install.

All the best

---

### Post by euchrid33 on 2008-06-08
I'm getting this error as well.  Does anyone know what causes it?

---

### Post by SPACEQWERTY on 2009-06-16
> **tiggerntatie said:**
> This afternoon I booted up the laptop with Hardy and when I launched Firefox I get this popup first: 
 
*Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.*
 
The consequences of this are that attempting to hit a https site kills Firefox instantly.
 
Renaming ~/.mozilla fixes the problem but I lose all bookmarks, etc., so I am not crazy about that. What should I delete inside ~/.mozilla?
 
 
 
IT'S SO SIMPLE PEOPLE, ALL YOU HAVE TO DO IS GO TO YOUR PROFILE DIRECTORY:
C:\Documents and Settings\yourprofile\Application Data\Mozilla\Firefox\Profiles\someweirdlettersand#'s.default AND RIGHT CLICK(ANYWHERE IN THE BACKROUND), CLICK PROPERTIES, AND UNCHECK THE READ ONLY BOX, CLICK APLLY, THEN CLICK "APPLY TO CHANGES TO THIS FOLDER, SUBFOLDERS, AND FILES", CLICK OK, AND YOUR DONE, EVERYTHING SHOULD BE BACK TO NORMAL. POSTED BY SPACE.

---

### Post by jhansonxi on 2011-01-05
Correct solution [**is here**]("http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component").

---

### Post by diesal3 on 2012-02-22
> **SPACEQWERTY said:**
> IT'S SO SIMPLE PEOPLE, ALL YOU HAVE TO DO IS GO TO YOUR PROFILE DIRECTORY:
C:\Documents and Settings\yourprofile\Application Data\Mozilla\Firefox\Profiles\someweirdlettersand#'s.default AND RIGHT CLICK(ANYWHERE IN THE BACKROUND), CLICK PROPERTIES, AND UNCHECK THE READ ONLY BOX, CLICK APLLY, THEN CLICK "APPLY TO CHANGES TO THIS FOLDER, SUBFOLDERS, AND FILES", CLICK OK, AND YOUR DONE, EVERYTHING SHOULD BE BACK TO NORMAL. POSTED BY SPACE.

Hey, remember, we don't all use windows here. Also, your post look ugly in capitals. You could possible also write out the path to directory better so that people can read it.

---

### Post by oldos2er on 2012-02-22
Closed, necromancy.

---

