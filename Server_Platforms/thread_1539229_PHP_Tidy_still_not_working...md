---
title: "PHP Tidy still not working.."
date: 2010-07-26
forum: Server Platforms
---

### Post by bartrail on 2010-07-26
hi friends,
i followed this very nice thread and successfully installed tidy on my apache running php5:
[http://ubuntuforums.org/showthread.php?t=195636&page=2](http://ubuntuforums.org/showthread.php?t=195636&page=2)

unfortunately it seems I can't get it working.. when calling this example [http://www.php.net/manual/en/tidy.examples.basic.php#89334](http://www.php.net/manual/en/tidy.examples.basic.php#89334) 

I get following errors, 
1st:  tidy_parse_string() expects exactly 1 parameter, 3 given -> so I remove the last two parameters, then this:
2nd:  Fatal error: Call to a member function cleanRepair() on a non-object..

this example using new tidy() doesn't work either (Class 'tidy' not found  (or 'Tidy' - tried everything that came to my mind)) [http://www.php.net/manual/en/tidy.examples.php](http://www.php.net/manual/en/tidy.examples.php)

in my phpinfo() output, everything seems ok: tidy is installed with libTidy Build Date 25 march 2009...

any help would be appreciated.

System is Ubuntu10.04 with PHP Version 5.3.2-1ubuntu4.2

---

