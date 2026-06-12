---
title: "Get server information again"
date: 2009-12-21
forum: Server Platforms
---

### Post by humphreybc on 2009-12-21
When you first login to a server (either remotely via openssh or on the server itself) it gives you something like:

```

Linux benjamin-server 2.6.31-16-generic-pae #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Mon Dec 21 22:14:03 NZDT 2009

  System load: 1.16              Memory usage: 8%   Processes:       73
  Usage of /:  21.8% of 4.58GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Mon Dec 21 22:11:17 2009

```

What's the command to bring up this (obviously updated) information again?

And perhaps instead of having the "Usage of" showing the first partition (which in the case above is just the OS install partition) how can you set it to show another partition? (Like the data one - what you really want to know about)

---

### Post by BkkBonanza on 2009-12-21
The file that ultimately determines the login message is /etc/motd.
However, this is a link to an auto built version in /var/run/motd.
That version is built by a series of run-part scripts in /etc/update-motd.d/ directory.
And that process is apparently started by pam-motd under control of pam for login.
I say apparently because they seem to change this process often in my looking at various info around the web.
I believe you need to edit the scripts in /etc/update-motd.d/ to get the results you desire. They get run in numeric order to make the motd text.

(Note this seems to be current for Karmic as the changes were apparently made last summer. So if you are on older versions reading this then it is likely different)

---

### Post by Xanthomryr on 2009-12-21
> **humphreybc said:**
> When you first login to a server (either remotely via openssh or on the server itself) it gives you something like:

```

Linux benjamin-server 2.6.31-16-generic-pae #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Mon Dec 21 22:14:03 NZDT 2009

  System load: 1.16              Memory usage: 8%   Processes:       73
  Usage of /:  21.8% of 4.58GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Mon Dec 21 22:11:17 2009

```

What's the command to bring up this (obviously updated) information again?


The command is landscape-sysinfo. How you can change the shown partition I don't know.

---

### Post by BkkBonanza on 2009-12-21
The landscape-sysinfo program is called by /etc/update-motd.d/50-landscape-sysinfo which is a symlink to /usr/share/landscape/landscape-sysinfo.wrapper.

So to change that format you would have to create your own script that produced it as you like and then link it in instead of this one.

/usr/bin/landscape-sysinfo itself appears to be a python script so it's possible to use that as a base but you wouldn't want to directly change it as that could break anything that may depend on it.

---

### Post by humphreybc on 2009-12-21
Sigh - all seems a bit too complicated just to see space available on another partition.

Any other ideas?

---

### Post by HighCommander540 on 2009-12-21
> **humphreybc said:**
> Sigh - all seems a bit too complicated just to see space available on another partition.

Any other ideas?

Yeah, its really easy actually.

```
df -a
```

---

### Post by BkkBonanza on 2009-12-21
As HighCommander notes df -a will work. Add -h for human readable units.
If that output satisfies you then to have it show upon login replace the script,

/etc/update-motd.d/50-landscape-sysinfo

with a simple one that calls df. You can get fancier, like landscape-sysinfo, or just keep it simple.

I guess landscape-sysinfo is a fairly new thing as otherwise I don't know why they haven't built more options/choices into it.

---

### Post by Queue29 on 2009-12-22
This is a script that some other UF user posted a while back. It's a php script that shows a bunch of info when you navigate to it:

```
<?php
// ==================================================================
// Basic server infomation and links to internal webpages.
// ==================================================================
?>

<html>
<head>
<title> Server</title>
<center>
<br/>
<h1>Server Pages</h1><br/>
<a href="http://google.com"> Add Links Here </a>


</center>
<br/>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; COLOR: black; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0 0 0 0;  }
#turnkey-credit #override { display: none; }
</STYLE>
</head>
<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>External I.P.</b>
<?php system("wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null"); ?>

<!--
<b>System Information:</b>
<?php system("lsb_release -a"); ?>
-->
<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

</body>
</html>

```

(I modified it just a bit, commenting out one thing and adding in the fetching the external IP command)

[sample]("http://bozosort.com/stats.php")

---

