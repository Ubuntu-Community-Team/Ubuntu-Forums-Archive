---
title: "small pictures problem"
date: 2011-06-07
forum: Server Platforms
---

### Post by JBtje on 2011-06-07
Hello there,
 
Well, I kinda have a problem.
I have a web server (apache2) which does not load images correctly.
 
If i clear my browser cashe and load the page, it sometimes loads the foto's correctly, but when its a page with "many" (lets say 50+) foto's, it only loads a few of them and basically does nothing with the other images :| (doesn't show them at all :|)
 
The server has an upload and download connection of over 150 Mb/s, 2 GB ram and 4x 2.6 GHz CPU available (which he needs to share with some other Virtual Machines, that basically do nothign...). 
It runs Ubuntu 10.04 in combination with Apache2 and PHP5, managed by ISPconfig.
 
The directory that contains the "foto's" (foto's are only 50-100 KB each), contains 1250+ foto's.
 
So i was wondering, what could be the reason that not all foto's are loaded? how "bad" is it to have 1250+ foto's in one dir? can that, for whatever reason, be the problem?
 
Let me know if i can check some config of apache :)
 
Thanks,
JB

---

### Post by arrrghhh on 2011-06-07
How are you web pages structured?  Do you just have a ton of HTML that has each image laid out on the page or...?

---

### Post by JBtje on 2011-06-07
heya,
 
The page is build with tables, but not that many that I would say it is overkill.
Also, the layout just loads perfect (and really quick), its only the images that dont want to load, or load only partially...
 
JB

---

### Post by arrrghhh on 2011-06-07
> **JBtje said:**
> heya,
 
The page is build with tables, but not that many that I would say it is overkill.
Also, the layout just loads perfect (and really quick), its only the images that dont want to load, or load only partially...
 
JB

Huh.  I have an apache server, but never have had that issue.  Is it on a LAN?  (Also, you're using the local IP to connect to the page?)  The page actually finishes loading, says "Done" at the bottom?

I'm not an expert on apache by any means, so hopefully someone else will chime in - but have you perused the apache logs at all, see anything suspicious while the page is loading or 'finished' loading?

---

### Post by JBtje on 2011-06-08
Heya,
 
The server is connected to the internet directly and got its own IP / domain. With the modern browsers, it doesn't tell "done" anymore, so I cannot tell wherever or not it sais that.
The apache logs show that there is an error with loading sqli module, but I dont use that on the webpage... beside that there are alot of notices and warnings, because of varriables not being checked correctly, thought also that cant be the problem.
 
I have not yet checked the access log, will do a.s.p and report if there is anything weird in it..
 
Greetings,
JB

---

### Post by arrrghhh on 2011-06-08
> **JBtje said:**
> The server is connected to the internet directly and got its own IP / domain. **With the modern browsers, it doesn't tell "done" anymore**, so I cannot tell wherever or not it sais that.
The apache logs show that there is an error with loading sqli module, but I dont use that on the webpage... beside that there are alot of notices and warnings, because of varriables not being checked correctly, thought also that cant be the problem.

My browser still says 'Done' at the bottom... Firefox4?  Says it right now in fact, it stays there too..

Well I'd check the logs while you're hitting the page.  See what is happening *while* the page is loading.  I would assume those errors would be relevant.

---

### Post by SeijiSensei on 2011-06-08
I think this problem has more to do with the number of images you're sending than their total bandwidth required.

Consider that the browser will need to create 1250 separate connections to the server if you open the directory with no index page to manage things.  The browser will also display the images on the rendered page.  That all takes time. 

You may want to try increasing the number of "children" that Apache spawns to handle requests.  If you run "ps ax | grep apache" you should see six entries, one master server and five children. The number of children is controlled by the StartServers directive in /etc/apache2/apache2.conf.  You'll see three different entries for StartServers.  Just concentrate on the first set where you see the directive

```
StartServers  5
```

Try changing that to 10 or even 20 and see if performance improves.

The other option to consider is creating an index page that shows only N images at a time with a paging option.  Looking around I found [PHP Photo Album]("http://www.dynamicdrive.com/dynamicindex4/php-photoalbum.htm").  I just now installed it into a directory of images I have and found it very easy to configure.  You might give that a try.

---

### Post by JBtje on 2011-06-08
Heya, thank you for the reply!
 
 
> **SeijiSensei said:**
> I think this problem has more to do with the number of images you're sending than their total bandwidth required.
 
Consider that the browser will need to create 1250 separate connections to the server if you open the directory with no index page to manage things. The browser will also display the images on the rendered page. That all takes time. 
eeh, well... there are 1250+ images in the directory, but its not showing all at once :)
It shows them depending on the name (starting with the letters a-z) and that gives a page with about 20-60 images, which the browser has to load (lukely thats not "that" many)
 
> **SeijiSensei said:**
> 
You may want to try increasing the number of "children" that Apache spawns to handle requests. If you run "ps ax | grep apache" you should see six entries

dont ask me, but it shows 12 :) (guess i have changed some standard config already)
There is indeed a "leader" and 11 "normal" processes.
 
