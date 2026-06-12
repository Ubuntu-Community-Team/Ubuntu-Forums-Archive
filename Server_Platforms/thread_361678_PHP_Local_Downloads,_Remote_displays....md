---
title: "PHP Local Downloads, Remote displays..."
date: 2007-02-14
forum: Server Platforms
---

### Post by firedrow on 2007-02-14
I recently wiped my laptop and installed Edgy on it.  I got everything working, so I decided to move onto installing LAMP software.  I installed Apache, MySQL, and PHP, I tried Apache2, MySQL, PHP4 and PHP5, and then tried XAMPP.

Everytime I open the localhost web browser I get the message:


 Download this file?
 File Type: "backup file".

 Your have no application able to open
 "". You can download it instead.
 Save As...      Cancel        Download


I'm using Epiphany, but have tested under Galeon and Firefox.  On my work laptop on the same network using Opera, it displays just fine.  I had this problem on Dapper, but I can't seem to find the solution again and I can't remember.  I thought it had to do with deleting something, but I don't remember.  Any help would be greatly appreciated.  I can also post conf files if needed.

---

### Post by cyberdonaldson on 2007-02-21
I'm having the same problem.  I'm running edgy with apache2 and php5, and firefox just keeps trying to save the php.  Anybody have any ideas?

---

### Post by firedrow on 2007-02-21
Mine seemed to have fixed itself, but I have a couple suggestions on things I did that might have made a difference.

Try a couple other browsers, see if one of them will reset the mime association of .php files.  I tried Firefox, Epiphany, and Galeon.  Hopefully one of them will load it right, then the others should too.

Do a forced reload on the browser, either shift+tab or ctrl+tab.  I hit one of these a couple times in quick succession.  It's supposed to clear any little options, such as download .php files.

If these don't work, then keep scouring I guess.  I had this problem on Dapper before I moved to Edgy and someone had me delete a mime file and it worked, but I don't remember what it was.

---

### Post by cyberdonaldson on 2007-02-22
> I had this problem on Dapper before I moved to Edgy and someone had me delete a mime file and it worked, but I don't remember what it was.

I've tried several different browsers now, including firefox, epiphany, galeon, konqueror, and w3m.  Still the problem persists.

Thanks for the help, you've given me great suggestions.  I'll do some more searching and see if anything about the mime files comes up.

---

### Post by cyberdonaldson on 2007-02-22
I got it working at last!

I followed the advice from [_this thread_]("http://ubuntuforums.org/showthread.php?t=344802"), which explained how to fully and completely remove apache2 and then reinstall.  Once it was fully wiped, and all the config files were gone, I reinstalled apache2 php5 and mysql and it works first thing.

Thanks so much for you help!

---

