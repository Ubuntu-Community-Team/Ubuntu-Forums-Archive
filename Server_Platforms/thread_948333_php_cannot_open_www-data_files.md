---
title: "php cannot open www-data files"
date: 2008-10-15
forum: Server Platforms
---

### Post by ierse010 on 2008-10-15
Hi,

I'm a noob to setting up a server platform in Ubuntu and have a question. 

I created a python script which creates folders and files in a temp directory among my webserver files. This all works fine. Running my python script from terminal it creates the files and folders as user 'dertig' and group 'dertig', this is my default user. Also i can accesse the created files by http.

The problem arises when running the python script from php (using popen) though. Still the python script creates all the files as expected, but now the user is 'www-data' and group is 'www-data' All the created files can be accessed from http, no problem.

The problem i'm facing is trying to access the files from php using:
[PHP]
$localfile = '/var/www/webproject/temp/2008_10_14_16_04_12_65075_zip/file.zip';

	Header("Pragma: public");
	Header("Expires: 0"); // set expiration time
	Header("Cache-Control: must-revalidate, post-check=0, pre-check=0");
	Header("Content-Type: application/zip");
	Header("Content-Disposition: attachment; filename=file.zip");
	Header("Content-Transfer-Encoding: binary");
	Header("Content-Length: ".filesize($localfile));
	readfile($localfile);[/PHP]

PHP doesnt seem to have access to the files.
When i force php to read files created by user 'dertig' it is posible to read them using PHP. So the problem is reading www-data files using php commands like readfile() and filesize()

example of dir listing and rights:

```
drwxrwxrwx 18 www-data dertig   4096 2008-10-15 10:59 .
drwxr-xr-x  4 nobody   nogroup  4096 2008-10-14 16:18 ..
drwxrwxrwx  2 www-data www-data 4096 2008-10-14 16:22 2008_10_14_16_22_35_76099
drwxrwxrwx  2 www-data www-data 4096 2008-10-14 16:22 2008_10_14_16_22_35_76099_zip
drwxrwxrwx  2 dertig   dertig   4096 2008-10-15 10:24 2008_10_15_10_24_11_88975
drwxrwxrwx  2 dertig   dertig   4096 2008-10-15 10:24 2008_10_15_10_24_11_88975_zip
drwxrwxrwx  2 www-data www-data 4096 2008-10-15 10:26 2008_10_15_10_26_35_32756
drwxrwxrwx  2 www-data www-data 4096 2008-10-15 10:26 2008_10_15_10_26_35_32756_zip
```

---

