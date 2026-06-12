---
title: "Ubuntu 10.04 LTS  Problem with PHP passthru() and corrupting images."
date: 2010-10-20
forum: Server Platforms
---

### Post by zooppoop on 2010-10-20
So I have a simple php page that just uses the passthru() function in PHP to output an image.  This has worked for many years on my other systems  SLES, RHEL, Mandrake, ...   Anyway recently I have moved this to be on this server running Ubuntu 10.04 TLS.  I myself and not that familiar with Ubuntu or the apt-get style package managers so I may be doing something stupid.  And I may not know how to provide information requested without a little detail on the command.  

My program uses a perl program to generate PNG images from RRD DBs.  This is called via passthru().  I am able to generate an image with the perl program and dump the output to a file and have the webserver host that static image without any issue.  But when using passthru() in php it corrupts the image according to firefox etc.  I have done the same with a Curl command and outputted the result to a file which does generate a file that the system is unable to identify.  So I have also just used this on a normal image file using 'cat image.png'  and the web server/php still corrupts the image.  

As far as what it is doing I'm not sure.   Below is a copy of the php code in it's entirety.

```

<?php
    require('../db/config.inc.php');
    if ( $_SESSION['curBillcus'] ) {
        if ($_GET['type'] == "grp")
            $cmd = "cd ".$billscriptsdir."; ".$billscriptsdir."/gengraph --id ".$_SESSION['curBillgrp']." --type ".$_GET['type']." --period ".$_GET['time']." --routergroup ".$_GET['rgroup'];
        else
            $cmd = "cd ".$billscriptsdir."; ".$billscriptsdir."/gengraph --id ".$_SESSION['curBillcus']." --type ".$_GET['type']." --period ".$_GET['time']." --routergroup ".$_GET['rgroup'];
         
       // TEST OVERRIDE
       $cmd ="cat /tmp/test.png";
        header('Content-type: image/png');
        passthru($cmd,$ret);
    } else {
        header('Status: 404 Not Found');
    }
?>

```Thank you for your time.

---

### Post by Ryan Dwyer on 2010-10-20
Are you running PHP in safe mode?

Check /var/log/apache2/error.log to see what's going on. For debugging, you could put error_reporting(E_ALL) and ini_set('display_errors','on') anywhere before calling passthru() and comment the header() line.

---

### Post by zooppoop on 2010-10-22
I am not using safe mode.  Definitely have checked the log.  But Debugging logging seems like a safe bet. ;)  Thanks will post back with that result.

---

### Post by zooppoop on 2010-10-22
Tried using debugging didn't show anything.  Everything does execute without issue, it is just something with maybe corrupting the image header itself.   Anyway I did put it in there without the header() option and enabled debugging with display errors.  The result is the binary data being displayed as text.  Attaching image. 

Let me know if there is something else I can provide.

Thanks again

---

### Post by dtfinch on 2010-10-22
There's mention of a similar issue at [http://www.php.net/manual/en/function.passthru.php#54108](http://www.php.net/manual/en/function.passthru.php#54108) . It went away when they did exit() after the passthru, but I have no idea why.

---

### Post by Ryan Dwyer on 2010-10-22
If there's more than one blank line (or any other content) after the ?> at the end then that will be echoed and will corrupt the image. It's good practice to never put ?> at the end of a script if the whole script is in PHP mode.

---

### Post by zooppoop on 2010-10-25
I tried as you both suggested, but I still get the same result.  Tested it with the exit() directly after the passthru as well as with out the ending code marking  I did verify that there were no extra lines as well.

---

### Post by Ryan Dwyer on 2010-10-25
You said if you cat image.png from PHP and save it to a file then it comes out corrupted, right? In that case, my next step would be to use a hex editor (such as ghex) to find out exactly what the difference is between the two files.

---

### Post by zooppoop on 2010-10-28
So here are the command I ran which just shows you kinda what I'm doing gengraph is just a perl program I wrote to output the image.  The image.php file just calls this via the passthru() fuction.

```

curl "http://127.0.0.1/bill/image.php?time=month&type=total&rgroup=101" >httpout.png

./gengraph --type total --period month --routergroup 101 > /net/html/bill/perlout.png

```I will upload the resulting image files.    I will work on getting a hex editor so I can view this right now I am not at a linux machine with X.

This will not accept my corrupt PNG file it seems so I had to zip it and upload.

thanks

---

### Post by Ryan Dwyer on 2010-10-28
Your httpout file contains 0x0A before the start of the 0x89504E47 signature. In simple terms, it means there's a line break before the image data. If you can't fix this in your gengraph script, a workaround would be to save the gengraph output to a variable then use substr($output, 1) to trim off the first character.

---

### Post by zooppoop on 2010-10-29
This is what I did it did not seem to make a difference. ```
                 $data = passthru($cmd,$ret);                 $data = substr($data,1);                 print $data; 
```  I also tried with exec() and System() but not sure how they would have an affect on the Binary data.  Not sure what to say I guess that this means that it is not the passthru function that is adding the extra linefeed?  That something else in php or apache is adding it corrupting the image?  As for Gengraph I would say that there is not a way for it to trim the extra line feed because it is not the one generating it right?  as I can run it > to a file and the image is correct.  but if I do passthru("cat imagefile"); apache sends corrupt version of it.  I think this has to be something with php or apache in some weird way.

---

### Post by dtfinch on 2010-10-29
Did you check "../db/config.inc.php" and everything it depends on to make sure none of them are adding a blank line? (like after the closing "?>" tag in any of them)

---

### Post by zooppoop on 2010-10-29
Thank you for the help.  I did have a ending tag in the config file.  interesting.  Thank you all for the help!

---

