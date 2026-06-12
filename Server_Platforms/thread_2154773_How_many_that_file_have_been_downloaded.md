---
title: "How many that file have been downloaded ?"
date: 2013-06-15
forum: Server Platforms
---

### Post by Raafat1991 on 2013-06-15
Hi guys...i'm looking for a tool tells me information about a certain file like :

1- how many that file have been downloaded ?
2- How much the data have been transmitted 3MB 3GB...etc of a single file and the total of my server (ubuntu server) ?


thank you .

---

### Post by byStanderone on 2013-06-15
...there is download monitor in the software package...not sure if that works also for servers...am on desktop

---

### Post by lisati on 2013-06-15
You might be able to do some analysis of your log files. Which one you look at will depend on what kind of server you are running. Are you running a web page, or are you sharing files?

---

### Post by Raafat1991 on 2013-06-16
A web page and i'm running apache2 server .

---

### Post by SeijiSensei on 2013-06-16
To count up the number of downloads:

```
grep filename /var/log/apache2/access.log | wc -l
```

Once you know the number of downloads the total amount of traffic is simply

(number of downloads) X (size of file)

---

### Post by Cheesemill on 2013-06-16
For the total network utilization of your server you can use vnstat.

---

### Post by Raafat1991 on 2013-06-20
> **SeijiSensei said:**
> To count up the number of downloads:

```
grep filename /var/log/apache2/access.log | wc -l
```

Once you know the number of downloads the total amount of traffic is simply

(number of downloads) X (size of file)

But what about the downloads that didn't upload all their bits ?

---

### Post by SeijiSensei on 2013-06-20
The log records show the amount of traffic exchanged.  For instance,

```
10.10.10.10 - - [06/Aug/2012:11:01:39 -0400] "GET /images/welcome.gif HTTP/1.1" 200 1533 "https://www.example.com/" "Mozilla/5.0 (Windows NT 5.1; rv:14.0) Gecko/20100101 Firefox/14.0.1"
```

The "1533" is the number of bytes transferred in response to that request.  In this case it is the size of "welcome.gif".

It's pretty rare that people cancel out in the middle of a download unless we're talking about files in the 100s of megabytes, and even then I'd be surprised if aborted downloads constituted more than a couple of percent of all transfers.

One solution is to use a web log parser like [analog](http://www.analog.cx/).  It will construct reports that include the number of transfers for each file and the total amount of traffic involved.

---

### Post by Raafat1991 on 2013-06-22
> **SeijiSensei said:**
> The log records show the amount of traffic exchanged.  For instance,  ```
10.10.10.10 - - [06/Aug/2012:11:01:39 -0400] "GET /images/welcome.gif HTTP/1.1" 200 1533 "https://www.example.com/" "Mozilla/5.0 (Windows NT 5.1; rv:14.0) Gecko/20100101 Firefox/14.0.1"
```  The "1533" is the number of bytes transferred in response to that request.  In this case it is the size of "welcome.gif".  It's pretty rare that people cancel out in the middle of a download unless we're talking about files in the 100s of megabytes, and even then I'd be surprised if aborted downloads constituted more than a couple of percent of all transfers.  One solution is to use a web log parser like [analog](http://www.analog.cx/).  It will construct reports that include the number of transfers for each file and the total amount of traffic involved.    Thank you that's a great advice *______*

---

### Post by SeijiSensei on 2013-06-22
Which "advice" exactly?  Using analog?

---

### Post by Raafat1991 on 2013-08-27
Hi:grin:...a great advice about apache2 server's logs.But what if apache2 server was't the responsible about uplaoding and downloading operations ?
If you have any an article about installng and configuring Analog on ubuntu server ?

thank you.

---

### Post by Raafat1991 on 2013-08-27
For more clarity about my first question,i did't mean other servers like Light-weight,nginx..etc but precisely i meant a program on my ubuntu server is uploading some files to a client. for example,A torrent server utorrent,ktorrent is uploading files to clients .

---

### Post by SeijiSensei on 2013-08-27
If you know what ports are involved, you can use iptables logging to tally packets.

For instance, if you were using the standard 6881-6889 ports for BT, you might include:

```
/sbin/iptables -A INPUT -p tcp --dport 6881:6889 -j ACCEPT
```

in the iptables ruleset.  That would tabulate all outbound traffic sent to ports 6881-6889 on any remote machine.  Then if you run "sudo /sbin/iptables -L -nv" you'll see entries like this:

```
 
 2099  117K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
 9696  530K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 

```

This examples shows the number of packets (2099/9696) and the number of bytes (117K/530K) that were sent to this web server's HTTP and HTTPS ports since the last time the firewall was restarted.
  
As for analog, I use CentOS on servers and have only installed analog on that platform.  However I know it is in the Ubuntu repositories, so you can install it with "sudo apt-get install analog".  The binary is /usr/bin/analog, and all the associated files are in /usr/share/analog.  The default configuration file is /etc/analog.cfg.  For details on configuring analog, the best choice is the official user's guide.  On the server, point a browser to file:///usr/share/doc/analog/docs/Readme.html.

---

### Post by Raafat1991 on 2013-08-27
Hi...But can iptables tell me about those bits where was coming from (meaning which file has those bits)?

Has Analog a web-based interface ?i think that will be much better than just using command line for interactiving with Analog.

---

### Post by SeijiSensei on 2013-08-27
No and no.

---

### Post by Raafat1991 on 2013-08-27
Thank you...but expect a replay *________*

---

