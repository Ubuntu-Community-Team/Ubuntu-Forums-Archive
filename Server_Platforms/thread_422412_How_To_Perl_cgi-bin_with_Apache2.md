---
title: "How To: Perl cgi-bin with Apache2"
date: 2007-04-25
forum: Server Platforms
---

### Post by kdnewton on 2007-04-25
Hi all. This isn't necessarily the "right" way to do this. I hope if what I'm writing leaves a gaping security flaw that someone more knowledgeable will point it out and correct me. The current ubuntuguide wiki does not explain how to set up the "P" in "LAMP" so I'm hoping this will point people in the right direction. Perl is already included in the base Ubuntu install.

So you've already

sudo aptitude install apache2

And next you'll want to

sudo aptitude install libapache2-mod-perl2

(or do both in one step, whatever). Your base webserver files are stored in /var/www/ and you'll probably want to run your cgi scripts from /var/www/cgi-bin/ for consistency. The install of apache2 reads its cgi from /usr/lib/cgi-bin/ which you might notice doesn't even exist! [Edit: If it does exist, as it did on my second server it is safe to "sudo rm -r /usr/lib/cgi-bin" and then follow the later step to create a sym-link to /usr/lib/cgi-bin)

What the official apache site would say is to edit /etc/apache2/httpd.conf and add some ScriptAlias, then you have to restart apache (sudo /etc/init.d/apache2 restart) and be disappointed when it doesn't work. Here's what I did:

you'll want that cgi-bin directory in /var/www/

sudo mkdir /var/www/cgi-bin

and make a soft-link to /usr/lib. I put myself into the /usr/lib directory to be sure (I sometimes forget how ln -s works).

cd /usr/lib/
sudo ln -s /var/www/cgi-bin/ cgi-bin

Now write up a quick perl script, I use nano for an editor. For this we'll call it test.pl

cd /var/www/cgi-bin
sudo nano test.pl

###We're inside the text editor now###

#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing some things.<br />\n";

for ($i=0; $i<10; $i++)
{
    print $i."<br />";
}

###Done editing text. Save and exit program###

make sure you change permissions on it

sudo chmod a+x test.pl

Now load up "localhost/cgi-bin/test.pl" in a browser. It should be working. We've written a sym-link to the directory that apache2 looks for cgi scripts (/usr/lib/cgi-bin/) and are storing them in our /var/www/cgi-bin. So I hope that works for you otherwise I've wasted a lot of my time writing this out.

---

### Post by TomFumb on 2007-05-14
Hi, thanks for your how-to, I've done everything you said, but my perl scripts don't execute, they're just offered as a download, any idea how to fix this?

they're all chmoded 0755, and I've added 'ExecCGI' to the /etc/apache2/apache2.conf file or whatever it's called

Any help much appreciated

tom

---

### Post by thepeel on 2007-05-16
I think the correct location to modify where apache looks for the cgi-bin directory in the default install is here:

/etc/apache2/sites-available/default

Simply change this:

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">

To this:
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin">

---

### Post by tr333 on 2007-05-17
anytime you write CGI scripts with perl, you should include the "-T" option as well as "-w" and strict mode.
this forces perl into "Taint mode" which is more secure than the standard perl.  read more on this with "perldoc perlsec" or "tkpod perlsec" if you have Tk::Pod installed.

---

### Post by westdale on 2007-05-18
Tom Fumb..
I spent an hour wondering why my shiny new LAMP server was offering me downloads of a Perl script as well.
My apologies for suggesting you may be anywhere near as daft as me but  I put test/html instead of text/html in the first Perl print statement. If you do that - or something similar, the browser then offers you the file.

---

### Post by nehalem on 2007-06-20
Thanks for this.  It helped immensely.

---

### Post by btechcs on 2007-07-03
I have the same problem, ur tutorial I followed twice, After reinstalling ubuntu and a working LAMP server. There must be some problem. I know that [http://localhost/cgi-bin/first.pl](http://localhost/cgi-bin/first.pl) points to /usr/lib/cgi-bin/first.pl. But even when I put [http://localhost/cgi-bin/first.pl](http://localhost/cgi-bin/first.pl) it offers to download the perl file. Serious problem, please help.

---

