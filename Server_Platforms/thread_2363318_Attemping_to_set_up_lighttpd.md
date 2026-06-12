---
title: "Attemping to set up lighttpd"
date: 2017-06-08
forum: Server Platforms
---

### Post by jamesr on 2017-06-08
Hi,

I am attempting to set up a new copy lighttpd . I normally have no problems as I use lighttpd as an intranet server.

I accept that I may have forgotten how to set it up, old age and all that!!.

I have tried 2 approaches,

1) follow the documentation here [https://help.ubuntu.com/community/lighttpd]("https://help.ubuntu.com/community/lighttpd") 
and it fails after entering the line ```
sudo service lighttpd reload
```

2) using the information on the lighttpd wiki [//https://help.ubuntu.com/community/lighttpd]("//https://help.ubuntu.com/community/lighttpd")

and even the first section fails. It seems that the lighttd server is not running.

The only difference between the 2 systems is that one that works is  i686 
> Linux dobby2 4.8.0.54- generic #57-16.04.1-Ubuntu SMP Wed May24 16:20:44 UTC 2017 i6b6 i686 i686 GNU/Linuxand the failing one is running> jdscioffx@jdscioffx:~$ uname -a
Linux jdscioffx 4.4.0-79-generic #100-Ubuntu SMP Wed May 17 19:57:27 UTC 2017 i686 athlon i686 GNU/Linux

I have tried to register on the lighttpd forum that gives an error

---

### Post by cariboo on 2017-06-08
It looks like you are using 16.04 or newer, so you need to use systemd to start, stop and check services. to make sure lighttpd starts automatically use the following command:

```
sudo systemctl enable lighttpd.service
```

then to start the service:

```
sudo systemctl start lighttpd.service
```

top stop the service use stop. To check the status:

```
sudo systemctl status lightppd.service
```

I don't have lighttpd running here, but the staus output should look something like this:

```
systemctl status apache2.service
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: active (running) since Thu 2017-06-08 11:49:57 PDT; 4h 35min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1526 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
    Tasks: 8
   Memory: 83.0M
      CPU: 1.765s
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;1765 /usr/sbin/apache2 -k start
           &#9500;&#9472;1950 /usr/sbin/apache2 -k start
           &#9500;&#9472;1951 /usr/sbin/apache2 -k start
           &#9500;&#9472;1952 /usr/sbin/apache2 -k start
           &#9500;&#9472;1953 /usr/sbin/apache2 -k start
           &#9500;&#9472;1954 /usr/sbin/apache2 -k start
           &#9500;&#9472;8198 /usr/sbin/apache2 -k start
           &#9492;&#9472;8208 /usr/sbin/apache2 -k start

Jun 08 11:49:08 willy systemd[1]: Starting LSB: Apache2 web server...
Jun 08 11:49:08 willy apache2[1526]:  * Starting Apache httpd web server apache2
Jun 08 11:49:38 willy apache2[1526]: [Thu Jun 08 11:49:38.262328 2017] [alias:warn] [pid 1762] AH00671:
```

---

### Post by jamesr on 2017-06-09
Hi Cariboo,

Thanks for the reply

I tried the first line > sudo systemctl enable lighttpd.servicethat you suggested with the following result```
jdscioffx@jdscioffx:~$ sudo systemctl enable lighttpd.service
[sudo] password for jdscioffx: 
Synchronizing state of lighttpd.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable lighttpd
``` looking good!!

2nd command> sudo systemctl start lighttpd.service with no message as a result```
jdscioffx@jdscioffx:~$ sudo systemctl start lighttpd.service
```

3rd command> sudo systemctl status lightppd.service with the resulting output ```
jdscioffx@jdscioffx:~$ sudo systemctl status lightppd.service
&#9679; lightppd.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
t

```
so ran status for apache2 ```
jdscioffx@jdscioffx:~$ systemctl status apache2.service
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: active (running) since Thu 2017-06-08 22:06:20 EDT; 40min ago
     Docs: man:systemd-sysv-generator(8)
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;1537 /usr/sbin/apache2 -k start
           &#9500;&#9472;1540 /usr/sbin/apache2 -k start
           &#9492;&#9472;1541 /usr/sbin/apache2 -k star
```
I ran this check I was seeing the Apache2 Ubuntu Default Page  on another PC on my intranet

I tried changing the location of the index file to ones that were appropriate for my system and I was still seeing the Apache2 placeholder. If I selected the index.lighttpd.html manually by setting xxx.xxx.xxx.163/index./html/lighttpd.html I could see the lightty placeholder.

Is only Apache2 running?

Rechecked this morning after powering off both PCs and rebooting both

Now I see the Apache2 placeholder by selecting localhost 
whereas ```
http://localhost/html/index.lighttpd.html
``` I see the placeholder for lighty.

Rerunning the status tests gives the following results ```
jdscioffx@jdscioffx:~$ sudo systemctl status lightppd.service
[sudo] password for jdscioffx: 
&#9679; lightppd.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
jdscioffx@jdscioffx:~$ systemctl status apache2.service
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: inactive (dead) since Fri 2017-06-09 11:13:15 EDT; 34min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1310 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0
  Process: 1121 ExecStart=/etc/init.d/apache2 start (code=exited, status

Jun 09 11:13:15 jdscioffx apache2[1121]: (98)Address already in use: AH0
Jun 09 11:13:15 jdscioffx apache2[1121]: (98)Address already in use: AH0
Jun 09 11:13:15 jdscioffx apache2[1121]: no listening sockets available,
Jun 09 11:13:15 jdscioffx apache2[1121]: AH00015: Unable to open logs
Jun 09 11:13:15 jdscioffx apache2[1121]: Action 'start' failed.
Jun 09 11:13:15 jdscioffx apache2[1121]: The Apache error log may have m
Jun 09 11:13:15 jdscioffx apache2[1121]:  *
Jun 09 11:13:15 jdscioffx apache2[1310]:  * Stopping Apache httpd web se
Jun 09 11:13:15 jdscioffx apache2[1310]:  *
Jun 09 11:13:15 jdscioffx systemd[1]: Started LSB: Apache2 web server.

```

Thanks again for the information

Another 2 comments/questions 
Do I have to re-enable and/or restart lighty
I noted that when I removed lighttpd using sudo apt-get remove lighttpd, the system reinstalled Apache2??but only the main module.

---

### Post by cariboo on 2017-06-09
If apache2 and lighttpd are using the same port (80) you are going to run into problems. Try running one of them on another port

---

### Post by jamesr on 2017-06-09
Hi Cariboo,

BC per chance?

I thought that I done that change before to no avail. But I repeated it all the same.

Changed port to 81.
Then I tried to restart. See the attached part on terminal.

```
jdscioffx@jdscioffx:~$ light_conf_eds
jdscioffx@jdscioffx:~$ sudo systemctl start lighttpd.service
jdscioffx@jdscioffx:~$ sudo systemctl status lightppd.service
&#9679; lightppd.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
jdscioffx@jdscioffx:~$ sudo systemctl restart lightppd.service
Failed to restart lightppd.service: Unit lightppd.service not found.
jdscioffx@jdscioffx:~$ sudo systemctl stop lightppd.service
Failed to stop lightppd.service: Unit lightppd.service not loaded.
jdscioffx@jdscioffx:~$ 


```
light_conf_eds is an alias. I have not set the others as aliases as yet.

Start gives an error "no output no ok or fail". Is that normal?
Status "no such file or directory" which directory? inactive (dead)?

Stop = Unit lightppd.service not loaded. ??

Thanks again and my apologies about asking all of these questions about lighttpd.

---

### Post by cariboo on 2017-06-09
Can you check /var/log/lighttpd/error.log to see what error if any show up?

---

### Post by jamesr on 2017-06-15
Hi Cariboo,

My apologies about replying sooner but life got the the way.

I have just seen your last reply and I had already thought about checking this point as well > Can you check /var/log/lighttpd/error.log to see what error if any show up?  so I have an immediate answer and the answer is there is no log file?
 
Further to  your previous reply I had changed the port to 81 in the  lighttpd.conf  file. Restarting no change. So shut-down the PC.

Next day restarted PC from cold . I now could see the placeholder file on port 81.
Removed Apache2 using synaptic, changed the port back to 80 restarted lighttpd  no change. Powered down PC

Next day restarted PC from cold . I now could see the placeholder file on port 80.
Along with Apache index.html page. Edited lighttd place holder file (index.html). Restarted but no change. Powered down PC.

Today I  restarted this PC(this one) from cold to check the forum . I now could see the modified placeholder file on port 80.
Conclusions??
Lighttpd is running some how. But no log file.
Restart does not seem to work either way but cold reboot seems to reload the files correctly. I have the pages set up as my home pages in Firefox.

I have attached .png files to see the home page tabs (using localhost) and the modified placeholder page.

---

### Post by jamesr on 2017-06-15
Hi Cariboo,

I had to send a partial reply Because I was interrupted by a phone call and I was not sure how long it would last.

The additional comments are related to the fact associated with the errors/symptoms being "unusual", i.e only working on a cold boot, no log files yet working. I am going to set-up lighttpd on a another PC where the architecture is i686 and is also Xubuntu 16.04-3. The failing PC is using 16.04-2 plus updates on an amd64 system. 

Thanks for the help.

---

### Post by cariboo on 2017-06-15
I installed lighttpd on my desktop running 17.10 changed the port it is listening on to 8080, here is what my /etc/lighttpd/lighttpd.conf looks like:

```
cat lighttpd.conf
server.modules = (
	"mod_access",
	"mod_alias",
	"mod_compress",
 	"mod_redirect",
)

server.document-root        = "/var/www/html"
server.upload-dirs          = ( "/var/cache/lighttpd/uploads" )
server.errorlog             = "/var/log/lighttpd/error.log"
server.pid-file             = "/var/run/lighttpd.pid"
server.username             = "www-data"
server.groupname            = "www-data"
server.port                 = 8080


index-file.names            = ( "index.php", "index.html", "index.lighttpd.html" )
url.access-deny             = ( "~", ".inc" )
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )

compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ( "application/javascript", "text/css", "text/html", "text/plain" )

# default listening port for IPv6 falls back to the IPv4 port
## Use ipv6 if available
#include_shell "/usr/share/lighttpd/use-ipv6.pl " + server.port
include_shell "/usr/share/lighttpd/create-mime.assign.pl"
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"
```

---

### Post by jamesr on 2017-06-17
Hi Cariboo,

Thanks for the last update, but before I reply to your update, I will update with my results of setting "lighttpd" up another PC. It worked!! without any fiddling around so that solves my intermediate problem about a local test bed for testing of website before releasing it to the world.

Installation was very simple:-
a) Install using synaptic, noted that there were more dependencies than the previous installation including one that previously I had to manually install (gamin).
b) I  noted that I could see the temporary place holder for lighttpd within minutes.
c) Edited lighttpd.conf to change "var/www/html" to "var/www". Here is my copy noting lines 9 and 10
```
server.modules = (
	"mod_access",
	"mod_alias",
	"mod_compress",
 	"mod_redirect",
#       "mod_rewrite",
)

#server.document-root        = "/var/www/html"
server.document-root        = "/var/www"
server.upload-dirs          = ( "/var/cache/lighttpd/uploads" )
server.errorlog             = "/var/log/lighttpd/error.log"
server.pid-file             = "/var/run/lighttpd.pid"
server.username             = "www-data"
server.groupname            = "www-data"
server.port                 = 80


index-file.names            = ( "index.php", "index.html", "index.lighttpd.html" )
url.access-deny             = ( "~", ".inc" )
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )

compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ( "application/javascript", "text/css", "text/html", "text/plain" )

# default listening port for IPv6 falls back to the IPv4 port
## Use ipv6 if available
#include_shell "/usr/share/lighttpd/use-ipv6.pl " + server.port
include_shell "/usr/share/lighttpd/create-mime.assign.pl"
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"
```
d) Tested my new file using my alias "light_conf_test"
```
kats@kats2:~$ light_conf_test
Syntax OK/CODE] 
It worked!!. The alias is equivalent to[CODE]alias light_conf_test='sudo lighttpd -t -f /etc/lighttpd/lighttpd.conf'

```
e) Restarted using my alias "alias light_reload" which is equivalent to
```
alias light_reload='sudo /etc/init.d/lighttpd force-reload'

```and it worked, see result```
kats@kats2:~$ light_reload
[ ok ] Reloading lighttpd configuration (via systemctl): lighttpd.service.
kats@kats2:~$ 

``` Note that it still is using the old style of restart that previously failed of the other PC. I have not tried the new style as yet, I was too pleased to have solved the immediate problem.

