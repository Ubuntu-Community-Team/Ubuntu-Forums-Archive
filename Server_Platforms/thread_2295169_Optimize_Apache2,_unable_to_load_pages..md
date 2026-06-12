---
title: "Optimize Apache2, unable to load pages."
date: 2015-09-16
forum: Server Platforms
---

### Post by stephanos2 on 2015-09-16
Hi al

I have a website with a decent amount of users running on it. Theres a livechat where all users can chat with eachother etc, so I'm guessing those requests take a lot from the server already. Though when the server is just booted, everything works fine. Ram usage goes up slowly even though if nothing special is being done. I know you can finetune your Apache server so u don't have to restart it, but I have no clue how.
I know in the config u can change MaxClients, Spareservers etc etc, but I have no clue on how to put these to be exact. Right now I'm using the module mpm_prefork, and I have these things set in : mpm_prefork.conf ( right now it looks like this )
```
<IfModule mpm_prefork_module>
        StartServers              5
        MinSpareServers           5
        MaxSpareServers          20
        MaxRequestWorkers        250
        MaxConnectionsPerChild   0
        MaxClients      100
</IfModule>
```
So far I really have to restart my Apache2 once every 15-30 minutes in order to make users able to reload webpages, without that the webpages wont load anymore... My server has 2 cores and 4GB Ram which I think for like ( so far only 20 users at a time max, being online ) should be plenty...
Any help on this to where I can change my config so it works better?
This is on Ubuntu 14 btw!
Thanks already.

---

### Post by SeijiSensei on 2015-09-16
The next time things slow down, before you restart Apache, run the command
```
ps ax | grep apache | wc -l
```
to see how many running instances you have at that point.  Then you can better tune the parameters for mpm_prefork.

As a start you could try 
```

StartServers 20
MinSpareServers 10
MaxSpareServers 40

```
and see if that helps.

Does this website rely on an SQL database for any of its services, like collecting and storing the message traffic?  If so maybe you need to tune [MySQL]("https://www.percona.com/blog/2014/01/28/10-mysql-settings-to-tune-after-installation/") or [PostgreSQL]("https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server") or whatever you are using.

---

### Post by stephanos2 on 2015-09-16
Yea it does use MySQL for the messages, any tips on how I should finetune my MySQL then? and I'll try that already one sec. And for some reason while trying that now there are 78 instances running, but never ever ever that I have 78 users. Today maybe there were 20 online in total...

---

### Post by SeijiSensei on 2015-09-18
A single user visiting a single webpage can generate multiple connections as they download text, graphics, etc.

[MaxSpareServers]("http://httpd.apache.org/docs/2.4/mod/prefork.html#maxspareservers") is supposed to kill any idle child processes in excess of the limit, 20 in your case.  I don't understand how you got to 78.  

You might try tuning MaxRequestWorkers as well.  Read the whole linked page for details.

I included a link to a MySQL tuning page in my initial reply.

---

