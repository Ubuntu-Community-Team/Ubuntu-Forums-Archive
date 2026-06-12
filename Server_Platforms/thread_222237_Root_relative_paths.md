---
title: "Root relative paths"
date: 2006-07-24
forum: Server Platforms
---

### Post by shendric on 2006-07-24
I apologize if this has been discussed before, but I couldn't find anything that addressed it.  I've got Apache running on my Drake box, and I'm trying to run some php scripts.  The biggest problem I'm running into is that I'd like the php scripts to include files that are located in the root directory.  I've set doc_root to the root directory in php.ini, but it cannot find the file with:

include('/header.inc');

I could just make a flat structure to my site, but I'd rather give it a nested structure to make it easier to maintain.

The error I get is:

Warning: include(/MySite/header.inc) [function.include]: failed to open stream: No such file or directory in /var/www/MySite/Directory1/File1.php on line 2

Warning: include() [function.include]: Failed opening '/MySite/header.inc' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/MySite/Countries/Directory1/File1.php on line 2

Any help would be appreciated.  I can get root relative links to work, just not from a php script.

Sean

---

### Post by lamego on 2006-07-26
Some PHP software achieves this by detecting the current absolute path during the install.php script, then this path is written to the "relative" config.php, then you just need to include the relative config.php on your scripts and use the variable from it to refer to full paths...

---

