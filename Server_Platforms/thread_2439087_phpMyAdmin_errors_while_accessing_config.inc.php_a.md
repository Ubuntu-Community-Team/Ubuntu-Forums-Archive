---
title: "phpMyAdmin errors while accessing config.inc.php and blowfish_secret.inc.php"
date: 2020-03-22
forum: Server Platforms
---

### Post by bokime on 2020-03-22
Hello guys,

this is not really an ubuntu-exclusive question, but highly related to ubuntu...

  I'm running phpMyAdmin 4.6.6deb5 on the following configuration:
  
[LIST]
[*]Ubuntu Server 18.04.3 
[*]nginx/1.17.9 
[*]7.2.24-0ubuntu0.18.04.3 
[/LIST]
  phpMyAdmin seems to work, but there's this red error message that  says something about the blowfish secret. Somehow there's no way to get  rid of it. The error-log contains the following entries:
  
```
2020/03/22 21:46:30 [error] 26664#26664: *53 FastCGI sent in stderr: "PHP message: phpmyadmin: Failed to load /var/lib/phpmyadmin/blowfish_secret.inc.php Check group www-data has read access and open_basedir restrictions. PHP message: phpmyadmin: Failed to load /var/lib/phpmyadmin/config.inc.php Check group www-data has read access and open_basedir restrictions" while reading response header from upstream, client: 87.147.18.48, server: ***, request: "GET /phpmyadmin/js/get_image.js.php?theme=pmahomme&v=4.6.6deb5 HTTP/2.0", upstream: "fastcgi://unix:/run/php/php7.2-fpm.sock:", host: "***

```
Both, the folder and the files, are assigned to www-data. I've also assigned the following permissions:

  ```
# chmod 755 /var/lib/phpmyadmin
# chmod 664 /var/lib/phpmyadmin/blowfish_secret.inc.php  
# chmod 664 /var/lib/phpmyadmin/config.inc.php
``` 

Doesn't work... :(

  What seems strange to me is the fact that the config.inc.php is empty and the blowfish_seceret.inc.php looks like this:
  
```
<?php
$cfg['blowfish_secret'] = 'j(<purKyJl>5D]yzlPoKFLNfH9es6.-T';
``` 

It seems like both files are broken. Could anybody tell me where I can find right files? I know that there are several config.inc.php filesin different folders, some of them including the line for the blowfish_secret, but I don't know which of them is the right one to copy to /var/lib/phpmyadmin.
 
I've found similar issues while searchig on stackoverflow and other forums, but none of the suggested solutions worked for me.
  
Thanks in advance

  Best Regards
Boris

---

### Post by LHammonds on 2020-03-25
You might want to check out [Adminer](https://www.adminer.org/en/phpmyadmin/)

LHammonds

---

### Post by SeijiSensei on 2020-03-25
Does blowfish_secret.inc.php actually have no closing "?>" tag?  If it doesn't, try adding that as the last line of the file.

```
<?php
$cfg['blowfish_secret'] = 'j(<purKyJl>5D]yzlPoKFLNfH9es6.-T';
?>

```

---

