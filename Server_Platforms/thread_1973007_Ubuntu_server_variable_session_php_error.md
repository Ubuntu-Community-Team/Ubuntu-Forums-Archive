---
title: "Ubuntu server variable session php error"
date: 2012-05-04
forum: Server Platforms
---

### Post by nandosfxdj on 2012-05-04
Hi, I hope you can help me with a problem. Some years ago I developed a gis with apache + php + mapserver + postgresql + postgis + chameleon. I had two systems: one in Windows XP 
32bit and the other with Ubuntu Server 9.10 32bit. I upgraded to v3.0.2 MS4W with (MapServer 5.6.6, PHP 5.3.6, Apache 2.2.17 with OpenSSL 0.9.8o) with Chameleon 2.6rc, PostgreSQL 9 and PostGIS 1.5 on 
windows and have installed on the server a Ubuntu Server 11.10 64bit with Mapserver 5.6.6, PHP 5.3.6-13, Apache 2.2.20, Chameleon 2.6rc, PostgreSQL 9 and PostGIS 1.5.
In windows everything works fine without any error, but in linux all the gis works well except the generation of map images. Chameleon gives me the following error:

"Error rendering map image:
A fatal error has occurred restoring your session.
Please restart the application ".

This error occurs randomly, ie sometimes appear soon after starting the web that maps samples and sometimes tear good maps and after interacting with buttons such as zoom, search, select layers, etc.. comes a time when the error occurs.

I tried to load the maps with various browsers: Internet Explorer 8 and 9, Firefox 9, 11 and 12, with Chrome, etc and all the error (sometimes earlier and sometimes later).

I located the error message in the files of Chameleon and occurs when the session is lost. After questioning the official mailing list Chameleon I have not responded to or Chameleon Mapserver issue, but the problem is the PHP session variables in Ubuntu that are not properly read.
I looked where the variables that make Ubuntu is in / var/lib/php5 / and when I go into the GIS files are created.
For example the content of this folder is:

-Rw-r - r - 1 www-data www-data 0 05/02/2012 12:29 DELETEME
drwxr-xr-x 2 www-data www-data 4096 02/05/2012 13:00 sess_4fa1124a4c1b0
drwxr-xr-x 3 www-data www-data 4096 02/05/2012 13:03 sess_4fa113d58b836
drwxr-xr-x 3 www-data www-data 4096 02/05/2012 13:28 sess_4fa11a52ecf87
drwxr-xr-x 3 www-data www-data 4096 02/05/2012 13:30 sess_4fa11ac13d4a7
drwxr-xr-x 3 www-data www-data 4096 8:15 sess_4fa22030ecf5a 05/03/2012
drwxr-xr-x 3 www-data www-data 4096 8:33 sess_4fa2248dd36d3 05/03/2012
drwxr-xr-x 2 www-data www-data 4096 8:35 sess_4fa2272b9d3c6 05/03/2012
drwxr-xr-x 3 www-data www-data 4096 8:43 sess_4fa228e314a33 05/03/2012
drwxr-xr-x 2 www-data www-data 4096 05/03/2012 10:00 sess_4fa23b23bcd80
drwxr-xr-x 3 www-data www-data 4096 05/03/2012 12:29 sess_4fa25d60a2ea9
-Rw ------- 1 www-data www-data 185 05/03/2012 12:26 sess_gmi7nemimpfsaf2lppn55m92c2

