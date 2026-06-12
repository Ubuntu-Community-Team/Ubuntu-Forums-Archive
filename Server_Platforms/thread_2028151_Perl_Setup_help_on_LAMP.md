---
title: "Perl Setup help on LAMP"
date: 2012-07-17
forum: Server Platforms
---

### Post by simple1689 on 2012-07-17
I've recently up a LAMP server. Apache is set up and working (it's pointed to its default directory), I've ran PHP test and PHP is installed correctly, but I can't seem to get Perl to display my scripts in my browser. I should note that running perl -v shows that I have perl installed on my local machine. I keep the perl scripts stored in /var/www/cgi-bin

Now I am a little confused on which conf file I need to edit for perl to pointed to my cgi-bin. 

In my /etc/apache2/sites-available/default I have this between the <VritualHost>

> 
        ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews Indexes      +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                AddHandler cgi-scripts cgi pl
        </Directory>

In my /etc/apache2/sites-enabled/000-default I have this between the <VritualHost>

>  ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews Indexes +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                AddHandler cgi-scripts cgi pl
        </Directory>


Now when I type in myurl/cgi-bin/script.pl it downloads my file. Am I to assume everything is working? I should mention this perl script is very basic:

> print "Welcome!\nEnter two numbers to add...\n";
print "First Number\t";
$num1=<>;
chomp($num1);
print "Second Number\t";
$num2=<>;
chomp($num2);
$sum=$num1+$num2;
print "Sum of the two given numbers is = $sum\n";


---