f) Edit my *.html files in a separate folder ```
/home/kats/Intra/kats
```
g) copy to var/www using another alias webupdate equivalent to ```
alias webupdate='sudo cp /home/kats/Intra/kats/*.* /var/www'

``` and reload_light
```
kats@kats2:~$ webupdate
kats@kats2:~$ light_reload
[ ok ] Reloading lighttpd configuration (via systemctl): lighttpd.service.
kats@kats2:~$ 

```
hey presto "all is hunky dory" i.e. working 

So I could stay the problem is partially solved i.e. works on one PC but not another. I will not be changing the title as solved because the original problem is still not solved!!!

Going back the the original PC I will try your lightttpd.conf file along with my working one.
I have just noticed this morning that my automatic Saturday morning "mondorescue" backup did not work so it looks as if there may other problems with that PC. It looks as if cron is not running.??

My probable approach now with original PC (lets call it jds) will be
a) solve the backup problem
b) redo the tests with your conf file etc
c) check if there are any missing files with respect to ligghtd by comparing the dependencies. 

Thanks for the help so far and I will keep you informed on my progress and I will possibly be asking questions.

---

### Post by jamesr on 2017-06-19
Hi Cariboo,

Just an update re the my last comments> My probable approach now with original PC (lets call it jds) will be
a) solve the backup problem
b) redo the tests with your conf file etc
c) check if there are any missing files with respect to lighttpd by comparing the dependencies. 
Problem a) solved, I keep a file of the crontab file (crontab) and I recopied that file into the active crontab using another one of my aliases ```
alias rjd_crontab_up='crontab /root/.rjd_scripts/.rjd_crontabm'

```
I use these aliases because I can go from one server to another and only have to remember part of the name of the alias.
Any way the cron problem by reloading the crontab file.

