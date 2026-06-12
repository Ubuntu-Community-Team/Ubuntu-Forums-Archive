---
title: "Apache and mod-security"
date: 2011-09-11
forum: Server Platforms
---

### Post by Volens on 2011-09-11
Having some issues getting the security module for apache running after following this guide:

[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

Only changes I made were DL'ing the most recent set of rules and leaving out "/etc/apache2/conf.d/modsecurity2.conf" because ubuntu automatically includes it.

When restarting apache I get this:

```

me@mycompy:/etc/apache2/conf.d/modsecurity$ sudo service apache2 restart
apache2: Syntax error on line 227 of /etc/apache2/apache2.conf: Syntax error on line 301 of /etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data: /etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data:338: <input> was not closed.\n/etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data:301: <![cdata[> was not closed.
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```The apache error log had nothing beyond past errors I have already resolved when I was setting up multiple virtual hosts a week or so back, so it was pretty useless.

modsecurity_40_generic_attacks.data is just a list commands and tags as far as I can tell.

Line 388 had "<input" and line 301 had "<![cdata[" so I tried closing them with ">", but even with them, apache spit out the same error verbatim.

I'll assume that I have something set up so that apache isn't reading this file as it should and thinks its something else. I'm not too experienced with apache and web servers in general as this is supposed to be a learning project for me so I've kinda hit a wall here.

Any suggestions (even just towards another config/hardeing guide) are welcome.

---

### Post by zackwasa on 2011-09-11
Try closing the *<input>* with a *</input>*

Let me know if it did not work

---

### Post by Volens on 2011-09-11
I don't think thats the issue. After poking around on google some more, it seems that I'm missing some line in a config to tell apache how to read the file. Apparently something to do with wildcarding.

The reason I don't think your solution will work is because I think the file is supposed to be a bank of improper code that the hosted web pages are checked against to prevent security holes from poor coding.

I read an archived question that had the solution of "explicitly including the file" which I assume is something along the lines of the second post in the thread here:

[http://www.apachelounge.com/viewtopic.php?t=3120](http://www.apachelounge.com/viewtopic.php?t=3120)

However, I tried putting this in httpd.conf as follows to direct it to "modsecurity_crs_10_config.conf" and apache still gave me the same error.

```

<IfModule mod_security2.c>
Include conf.d/modsecurity/*.conf
</IfModule>

```

---

### Post by Dangertux on 2011-09-11
You have to also include the .data files by using the lua extension, not just the .conf

[code]
LoadFile /usr/lib/libxml5.so
LoadFile /usr/lib/liblua.1.so
<IfModule mod_security2.c> 
Include conf.d/modsecurity/*.conf
Include conf.d/modsecurity/base_rules/*.conf
</IfModule>

Hope that helps

---

### Post by dragonetti on 2011-09-24
I had the same problems with "..._40_generic..."
I was blindly following the sulotion of adding / changing to the inclusion of "*.conf"
 
But the lightbulb on my head switched on the moment I understood WHY "*.conf" is so important.
 
First i changed my setup to:
 
 
modsecurity2.conf
```

<ifmodule mod_security2.c>
Include conf.d/modsecurity/*.conf
</ifmodule> 

```
 
apache2.conf
```

# Include configurations:
Include /etc/apache2/conf.d/*.conf

```
 
 
httpd.conf (If you have something in your httpd.conf) it should be
```

Include conf.d/modsecurity2.conf

```
 
Why?
 
The important thing to remember is that the ".data" files ar meant for input for the ".conf" files. They (.data) files will be accessed when needed because of the code within the .conf files include the .data files.
.conf files are structured in a specific way so that they only contain the security procedures. .data don't
 
For example look at the .conf: modsecurity_crs_40_generic_attacks.conf 
(open it in notepad++)
And you'll see that the corresponding .data is included in there: odsecurity_40_generic_attacks.data
 
So do NOT include the .data file anywhere, just copy alle the files (.data & .conf) and then **only** include the .conf in the corresponding config files. Hence the: *.conf inclusion you see in many awnsers.
 
Could someone verify my awnser.... i'm using modsecurity for a few months now... so I could be wrong.
 
Once you get past the error stated in the topic starters post, you'll encounter some other error(s)
Like the "[FONT=Courier New][SIZE=2]REQBODY_ERROR[/SIZE][/FONT]" in
 
[FONT=Courier New]modsecurity_crs_20_protocol_violations.conf[/FONT]
[FONT=Courier New]My solution was to replace "[/FONT][FONT=Courier New]REQBODY_ERROR" by: [/FONT]
[COLOR=#222222][FONT=Calibri][SIZE=3]REQBODY_PROCESSOR_ERROR[/SIZE][/FONT][/COLOR]

---

### Post by Dangertux on 2011-09-24
You don't have to do all that. 

I created an easy install procedure that doesn't require editing any of the .data files , etc they should work as they are.

You may view it here : [http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

---

### Post by dragonetti on 2011-09-25
@Dangertux
 
Well, the essence of my post is to _only_ include *.conf files and nothing else has to be done.
 
What is in my configuration files is just an example. (It could certainly be done differently / better)
 
And does your method address the [REQBODY_ERROR]("http://www.google.nl/#hl=nl&sugexp=pfwc&cp=13&gs_id=2&xhr=t&q=REQBODY_ERROR&pf=p&sclient=psy-ab&site=&source=hp&pbx=1&oq=REQBODY_ERROR&aq=0L&aqi=g-L1&aql=f&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=33b5ffc197b9bfd2&biw=1106&bih=709") (I _think_ it's in 2 versions now the current and previous one).
That's why I added the way how I handled that error, but there will be a better ways to handle it... (I just don't know it).
 
And not to sound rudebut at first sight your method doesn't seem shorter than:
- install modsecurity from the repository
- download latest ruleset ([using the rules-updater script]("https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project") => click "download" tab) and extract/move all the rules to the right directory (but your described method for this step is faster!)
- adjust the config file(s)
- **if **you have problems with some rules (*.conf) you need(?) to edit them
 
I see you build the modsecurity install? Is that why you can avoid *.conf errors?
I install it from the repository... I do not know which method is better?

---

