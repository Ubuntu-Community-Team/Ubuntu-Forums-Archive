---
title: "Problem with PHP and Apache2"
date: 2005-09-18
forum: Server Platforms
---

### Post by tim_astley on 2005-09-18
This seems a common problem but I can't quite work out how others have solved the problem.

I am setting up Apache2/PHP/MySQL - so far most things are going to plan. PHP is working and I can see what I expect. However I have one glitch.

If I go to 
[http://localhost/Cricket](http://localhost/Cricket) 
I get asked by my Mozilla how to download a PHTML file
but if I go to
[http://localhost/Cricket/index.php](http://localhost/Cricket/index.php)
it all works fine.  Something is wrong with a config file I presume but I can't see what. I am used to Redhat and am finding Ubuntu great - once I know where to look!

I hope this problem can be simply solved

Thanks
Tim

---

### Post by deuce868 on 2005-09-18
Search your apache2.conf and make sure you add index.php to the line that starts with DirectoryIndex

See if that works

---

### Post by tim_astley on 2005-09-18
[QUOTE=deuce868]Search your apache2.conf and make sure you add index.php to the line that starts with DirectoryIndex

See if that works[/QUOTE]

Got that already. I think that was default in my install. Good thought though.

Tim

---

### Post by obscenic on 2005-11-08
I'm having the exact same problem and also can't figure out how anyone else solved it.  Did you ever find a solution?

---

### Post by LordHunter317 on 2005-11-08
What does access_log and error_log say about the first request?

---

### Post by obscenic on 2005-11-13
Not sure when I fixed it, tried lots of different suggestions - cleared browser cache completely and it worked...

---

### Post by PokerFacePenguin on 2005-11-16
[QUOTE=obscenic]I'm having the exact same problem and also can't figure out how anyone else solved it.  Did you ever find a solution?[/QUOTE]

I have it too...still scratchin my head.

---

### Post by herrpoon on 2005-11-17
[QUOTE=PokerFacePenguin]I have it too...still scratchin my head.[/QUOTE]

Which version of apache are you using?

From that piccie, at the bottom it says 1.3.33.

---

