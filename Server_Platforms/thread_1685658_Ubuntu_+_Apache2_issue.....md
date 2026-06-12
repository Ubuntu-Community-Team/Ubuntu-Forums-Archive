---
title: "Ubuntu + Apache2 issue...."
date: 2011-02-11
forum: Server Platforms
---

### Post by zkriesse on 2011-02-11
Ok, recently began testing a BASH script + a PHP script and using Apache2/php5 etc on a Ubuntu system. Tonight my system is flashing that I only have 8.0 KB left for available empty space...it's an almost 200 GB harddrive so I'm a bit worried and confused as to how this could happen...is it the Apache2 session logs? If so where would I find them? If not what else could it possibly be? Any help is appreciated...thanks all. I shall await any and all possible answers....

---

### Post by iiz on 2011-02-11
> **zkriesse said:**
> Ok, recently began testing a BASH script + a PHP script and using Apache2/php5 etc on a Ubuntu system. Tonight my system is flashing that I only have 8.0 KB left for available empty space...it's an almost 200 GB harddrive so I'm a bit worried and confused as to how this could happen...is it the Apache2 session logs? If so where would I find them? If not what else could it possibly be? Any help is appreciated...thanks all. I shall await any and all possible answers....

Session logs: /var/log/apache2/access.log /var/log/apache2/error.log

Those are defaults. I doubt they could take up 200gbs though in a couple days.

You can always go hunting for the folders that are using the most space:
```
du -h --max-depth=1
```
This will print like ls but with the total size of everything in those directories. You can just follow the huge folders till you find the culprit.

I guess you can also do:
```
lsof | grep www-data | less
```

prepare for a lot of output though. The fields in the output are:
```
COMMAND     PID     USER   FD      TYPE             DEVICE SIZE/OFF       NODE NAME
```

Are you using cron to execute the scripts?
Can you post the source code of those scripts?

That could help, it's possible that you are creating some files or looping forever in one of those scripts. Cron would only magnify the problem.

---

### Post by zkriesse on 2011-02-11
Not using CRON, my BASH and PHP Scripts are as follows...

[COLOR="Blue"]BASH Script[/COLOR]
```

#!/bin/bash
cd /var/www/JoeTest || { echo "dir doesn't exist" >&2; exit 1; }
while sleep 5; do cat filea > fileb; 
php gogo.php; done
done



```

[COLOR="blue"]PHP5 Script[/COLOR]
```

<?php
	$myFile = "a.txt";
	$fh = fopen($myFile, 'r');
	$theData = fread($fh, filesize($myFile));
	fclose($fh);
	
	$myFile = "b.txt";
	// @chmod( $myFile, 0777 );
	$fh = fopen($myFile, 'w') or die("can't open file");
	$stringData = $theData;
	fwrite($fh, $stringData);
	fclose($fh);
?>

```

---

### Post by zkriesse on 2011-02-18
Think I found out what it was...php was running without stopping or something...

---