And for example in the directory sess_4fa25d60a2ea9 / that is created by entering the sig files are:
-Rw-r - r - 1 www-data www-data 1336040950-15887 3/5/2012 12:29 8569.map
-Rw-r - r - 1 www-data www-data 1336040951-15887 3/5/2012 12:29 2414.map
-Rw-r - r - 1 www-data www-data 1336040951-15887 3/5/2012 12:29 3346.map
-Rw-r - r - 1 www-data www-data 1336040957-15887 3/5/2012 12:29 2107.map
-Rw-r - r - 1 www-data www-data 1336040957-15887 3/5/2012 12:29 2317.map
-Rw-r - r - 1 www-data www-data 1336040959-15887 3/5/2012 12:29 3372.map
-Rw-r - r - 1 www-data www-data 1336040959-15887 3/5/2012 12:29 7593.map
-Rw-r - r - 1 www-data www-data 1336040960-15887 3/5/2012 12:29 7987.map
-Rw-r - r - 1 www-data www-data 1336040961-15887 3/5/2012 12:29 4889.map
-Rw-r - r - 1 www-data www-data 1336040963-15864 3/5/2012 12:29 2339.map
-Rw-r - r - 1 www-data www-data 1336040963-15864 3/5/2012 12:29 2976.map
-Rw-r - r - 1 www-data www-data 1336040972-15948 3/5/2012 12:29 4146.map
-Rw-r - r - 1 www-data www-data 1336040972-15948 3/5/2012 12:29 8593.map
-Rw-r - r - 1 www-data www-data 128 05/03/2012 12:27 8b4b39babc2d1b7a1b23490574832862.shp
-Rw-r - r - 1 www-data www-data 108 05/03/2012 12:27 8b4b39babc2d1b7a1b23490574832862.shx
-Rw-r - r - 1 www-data www-data 14 967 05/03/2012 12:26 mapDHTML_adjust.map
drwxr-xr-x 2 www-data www-data 4096 05/03/2012 12:29 queryresultdir
-Rw-r - r - 1 www-data www-data 13 898 05/03/2012 12:29 session_file

I searched the internet error php session variables in linux, but what I find is not related to my problem.
I installed everything on the server with Ubuntu 10.11 32bit Ubuntu 4.12 and then with 32 and 64bit and error is the same.

Can anyone give me a clue how to fix it?

---

### Post by Jonathan L on 2012-05-04
Hi nandos

> 
"Error rendering map image:
A fatal error has occurred restoring your session.
Please restart the application ".

This error occurs randomly, ie sometimes appear soon after starting the web that maps samples and sometimes tear good maps and after interacting with buttons such as zoom, search, select layers, etc.. comes a time when the error occurs.

PHP session variables in Ubuntu that are not properly read.
...  sounds as though there's a reliance on something to do with the PHP versions (or something similar).  The bug is triggered when you browse and need to generate a map ... so it will seem random.

May I suggest you look in /var/apache2/error.log which may contain more precise clues.  Post anything you find which you think looks like useful messages.

I'd also look at the output of phpinfo on your working and your non-working systems.
```
<?php phpinfo(); ?>
```

For what it's worth, my suggestion would also be Ubuntu 10.04.4 LTS server: it's very well deployed and you're likely to have a stable and similar environment to other users.  Still good to 2015.

I hope that helps.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2012-05-04
Do you see any errors in /var/log/apache2/error.log, or whatever custom log file you use for this site?  Are you sure you're writing any temporary files you need to a directory to which the www-data user has permissions?

---

### Post by nandosfxdj on 2012-05-07
Hi Jonathan, thanks for your comments, I think the problem with Ubuntu 10.04 is not going to solve, I'm considering the possibility of forgetting linux and instead use Windows Server 2008, because I have too many days trying to fix a problem without solution. I have written countless gis forums, ubuntu, linux, etc and no one seems to know the solution.

The output of phpinfo () I have saved in a pdf and have attached.

Hi SeijiSensei, 
   the apache log is empty, nothing appears. When the error occurs no line appears in the file.

---

### Post by Jonathan L on 2012-05-07
> **nandosfxdj said:**
> Hi Jonathan, thanks for your comments, I think the problem with Ubuntu 10.04 is not going to solve, I'm considering the possibility of forgetting linux and instead use Windows Server 2008, because I have too many days trying to fix a problem without solution. I have written countless gis forums, ubuntu, linux, etc and no one seems to know the solution.

The output of phpinfo () I have saved in a pdf and have attached.

Hi SeijiSensei, 
   the apache log is empty, nothing appears. When the error occurs no line appears in the file.

Hi nandos

Sorry you've had such trouble with it. Certainly if you have something which works, go with that.

If you're minded to give it a final push ..

Your phpinfo() output shows that you don't have errors configured to go to a file.  You'll have to fix that to get any more meaningful error messages.

In your /etc/php5/apache/php.ini you need something like this
```
log_errors = On
error_reporting = E_ALL

```Restart apache
```
sudo /etc/init.d/apache2 restart
```Make a little web page 'div0.php' with the following:

```
<?php
print $hello;
print 1/0;
?>
```When you access that your should get two lines in you /var/log/apache2/error_log:

```
[Mon May 07 11:42:29 2012] [error] [client 192.168.0.234] PHP Notice:  Undefined variable: hello in /var/www/div0.php on line 2
[Mon May 07 11:42:29 2012] [error] [client 192.168.0.234] PHP Warning:  Division by zero in /var/www/div0.php on line 3
```
Once your certain error messages are showing in your log, then try your app again to see if you get something more useful to help track the problem.

My comment about 10.04 wasn't to fix the problem, it was just a suggested version to use while you tried to track it down.

Hope that's some help.

Kidn regards,
Jonathan.

---

### Post by nandosfxdj on 2012-05-09
Hi again, I couldn't answer you before because I was with another job. I restarted apache server as you told me and now the error file show information.

error.log:

[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Warning:  fread (): Length parameter must-be Greater than 0 in / opt / chameleon /  htdocs / common / session / session.php on line 216, referer: [http://150.214.120.135/sig-uco/sigucotecnico.phtml](http://150.214.120.135/sig-uco/sigucotecnico.phtml)
[Wed May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Warning: ini_set (): A session is active. You  can not change the session module's ini settings at this Time in / opt /  chameleon / htdocs / common / session / session.php on line 449,  referer: [http://150.214.120.135/sig-uco/sigucotecnico.phtml](http://150.214.120.135/sig-uco/sigucotecnico.phtml)
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice: A  session Already HAD been started - Ignoring session_start () in / opt /  chameleon / htdocs / common / session / session.php on line 512, referer: [http://150.214.120.135/sig-uco/sigucotecnico.phtml](http://150.214.120.135/sig-uco/sigucotecnico.phtml)
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice:  Undefined index: gnMapSessionMode in / opt / chameleon / htdocs /  UpdateMap.php on line 70, referer: [http://150.214](http://150.214). 120.135/sig-uco/sigucotecnico.phtml
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice:  Undefined index: gszTmpPath in / opt / chameleon / htdocs /  UpdateMap.php on line 84, referer: [http://150.214](http://150.214). 120.135/sig-uco/sigucotecnico.phtml
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice:  Undefined index: gszCurrentState in / opt / chameleon / htdocs /  UpdateMap.php on line 86, referer: [http://150.214](http://150.214). 120.135/sig-uco/sigucotecnico.phtml
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice:  Undefined index: gszMapName in / opt / chameleon / htdocs /  UpdateMap.php on line 87, referer: [http://150.214](http://150.214). 120.135/sig-uco/sigucotecnico.phtml
[Wed  May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Notice:  Undefined index: gszMapPath in / opt / chameleon / htdocs /  UpdateMap.php on line 88, referer: [http://150.214](http://150.214). 120.135/sig-uco/sigucotecnico.phtml

access.log:

150,214,115,194  - [09/May/2012: 10:30:28 +0200] "POST / sig-uco/sigucotecnico.phtml  HTTP/1.1" 200 19547 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_11_0_20_18_s0_2b80ff_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_10_0_20_18_s0_8c00_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_9_0_20_18_s0_806600_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_8_0_20_18_s0_bb19ff_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_6_0_20_18_s0_a153_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_7_0_20_18_s0_35a800_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_5_0_20_18_s0_ff3f3f_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_4_0_20_18_s0_6900a6_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_3_0_20_18_s0_d86600_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_2_0_20_18_s0_8e9000_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_1_0_20_18_s0_646464_ffffffff_c7c7c7_0__360.png  HTTP/1.1" 200 443 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/1336552228_0_0_20_18_s0_f69e04_feca70_646464_1_74616269717565726961000000000000_360.png  HTTP/1.1" 200 475 "http://150.214.120.135/sig-uco/sigucotecnico . phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/buttons/b9257843f96dd25b7454275931bdcf721.png HTTP/1.1" 200  540 "http://150.214.120.135/sig-uco / sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/buttons/b36d7d096e0c45ef7922948e1f4082b5e.png HTTP/1.1" 200  558 "http://150.214.120.135/sig-uco / sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET /  tmp/ms_tmp/buttons/bcf23fdd92acf3ce9e0e4915f89eebee3.png HTTP/1.1" 200  551 "http://150.214.120.135/sig-uco / sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET / chameleon / common / / wrapper /  drawmap.php? Map_session_mode = 1 & REQUEST = KEYMAP & sid =  4faa2b160e534 HTTP/1.1" 200 5679 "http: / / 150.214.120.135/sig-uco/sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194 - [09/May/2012: 10:30:28 +0200] "GET HTTP/1.1  "200 2227" [http://150.214.120.135/sig-uco/sigucotecnico.phtml](http://150.214.120.135/sig-uco/sigucotecnico.phtml) ""  Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "GET / chameleon / widgets / MapNotes /  processing.phtml? Sid = 4faa2b160e534 HTTP/1.1" 200 811  "http://150.214.120.135 / sig-uco/sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194  - [09/May/2012: 10:30:28 +0200] "POST / chameleon / UpdateMap.php?  4faa2b160e534 & sid = U = 1336552306609584 HTTP/1.1" 200 599  "http://150.214.120.135/sig -uco/sigucotecnico.phtml "" Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
150,214,115,194 - [09/May/2012: 10:30:28 +0200] "GET HTTP/1.1  "200 1245" [http://150.214.120.135/sig-uco/sigucotecnico.phtml](http://150.214.120.135/sig-uco/sigucotecnico.phtml) ""  Mozilla/5.0 (Windows NT 5.1; rv: 9.0.1) Gecko/20100101 Firefox/9.0.1 "
127.0.0.1 - [09/May/2012: 10:30:33 +0200] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"

I think it is problem of chameleon code and how it controls the sessions. Perhaps from the Ubuntu 9.10 versions has been updated PHP or Linux that are incompatible with the chameleon code now.

I attached the file which we used Chameleon to control sessions if you can help with anything.

I  must also tell you that I installed everything on Windows Server 2008  Standard Edition and I have no problem and has the same  versions of php, apache, postgresql, mapserver and chameleon. Thanks a lot.

---

### Post by SeijiSensei on 2012-05-09
Well this is the only real error I see:

```
[Wed May 09 10:30:28 2012] [error] [client 150.214.115.194] PHP Warning: fread (): Length parameter must-be Greater than 0 in / opt / chameleon / htdocs / common / session / session.php on line 216, referer: http://150.214.120.135/sig-uco/sigucotecnico.phtml
```

Since fread() takes both a file pointer and a length parameter, the latter is undefined in your script.  I'd start by figuring out why that's the case.  Usually I just set it to an arbitrary value like 1024, but perhaps there's a PHP variable that is supposed to contain this variable but is undefined.

What about the errors concerning undefined array indexes?  Have you looked at those lines in the code?

I'll again ask about file permissions since *nix is much stricter about these things than Windows typically was.  Are you sure that you have permission to write any files that get created along the way in the specified directories?  What about the sessions, where are they stored?  What are the permissions on /tmp/ms_tmp?

---

### Post by Jonathan L on 2012-05-09
Hi

As you've found ouf the versions of PHP etc are okay, what's left are differences between Windows and Ubuntu: of which, file permissions are well worth checking.  I agree with Seiji about the only real error being the first one.

The line of code which is failing is the filesize in the following:
```
if ($fp = @fopen($szSessionFile, "r"))     {
  $szSessionData = fread($fp, filesize($szSessionFile));
  fclose( $fp );
  return($szSessionData);
}
```My belief is that the filesize is returning 0 (or just possibly false), which would generate the error you see.  If we can't read the session data, we'll have all kinds of subsequent errors, such as undefinred indexes, so I'm ignoring those for the time being.  We believe the fopen is working.  What we see is consistent with the files being empty.

As Seiji says: 
> I'll again ask about file permissions since *nix is much stricter about these things than Windows typically was.  Are you sure that you have permission to write any files that get created along the way in the specified directories?  What about the sessions, where are they stored?  What are the permissions on /tmp/ms_tmp?I'd check and check again the file permissions of the directories we need to write into, and the user settings in apache, and the umask.

Hope that's helpful.

Kind regards,
Jonathan.

PS.  

Further reading of the source file ... ( also at [http://www.koders.com/php/fid332F880C82474F284D160479174CBBF263D25BE5.aspx](http://www.koders.com/php/fid332F880C82474F284D160479174CBBF263D25BE5.aspx) ) and I noted in it that there's a debug mechanism (line 81). You could switch that on with something like: [FONT=monospace]
[/FONT]```
$GLOBALS['bDebug'] = [COLOR=Red]true[/COLOR];
$GLOBALS['szDebugDir'] = "[COLOR=Red]/tmp/debuggery[/COLOR]";
```

That might help nail it.

---

### Post by nandosfxdj on 2012-05-21
Hi again, thanks for your help. I had to make this a bit but I've done several tests and found the sequence of actions that always generates the error.

1)  Call the file launcher. Phtml (sigucotecnico.phtml) with chamelon  template file. Html (plantilla_edificios.htm) -> Chameleon interface  displays correctly and the image generated by mapserver correctly
2) I use the widget called "locatebyattribute" to find an id in the picture. Using this widget opens a popup. After entering a value exists, the template is regenerated and shows me the desired value in the image.
3)  I use the widget called "ClearQuery" to clear the search and to  regenerate all mapserver displays the error: "Error rendering map  image."

Jonathan, I turned on the session.php file the lines:
$ GLOBALS ['bDebug'] = true;
$ GLOBALS ['szDebugDir'] = "/ opt / sig-uco /";

And I've created a file called session.log I've attached. I have checked visually described the following pattern:

05/21/2012 10:57:32.3930: not set: initializeSession (sid,,)
05/21/2012 10:57:32.3931: not set: Opened () / var/lib/php5, sid
05/21/2012 10:57:32.3932: not set: session_id () says 4fba037bcbe9d
05/21/2012 10:57:32.3932: not set: Read () 4fba037bcbe9d
05/21/2012 10:57:32.3968: not set: Write () 4fba037bcbe9d
05/21/2012 10:57:32.3973: not set: Closed ()

except when you press the button "ClearQuery" which is the end where lack Close ()

I attached the file "ClearQuery.widget.php" just can take a look and maybe see what may be missing.

The directory permissions I have checked and all is well. This is what is in session variables Ubuntu:

var/lib/php5/sess_4fba037bcbe9d sigucoserver root @ :/ # ls-l
total 120
-Rw-r - r - 1 www-data www-data 15 112 21/05/2012 10:57 1337590652-4874.map
-Rw-r - r - 1 www-data www-data 15 126 21/05/2012 10:57 1337590652-8456.map
-Rw-r - r - 1 www-data www-data 15 670 21/05/2012 11:01 1337590884-3028.map
-Rw-r - r - 1 www-data www-data 15 670 21/05/2012 11:01 1337590884-7221.map
-Rw-r - r - 1 www-data www-data 15 658 21/05/2012 11:01 1337590884-7328.map
-Rw-r - r - 1 www-data www-data 15 213 21/05/2012 11:02 1337590926-4469.map
-Rw-r - r - 1 www-data www-data 14 311 21/05/2012 10:57 mapDHTML_adjust.map
drwxr-xr-x 2 www-data www-data 4096 05/21/2012 11:01 queryresultdir
-Rw-r - r - 1 www-data www-data 134 21/05/2012 11:02 session_file
var/lib/php5/sess_4fba037bcbe9d sigucoserver root @ :/ #

What I can do more? I don't know how to solve it. Maybe going back to ask the Chameleon mailing list and exposing all this, give me a solution.

---

### Post by nandosfxdj on 2012-06-12
Hi, I have finally found the problem and solution. Thanks to a system administrator ubuntu (Sergio) of Spain, we have refined the code of the libraries of Chameleon and found out why there was "Error rendering map".
 The problem  appeared when the function fwrite working in "w" truncated files php session, so the fread function returned a 0 at times. We assumed that was needed while a blocking function fwrite is writing so when looking at the code find the solution. Line 85 of file "session.php" of chameleon says:

 / * File-based locking session based on code Contributed by
 * Andreas Hocevar [email]ahocevar@hotmail.com[/email] * /
 if (isset ($ GLOBALS ['bLockSession']))
           $ GLOBALS ['bLockSession'] = false;

 If you change it to this:

 $ GLOBALS ['bLockSession'] = true;

 deleting the if statement, since there is no error anymore on ubuntu server.

---

