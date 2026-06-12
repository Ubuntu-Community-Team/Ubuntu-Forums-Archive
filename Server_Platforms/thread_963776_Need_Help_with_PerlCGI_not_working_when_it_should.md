---
title: "Need Help with Perl/CGI not working when it should"
date: 2008-10-30
forum: Server Platforms
---

### Post by TCarr on 2008-10-30
I have a VERY unusual problem. I hope someone can help because I haven't a clue what is going on. 

I have Ubuntu 8.04 LTS server installed on VMWare and I can't get perl/CGI to work. This test program:

#!/usr/bin/perl
use CGI;
print "Content-type: text/html\n\n";
print "Hello World.<br />";

Will just list the source code. I double checked the Apache config and I have entered in the right stuff:

<VirtualHost *>
DirectoryIndex index.html index.htm index.php index.cgi index.pl index.shtml
</VirtualHost>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory /var/www/users/*/>
AddHandler cgi-script .cgi
Options +ExecCGI +Includes
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
</Directory>

The VMWare is on my home server and does not have a static IP. PHP works fine.

Now, I have the SAME EXACT settings and file on TWO other servers WITH static IP (which are NOT running from within VMWare or a virtual machine) and those work fine with Perl/CGI!

Someone want to tell me what is going on here? What should I look into to get this working on the VMWare server?

Note also that I've installed libapache2-mod-perl2 on all servers and it is showing up in the list of loaded apache modules ok.

---

### Post by Vegan on 2008-10-30
Are you behind a home router/gateway? If so you might want to use a fixed address using the appropriate IP address such as 192.168.1.250 or something outside the DHCH address range.

As for you Perl script, I am not too familiar with VMware but if its anything like Virtual PC then you have another layer of DHCP to contend with.

Considering this could affect some functionality.

Still the .pl code should be ok, I presume Perl is installed fine.

---

### Post by alienprdkt on 2008-10-30
here you go this is from here (and it worked for me):

[http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html)

**Configure a cgi-bin directory**
 You need to create a cgi-bin directory using the following command
 sudo mkdir /home/www/cgi-bin
 Configuring Apache to allow CGI program execution is pretty easy. Create a directory to be used for CGI programs and add the following to the site configuration file (again between the <VirtualHost> tags).


(within your /etc/apache2/httpd.conf)
[INDENT]ScriptAlias /cgi-bin/ /home/www/cgi-bin/
 <Directory /home/www/cgi-bin/>
Options ExecCGI
AddHandler cgi-script cgi pl
</Directory>
[/INDENT]The first line creates an alias that points to the directory in which CGI scripts are stored. The final line tells Apache that only files that end with the *.cgi and *.pl extensions should be considered CGI programs and executed.
 **Test your Perl Program**
 cd /home/www/cgi-bin
 sudo nano perltest.pl
 Copy and paste the following section save and exit the file.[INDENT]###Start###
 #!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
[print]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html#") "Hello there!<br />\nJust testing .<br />\n";
 for ($i=0; $i<10; $i++)
{
print $i."<br />";
}
 ###End###
[/INDENT]make sure you change permissions on it
 sudo chmod a+x perltest.pl
 Now open your web browser open [http://yourserverip/cgi-bin/perltest.pl.It](http://yourserverip/cgi-bin/perltest.pl.It) should be working.

---

### Post by TCarr on 2008-10-31
> **alienprdkt said:**
> here you go this is from here (and it worked for me):

Thanks, but my setup DOES work on two static-IP based servers, so the apache2 setup doesn't seem to be the problem. It seems related to that one difference - I don't have a static IP.

> **Vegan said:**
> Are you behind a home router/gateway? If so you might want to use a fixed address using the appropriate IP address such as 192.168.1.250 or something outside the DHCH address range.

Yes, I'm behind a wifi router in my home network. I can FTP to the host machine, and also connect to the outside internet just fine in the Guest OS (Ubuntu Server). I can also access the web pages on the guest OS via a browser on the HOST OS using the guest OS's IP. The /etc/network/interfaces file is automatically set up for dhcp because I do not have a DNS. 

The FQDN seems to be [hostname].localdomain. I use apache's sites-available and not httpd.conf (which is blank by default in the setup anyway).

I did get somewhere today so now instead of listing the source code I'm getting a 500 Internal Server Error. So now hopefully looking at logs, I see "premature end of script headers" even though I have the content type in there. I'm still trying to figure this out. I added to the sites-available/default the CGI stuff anyway and then changed the host from 128.x.x.x, etc. to the server's actual IP address it's using.

I did get a perltest.cgi script to work on there though. So as for the test.cgi, it's gotta be something in the code (oddly, it does work fine on the other two servers).

But at least it's working. Thanks guys!

In summary, I needed to add the CGI stuff to the /etc/apache2/sites-available/default and change the IP in that file to that of the Guest OS. (using ifconfig can give you the IP Address, for those who are reading and don't know how to find it).

---

### Post by alienprdkt on 2008-10-31
right... you added this i assume to your sites-available page:

ScriptAlias /cgi-bin/ /var/www/cgi-bin/
    <Directory "/var/www/cgi-bin">
        AllowOverride None
        Options ExecCGI 
        AddHandler cgi-script cgi pl
                Order allow,deny
        allow from all
    </Directory>

and this is stright from my test page ... to check the coding from my cgi-bin folder:

#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing .<br />\n";

for ($i=0; $i<10; $i++)
{
print $i."<br />";
}



glad to help:D good luck

oh' I don't have static either, I use dyndns.org to resolve my dns

---

### Post by TCarr on 2008-11-02
I have my router set to use DynDNS so that any computer on my home network will use it.

As for sites-available, we put that in the apache2.conf instead on the static IP servers and then each domain gets it's own file in the sites-available directory. But it doesn't seem to want to work that way in the non-static virtual server so I have to just do it differently then. Not a problem as on the virtual server, I put a symlink to any mock-domains in the /var/www directory.

---

### Post by n00rt on 2008-11-05
ah ha - after about 5 hours stumbling around to get apache working it finially is - thanks to alienprdkt - the only reason mine didn't work was that i hasd missed the AddHandler line out of the httpd.conf file...
..now i can get on with some work

---

