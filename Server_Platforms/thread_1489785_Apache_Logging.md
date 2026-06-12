---
title: "Apache Logging"
date: 2010-05-21
forum: Server Platforms
---

### Post by tgeorge06 on 2010-05-21
Hello Ubuntu Community!

My boss would like to have stats on which domains are getting the most traffic. (Extremely vague) So my question is, How do I track which domain names we own are pulling the most traffic?

**Ok so now down to the specifics, this is what I have**:

5,000 Domain names pointed to the web server,

600 Domain names have directories and virtual hosts configured and are working correctly,

So the other 4,400 Domain names are just bouncing to the default page which I have traffic redirecting towards one of our main websites from there (Which is what I want).

This current setup works properly and I can pull stats from the log files globally, but I needed to refine the stats down to one specific virtual host, the default page.

**This is what I have done:**

edited the directives to show 
CustomLog /var/log/apache2/customlog

which works so I use my log analyzer, WebLog Expert, to pull that file and parse it. So when I look for the Top Domains that are being typed in to reach me, I find source IP's and DNS's. 

What I'm trying to accomplish is recording the stats of which domain names pointed to the webserver are pulling the most traffic. **(The ones without pages made and are being redirected elsewhere)**

---

### Post by cdenley on 2010-05-21
You can configure apache to log just about anything.
```

LogFormat "%h %{Host}i %B \"%r\"" trafhost
CustomLog /var/log/apache2/trafhost.log trafhost

```
This will log in the following format.
```

123.123.123.123 www.mydomain.com 1234 "GET / HTTP/1.1"

```
This line would indicate that the request "GET / HTTP/1.1" for the hostname [www.mydomain.com](www.mydomain.com) came from the IP 123.123.123.123, and the server's response was 1,234 bytes, excluding the response header.

[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats)
[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats)

---

### Post by tgeorge06 on 2010-05-21
Thank you for your reply.

Syntax error on line 204 of /etc/apache2/apache2.conf:
Unrecognized LogFormat directive %

Am I not supposed to put the LogFormat into apache2.conf?

Scratch all that, I caught your edit and applied it. Testing it now I will post back with results soon.

---

### Post by tgeorge06 on 2010-05-21
Thank you for coming to my rescue, I knew the solution had to be simple and it was. 

Do you have any recommendations on a log analyzer that can parse the trafhost.log file and put the information into graphs and such?

Also while I have you in the thread, Can I filter out certain IP addresses from getting logged?

---

### Post by cdenley on 2010-05-21
> **tgeorge06 said:**
> 
Am I not supposed to put the LogFormat into apache2.conf?


I believe if you put that in apache2.conf (or any global configuration file), then that will only log requests which aren't handled by a virtual host. If you want to log all requests by any virtual host, I think you need to put that in each virtual host configuration. You could probably make a global logging configuration file like "/etc/apache2/vhostlog.conf", then add "Include /etc/apache2/vhostlog.conf" to each vhost. This way, if you want to change that LogFormat for all vhosts, you only edit one file. Or maybe I am mistaken? Never tried it out.

I just made that format up, so I doubt you will find any log analyzer which will understand that. Perhaps you can script one yourself.

---

### Post by tgeorge06 on 2010-05-21
I put it in apache2.conf and it seems to be working how I need it, i just put the CustomLog in the vhost config itself.

so what global format would track host like the one you made up?

I can have other data as well it doesn't have to be limited down as much as you made it. the common format worked on logs i used for the global vhosts, but trying to single this one vhost out... it didn't want to show the host names.

---

### Post by cdenley on 2010-05-21
> **tgeorge06 said:**
> 
so what global format would track host like the one you made up?

You mean what format would log the "Host" field from the request header and be understood by log analyzers? I'm not sure, since I'm not familiar with any log analyzers. I usually use the "grep" and "sed" commands to find what I need from logs.
> **tgeorge06 said:**
> 
the common format worked on logs i used for the global vhosts, but trying to single this one vhost out... it didn't want to show the host names.

You mean you have a vhost which that LogFormat example I gave doesn't log the hostname? That would only happen if no hostname was given in the request header.

---

