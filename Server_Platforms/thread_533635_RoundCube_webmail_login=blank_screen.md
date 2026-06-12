---
title: "RoundCube webmail login=blank screen"
date: 2007-08-24
forum: Server Platforms
---

### Post by b06dqn on 2007-08-24
I've installed the webmail, and edited those 2 config files, when i go to the login page it times out and returns a blank screen, as you can see here [http://89.44.128.136/roundcubemail/](http://89.44.128.136/roundcubemail/)

the error log says the problems comes from here:
PHP Fatal error:  Maximum execution time of 120 seconds exceeded in /var/www/roundcubemail/program/lib/imap.inc on line 132

from this file line 132 is :
```
$buffer = fgets($fp, 2048);
```

and it is part of this function:

```
function iil_ReadLine($fp, $size){
	$line="";
	if ($fp){
		do{
			$buffer = fgets($fp, 2048);
			$line.=$buffer;
		}while($buffer[strlen($buffer)-1]!="\n");
	}
	return $line;
}
```

Those anyone know what do i need to do?
i found similar errors with the blank screen on other forums but with no actual solution.
Thanks

---

