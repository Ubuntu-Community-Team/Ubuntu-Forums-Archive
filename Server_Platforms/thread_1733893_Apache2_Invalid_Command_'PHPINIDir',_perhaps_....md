---
title: "Apache2: Invalid Command 'PHPINIDir', perhaps ..."
date: 2011-04-19
forum: Server Platforms
---

### Post by honeytech on 2011-04-19
Hello Everyone

I've recently been trying to secure my Apache2 server running suPHP on an Ubuntu 10.10 box.  My ideal solutions are to

1) Specify a specific php.ini on a per virtualhost basis.  I have tried using the PHPINIDir directive inside a virtualhost block in my 'sites-available/default' file, but the parser throws an error 

**Invalid command 'PHPINIDir', perhaps misspelled or defined by a module not included in the server configurations**

I have figured out that the reason this directive is not recognized is because my server is running mod suPHP instead of mod php5.  The default site on the server requires suPHP to perform certain administrative functions.  First question would be, is there some other way to specify a specific php.ini besides using PHPINIDir, or does anyone have any ideas of how to get PHPINIDir to be understood under the current configuration?

-My other option-

2) Activate/Deactivate php5 on a per virtualhost basis.  This will allow me to use PHPINIDir to specify a specific and secure php.ini.  I know that I have php5 installed, as 'a2enmod php5' with a restart will activate php5 and override suPHP.  Does anybody know what the commands would look like to load the php5 modules from inside a virtualhost block?  

I have looked around on the internet and found these two lines of code to add that will supposedly activate php5 under a virtualhost
[I]LoadModule php5-module modules/libphp5.so
AddHandler php5-script php[/I]
I do not have a 'modules' directory in my /etc/apache2 folder, so I did a search for libphp5.so and found the only copy on my machine located in /usr/lib/apache2/modules.  Naturally, I tried
[I]LoadModule php5-module /usr/lib/apache2/modules/libphp5.so
AddHandler php5-script php[/I]
but received an error 
**apache2: Syntax error ...: Can't locate API module structure 'php5-module' in file /usr/lib/apache2/modules/libphp5.so**

Surely I can't be the only one who's needed to specify different php.ini files for different virtualhost's while using suPHP, and I'd also have to assume I'm not the first one who's tried to integrate suPHP and php5 on a per virtualhost basis.  Anyone have any ideas? I'm completely stuck, and that's the worst kind of stuck.:confused:

The Apache2, suPHP, and php5 installations on my machine are standard for Ubuntu 10.10

---

### Post by honeytech on 2011-04-19
Solved!!!

LoadModule php5-module /usr/lib/apache2/modules/libphp5.so
AddHandler php5-script php

Should actually be 

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddHandler php5-script php

Now PHPINIDir works.

And I thought I'd tried everything...

---

