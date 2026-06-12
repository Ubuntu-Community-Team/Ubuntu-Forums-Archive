---
title: "Need help setting up perl cgi-bin"
date: 2008-03-31
forum: Server Platforms
---

### Post by Westerberg on 2008-03-31
I have a fresh install  of lamp.  I installed libapache2-mod-perl2 via apt-get.  I created

/usr/lib/cgi-bin

 and made a soft link from it to 

/var/www/cgi-bin

I have a test script
```
#!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing some things.<br />\n";

for ($i=0; $i<10; $i++)
{
print $i."<br />";
}

``` 

that I placed in 

/var/www/cgi-bin

and made executable.

If I enter "localhost" into the browser address bar, I see the "cgi-bin" directory, but if I click on it I get a message saying > Forbidden

You don't have permission to access /cgi-bin/ on this server.

In /var/log/apache2/error.log the message says >  [error] [client 127.0.0.1] attempt to invoke directory as script: /usr/lib/cgi-bin/, referer: [http://localhost/](http://localhost/)

If I open /var/www/cgi-bin/test.pl with the browser, it just prints out the contents of the script without processing them.

One thing I noticed -- not sure whether it's important -- there is no perl.conf file in /etc/apache2/mods-enabled.

Any help/advice/suggestions would be appreciated.

---

### Post by twistedtwig on 2008-04-01
think you *might* need to enable the perl module

a2enmod perl (or something like that)

also check that you have a .pl handler.. in the apache config files:

AddHandler .cgi .pl

I think it has others on it but I am not at home and thinking off the top of my head.

GL

Let us know how you got on

---

### Post by Westerberg on 2008-04-01
Thanks for your attention.  I've got the problem about half sorted.
I think the problem was I made a link from /usr/lib/cgi-bin to /var/www/cgi-bin instead of the other way around.  That changed, I am able to run scripts at least.

If I enter

localhost/cgi-bin/test.pl

into the browser address bar, the script will run.

However, if I enter "localhost" into the address bar and then click on the cgi-bin directory, I am still greeted with> 403 Forbidden

You don't have permission to access /cgi-bin/ on this server.

Could the problem be with my 

/etc/apache2/sites-enabled/000-default

file?  Do I have to change something in there? 

Any suggestions/advice/comments/help would be appreciated.

---

### Post by twistedtwig on 2008-04-01
just guessing but it could be something on the lines of no browsing permissions... sorry for the Microsoft wording but I can't think of what its called in Linux

I did the same thing with the links the first time I tried to set it up.

I ended up having a custom.conf file in apache2 folder that has all my personal settings including the link for cgi bin

---

