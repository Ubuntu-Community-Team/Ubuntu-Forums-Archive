---
title: "SQL-Ledger Installation - Apache is not configured correctly?"
date: 2016-03-28
forum: Server Platforms
---

### Post by tom_w2 on 2016-03-28
Greetings!

I am fairly new to Ubuntu, so please forgive me if I make some basic mistakes.  I am somewhat familiar with Unix though, so hopefully this is an easy question.

I am installing SQL Ledger on Ubuntu 14.04.4.  I was following these directions:

[http://www.sql-ledger-network.com/dokuwiki/doku.php?id=step_by_step_installation:ubuntu](http://www.sql-ledger-network.com/dokuwiki/doku.php?id=step_by_step_installation:ubuntu)

So far, so good.  I think I configured everything correctly, but when I go the [http://localhost/sql-ledger](http://localhost/sql-ledger) I get the actual text of the login.pl file.   Now I think that sounds like Perl is not installed?  But when I run the setup.pl file SQL Ledger seems like it actually installs (I think).  

Is there a resource out there for a fairly new Ubuntu person to complete this installation?  If not, could someone help me understand what I need to do to finish configuring the package?

I appreciate any and all help!

Thanks,

Tom

---

### Post by HermanAB on 2016-03-28
Uhmm, pay for it and send an email to Dieter Simader.  He has to eat too, so pay him.  He'll help.

---

### Post by SeijiSensei on 2016-03-28
While I'll all in favor of supporting people who make valuable software, I will also suggest that you try running
```
sudo apt-get install libapache2-mod-perl2
```

If it's already installed, try running "sudo a2enmod perl" followed by "sudo service apache2 restart".

---

### Post by tom_w2 on 2016-03-28
> **SeijiSensei said:**
> While I'll all in favor of supporting people who make valuable software, I will also suggest that you try running
```
sudo apt-get install libapache2-mod-perl2
```

If it's already installed, try running "sudo a2enmod perl" followed by "sudo service apache2 restart".


I did try and contact him - he indicated he was not super familar with the ubuntu set up.  I would be happy to pay him if it comes to that (I am sure it is just a conf file issue).

That being said, I am trying to evaluate the software.  The first step is of course to get it installed.  I tried the above and it did install something.  That did not correct the issue though.  

I am not 100% sure if I have this correct - do I actually modify the apache2.conf file, or do I do some sort of symbolic link to the sites-available directory?  I ran the package from the repositories, and it installed in usr/share/sql-ledger.  I assume this correct as well?

Well, I am making progress.  I have the app enable directories working now.  

However, when the perl script comes up (and login.pl does come up) it shows up as text.  I think I still have some configurations to do to make this work?

I configured perl using - s[COLOR=#0A0200][FONT=Arial]udo aptitude install libapache2-mod-perl2.

That did not fix it though.[/FONT][/COLOR]

Success!  I had to restart Apache after the changes, not just reload.  I finally got the login screen.  

For those that are curious, I did the following:

1.  I took the sql-ledger-httpd.conf file and copied it to /etc/apache2/sites-available as sql-ledger.conf
2.  Then I ran sudo a2ensite sql-ledger.conf.
3.  Finally, I restarted Apache.  sudo Service apache2 restart

That worked.

Thanks for the input.

oops, one issue.  The admin perl script is now showing up in text, but the login script is not.  :confused:

Wow, very strange.  It loads when I reload the page.

I have a good deal of reading to do to brush up on Unix again.

---

### Post by howefield on 2016-03-29
Thread moved to the "*Server Platforms*" forum.

---

### Post by cariboo on 2016-03-31
If you just want to try the package, why not just install it from the repositories.

---