apache2.conf shows:
```

KeepAlive On
MaxKeepAliveRequests 1000
KeepAliveTimeout 15
 
 
<IfModule mpm_worker_module>
    StartServers          5
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild 1000
</IfModule>
 
<IfModule mpm_event_module>
    StartServers          5
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild 1000
</IfModule>
 
<IfModule mpm_event_module>
    StartServers          5
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild 1000
</IfModule>
 
...
 
HostnameLookups Off

```Have changed the first StartServer to 10 and restarted the whole server (not only apache this time...)
ps ax | grep apache2 still shows 12 instances of apache (isn't that weird?)
but, the images load within an eye blink! not sure wherever that was because of the server reboot, or the config change. If it was the hard reboot, what else could give such preformance issues?
 
@arrrghhh: The "Done" on the bottom of the screen is not available here i guess (FF4 / IE 9), but! the icon which is shown on the tab of the webpage, kept showing the "still loading" image, in stead of the web page's icon... so, it was not done loading as I thought it was...
 
ok... I was thinking... I got, on another webserver, a script running which checks the uptime of the server by trying to connect every minute to the server.
 
[PHP]
//PHP code:
...
$e = 20;
for($r=0;$r<$e;$r++)
{
    if($y=fopen($l['url'],'rb')) // open URL $e keer
    {
        $m = 1;
        break;
    }
    usleep(100);
}
if($m==1) // aka online
{
    fclose($y); // close connection
    // do something...
[/PHP]with $l['url'] being a link to a TXT file on the server, containing the letter "a". Can this cause the problems? Cuz I do close the connection as I should....
 
JB

---

### Post by JBtje on 2011-06-09
ok... Yesterday it was quick after the reboot, today its slow again...
Will reboot again and turn off the uptimer, hope that solves the problem...

JB

---

### Post by SeijiSensei on 2011-06-10
Why not just keep the uptimes in a log on the server?

```

#!/bin/bash
LOG=/var/www/uptime-log.txt

echo -n "`date +%F` " >> $LOG 
uptime >> $LOG


```

Put this in a cron job.  Then you can just check the log with a browser from time to time.

---

### Post by JBtje on 2011-06-15
> **SeijiSensei said:**
> Why not just keep the uptimes in a log on the server?
 
```

#!/bin/bash
LOG=/var/www/uptime-log.txt
 
echo -n "`date +%F` " >> $LOG 
uptime >> $LOG
 

```
 
Put this in a cron job. Then you can just check the log with a browser from time to time.
 well, for two reasons actuallt
1) Never thought about doing it that way
2) its not a "true" uptime, since I would like to know the website uptime, I need to know wherever or not the site is available from the outside.
Currently we have some problems with the HP switches that are being used to manage the network, and they have the intention to block us from the internet for no reason...
With an uptime scrtipt from the outside, i'm able to see wherever or not the whole "picture" works, in stead of just the uptime of the machine.
 
