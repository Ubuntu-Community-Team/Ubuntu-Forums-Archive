---
title: "Custom Apache Logging + Conky"
date: 2011-05-22
forum: Server Platforms
---

### Post by Hack.The.Pow. on 2011-05-22
Hello All.  I have been running a web server to practice my web design skills and to host some files to my friends.

It is quite simple.  I have the main site available to everybody then I have a directory that holds all my media that is password protected by the apache config file.  

What I would like to do is create a custom log file that shows me all the files that my friends have downloaded from this Media directory.  I understand that the access.log file shows this but it is all convoluted with other stuff so I would like a separate one.

Using this Then I would like to add an entry into my conky setup to monitor how many downloads there have been in total, daily, and monthly.

Can somebody help me out with this?  Much appreciated

---

### Post by Lars Noodén on 2011-05-22
Custom [Apache log formats](http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats) are easy to set up.  See the section on [the Apache access log](http://httpd.apache.org/docs/current/logs.html#accesslog)

One mod that I tended to make when I ran Apache was to make the fields of the log file tab-delimited.

---

### Post by Hack.The.Pow. on 2011-05-22
Ok so I just added this to my apache2.conf file because I believe this is what I want

```
CustomLog /var/log/apache2/files_downloaded_log "%a %h %{User-agent}i %t %f %r %B"
```

The files_downloaded_log file is showing but nothing is being written to it.  Do i need to enable logging somewhere as well to get it to work?

Also is there an explicit way to only log requests where a user accesses a file(not a directory transversal)?  If so was that the right way to do it?

Thanks

---

### Post by Hack.The.Pow. on 2011-05-23
Bump!

Anybody?  This is really irritating me.  I checked the permissions and they seem right...  The write lines are being written to the access log but just not my custom one.

---

### Post by Lars Noodén on 2011-05-23
Don't you need to set the log file format using "LogFormat" ?

---

### Post by Hack.The.Pow. on 2011-05-23
> **Lars Noodén said:**
> Don't you need to set the log file format using "LogFormat" ?

You can but what I did before was just a shortcut.  I actually just tried changing it back to the long way: 

```
LogFormat "%a %h %{User-agent}i %t %f %r %B" downloads
CustomLog /var/log/apache2/files_downloaded.log downloads
```

But that didn't work either

---

### Post by Hack.The.Pow. on 2011-05-24
Anybody?

---

### Post by Lars Noodén on 2011-05-25
I set up Apache2 on a spare system and could not duplicate your error. 

What does the line for the default access log look like for your system and is that working?

---

### Post by Hack.The.Pow. on 2011-05-25
I'm not exactly sure where the format for the access log should be.  I suspect it should be in the apache2.conf file but I can't find a exact point to the access log file.  That log file is working perfectly however.

I have attached my conf file.

Thanks for helping

---

### Post by Lars Noodén on 2011-05-25
> **Hack.The.Pow. said:**
> I'm not exactly sure where the format for the access log should be. 

Shouldn't the configuration file for your vhost for Apache**2** be somewhere under /etc/apache2/sites-enabled ?  Putting everything in a single configuration file was the Apache 1.3 way of doing things.

What is the result of Apache's configtest?

I've looked at your configuration file and at first glance it looks ok if the directory **/var/log/apache2/** really does exist.

---

### Post by Hack.The.Pow. on 2011-05-25
> **Lars Noodén said:**
> Shouldn't the configuration file for your vhost for Apache**2** be somewhere under /etc/apache2/sites-enabled ?  Putting everything in a single configuration file was the Apache 1.3 way of doing things.

What is the result of Apache's configtest?

I've looked at your configuration file and at first glance it looks ok if the directory **/var/log/apache2/** really does exist.

Ahh Finally!! I got the custom log to work.  I just put the Custom Log declaration in the /etc/apache2/sites-enabled/000-default file.  Apparently you have to declare what you want in the apache2.conf file and then say where you want the file in the 000-default file?  Whatever it works now.

I just have to work on filtering these entries now into what I exactly want.  

Do you know how to restrict logging to a particular directory.  And only log the GET's of end files?(not directories, or other things)

Oh also I'm getting a ton of entries looking for a favicon.ico?  No idea why.  Any clue?

---

### Post by Lars Noodén on 2011-05-26
> **Hack.The.Pow. said:**
> ... then say where you want the file in the 000-default file?  ...


All the configurations for your virtual host should be in the **sites-enabled** directory.  It's just that right now you only have one virtual host.

> **Hack.The.Pow. said:**
> ..
Do you know how to restrict logging to a particular directory.  And only log the GET's of end files?(not directories, or other things)

Oh also I'm getting a ton of entries looking for a favicon.ico?  No idea why.  Any clue?

A lot of browsers look for an icon to display in the address bar.  

Make a 16x16 icon in GIMP and then save it to your web site.  Then try something like *one* of the following.
```

<link rel="icon" type="image/ico" href="favicon.ico" />
<link rel="icon" type="image/png" href="favicon.png" />
<link rel="icon" type="image/gif" href="favicon.gif" />
<link rel="shortcut icon" href="favicon.ico" />

```

GIFs can be animated if you want a really annoying icon.

---

### Post by Hack.The.Pow. on 2011-05-26
Ok I'll make up an icon so that stops bothering me.

Anyway do you know anything about regular expressions?

From my experience in Perl this should work to identify any string that has Media in the directory and then a file in it.  However it doesn't seem to be working for apache.  Any help?

```
SetEnvIf Request_URI "/Media.*\..*$/" mediaLog
CustomLog ${APACHE_LOG_DIR}/files_downloaded.log downloads env=mediaLog
```

---

### Post by Lars Noodén on 2011-05-27
At the moment I can only say that Apache should handle [PCRE](http://httpd.apache.org/docs/2.2/new_features_2_2.html).

---

### Post by Hack.The.Pow. on 2011-05-29
So I actually did figure it out.

```
#Custom log for files downloaded from my Media Directory
SetEnvIf Request_URI "Media.*\..{2,4}" mediaLog
CustomLog ${APACHE_LOG_DIR}/files_downloaded.log downloads env=mediaLog
```

I also figured out how to get the total downloads for my conky setup.

```
${color blue}APACHE ${hr 2}$color
Total Downloads:${execi 30 wc -l /var/log/apache2/files_downloaded.log | awk '{print " ",$1}'}

```

Still working on the monthly and daily totals.  If anybody has any suggestions for that it would be great.

I am having trouble getting the 3 last downloads from this log file for conky.  Can anybody help me out?  The log file looks like this.

```
129.33.1.37 Mozilla/5.0 (Windows NT 5.1) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24 [27/May/2011:13:08:58 -0400] /var/www/Media/Music/Eminem/Eminem-Recovery-2010/14. Almost Famous.mp3
129.33.1.37 Mozilla/5.0 (Windows NT 5.1) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24 [27/May/2011:13:08:58 -0400] /var/www/Media/Music/Eminem/Eminem-Recovery-2010/14. Almost Famous.mp3
129.33.1.37 Mozilla/5.0 (Windows NT 5.1) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24 [27/May/2011:13:14:00 -0400] /var/www/Media/Music/Eminem/Eminem-Recovery-2010/7. Not Afraid.mp3
129.33.1.37 Mozilla/5.0 (Windows NT 5.1) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24 [27/May/2011:13:14:00 -0400] /var/www/Media/Music/Eminem/Eminem-Recovery-2010/7. Not Afraid.mp3
```

I have been trying this but it hasn't worked.

```
tail -n3 /var/log/apache2/files_downloaded.log | grep -o '/.*\/var\/www\/Media\/(*.\..{2,4})$/'
```

Edit:  Got it working.  Here is the command that I used.  I decided to include the path to the file from Media to give me more info.

```
${color blue}LAST DOWNLOADS ${hr 2}$color
${execi 30 tail -n3 /var/log/apache2/files_downloaded.log | sed 's/.*Media//'}
```

---