Skipped stage b because I am seeing another problem but in the process solved original problem.
New problem is that I can see the /var/lighttpd/error.log file but I cannot open the log file with gnome log viewer , I see a permission error when trying to add lighttpd to the log viewer. I could also always use another alias to read the file.
After googling for that error there were many suggestions including several about a missing dependency i.e. gamin is missing. 
Record of history>   392  sudo apt-get install gamin
  393  sudo apt autoremove
  394  thunar
  395  root_thunar

My apologies but I thought I had saved the terminal information.
line 392 responded gamin  was the latest but it suggested that there files that could be removed and the list included apache2-bin .
line 393 removed all files but could not remove some apache2 log files because they were not empty.
line 394 I manually deleted the files.
```
  396  sudo systemctl start lighttpd
  397  systemctl status lighttpd.service -l
  398  light_reload

``` All seems to work including a reload of of an earlier update of my files in /var/www

So the original problem seems to be solved!!!

so now to another question  what are your permissions of the following folders and files
/var
```
root@jdscioffx:~# ll /var
total 64
drwxr-xr-x 16 root      root     4096 May  4 18:18 ./
drwxr-xr-x 23 root      root     4096 Jun  7 16:35 ../

drwxrwxr-x 16 root      syslog   4096 Jun 19 09:06 log/
drwxrwsr-x  2 root      mail     4096 Jun 17 11:39 mail/

drwxrwxr-x  4 jdscioffx www-data 4096 Jun 19 09:06 www/
root@j
```
/var/log```
root@jdscioffx:/var# ll /var/log
total 6616
drwxrwxr-x 16 root              syslog    4096 Jun 19 09:06 ./
drwxr-xr-x 16 root              root      4096 May  4 18:18 ../
 
-rw-r--r--  1 root              root         0 Jul 24  2015 cron
-rw-r-----  1 syslog            adm       3101 Jun 19 11:17 cron.log

drwxr-x---  2 www-data          syslog    4096 Jun 15 19:58 lighttpd/
 
-rw-r-----  1 syslog            adm       9786 Jun 19 11:53 syslog

root@jdscioffx:/var# 
```
 I have removed most files but included others that might be relevant.

ll /var/log/lighttpd
```
root@jdscioffx:/var# ll /var/log/lighttpd
total 8
drwxr-x---  2 www-data syslog   4096 Jun 15 19:58 ./
drwxrwxr-x 16 root     syslog   4096 Jun 19 09:06 ../
-rw-r--r--  1 root     www-data    0 Jun 15 19:58 error.log
root@jdscioffx:/var# 

```

Is the problem the last line i.e. syslog group as some of the google answers suggest. 

Best Wishes
Jim

---

