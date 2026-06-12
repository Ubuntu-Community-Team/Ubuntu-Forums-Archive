---
title: "Correct localhost path for running php FTP script"
date: 2010-02-16
forum: Server Platforms
---

### Post by enixon on 2010-02-16
Hello wise and merciful Ubuntu elders! I'm learning how to access a FTP server with php. I've written a script from a tutorial but I'm getting errors with the ftp_get function.

[PHP]<?php
$resource = ftp_connect('hiddenforsafty');

$login = ftp_login($resource, 'hidden', 'hidden');
if($login){
printf("We are now connected");
}else{
printf("Connection faild");
}

$file = ftp_get($resource, '/var/www/download.txt/', '/IDX/', FTP_ASCII);
?>
[/PHP]

I'm able to login with a ftp client, and when I run this script I get the "we are now connected" message so the login works. But here's my results
> 
We are now connected
Warning: ftp_get(/var/www/download.txt/) [function.ftp-get]: failed to open stream: Is a directory in /var/www/gwr/connect.php on line 11

Warning: ftp_get() [function.ftp-get]: Error opening /var/www/download.txt/ in /var/www/gwr/connect.php on line 11


So I'm having trouble with the ftp_get function and I believe the problem is with the local server path. In this case var/www/download.txt I've also used a folder in that directory called download in the place of the .txt file and it gives the same errors. 

Is var/www/ the correct path to tell php where to download the files to? I've experimented with the files permission and nothing has worked. I'm running a standard ubuntu desktop install,  Karmic Koala.

Thank you very much for your time all of you who've read this.

---

### Post by Satoru-san on 2010-02-16
here is the problem.

```
[COLOR=#000000][COLOR=#DD0000]/var/www/download.txt/[/COLOR][/COLOR]
```

it thinks thats a directory. you need to remove the tailing /

```
[COLOR=#000000][COLOR=#DD0000]/var/www/download.txt[/COLOR][/COLOR]
```

could also be you need to enable url_fopen in your php config.

---

### Post by enixon on 2010-02-18
Hey that did the job. The errors are gone now. Thank you very much for your time. The script now looks like this.

[PHP]<?php
$resource = ftp_connect('hidden');

$login = ftp_login($resource, 'hidden', 'hidden');
if($login){
printf("We are now connected");
}else{
printf("Connection faild");
}

$list = ftp_rawlist($resource, '/idx', true);

if (ftp_get($resource, '/var/www/downloads', '/IDX/features.txt.gz', FTP_BINARY)){
printf("...Files downloaded correctly");
}else{
printf("...Files not downloaded correctly");
}

?>[/PHP]

When I run the script it tells me "Files downloaded correctly, But there's no files in the directory and none appear to be downloaded. I told it to download a specific file that I know is inside there because I didn't know how to tell it to download all. When I change the downloads folder back to download.txt the result is the same. 

Just checking if there's any thing with the localhost path that I've missed since the functions appear to be doing their job.

Thank you again for your time

---

### Post by enixon on 2010-02-21
I apologize for the last post. I simply was telling php to put it in one directory above the one I expected. I am now able to download the files one at a time but when they download they are gzip archives. I can open the gzip file and see the file inside but it will not let me extract it or open it. The archive manager error says "an error occurred while extracting files". Any thoughts on why this is? Also, what is the key insignia to download all in the file? /. /* ??

Thank you greatly for your time.

---

