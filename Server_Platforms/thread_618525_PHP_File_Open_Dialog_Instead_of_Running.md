---
title: "PHP File Open Dialog Instead of Running"
date: 2007-11-20
forum: Server Platforms
---

### Post by AlanMacdonald on 2007-11-20
Hello,

I have recently installed Ubuntu 7.10.

I have installed php5 which synaptic choose apache2 and it's php module as dependencies for me.  It was all very painless and I can verify that the web server is working using http:/localhost and finding the default apache page.

I was in fact following the guide on how to install EyeOS from here [http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy#Step_10]("http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy#Step_10").  I have verified that the basic PHP processing is working as directed from this page [https://help.ubuntu.com/7.10/server/C/php5.html]("https://help.ubuntu.com/7.10/server/C/php5.html") i.e. [http://localhost/phpinfo.php](http://localhost/phpinfo.php) works and returns info on my computer.

My problem is when I try to point Firefox to [http://localhost/apache2-default/eyeOS/install.php](http://localhost/apache2-default/eyeOS/install.php) as stated in step 10 of the EyeOS install guide, then instead of the installer running, Firefox throws up an Open Dialog for install.php to be opened by Gedit by default instead of the web server processing the PHP file and running the installer.  Does anyone know why this is the case?  I have tried restarting my computer to make sure the newly installed stuff was running but the Ubuntu page which I followed seems to show that both PHP and Apache are running anyway.

Your suggestions would be much appreciated.


Thanks,

Alan

---

### Post by p_quarles on 2007-11-20
One thing that *could* have happened is that the ownership changes didn't take effect correctly. Could you post the output of this command?:
```
ls -l /var/www/apache2-default/eyeOS
```

---

### Post by AlanMacdonald on 2007-11-20
Thanks for the reply.

Here's the output:

-rwxrwxrwx 1 alan alan 1915246 2007-10-30 23:50 eyeOS1202.eyepackage
drwxrwxrwx 2 alan alan    4096 2007-10-29 21:46 img
-rwxrwxrwx 1 alan alan  143076 2007-10-30 23:50 install.php
-rwxrwxrwx 1 alan alan   35065 2007-10-25 05:41 license.txt
-rwxrwxrwx 1 alan alan    3635 2007-10-29 23:27 README.txt

I'm not sure that's the problem then.

Anymore ideas?

Many thanks

---

### Post by p_quarles on 2007-11-20
That's exactly the problem. You seem to have skipped step 9, which guarantees that the next step won't work. Either go back to that step and follow the instructions, or you can run this:
```
sudo chown -R www-data:www-data /var/www/apache2-default/eyeOS
```

---

### Post by AlanMacdonald on 2007-11-20
Thanks again for the reply.

Ah, I did in fact run step 9 and I checked that the permission showed in the right click permission window as directed by the instructions but yet as you suggested this did not work as it said it should which would suggest a bug in Gnome or something?  Anyway I ran the chown command and restarted apache using sudo /etc/init.d/apache2 restart and it's still not working :-| 

Maybe I should restart but I would've thot restarting Apache was good enough.

Cheers

---

### Post by AlanMacdonald on 2007-11-20
-rwxrwxrwx 1 www-data www-data 1915246 2007-10-30 23:50 eyeOS1202.eyepackage
drwxrwxrwx 2 www-data www-data    4096 2007-10-29 21:46 img
-rwxrwxrwx 1 www-data www-data  143076 2007-10-30 23:50 install.php
-rwxrwxrwx 1 www-data www-data   35065 2007-10-25 05:41 license.txt
-rwxrwxrwx 1 www-data www-data    3635 2007-10-29 23:27 README.txt

would now appear correct yes?

---

### Post by p_quarles on 2007-11-20
Hmm. Yeah, the ownership is correct now, so I'm not sure why it won't run. Restarting the computer won't do anything. Two wild guesses, though:
1) Maybe your user account is holding onto those files until you've logged out. Try logging out, and then starting a new session.
2) It's possible that Apache doesn't want to parse a .php script with such loose permissions. You could try setting a permissions level that will work with the default Apache setup:
```
sudo chmod 775 /var/www/apache2-default/eyeOS/install.php
```
That will take the ability for other users to write to that file away. 

Note that while I'm not sure changing permissions will fix it, you should do that anyway. The current config is a potential security risk.

---

### Post by AlanMacdonald on 2007-11-20
Thanks for the adivce I changed the permission as you suggested but to no avail and then I logged out and back in, again to no avail.. Very strange.  I'll be off to my bed now but I'll keep trying tomorrow to see if I can get to the bottom of it.

Cheers.

---

### Post by p_quarles on 2007-11-20
I was just thinking about this again, and I wonder if maybe the file somehow got corrupted during the download, or maybe there's a bug in the current script? You might try dl'ing it again and seeing if there's any difference this time. 

The other thing that occurred to me is a PHP interpreter. I have no experience with this, since the PHP I work with is relatively simple and meant for the web. But, this is just a command line interface that runs PHP code instead of Bash code. I just thought this *might* at least allow you to run the installer while bypassing Firefox. 

You can get the interpreter with this command:
```
sudo apt-get install php5-cli
```
or by searching in Synaptic. 

Like I said, I have no idea if this will do anything, since the installer was clearly designed to be used with an html rendering engine. Just an idea that came to me.

