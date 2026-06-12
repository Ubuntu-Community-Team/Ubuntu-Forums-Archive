---
title: "Possible Apache cache issue"
date: 2012-12-19
forum: Server Platforms
---

### Post by thnewguy on 2012-12-19
I have run into a problem with Apache on my Ubuntu Server (version 12.04). The problem looks to be a caching issue. I have a PHP script on the server and I find that when I change the script (and save the changes) and then reload the page I still see the original page.

As an example, let's say my original script was called start.php and it just contains this:

```

<?php
echo 'Hello';
?>

```

When I change the script to something like this:
```

<?php
echo 'Good-bye';
?>

```

and then refresh the page in my browser I still see the original "hello" message in my browser. I have tried restarting the Apache service and wiping my browser cache. Does Apache store a cache somewhere that will persist across service restarts?

---

### Post by Doug S on 2012-12-19
On my 12.04 server I did what you did. The new page loaded fine, when I refreshed the page in the web browser. I was using Internet Explorer from a windows vista computer to access the web page. What do you see in the /var/log/apache2/access.log file? I see the new file is delivered in mine, as I made the number of bytes delivered different to know for sure.

---

### Post by thnewguy on 2012-12-19
Doug, thank you for the suggestion. Browsing through the log I found that calls to my page were being redirected (code 302) to another version of the script. I've made adjustments and things now seem to be working properly. I appreciate your help.

---

### Post by SeijiSensei on 2012-12-21
In PHP, you can force the browser not to cache pages by sending these commands in advance of any page output:

```

### don't allow this page to be cached               
header("Expires: -1");               
header("Cache-Control: no-cache");               
header("Cache-Control: must-revalidate");               
header("Pragma: no-cache");               

```

I run an "init" script ahead of all the content, and these are the first commands I run in that script.

---

