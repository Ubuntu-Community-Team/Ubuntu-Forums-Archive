---
title: "Snort - PHP - MySQL error"
date: 2007-12-05
forum: Server Platforms
---

### Post by MaindotC on 2007-12-05
Hi, all.  I'm in a network defence class and I'm making an IDS using this tutorial: 

[http://www.openmaniak.com/snort_tutorial_snort.php#ancre-point2](http://www.openmaniak.com/snort_tutorial_snort.php#ancre-point2)

I did a clean install of 7.04, installed all the prerequisites, used the same user name and password stated in the tutorial (snortuser, snortpassword) and I'm having problems with step 2 of the BASE setup.  When I enter the information specified in the boxes, click "submit query", I get the following error messages: ```
 Warning: include(adodb.inc.php) [function.include]: failed to open stream: No such file or directory in /var/www/base/base-1.3.9/setup/setup2.php on line 25

Warning: include()[function.include]: Failed opening '/adodb.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/base-1.3.9/setup/setup2.php on line 25

Fatal error: Call to undefined function NewADOConnection() in /var/www/base/base-1.3.9/setup/setup2.php on line 49 
```

I'm a student and I've taken C and VB but I've no experience or concept of MySQL or PHP.  I've googled, and I can't find my specific issue yet so I'm hesitant to go around changing things.  Can you explain to me the concept of what is going wrong - like it seems to me that a variable is referring to a value that is non existent.  Is that correct?  Here are lines 25 and 49 from setup2.php:
```


#line 25

include($_SESSION['adodbpath']."/adodb.inc.php");

#line 49

$db = NewADOConnection($dbtype);


```

I don't currently have the IDS connected to the internet so let me know if you need any contents of files copied/pasted and I'll connect it.  Also, if anyone wants to VNC into it and give it a shot, I'm in dire need so no problem.  Thanks for anything you can do.

---

### Post by kmac on 2007-12-05
Take out the "/"

```

#line 25

include($_SESSION['adodbpath']."[COLOR="Red"]/[/COLOR]adodb.inc.php");


```

Either that or make sure adodb.inc.php is in the right directory. I think the second error is based off the first. Line 25 is calling upon another file and the "/" may try to direct the program to your root, and the file may not be there (not quite sure). Then line 49 is callign on a function in the file that is being called in line 25, and since line 25 was unsuccessful, line 49 has no idea where that function is. 

--Kyle

---

### Post by MaindotC on 2007-12-05
Thanks, kmac.  I can't get up to the box right now but around 6 pm my time I'll give it another go.  Thanks for replying so promptly!  My network goes "live" on Monday :)  I'll be in touch.

---

### Post by MaindotC on 2007-12-06
Hey, Kyle.  I tried your suggestion and I haven't had any change in my status.  I start/stopped and I also rebooted.  Sorry I know that's kind of newb troubleshooting, but I just made the mistake of taking on something too big for my understanding (at this point).  Can you suggest the next step in troubleshooting?  Want to VNC into it and give it a shot?  It's just a lab computer that will be destroyed in a week anyway so you're welcome to do with it as you wish, as long as I get the IDS working.

---

