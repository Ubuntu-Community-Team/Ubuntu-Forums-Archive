---
title: "Server Monitoring Script"
date: 2010-10-25
forum: Server Platforms
---

### Post by Chrus on 2010-10-25
I've got an Ubuntu server running Asterisk and im looking for a simple way to monitor it. I dont really need a lot out of it, just the basics like HDD/RAM/CPU usage. I was thinking something like a script that ran as a cron job every morning that sent me an email with a heap on data would be the way to go.

Surely this has been done before. Anyone know where I could find such a script? Or know of a better/easier way to get a similar result?

Cheers

---

### Post by HermanAB on 2010-10-25
Use top:

$ top -n 1 > top.txt

Then email the file to yourself.

---

### Post by abix_adam_pl on 2010-10-25
Or use Canonical Landscape, or [http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/), or any other RDD tool, there are a lot of them in net.

Adam

---

### Post by SeijiSensei on 2010-10-25
[Logwatch]("http://sourceforge.net/projects/logwatch/files/") is a nice little program that summarizes your server logs.  It's in the repositories.  Run it from cron.daily and pipe its output to the mail command to send you the report.  Running "sudo logwatch" from the prompt will display the standard report on the console.

---

### Post by d3v1150m471c on 2010-10-25
```

#!/bin/bash

# the following command will pipe top's output for "x" iterations  to a file.
# modify to your needs

top -n 1 > file1

# next we'll pipe the output of df to a file to get our mounted drives usages

df -h > file2

# put the 2 files together

cat file1 file2 > email-text

# you may need mailutils for the following. if so:
# sudo apt-get install mailutils

cat email-text | mail -s "server status" youremail@youremaildomain.com


```

now all you'll need to do is set the cron job. :)

---

### Post by Chrus on 2010-10-25
Thanks for that guys. Looks like some good stuff there. Should keep me busy for a while.

---

### Post by confusedstingray on 2010-10-27
i have found a web page that i use it is from one of the ubuntu forum members

[HTML]
!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<?php
// ==================================================================
// Script written by quietas (http://ubuntuforums.org/member.php?u=300503)
// Script Modified 24 Feb 2009 by ussr - CHANGE THIS WHEN YOU MOD THIS
// Make sure this is all good for running over SSL.
// ==================================================================
?>

<html>
<head>
<BODY BGCOLOR="#000000" TEXT="#00CC00">
<title>SERVER PAGE</title>

<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0$
</STYLE>
</head>

<center><h1>ADMINISTRATION PAGE FOR SERVER</h1></center><br>
<center>AUTHORIZED ACCESS ONLY. SERVER LOGS ARE MONITORED</center<br>



<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>Users:</b> 
<?php system("users"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>Mounted Filesystems:</b>
<?php system("di"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

<center><h3>Report bugs <a href="mailto:youremail"> here </a></h3></center>

<meta http-equiv="refresh" content="30">
<?php
 echo' Last updated: '.date('j F Y', getlastmod()); ?>
 </div>
</body>
</html>

[/HTML]

---

### Post by confusedstingray on 2010-10-27
forgot you need to put this in your default www directory it up dates at 2omin intervals

---

