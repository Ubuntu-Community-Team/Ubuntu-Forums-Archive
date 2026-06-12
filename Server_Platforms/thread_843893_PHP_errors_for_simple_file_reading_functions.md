---
title: "PHP errors for simple file reading functions"
date: 2008-06-28
forum: Server Platforms
---

### Post by skunkbad on 2008-06-28
New LAMP server has errors with php functions file_get_contents(), file() or fread():

Warning: file_get_contents() [function.file-get-contents]: php_network_getaddresses: getaddrinfo failed: Name or service not known in /var/www/test/test.php on line 3

Warning: file_get_contents([http://someweb.com/index.html](http://someweb.com/index.html)) [function.file-get-contents]: failed to open stream: Connection refused in /var/www/test/test.php on line 3

The test folder is CHMODed to 777, and also the file, because I had guessed it was a permissions type error. I am the owner, not root, so maybe that is the problem?

---

### Post by windependence on 2008-06-28
What is line 3 of test.php? Can you cut and paste it EXACTLY from your code?

-Tim

---

### Post by skunkbad on 2008-06-28
This is the whole thing:

```
<?php

      $file   = file_get_contents('http://dynamic.zoneedit.com/checkip.html');



?>
```

---

### Post by skunkbad on 2008-06-28
I believe the problem might be that I CHOWNed the www directory so I could upload files via sftp.

I think if I can figure out how to add apache back to co-ownership I will be ok.

---

### Post by windependence on 2008-06-28
Do you have the allow_url_fopen directive on in your php.ini?

allow_url_fopen = On

Also this first error could be a bug:

[http://bugs.php.net/bug.php?id=11058](http://bugs.php.net/bug.php?id=11058)

The second error looks like the server you are trying to access may not be allowing you to connect.


This is a nice and simple substitute to get_file_contents() using curl, it returns FALSE if $contents is empty.

[PHP]<?php
function curl_get_file_contents($URL)
    {
        $c = curl_init();
        curl_setopt($c, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($c, CURLOPT_URL, $URL);
        $contents = curl_exec($c);
        curl_close($c);

        if ($contents) return $contents;
            else return FALSE;
    }
?>[/PHP]

-Tim

---

### Post by skunkbad on 2008-06-29
OK, I found out that the problem is a DNS issue... I am running 2 sites on name based virtual host. I must not have set it up right. I'm really new to server administration, so I'm not surprised there was a problem with DNS.

---

### Post by windependence on 2008-06-29
> **skunkbad said:**
> OK, I found out that the problem is a DNS issue... I am running 2 sites on name based virtual host. I must not have set it up right. I'm really new to server administration, so I'm not surprised there was a problem with DNS.

Good deal. Glad yo got it fixed. You may still want to look at the curl example because the allow_url_fopen being on is not secure.

-Tim

---