### Post by tgeorge06 on 2010-05-21
> **cdenley said:**
> You mean what format would log the "Host" field from the request header and be understood by log analyzers? I'm not sure, since I'm not familiar with any log analyzers. I usually use the "grep" and "sed" commands to find what I need from logs.


You mean you have a vhost which that LogFormat example I gave doesn't log the hostname? That would only happen if no hostname was given in the request header.

I will look more into grep and sed.

Your logformat worked fine, i'm just trying to find a pretty way to show the data to my boss haha.

---

### Post by cdenley on 2010-05-21
Here is a simple PHP script which totals the bytes for each hostname in a given log file.
[PHP]
#!/usr/bin/php
<?php
if(count($argv)<2) die("usage: ./bwlog.php /path/to/logfile.log");
$logfile=$argv[1]; // path to logfile was given as an argument
$fh=fopen($logfile,'r');
$hostnames=array(); // initialize empty array to store byte totals for each host
while(!feof($fh)) {
        $data=explode(' ',fgets($fh,1024),4); // read a line and split it by space
        if(count($data)>3 && ctype_digit($data[2])) { // if there are more than three fields and the field at index 2 has only digits
                if(!isset($hostnames[$data[1]])) // if there isn't a count for this host, set it to zero
                        $hostnames[$data[1]]=0;
                $hostnames[$data[1]]+=intval($data[2]); // add the bytes from this line to the host's byte count
        }
}
fclose($fh);
foreach($hostnames as $hostname=>$bytes) { //print each host's byte count
        print "$hostname => $bytes bytes\n";
}
?>
[/PHP]

---

### Post by tgeorge06 on 2010-05-21
your sir = 1337

I need to sit down and mash my face on the keyboard some more and learn php for myself. Thanks for all of your help, i'll respond with some results of the php script.

Thanks again!

---

### Post by tgeorge06 on 2010-05-21
usage: ./bwlog.php /var/log/apache2/trafhost.log


thats the output I get when I run the php script.

---

### Post by cdenley on 2010-05-21
> **tgeorge06 said:**
> usage: ./bwlog.php /var/log/apache2/trafhost.log


thats the output I get when I run the php script.

It's telling you you need to provide the path to your log as an argument.

---

### Post by tgeorge06 on 2010-05-21
```
#!/usr/bin/php
<?php
if(count($argv)<2) die("usage: ./stat.php /var/log/apache2/trafhost.log");
$logfile=$argv[1]; // path to logfile was given as an argument
$fh=fopen($logfile,'r');
$hostnames=array(); // initialize empty array to store byte totals for each host
while(!feof($fh)) {
        $data=explode(' ',fgets($fh,1024),4); // read a line and split it by space
        if(count($data)>3 && ctype_digit($data[2])) { // if there are more than three fields and the field at index 2 has only digits
                if(!isset($hostnames[$data[1]])) // if there isn't a count for this host, set it to zero
                        $hostnames[$data[1]]=0;
                $hostnames[$data[1]]+=intval($data[2]); // add the bytes from this line to the host's byte count
        }
}
fclose($fh);
foreach($hostnames as $hostname=>$bytes) { //print each host's byte count
        print "$hostname => $bytes bytes\n";
}
?>
```

Ok, I see what you mean... got it to work.

How would I tweak this code to make it show the quantity of each domain name and possibly arrange them in order from most visited to least?

---

### Post by cdenley on 2010-05-21
That works for me.
```

cdenley@www:~$ ./stat.php /var/log/apache2/test.log
mydomain1.com => 42161 bytes
www.mydomain1.com => 58765443 bytes
www.mydomain2.com => 2125810 bytes
www.mydomain1.net => 326729 bytes
mydomain2.com => 388944 bytes
www.mydomain3.com => 0 bytes

```

---

### Post by tgeorge06 on 2010-05-21
ya after some playing with it, I figured out my mistake.

I'm a complete newb at php so how would you code this to show the quantity of each and arrange them as so?

---

### Post by cdenley on 2010-05-21
> **tgeorge06 said:**
> ya after some playing with it, I figured out my mistake.

I'm a complete newb at php so how would you code this to show the quantity of each and arrange them as so?

