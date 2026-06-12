---
title: "Need files to be served before fully loaded in browser"
date: 2011-03-09
forum: Server Platforms
---

### Post by asondag on 2011-03-09
Hey all,

I would like files to be served to the browser before they are completely loaded. Some sections of my website aggregate info from around the web, and so they usually take a few moments to load. Because of this, I have setup a nice javascript loading bar. However, my server seems to be waiting for the file to be completely loaded before serving it out. This means that all the user sees is the windows hourglass. How can I change this in Apache2? Thanks.

---

### Post by asondag on 2011-03-09
This seems to maybe be a php problem as well. When I run an intensive php script, it will wait for it to completely finish. I've checked the php.ini script and output_buffering = off.

---

### Post by dtfinch on 2011-03-09
It's hard to say for sure without seeing the page.

Things I'm aware of that often delay a page from displaying in a browser:
* If an img tag doesn't specify width and height, the browser can't calculate layout until the image has started loading, so they'll often delay rendering until then to avoid frequent relayouts.
* Long tables with uncertain dimensions probably also delay rendering until the rest of the table has been served.
* External script tags at the top of the page. Anything below a script tag won't be displayed until the script has been loaded and run. It's a frequent problem on sites with top banner ads. Like if an ad server stops responding, all the pages serving them can suddenly take minutes to display, even if the rest of the page loaded almost immediately.

I'd probably leave output buffering on, just for performance if you do a lot of small writes, but flush() (and/or ob_flush(). It's been a while for me) before doing anything intensive.

---

### Post by wongo888 on 2011-03-09
[LIST=1]
[*]Try caching the page
[*]Move script tags to bottom of page from the head
[*]Retrieve section content from server in chunks as JSON rather than all at once prior to page rendering
[/LIST]

---

### Post by asondag on 2011-03-09
To make this clearer, I have the website running on two servers right now. One is the one I just configured, and the other is my old shared hosting plan. The shared hosting plan loads it as it comes, while the ubuntu/apache2 server I just configured waits. Same exact code.

---

### Post by wongo888 on 2011-03-09
Try comparing the phpinfo output? Give a bigger buffer to output_buffering? What have you tried?

---

### Post by asondag on 2011-03-10
I'm kind of a noob, so I don't really know what I should be doing. It appears that both php and apache buffering is off, so I don't know where to go from there? :confused:

Also, the page in question is a straight up php code. It's a loooooooong loop with barely formatted echo outputs. No script tags or anything like that. Very straight forward.

I've got phpinfo for both pages, but I'm not really sure what I should be looking at. Thanks for being patient.

---

### Post by wongo888 on 2011-03-10
You might try turning on the APC php cache. It should show up on your *phpinfo* if it has been installed.

Otherwise:

```
$ sudo apt-get install php-apc
$ sudo apache2ctl -k restart
```

You can get at the config file here:

```
$ sudo vim /etc/php5/apache2/conf.d/apc.ini
```

The cache has a handy status script, but you have to dig a bit for it. Move it to the web root and unzip up.

```
$ sudo cp /usr/share/doc/php-apc/apc.php.gz /var/www
$ cd /var/www
$ sudo gzip -d apc.php.gz
```

Change the password on line 41 and 42 to something better than apc and password:

```
$ sudo vim apc.php
```

---

### Post by asondag on 2011-03-10
Thanks for the reply. Since that is not installed on the server that is working correctly, I don't want to jump into installing more programs. I'd rather find the root cause of the problem. I configured this server via LAMP, so I'm going to wipe the server clean and reinstall the parts individually. Maybe that will help. I'll let you know in a few hours.

---

### Post by asondag on 2011-03-10
Alright, I've reinstalled everything, no dice. I ran the following php script to confirm the problem and the page will never load when I run it.

[PHP]<?php
while (TRUE)
{
    echo 'x';
    flush();
    sleep(1);
}
?>[/PHP]

---

### Post by asondag on 2011-03-10
Sorry for what seems like spamming my own thread. I found a variable in the php.ini that is "implicit_flush". This is the equivalent of calling flush() after every html/echo block. Once I turned that on, my code worked as I wanted it to! However, this seems like a BIG bandaid for an underlying problem. Like I said, I am a noob, so I don't know where to go from here. Suggestions?

Also, output_buffering = Off, and it seems to be working. I tried to call a header after output it and threw an error, even when I turned the implicit_flush back off.

---

### Post by asondag on 2011-03-11
bump. please don't let this die guys! Still struggling:(

---

### Post by dtfinch on 2011-03-11
Did you try ob_flush() and flush() together?

---

### Post by asondag on 2011-03-11
Ok when I tried it on another script, flush() does the job. ob_flush() does not work. So I'm assuming this is an apache problem, not a php problem, correct?

---

### Post by asondag on 2011-03-11
Ok, something I've just noticed is that both of my scripts make calls to other websites (one is curl the other is through file_get_contents()). Hence the reason for the slow script in the first place. This doesn't change the fact that it is working on one server (without any flush() functions) and not mine. Just might be a clue to you gurus out there?

---

### Post by asondag on 2011-03-12
Alright I figured out my server is gzipping the data.

Here is a handy page to figure out if this is happening on your server.

[http://www.whatsmyip.org/http_compression/](http://www.whatsmyip.org/http_compression/)

---