ok, back to the problem.
I have turned off the external uptime script for the past 5 days, and during those days the image loading went from exelent to "i dont load at all".
so, im quite sure it was not the external uptime meter that caused the problems.
 
leaves us with the question: what does cause the problem?
 
 
I'm entirely no expert with Ubuntu, nor any other linux system, but I did install the whole server according to the "The Perfect Server - Ubuntu 10.04 [ISPConfig 3]" manual on howtoforge.com.
 
 
ok, there is running:
- postfix
- amavis
- clamAV
- Apache
- MySQL
- PHP5
 
ONE of these prosesses (well, most likely i guess) cause the server to stop loading the images with an exelent time, but how to check what process is the cause of all this???
who can help me out?
 
JB

---

### Post by arrrghhh on 2011-06-15
> **JBtje said:**
> ONE of these prosesses (well, most likely i guess) cause the server to stop loading the images with an exelent time, but how to check what process is the cause of all this???
who can help me out?

So you don't see any spikes on top when the page is loading slowly?  Have you looked at memory utilization?  Is the server under any stress, or are you the only client machine hitting it?

---

### Post by BkkBonanza on 2011-06-16
A couple things come to mind. 

You might try playing with Keepalive values. I'm not sure where Apache sets that now as it's been years since I used it (now always use Nginx - which is so much better for loading small static images in bursts like this). The Keepalive may cause issues with connections being kept open longer than you want and hence causing Apache to spawn more children than is optimal, causing slow downs and higher memory use.

Next, I'd be sure you don't have some firewall (HP switches?) that has settings to prevent DOS attacks that limit the number of connections in a brief time period from one IP source. If something like that was added with good intentions it could have the side effect of blocking legit usage.

Check your Apache log for evidence of whether the images are being requested and return error, or if they don't even get to Apache. Every image request should show up. You can look at times to see if they occur in a short burst or get delayed over time by a limit on open connections.

Lastly, because I'm very partial to it, I'd highly recommend Nginx as a small light web server that is very good at handling high connection rates with only 1-2 processes and little memory use. It's easy to install now from repos (but a bit more tricky to setup for PHP if needed). If you have it handle a subdomain just for images then it can run at the same time as Apache and only handle image requests. But this isn't to say that finding your problem and fixing it with Apache isn't the preferable solution anyway.

I would doubt that some other app is causing the image loading to fail.

If you wait a bit and select "reload" by right clicking on each image manually do they load? Or are they unloadable at any time - which would point to some problem with the links/program code.

---

### Post by JBtje on 2011-09-08
[SIZE=2]After testing for weeks, playing around with all kind of values in PHP.ini, and i have no idea what else... there is an answear.[/SIZE]
 
[SIZE=4]SWAP[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=2]The ESXI machine has 4 GB RAM installed, running 3 systems:[/SIZE]
[SIZE=2]Windows 7, 1,5GB[/SIZE]
[SIZE=2]Ubuntu webserver: 1GB[/SIZE]
[SIZE=2]Ubuntu fileserver: 512MB[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]In total that is 3GB, thought.... since ESXI takes some too, u get closer to the 4 than the 3 GB of ram usage.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]When u turn on one more VM, the amount of RAM in the machine is insuffient, meaning that ESXI starts making SWAP memory on the HDD.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]If i had a SSD in it, i would not have seen preformance loss, thought with a "normal" HDD, i did see alot of preformance loss, expecially while loading alot of small images (larger images did not seem to be a big problem)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]I hope i can help anyone else, by posting my result. I have ordered another 4 GB of RAM, so i can add one more VM and will keep about 2 GB of RAM unused :) just for in case[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]JBtje[/SIZE]

---