A more sane suggestion would be to try installing an alternate web browser (such as Epiphany, Konqueror, Opera, or Galeon) and seeing if it's a Firefox problem.

---

### Post by AlanMacdonald on 2007-11-22
Thanks for all your suggestions.  I redownloaded to no avail.  I installed the PHP CLI option and tried to run but lit didn't seem to work presumably because it needed to run as a web page.

I launched konqueror and tried and it worked!

So Firefox is doing something dumb.  Like I said before my basic test php page worked fine in Firefox so I have no idea why that one never.  I hope this doesn't come up again.

Many thanks.

---

### Post by p_quarles on 2007-11-22
That is weird. Do you have the NoScript extension for Firefox? It's possible that the installer uses some client-side scripting, and it was being blocked by Firefox.

---

### Post by PaulFXH on 2008-04-19
I'd like to resurrect this old thread as I have exactly the same problem. However, changing browser to Konqueror (in my case, neither Opera nor Firefox worked either) didn't solve the problem for me.

So, in summary I've been trying to install eyeOS in Gutsy on my MacBook using this [guide]("http://wiki.eyeos.org/HOWTO_Install_eyeOS_on_Ubuntu_Gutsy").
However, the install step, which involves navigating to [http://localhost/apache2-default/eyeOS/install.php](http://localhost/apache2-default/eyeOS/install.php), does not open the installer. Instead, I'm given the choice of saving the install.php file or opening it with Gedit.

None of the suggestions given by p_quarles have worked for me so far.

Has anybody else come across this problem and knows how to get around it?

---

### Post by p_quarles on 2008-04-19
Have you already verified that PHP test pages work on your installation? If not, you are likely facing a different (and much more common) problem than the OP.

---

### Post by PaulFXH on 2008-04-19
> **p_quarles said:**
> Have you already verified that PHP test pages work on your installation? If not, you are likely facing a different (and much more common) problem than the OP.

Thanks for the reply.
Actually, I have not verified the PHP test pages as I simply don't know how.
Basically if it wasn't mentioned in the guide, then I didn't do it.
Nevertheless, your reply seems to suggest that the solution to my problem might just be straightforward.
Any more clues?

---

### Post by p_quarles on 2008-04-19
I'm guessing that all you will need to do is enable PHP parsing in Apache, which can be done by following these steps:
```
sudo nano /etc/apache2/apache2.conf
```
Add the following line (for me, it's near the end of the file):
```
AddType application/x-httpd-php .php .phtml .php3
```
And restart Apache:
```
sudo /etc/init.d/apache2 restart
```
Let us know how it goes.

---

### Post by PaulFXH on 2008-04-19
Thanks for the reply but I'm afraid that didn't work for me.
I put the line you suggested as the very last line in /etc/apache2/apache2.conf.
However, after restarting apache, and even after a reboot, I still get the same behaviour when I try to launch the install.php script.

BTW, I should mention, if you haven't already guessed, that my server knowledge is severely limited. But, when I type "ps -e" in a terminal, while apache2 is running there's no sign of php5. Should I be worried?

---

### Post by p_quarles on 2008-04-19
Okay, try seeing if PHP itself is working. First, create the auto-generated test page:
```
sudo sh -c "echo '<?php phpinfo(); ?>' > /var/www/info.php"
```
Now, point your web browser to localhost/info.php. It should show a page describing the version of PHP installed.

And no, PHP won't show up as a process, since it is simply a library that is included in Apache's services. Standalone PHP parsers, such as php5-cli, would get their own processes, but the Apache module does not.

---

### Post by PaulFXH on 2008-04-19
Thanks again.
Well, it seems that PHP5, although it is installed, isn't fully funcional.
When I type the line you suggest and then browse to [http://localhost/info.php](http://localhost/info.php) I get a pop-up asking if I want to open or save the info.php file. This, of course, is exactly what I see when I try to launch the eyeOS install.php file.

---

### Post by Dr Small on 2008-04-19
Apparently Php is not installing, or something is messed up with it's default configuration... That's why I don't mess with it from the repositories and simply setup Xampp. It saves alot of headaches.

Dr Small

---

### Post by PaulFXH on 2008-04-19
@Dr Small
Thanks for your comments but I should mention that for clarification that I have already installed eyeOS through apache2/php5 (installed from Ubuntu repos) on two machines.
More interesting is that one of the machines is the MacBook with which I have the present problem.
The reason for me re-installing eyeOS (and therefore apache2 and php5) is due to a problem I had with Gutsy which meant I had to reinstall the entire OS.
So, given that everything did work fine before, it seems likely that whatever is wrong now has to be fairly minor.

---

### Post by PaulFXH on 2008-04-20
Well, looks like Dr Small hit the nail on the head.
I installed Xampp, then re-installed eyeOS (this time to /opt/lampp/htdocs/xampp rather than to /var/www) and install.php launched fine.
So, looks like php5 just wasn't working for me.
Would love to know why as the exact same procedure led to a successful eyeOS installation on the same machine about a month ago.
Thanks Dr Small

---

### Post by Dr Small on 2008-04-20
I think there is something screwy with Php5 from the repositories, and I never could get the gd2 libraries to load in, or I would be using that. It just never worked right, so I always use Xampp.

Just make sure you lock it down if it is connected to the web.
```
sudo /opt/lampp/lampp security
```

Dr Small

---

