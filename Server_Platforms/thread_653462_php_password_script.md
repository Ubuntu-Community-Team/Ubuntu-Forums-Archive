---
title: "php password script ?"
date: 2007-12-29
forum: Server Platforms
---

### Post by e1ektrob0y on 2007-12-29
I tried this script to create a login at my server. I only want the server to display as a directory with other directories within. I didn't know what to call the script so i called it index.php and now it just runs over and over and i cant get to the content at the IP of my server?


```
<?php
if ( $PHP_AUTH_USER != "guest" || $PHP_AUTH_PW != "18Mv0v3x" ) {
  header('WWW-Authenticate: Basic realm="192.168.1.254"');
  header("HTTP/1.1 401 Unauthorized");
  echo "Failed to log in.";
  exit();
  }
else {
  echo "You are logged in successfully as: ".$PHP_AUTH_USER;
  echo "192.168.1.254";
  }
?>

```

---

### Post by andol on 2007-12-29
Try replacing $PHP_AUTH_USER width $_SERVER['PHP_AUTH_USER'] and $PHP_AUTH_PW width $_SERVER['PHP_AUTH_PW']

Your way would probably have worked with *register_globals = on*. For security reasons *register_globals* is nowdays turned off by default.

---

### Post by e1ektrob0y on 2007-12-30
cool thanks, that works. Only problem is, it takes me to a blank page that says 
> You are logged in successfully as: [http://192.168.1.254/](http://192.168.1.254/)
how can i make the script show the contents of the web server as it would be without an "index.php file"? as in, just a listing of directories...thanks:)

---

### Post by andol on 2007-12-30
Feel the need for PHP to handle this? Or perhaps you could let Apache fix this on its own? Especially since you seem to be using http-auth anyway. 

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

---

