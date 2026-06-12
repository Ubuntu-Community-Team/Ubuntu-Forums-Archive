---
title: "Squid proxy server php redirect issues"
date: 2015-06-08
forum: Server Platforms
---

### Post by jeremy49 on 2015-06-08
Hello,
I have a squid proxy server up and running on port 3128 and an apache service running on port 80. My goal is to forward traffic to a php page I have created to change the url, I have read up and I think I am supposed to use the url_rewrite_program option but when i try this then firefox says the proxy server is refusing connections. i simply added "url_rewrite_program /etc/squid3/test.php" to the config and the issue arises but when commented out the proxy server works like a charm. please help!

---

### Post by SeijiSensei on 2015-06-08
If test.php is just a PHP script, it needs to be "wrapped"  in an executable script, call it test.sh, like this:
```

#!/bin/bash

/usr/bin/php -q /etc/squid3/test.php


```
Mark the script executable with "sudo chmod a+x /path/to/test.sh".  If Squid lets you specify a complete command in url_rewrite_program, then you can try using "/usr/bin/php -q /etc/squid3/test.php" in the directive itself and avoiding the wrapper.

I've not used this facility in Squid.  Does the script need to read any output from Squid?  If so, are you capturing it by using a construct like this?
```

$fd = fopen("php://stdin", "r");
while (!feof($fd)) {
         do stuff
}

```

---

### Post by jeremy49 on 2015-06-08
Thanks for the help! The proxy server now runs like it did before, forwarding in the original page as a proxy yet still doesn't load the php page. I'll play around with it some more I think there is some simple setting I am missing but I really appreciate the help, never thought to use a script to run the php..

so I took a look at the cache log and this error repeats over and over

> 2015/06/08 19:41:47| WARNING: redirector #1 exited2015/06/08 19:41:47| Too few redirector processes are running (need 1/20)
2015/06/08 19:41:47| Starting new helpers
2015/06/08 19:41:47| helperOpenServers: Starting 1/20 'redirect.php' processes
2015/06/08 19:41:47| ipcCreate: /etc/squid3/redirect.php: (2) No such file or directory
2015/06/08 19:41:47| WARNING: redirector #1 exited
2015/06/08 19:41:47| Too few redirector processes are running (need 1/20)
2015/06/08 19:41:47| Starting new helpers
2015/06/08 19:41:47| helperOpenServers: Starting 1/20 'redirect.php' processes
2015/06/08 19:41:47| ipcCreate: /etc/squid3/redirect.php: (2) No such file or directory
2015/06/08 19:41:47| WARNING: redirector #1 exited
2015/06/08 19:41:47| Too few redirector processes are running (need 1/20)
2015/06/08 19:41:47| Starting new helpers
2015/06/08 19:41:47| helperOpenServers: Starting 1/20 'redirect.php' processes
2015/06/08 19:41:47| ipcCreate: /etc/squid3/redirect.php: (2) No such file or directory
2015/06/08 19:41:47| WARNING: redirector #1 exited
2015/06/08 19:41:47| Too few redirector processes are running (need 1/20)
2015/06/08 19:41:47| Starting new helpers
2015/06/08 19:41:47| helperOpenServers: Starting 1/20 'redirect.php' processes
2015/06/08 19:41:47| ipcCreate: /etc/squid3/redirect.php: (2) No such file or directory
2015/06/08 19:41:47| WARNING: redirector #1 exited
2015/06/08 19:41:47| Too few redirector processes are running (need 1/20)
2015/06/08 19:41:47| Starting new helpers
2015/06/08 19:41:47| helperOpenServers: Starting 1/20 'redirect.php' processes
2015/06/08 19:42:02| Pinger exiting.




I raised the children level to 40 and that seemed to cause more of an issue.

---

### Post by SeijiSensei on 2015-06-09
This is the major problem:
> /etc/squid3/redirect.php: (2) No such file or directory
I'll say again though that a simple PHP script cannot act alone as it is not an executable program.  In the example I gave above, the script is run using the command-line parser /usr/bin/php.  So the entry in Squid for the program needs to be either 
```
url_rewrite_program "php -q /etc/squid3/redirect.php"
```
if that is valid syntax, or an executable wrapper script that runs the same command.

---

