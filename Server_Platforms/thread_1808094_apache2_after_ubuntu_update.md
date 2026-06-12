---
title: "apache2 after ubuntu update"
date: 2011-07-19
forum: Server Platforms
---

### Post by Stiner75 on 2011-07-19
Ok, here's my issue.  Earlier today, I had a server running ubuntu 9.** and apache2.  I had a webpage hosted on the server and was able to access it with my windows box.  All was happy and good until I decided I was going to update everything.  I now have Ubuntu 10.04, and a non-working apache2.  When prompted during the update process, I told it to use the maintainers packages instead of my altered config files.  I'm guessing that was my mistake.

I've gone through all the config files, made the right changes and enabled my page (index.html) but every time I go to access the page now, I get a "Problem loading page" displayed.  Everything looks good, so what am I missing?

The page is accessed by [http://192.168.*.*](http://192.168.*.*)  This WAS working before the upgrade.

(and by the way, this was only intended for use in my own network, so access from the outside was not my intention.)

Any help would be greatly appreciated.:confused:

---

### Post by Ryan Dwyer on 2011-07-20
Can you provide the error details?

I think the most likely cause is that Apache isn't running. You can verify this by running "service apache2 status" and start it by running "sudo service apache2 start".

---

### Post by Stiner75 on 2011-07-20
Wow, good call.  Apache2 is NOT running... and giving the command doesn't start it, even though it gives "Starting web server apache2  [ok]

As for more detail, there really isn't any.  I can give the commands to start/restart apache and it appears to.  But after checking the status after starting it, it still not running.  Which would explain why I can't connect to the webpage.  

The question now, is, why doesn't apache2 start when I tell it to?

Got it!!!!  Apache 2 wouldn't restart no matter what I did.  I just purged the installation of it thanks to the instructions of Harisund at this thread  [http://ubuntuforums.org/showthread.php?t=241157](http://ubuntuforums.org/showthread.php?t=241157)

After re-enabling my page and manually starting apache, boom.  There it was, pretty as day.  

Thanks, Mr. Dwyer, for your help.

---

### Post by Ryan Dwyer on 2011-07-20
For reference, if Apache doesn't start you can check the contents of /var/log/apache2/error.log to find out why.

---

