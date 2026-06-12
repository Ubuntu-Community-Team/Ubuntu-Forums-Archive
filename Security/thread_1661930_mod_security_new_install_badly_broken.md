---
title: "mod_security new install badly broken"
date: 2011-01-07
forum: Security
---

### Post by HypNemes on 2011-01-07
Hello all

I just decided to install mod_security..
I followed the blog tutorial here [http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/]("http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/")
Allot of posters on the forum give it a good review.

I did everything as told.
Installed the package via apt-get
Created a file in /etc/apache2/conf.d called modsecurity2.conf
Placed the relevant code in it so that conf.d/modsecurity/*.conf would be used and included.

Created the relevant symbolic link
ln -s /var/log/apache2/mod_security/ /etc/apache2/logs

I then got the latest rules
modsecurity-crs_2.1.1 and extracted them to their own dir in /etc/apache2/conf.d/modsecurity/modsecurity-crs_2.1.1

From here I was stuck - as I wasnt sure if that was all and I should just restart apache2 while making sure modsecurity was running OR if I had to take the file
modsecurity_crs_10_config.conf.example
and make it - the .example as a config file.
I assumed I had to otherwise why would it be there as an example?
So I had a quick look through it kept everything default and saved it without the .example on the end.

Now when I try to restart apache2 I get a mountain of syntax errors in config files.
Files I havent altered at all.

When I do an
/etc/init.d/apache2 restart

I receive the following..

apache2: Syntax error on line 231 of /etc/apache2/apache2.conf: Syntax error on line 133 of /etc/apache2/conf.d/modsecurity/modsecurity-crs_2.1.1/base_rules/modsecurity_40_generic_attacks.data: /etc/apache2/conf.d/modsecurity/modsecurity-crs_2.1.1/base_rules/modsecurity_40_generic_attacks.data:170: <input> was not closed.\n/etc/apache2/conf.d/modsecurity/modsecurity-crs_2.1.1/base_rules/modsecurity_40_generic_attacks.data:133: <![cdata[> was not closed.
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

So what have I done wrong?

There cant be that many errors in the config files can there?

The very first syntax error says
apache2: Syntax error on line 231 of /etc/apache2/apache2.conf: 

after checking /etc/apache2/apache2.conf line 231 I see that its the line following
#Include generic snippets of statements:
Include  conf.d/

That seems perfectly fine to me.

Anyone got any ideas im stuck?

Hyp

---

### Post by HypNemes on 2011-01-07
completely removed it until such time as there is a PROPER DOCUMENTED install text for ubuntu 10:10.

Following  [http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/]("http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/") to the letter as an install guide didnt not work at all.

Hyp

---

### Post by bodhi.zazen on 2011-01-07
Aye, this is a problem with mod_security, it changes fairly rapidly and documentation lags.

To run mod_security takes a real commitment as well, to installation and configuration.

I would post those errors on the mod_security mailing list.

When I have a problem with a rule I either comment it out or modify the syntax.

---

### Post by sot3 on 2011-02-28
I've just been through the same thing.  I have to agree that the "documentation" for mod_security is sorely lacking no matter what release you're using, IMHO.

Anyway, on Maverick 10.10 you need to modify the /etc/apache2/apache2.conf file.  The line that it's complaining about looks like this:

```
# Include generic snippets of statements
Include /etc/apache2/conf.d/

```

The result of this is that everything in that directory and below it is "included", but the only files you really want to include are the *.conf files.  Note that your errors cascade from this line into complaints about *.data files that never should have been included in the first place.

The solution is to modify it as follows and restart apache:

```
# Include generic snippets of statements
Include /etc/apache2/conf.d/*conf

```

---

### Post by sot3 on 2011-02-28
Well, now that I've said that, I think it's not entirely correct.  That will match only the *conf files in that one directory, but not in any of the subdirectories.  I've verified that by intentionally inserting an error in one of the modsecurity files and restarting apache: the error was not detected.

I think you'll want to use something more like this:

```
# Include generic snippets of statements
Include /etc/apache2/conf.d/*conf
Include /etc/apache2/conf.d/modsecurity/*conf
Include /etc/apache2/conf.d/modsecurity/base_rules/*conf
#Include /etc/apache2/conf.d/modsecurity/optional_rules/*conf

```

...which works fine for me until I include the optional rules as above.  When I do that, I get the following error:

```
$ /etc/init.d/apache2 restart
Syntax error on line 29 of /etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_crs_49_header_tagging.conf:
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

I'm only just learning how to manage a web server, but frankly it seems to me that the security of the system is important enough that it should be loaded along with apache, and it should be easy to configure it to update the rules on a regular basis.  There is a rules-updater.pl that seems intended for that purpose, but it's also poorly documented.  I'm getting close...

---

### Post by FuturePilot on 2011-02-28
> **sot3 said:**
> Well, now that I've said that, I think it's not entirely correct.  That will match only the *conf files in that one directory, but not in any of the subdirectories.  I've verified that by intentionally inserting an error in one of the modsecurity files and restarting apache: the error was not detected.

I think you'll want to use something more like this:

```
# Include generic snippets of statements
Include /etc/apache2/conf.d/*conf
Include /etc/apache2/conf.d/modsecurity/*conf
Include /etc/apache2/conf.d/modsecurity/base_rules/*conf
#Include /etc/apache2/conf.d/modsecurity/optional_rules/*conf

```
Any easy way to do that is to put
```
<ifmodule mod_security2.c>
Include conf.d/modsecurity/*.conf
Include conf.d/modsecurity/base_rules/*.conf
Include conf.d/modsecurity/optional_rules/*.conf
</ifmodule>
```
in a .conf file in /etc/apache2/conf.d/
> **sot3 said:**
> 
...which works fine for me until I include the optional rules as above.  When I do that, I get the following error:

```
$ /etc/init.d/apache2 restart
Syntax error on line 29 of /etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_crs_49_header_tagging.conf:
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

I'm only just learning how to manage a web server, but frankly it seems to me that the security of the system is important enough that it should be loaded along with apache, and it should be easy to configure it to update the rules on a regular basis.  There is a rules-updater.pl that seems intended for that purpose, but it's also poorly documented.  I'm getting close...

```
sudo a2enmod headers
```
Restart Apache then.

---

### Post by sot3 on 2011-02-28
Thanks!  But can you tell me how you figured out which mod to enable?

I'm getting a similar error for one of the experimental rules.

---

### Post by FuturePilot on 2011-02-28
> **sot3 said:**
> Thanks!  But can you tell me how you figured out which mod to enable?

I'm getting a similar error for one of the experimental rules.

From the error.
```
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration

```
Indicates it's most likely a module that's not loaded. I went and started looking through the modules for something related to headers.

---

