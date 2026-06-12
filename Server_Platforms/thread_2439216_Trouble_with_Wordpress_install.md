---
title: "Trouble with Wordpress install"
date: 2020-03-24
forum: Server Platforms
---

### Post by edvigil on 2020-03-24
Hello
I recently upgraded Ubuntu 16.02 to 18.02 on a localhost. I was using the Virualmin script to install Wordpress on Ubuntu 16.02. Always worked. After I upgraded I was unable to use the
script. It failed to install.
"Package 'php7.0-mysqli' has no installation candidate 
E: Unable to locate package php70-mysqli"




I switched php versions from 7.0.33 to 7.2.24 in Virtualmin server configuration and it seemed to install but when I clicked this link:


"WordPress initial installation complete. It can be completed at http://mysite.com/Support/wp-admin/upgrade.php"
It triggers a "save as" dialog box for "upgrade.php"




Same trigger happened when I tried to install a script of phpMyAdmin.


One more thing: I tried to install Wordpress manually with the same result. a "Save as" dialog box  pops up.

---

### Post by SeijiSensei on 2020-03-24
You probably need to install libapache2-mod-php which will invoke PHP for any script ending in .php.  If you install the LAMP package, all these interstitial bits are installed automatically along with Apache, PHP, and MySQL.

```
sudo apt install lamp-server^
```

I've always found the easiest way to install WP, assuming you have an empty MySQL database created for the purpose, is to simply unzip the current file, usually called "latest.zip" into the /var/www/html directory.  (You need to do this as root with sudo.)  Then point your browser to [http://localhost/wordpress](http://localhost/wordpress).

---

### Post by TheFu on 2020-03-24
What OS are you running?  None of those numbers make any sense.
**lsb_release -a** will show the release for Ubuntu systems.

Being correct on the details matters.

---

### Post by edvigil on 2020-03-24
Thank you SeijiSensei. I will try your suggestion. I have LAMP installed. Will this reinstall over existing my existing LAMP? I think you are on the right track [COLOR=#000000] with libapache2-mod-php being the problem.
[/COLOR][COLOR=#242729][FONT=Arial]"Without that library, the Apache don't know what is [/FONT][/COLOR].php[COLOR=#242729][FONT=Arial] file, and recognizes it like raw file which can be downloaded, without being interpreted by PHP" 
Does this sound correct to you? By the way I have Ubuntu Server 18.04.4 installed on a local machine.
Thanks again![/FONT][/COLOR]

---

### Post by SeijiSensei on 2020-03-25
> **edvigil said:**
> Thank you SeijiSensei. I will try your suggestion. I have LAMP installed. Will this reinstall over existing my existing LAMP? I think you are on the right track with libapache2-mod-php being the problem.
Usually that file is installed automatically when you install the lamp-server package.  Otherwise you can install it manually with
```
sudo apt install libapache2-mod-php
```

If you install lamp-server again, the installer will either say it is already installed and not do anything, or it will update the packages to their latest versions.

BTW, libapache2-mod-php isn't a library. It adds code to the Apache configuration to support files with .php extensions.

---

### Post by edvigil on 2020-03-25
Thanks SeijiSensei. I'm still trying out different things. Nothing seems to work. It seems anything php related just gives me a "Save As" dialog box. Even phpMy Admin.

---

### Post by SeijiSensei on 2020-03-26
Did you try reinstalling lamp-server^?  The "^" character at the end is important.

---

### Post by edvigil on 2020-03-26
Thanks SeijiSensei
I just tried reinstalling lamp-server^. I think we are definitely on the right track. The script installs Wordpress, but when I click the link to finish install I get the "Save As" dialog box. 
[COLOR=#242729][FONT=Arial]

I found some info on the internent about [/FONT][/COLOR][COLOR=#000000][FONT=&quot]libapache2-mod-php[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]"[/FONT][/COLOR][COLOR=#242729][FONT=Arial]without that , [/FONT][/COLOR][COLOR=#242729][FONT=Arial]Apache doesn't know what is [/FONT][/COLOR].php[COLOR=#242729][FONT=Arial] file, and recognizes it like raw file which can be downloaded" Maybe that's still the problem.

Thanks again for your time!
Eddie[/FONT][/COLOR]

---

### Post by SeijiSensei on 2020-03-27
You did restart the Apache server, right?

```
sudo systemctl restart apache2
```

---

### Post by edvigil on 2020-03-28
Hello SeijiSensei
Sorry for the delay in responding. Yes, I did restart Apache2. Same issue when I use Virtualmin script to install Wordpress or phpMyAdmin. I get a "Save As" dialog box. I even tried to install Wordpress into /var/www/html directory. 
That method has worked for me in the past, but not this time. 


Just to be clear, I was using Ubuntu Server 16.02. It told me that Ubuntu Server 18.04 was available and to do a do-release-upgrade. Thats when I began having issues with Virtualmin scripts like Wordpress and phpmyadmin. 
Also, under Webmin System information, it says that I am using  Ubuntu Linux 16.04.3 even though I am usuing 18.04. 
One more thing, the upgrade left the old php version 17.0.33 and the new version 17.2.24.

I just checked the Apache error logs I am getting mulptle errors like this:
Sat Mar 28 17:46:13.631779 2020] [php7:error] [pid 32270] [client 5.188.210.101:26340] script '/home/mysite.com/public_html/echo.php' not found or unable to stat, referer: [https://www.google.com/](https://www.google.com/)
I have tried to install wordpress and phpmyadmin muliple so I don't believe its an attack.

Thank you again for all of your help!
Eddie

---

### Post by LHammonds on 2020-03-29
The "do-release-upgrade" is only designed to upgrade the OS...has nothing to do with any custom apps/scripts.  When I upgrade my server, I do so by building a new server from scratch (typically in a virtual environment) with the current OS and app versions.  Once I get the base system working, I then copy the data over and get the new server running with the old data in such a way that it works perfectly.  I then document the entire process and do it again to ensure my documentation was not missing anything.  Once I am confident that I can get a new server setup and restore the data and get it working, I then do it for real.  If on a physical box, that means a final backup of the data, then erase the disks and install the new OS and restore the data according to my tested and verified documentation.

If the server is virtual, I simply create a new virtual and get it working, then swap the IP addresses and I'm done.

I do not use virtualmin and thus not familiar with its quirks but I did find the Ubuntu-18-specific information regarding virtualmin: [https://www.virtualmin.com/node/57208](https://www.virtualmin.com/node/57208)

I [install Wordpress manually]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=249") since I have a separate dedicated database server/cluster and as such, the typical hold-your-hand installers like those in the repository or custom installer scripts tend to only handle situations with all services on the same machine...which is not ideal for production environments.

LHammonds

---

### Post by SeijiSensei on 2020-03-30
PHP is at major version 7, not 17.  If I were you, I'd install server 18.04 from scratch, or perhaps 20.04 which is close to release in a few days.

[http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)

That's much easier than trying to diagnose why some combination of packages don't work correctly together.

---

### Post by edvigil on 2020-04-01
Thank you LHammonds! You and SeijiSensei have been incredibly helpful! I have learned a lot thanks to both of you. I am going to take your advice and install from scratch. 
I am going to mark this thread as solved.
Good luck to both of you and have a great day!
edvigil

---