You mean the quantity as in number of requests?
[PHP]#!/usr/bin/php
<?php
if(count($argv)<2) die("usage: ./bwlog.php /path/to/logfile.log");
$logfile=$argv[1];
$fh=fopen($logfile,'r');
$hostnames=array();
while(!feof($fh)) {
	$data=explode(' ',fgets($fh,1024),4);
	if(count($data)>3 && ctype_digit($data[2])) {
		if(!isset($hostnames[$data[1]])) {
			$hostnames[$data[1]]['bw']=0;
			$hostnames[$data[1]]['reqs']=0;			
		}
		$hostnames[$data[1]]['bw']+=intval($data[2]);
		$hostnames[$data[1]]['reqs']++;
	}
}
fclose($fh);
uasort($hostnames,'sortbyreqs');
foreach($hostnames as $hostname=>$data) {
	print "$hostname: ".$data['reqs']." requests for ".$data['bw']." bytes\n";
}

function sortbyreqs($a,$b) {
	if($a['reqs']<$b['reqs'])
		return 1;
	if($a['reqs']>$b['reqs'])
		return -1;
	return 0;
}
?>[/PHP]

---

### Post by tgeorge06 on 2010-05-21
i'm speechless haha, exactly what I needed. You are awesome.

Ok you have helped me way to much already but I'll ask for one more thing.

Can I filter out our ip addresses out of these results? I guess throw in a source IP into the log, and make the php script not parse those?

---

### Post by cdenley on 2010-05-21
Pass any IP addresses as arguments which you want to ignore. For whole networks, just give the common part. For example: 192.168.0. would ignore 192.168.0.1-192.168.0.254. It ignores any IP which begins with a string given as a parameter after the log file.

[PHP]
#!/usr/bin/php
<?php
if(count($argv)<2) die("usage: ./bwlog.php /path/to/logfile.log 192.168.0. 192.168.1.");
$ignoreip=array();
for($i=2;$i<count($argv);$i++)
	$ignoreip[]=$argv[$i];
$logfile=$argv[1];
$fh=fopen($logfile,'r');
$hostnames=array();
while(!feof($fh)) {
	$data=explode(' ',fgets($fh,1024),4);
	if(count($data)>3 && ctype_digit($data[2])) {
		$ignore=false;
		foreach($ignoreip as $ip) {
			if(strpos($data[0],$ip)===0)
				$ignore=true;
		}
		if($ignore)
			continue;
		if(!isset($hostnames[$data[1]])) {
			$hostnames[$data[1]]['bw']=0;
			$hostnames[$data[1]]['reqs']=0;			
		}
		$hostnames[$data[1]]['bw']+=intval($data[2]);
		$hostnames[$data[1]]['reqs']++;
	}
}
fclose($fh);
uasort($hostnames,'sortbyreqs');
foreach($hostnames as $hostname=>$data) {
	print "$hostname: ".$data['reqs']." requests for ".$data['bw']." bytes\n";
}

function sortbyreqs($a,$b) {
	if($a['reqs']<$b['reqs'])
		return 1;
	if($a['reqs']>$b['reqs'])
		return -1;
	return 0;
}
?>
[/PHP]

---

### Post by tgeorge06 on 2010-05-21
I'm noticing alot of spiderbot traffic, can I filter them out with wildcards?

./stat.php /var/log/apache2/trafhost.log *crawl* *spider*

That's what I tried and it didn't work for me.

---

### Post by cdenley on 2010-05-21
> **tgeorge06 said:**
> I'm noticing alot of spiderbot traffic, can I filter them out with wildcards?

./stat.php /var/log/apache2/trafhost.log *crawl* *spider*

That's what I tried and it didn't work for me.

No, that only ignores IP addresses which start with the strings you provide. It doesn't interpret wildcards. If you want to filter out spiders, you should have apache log the user-agent strings.

---

### Post by tgeorge06 on 2010-05-21
This is what I added for LogFormat

```
LogFormat "%h %{Host}i %B \"%r\" %{User-agent}i" trafhost
```

I probably have to declare something in the php script to only read user-agent correct?

I'm leaving work and going to go home and clear my head, I'll look around to see why the php script doesn't want to work web based. 

I'll check back tomorrow and see if you've posted anything else.

---

