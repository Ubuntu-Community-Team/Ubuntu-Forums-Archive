---
title: "Is this normal for OSSEC?"
date: 2012-08-25
forum: Security
---

### Post by Stonecold1995 on 2012-08-25
I have OSSEC HIDS installed and I'm using the web UI.  However, I'm getting a lot of errors with it.  Almost every line in the log says "Unknown problem somewhere in the system"...

[[IMG]http://www.pictureshack.us/thumbs/21682_OSSEC.png[/IMG]](http://www.pictureshack.us/images/21682_OSSEC.png)



Also, ever time I refresh the page, a line saying there's a PHP error is added to the log (so if I refresh 5 times, there's an extra 5 "PHP errors").

[[IMG]http://www.pictureshack.us/thumbs/35948_OSSEC1.png[/IMG]](http://www.pictureshack.us/images/35948_OSSEC1.png)

**Is this normal for OSSEC?**

After less than one day, doing a control+F and searching for "unknown" came up with 26,004 results, and "problem" came up with 26,006...

---

### Post by Ms. Daisy on 2012-08-25
I'm afraid I don't know anything about ossec aside from what I just googled.  It says it looks for root kits, and if it's anything like rkhunter & chkrootkit, then you have to run a baseline every time the kernel is updated and be aware of lots of false positives. 

Totally OT, you have got an absurd amount of tabs open in that browser :D

---

### Post by Stonecold1995 on 2012-08-25
> **Ms. Daisy said:**
> I'm afraid I don't know anything about ossec aside from what I just googled.  It says it looks for root kits, and if it's anything like rkhunter & chkrootkit, then you have to run a baseline every time the kernel is updated and be aware of lots of false positives. 

Totally OT, you have got an absurd amount of tabs open in that browser :D

It's not a rootkit message, that much I'm sure.  OSSEC doesn't just scan for rootkits, it tries to catch anything suspicious happening on the host computer.  And I don't think it's like rkhunter where it simply checks system files against the checksums of the last time it scanned.  Also, I didn't know chkrootkit needed to perform a baseline scan...  I use both rkhunter and chkrootkit and as far as I know, only rkhunter checks files against their last configuration, while chkrootkit simply looks for a list of files unique to rootkits.

And yes, I have a lot of tabs open.  In fact I have another Chromium window open with almost as many tabs.  I suck at organizing things!

---

### Post by unspawn on 2012-08-25
> **Stonecold1995 said:**
> I have OSSEC HIDS installed (..) Almost every line in the log says "Unknown problem somewhere in the system"
Rule Id 1002 means just egrep log file for "(core_dumped|failure|error|attack|bad |illegal |denied|refused|unauthorized|fatal|failed|segmentation fault|corrupted)" and report it w/o applying any filtering / logic, so that kind of "reporting" requires a human to read meaning (or not) into it. See the documentation for writing exclusion rules (local_rules.xml).


> **Stonecold1995 said:**
> Also, ever time I refresh the page, a line saying there's a PHP error
Seems the web UI hasn't been maintained for the past year or two. If you know PHP you could fix it and submit a patch.

---

### Post by Stonecold1995 on 2012-08-25
Is there a way to have it only display warning levels above a certain number, like only display level 5 warnings and up and hide the rest?  I wasn't able to find anything in the documentation.

It turns out that the PHP error is coming from this in the Apache error log:
```
[error] [client 127.0.0.1] PHP Warning:  fseek() expects parameter 3 to be long, string given in /var/www/ossec/lib/os_lib_alerts.php on line 842, referer: http://localhost/ossec/index.php
```
I have no idea what that means though...

---

### Post by ooVoh9em on 2012-08-26
> **Stonecold1995 said:**
> 
It turns out that the PHP error is coming from this in the Apache error log:
```
[error] [client 127.0.0.1] PHP Warning:  fseek() expects parameter 3 to be long, string given in /var/www/ossec/lib/os_lib_alerts.php on line 842, referer: http://localhost/ossec/index.php
```
I have no idea what that means though...

1) Open /var/www/ossec/lib/os_lib_alerts.php in your favorite text editor:
```
sudo nano /var/www/ossec/lib/os_lib_alerts.php
```

2) Scroll down to line number 842, which should look like the following:
```
fseek($fp, $seek_place, &#8220;SEEK_SET&#8221;);
```

3) Once the aforementioned line is located, change it so it looks like the example below:
```
fseek($fp, $seek_place, SEEK_SET);
```

This should correct the PHP errors and reduce the amount of information that accumulates in your logs.

Good luck, and I hope this solution works for you. If it does not work, or causes problems, simply change the line back to what it was originally and resume operations like normal.

---

### Post by Stonecold1995 on 2012-08-26
> **troopa said:**
> 1) Open /var/www/ossec/lib/os_lib_alerts.php in your favorite text editor:
```
sudo nano /var/www/ossec/lib/os_lib_alerts.php
```

2) Scroll down to line number 842, which should look like the following:
```
fseek($fp, $seek_place, “SEEK_SET”);
```

3) Once the aforementioned line is located, change it so it looks like the example below:
```
fseek($fp, $seek_place, SEEK_SET);
```

This should correct the PHP errors and reduce the amount of information that accumulates in your logs.

Good luck, and I hope this solution works for you. If it does not work, or causes problems, simply change the line back to what it was originally and resume operations like normal.

Thank you!  That seemed to have worked perfectly.  What did that do btw?  I don't know any PHP, only a little Bash...

---

### Post by ooVoh9em on 2012-08-26
> **Stonecold1995 said:**
> Thank you!  That seemed to have worked perfectly.  What did that do btw?  I don't know any PHP, only a little Bash...

The error message says the third paramater should be a different datatype than what is supplied, and made reference that the supplied datatype was a string.

With that information, it was a tad bit obvious that a developer made a simple typo and added quotes around the third paramater, forcing its datatype to be set as a string when that was not the intended datatype for that variable.

So, removing the quotes should have fixed the issue.

---

### Post by Stonecold1995 on 2012-09-01
> **troopa said:**
> The error message says the third paramater should be a different datatype than what is supplied, and made reference that the supplied datatype was a string.

With that information, it was a tad bit obvious that a developer made a simple typo and added quotes around the third paramater, forcing its datatype to be set as a string when that was not the intended datatype for that variable.

So, removing the quotes should have fixed the issue.

It did.  It also made it so that the log being displayed was trimmed (which is great because before that thousands of lines were displayed and the page size grew so massive Chromium began crashing).

---

### Post by bodhi.zazen on 2012-09-02
As with your other thread, ossec is going to throw a number of false positives.

You will need to read the ossec documentation and rules and you are best off filing a bug report(s) with ossec.

Editing the rules is a temporary, and less then ideal solution.

You can also white list certain IP. I usually white list my home network, router, and localhost.

---

### Post by Stonecold1995 on 2012-09-02
> **bodhi.zazen said:**
> You can also white list certain IP. I usually white list my home network, router, and localhost.

How do I do that?  In /var/ossec/etc/ossec.conf this is already present, and it looks like that means localhost is already whitelisted, but I'm still getting these errors.

```
<global>
  <white_list>127.0.0.1</white_list>
  <white_list>^localhost.localdomain$</white_list>
  <white_list>8.8.8.8</white_list>
  <white_list>192.168.1.254</white_list>
</global>

```

---

### Post by bodhi.zazen on 2012-09-02
I am not sure off the top of my head, did you try the ossec mailing list

---

