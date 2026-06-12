---
title: "Prevent PHP from accessing files above wwwroot"
date: 2010-09-12
forum: Server Platforms
---

### Post by megabuffen on 2010-09-12
I'm running Apache2 and PHP5, hosting multiple virtual domains on my server. The directories of the domains (/var/www/<domain>) aren't publicly readable, so the websites can't access each others content as the scripts are run using different user accounts. They can, however, access other folders on the system that have public access for any user. I tried using the following PHP code, which listed the filesystem root:

> <?php
$handle=opendir("../../../..");
while($file=readdir($handle)){
    echo $file . "<br/>";
}
?>I will be hosting sites for other people so I don't want them to be able to access my entire server with PHP. Is there any way i can do this?

---

### Post by alan8 on 2010-09-12
Hi, adding '*open_basedir'* to your php.ini should do the trick. As per

[http://php.net/manual/en/ini.core.php](http://php.net/manual/en/ini.core.php)

> 
***open_basedir***
         Limit the files that can be opened by PHP to the specified         directory-tree, including the file itself.  This directive          is *NOT* affected by whether Safe Mode is          turned On or Off.        
                 When a script tries to open a file with, for example,         [fopen()]("http://www.php.net/manual/en/function.fopen.php") or [gzopen()]("http://www.php.net/manual/en/function.gzopen.php"),         the location of the file is checked. When the file is outside the         specified directory-tree, PHP will refuse to open it. All symbolic         links are resolved, so it's not possible to avoid this restriction         with a symlink. If the file doesn't exist then the symlink couldn't be         resolved and the filename is compared to (a resolved)         **open_basedir** .        


---

### Post by megabuffen on 2010-09-12
It works. Thanks a lot.

---

