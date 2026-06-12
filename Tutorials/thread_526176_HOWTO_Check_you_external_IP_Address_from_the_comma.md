---
title: "HOWTO: Check you external IP Address from the command line"
date: 2007-08-15
forum: Tutorials
---

### Post by motin on 2007-08-15
I hope you know about the possibility to find out your IP Address by using visiting the site [http://www.whatismyip.com](http://www.whatismyip.com) . I needed a way to check this from the command line and this is what I came up with:

For this, you need the packages wget, grep and sed so make sure you have them by checking for them in Synaptic or running the following in a terminal:
```
sudo apt-get install wget grep sed
```

Then, as long as whatismyip.com prints out the IP-Address in the HTML page title, you can use this:

Create shell script:
```
cd ~
mkdir bin
nano  bin/whatismyip.sh
```

Insert this into nano (Copy, then paste into nano by pressing Ctrl + Shift + V):
```

#!/bin/bash

echo Your external IP Address is:
wget http://Www.whatismyip.com -O - -o /dev/null | grep '<TITLE>' | sed -r 's/<TITLE>WhatIsMyIP\.com \- //g' | sed -r 's/<\/TITLE>//g'

exit 0

```
(You can also use gedit instead of nano, but I chose to use nano above in case this is done through a remote text-based connection)

Press Ctrl + O, Enter, Ctrl + X, then run:
```
chmod u+x bin/whatismyip.sh
```

Now you can check your external IP Address by running:
```
~/bin/whatismyip.sh
```
...in a terminal.

---

### Post by defconoii on 2007-08-15
dude, kick *** little app, got any more little bash scripts like this? 
good work, ive been looking for something like this
defcon

---

### Post by GFree678 on 2007-08-16
Woah. I asked for something like these nearly half a year ago (with another account) and go no response. I guess I should be glad someone finally had an answer. :)

Thanks d00d!

---

### Post by Dragon45 on 2007-10-16
An update on this useful hack: As of this September, if you look at the source of WhatIsMyIP.com, you'll notice it says ```
Please set your code to scrape your IP from www.whatismyip.com/automation/n09230945.asp 
Please set your code to hit this page at a REASONABLE pace.
```

The full content of the script can now simply be 

```


#!/bin/bash

wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null

exit 0

```
Or, if you want it to keep wget from logging, and arrange the output so that the IP address isn't squashed up against the prompt:

```


#!/bin/bash

wget www.whatismyip.com/automation/n09230945.asp -O - -q
echo

exit 0

```

---

### Post by tturrisi on 2007-10-16
No need to apt-get wget, grep or sed, they are included in the base install.
The below also work well in Conky.

You can also use dyndns.org for wan ip address:
```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' 
```

lan ip address:
```
ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}' 
```

---

### Post by lemot66 on 2007-10-16
Thanks everyone, this is very helpful!  Both of your contributions make this nice little script for me:


```
#!/bin/bash

echo "\nExternal IP:  "
wget www.whatismyip.com/automation/n09230945.asp -O - -q
echo "\n\n Internal IP: "
ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
echo

exit 0
```

---

### Post by c8h10n4o2 on 2007-11-01
I know this is an old post but I would like to say thanks for the help. I've been trying to figure out how to traceroute. This is much simpler.

Just in case anyone wants it, I've created the following PERL script I keep in cron to check my IP and compare it to the previous and email me if it has changed.

```

#!/usr/bin/perl
$IP_FILE = "/home/c8h10n4o2/scripts/ipemail.result";
my $newip = `wget www.whatismyip.com/automation/n09230945.asp -O - -q`;
my $oldip = getoldip();
my $send_to = "To: me\@me.com\n";
my $reply_to = "Reply-to: me\@me.com\n"; 
my $from = "From: me\@me.com\n";
my $subject = "Subject: IP Address: $newip\n"; 
my $content = "<h1>$newip</h1>"; 
if($newip ne $oldip)
{
   writenewip($newip);
   unless(open (MAIL, "|/usr/sbin/sendmail me\@me.com")) 
   {
      print "error.\n";
      warn "Error starting sendmail: $!";
   }
   else{
      print MAIL $from;
      print MAIL $reply_to;
      print MAIL $subject;
      print MAIL $send_to;
      print MAIL "Content-type: text/html\n\n";
      print MAIL $content;
      close(MAIL) || warn "Error closing mail: $!";
      print "Mail sent\n";
   }
}

sub writenewip
{
   my($newip) = @_;
   print ("new IP = $newip\n");
   open IPFILE, ">$IP_FILE";
   print IPFILE "$newip\n";
   close IPFILE;
}

sub getoldip
{
   open IPFILE, "$IP_FILE";
   my($line) = 0;
   while ( <IPFILE> )
   {
      chomp;
      $line = $_;
   }
   close IPFILE;
   return($line);
}


```

---

### Post by Scimu on 2007-11-02
Nice thanks for this.. Works perfect the shorter code! :D

---

### Post by cokenl78 on 2007-11-14
This is a little bash script I made to email me and my friend (in CC, -c option in mail command) about IP changes for DNS record changes. Includes a logger to check if the cronjob is indeed running every day.
```

#!/bin/bash

IPFILE=/etc/ipaddress

CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)

MAIL_FROM="From: noreply@domain.org"

if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE

        MAIL_SUBJECT="IP address for domain.org changed"
        MAIL_BODY="The IP address for domain.org has been changed to $CURRENT_IP. Please change the nameserver records accordingly."

        echo $MAIL_BODY | mail -a "$MAIL_FROM" -s "$MAIL_SUBJECT" -c secondmoo@cows.org foobar@domain.org
        logger -t ipcheck -- IP changed to $CURRENT_IP
else
        logger -t ipcheck -- No IP change
fi

```

---

### Post by skipx on 2008-09-14
I now use:

```

#!/bin/bash
wget http://Www.whatismyip.org -O - -o /dev/null
echo
exit 0

```


Best!

---

### Post by Jivicin on 2008-09-15
Try this:

```
curl www.whatismyip.org

```

---

### Post by SkonesMickLoud on 2008-09-18
The last 2 posters should hit:

[http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp)

Especially if you're using this in Conky.  No need to put undue strain on their servers, and it doesn't have a restriction (or it has a much higher one) on hits in a specific time period.

---

### Post by kevdog on 2008-09-19
What about this:

wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'

That seems simple enough for me.  That will give you your external IP address.

---

### Post by Skalman5 on 2008-10-05
This is how i did it:

```
sudo gedit /bin/whatsmyip.sh
```

Paste the following:

```
#!/bin/bash

echo
echo "---External IP:  "
wget www.whatismyip.com/automation/n09230945.asp -O - -q
echo
echo
echo "---Internal IP: "
ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
echo

exit 0
```

Press save and exit then:
```
sudo chmod 777 /bin/whatsmyip.sh
```

next:
```
sudo gedit /home/**"your username here"**/.bashrc
```

Paste this in the end of .bashrc file:

```
# Own Scripts
	alias whatsmyip='/bin/whatsmyip.sh'
```

log out and in again.

Now you can see both your internal and external ip by typing:

```
whatsmyip
```

You can alter the alias in the .bashrc file to whatever you feel like if you're inconvenient with "whatsmyip"

---

### Post by lindylex on 2008-10-30
Thanks, tturrisi for your example.

---

### Post by casey02 on 2008-11-08
Hi All,

I tried to run the script,  but sendmail is not working !

Can anybody point me to the right direction ??

The error is like the following :

Error starting sendmail: No such file or directory at /usr/bin/email_ip.sh line 17.

TQ for your help in advance.

Regards

Casey


> **c8h10n4o2 said:**
> I know this is an old post but I would like to say thanks for the help. I've been trying to figure out how to traceroute. This is much simpler.

Just in case anyone wants it, I've created the following PERL script I keep in cron to check my IP and compare it to the previous and email me if it has changed.

```

#!/usr/bin/perl
$IP_FILE = "/home/c8h10n4o2/scripts/ipemail.result";
my $newip = `wget www.whatismyip.com/automation/n09230945.asp -O - -q`;
my $oldip = getoldip();
my $send_to = "To: me\@me.com\n";
my $reply_to = "Reply-to: me\@me.com\n"; 
my $from = "From: me\@me.com\n";
my $subject = "Subject: IP Address: $newip\n"; 
my $content = "<h1>$newip</h1>"; 
if($newip ne $oldip)
{
   writenewip($newip);
   unless(open (MAIL, "|/usr/sbin/sendmail me\@me.com")) 
   {
      print "error.\n";
      warn "Error starting sendmail: $!";
   }
   else{
      print MAIL $from;
      print MAIL $reply_to;
      print MAIL $subject;
      print MAIL $send_to;
      print MAIL "Content-type: text/html\n\n";
      print MAIL $content;
      close(MAIL) || warn "Error closing mail: $!";
      print "Mail sent\n";
   }
}

sub writenewip
{
   my($newip) = @_;
   print ("new IP = $newip\n");
   open IPFILE, ">$IP_FILE";
   print IPFILE "$newip\n";
   close IPFILE;
}

sub getoldip
{
   open IPFILE, "$IP_FILE";
   my($line) = 0;
   while ( <IPFILE> )
   {
      chomp;
      $line = $_;
   }
   close IPFILE;
   return($line);
}


```

---

### Post by casey02 on 2008-11-08
Bro,

I just realize that I did not have sendmail install and now it show the IP and show Email sent also !!

However, the problem now is that I did not get the mail in my gmail a/c ??

Not in the SPAM box either !

Can someone shed some light !

TQ and regards,

Casey

---

### Post by caco on 2008-11-12
Nice work folks...

try the code below just for fun ... it appears/seems better formatted.

#!/bin/bash
echo
echo " External IP: `wget [www.whatismyip.com/automation/n09230945.asp](www.whatismyip.com/automation/n09230945.asp) -O - -q echo `" 
echo " Internal IP: `ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`"
echo
exit 0

Keep up the good deeds:)

---

### Post by Salute on 2009-06-02
looking for the same thing I found that I can put this in my .bashrc file
alias out='wget -qO - [http://cfaj.freeshell.org/ipaddr.cgi](http://cfaj.freeshell.org/ipaddr.cgi)'
(obviously because 'in' is ifconfig)

You all have some nice scripts too, thanx

---

### Post by JorgeGhersa on 2010-11-01
Hi, I'm raising this topic back to life because I'm too proud of the simplest thing I just made up.

I wanted to always know what was the wan IP of my home PC when I'm using my netbook anywhere else. And since I'm using Ubuntu One to instantly share small files from both, this is what I came up with:

1) Run *crontab -e* to edit your crontab file (cron runs commands periodically as ordered).
2) Add this line at the bottom:
** * * * * wget -rnH [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -P /home/USER/U1-SHARED-FOLDER*

3) Save and enjoy...

...obviously replacing "user" and "U1-Shared-Folder" for your real folders.
The asteriscs at the beginning mean "every minute/hour/day/month/day-of-week". Since Ubuntu One will only sync it out when the local file changes in content, this doesn't create any distinguishable resource drain, at least on my PC here. 
You can set proper numbers if you want to go slower: for example 0 * * * 1 for hourly, o'clock, but only on mondays... Choice is yours.


Then, on every PC that shares the Shared Folder, there will be a copy of and "index.html" file with the IP stored, adapting its content in little more than a minute of delay...

---

### Post by scorp123 on 2010-11-14
Sorry for necro-posting ... but in case someone finds this via Google just as I did, I'd like to add this little bit:

I am a Dropbox user ... and Dropbox also exists for iPhone and Android phones ... so why not use Dropbox to record the external IP address? I could then check the IP via the web interface, or via my iPhone, or via any of my other computers that I sync with. Sounds like a good idea, doesn't it? :)

Based on the previously made suggestions by all the other posters here (thanks guys!) I have added this nifty little cronjob to one of my "green PC's" (it only consumes around 10 Watts) that is constantly running, so it's a good candidate for this job:

```
 */15 * * * * /usr/bin/wget http://www.whatismyip.com/automation/n09230945.asp -O - -q > /home/YourUserNameHere/Dropbox/ExternalIP/`hostname`.txt 
```

So this cronjob will run every 15 minutes and then output the external IP the system sees into a file that is located inside my Dropbox folder. The file will be named after the hostname this cronjob is running from.

So I could have this cronjob on multiple systems and they would all report their external IP address back to me, no matter where they are.

I hope this will be useful for anyone who finds this via Google ...  :)

---

### Post by Chazz44able on 2010-11-26
> **motin said:**
> I hope you know about the possibility to find out your IP Address by using visiting the site [http://www.whatismyip.com](http://www.whatismyip.com) . I needed a way to check this from the command line and this is what I came up with:

For this, you need the packages wget, grep and sed so make sure you have them by checking for them in Synaptic or running the following in a terminal:
```
sudo apt-get install wget grep sed
```

Then, as long as whatismyip.com prints out the IP-Address in the HTML page title, you can use this:

Create shell script:
```
cd ~
mkdir bin
nano  bin/whatismyip.sh
```

Insert this into nano (Copy, then paste into nano by pressing Ctrl + Shift + V):
```

#!/bin/bash

echo Your external IP Address is:
wget http://Www.whatismyip.com -O - -o /dev/null | grep '<TITLE>' | sed -r 's/<TITLE>WhatIsMyIP\.com \- //g' | sed -r 's/<\/TITLE>//g'

exit 0

```
(You can also use gedit instead of nano, but I chose to use nano above in case this is done through a remote text-based connection)

Press Ctrl + O, Enter, Ctrl + X, then run:
```
chmod u+x bin/whatismyip.sh
```

Now you can check your external IP Address by running:
```
~/bin/whatismyip.sh
```
...in a terminal.





this is all well and good... But surely you can just go on to remote desktop and it shows you there!

---

### Post by Cheesehead on 2010-11-26
All the cron-based approaches are a bit troubling - it can be rude to add unecessary load to somebody else's server. If you're not changing networks (laptop), you can also simply query your router. For me, it's about a second faster than using a foreign server.

```
wget -O - -o /dev/null http://192.168.1.1/Status_Router.asp --user=myRouterUserName --password=myRouterPassword | grep 'var wan_ip' | cut -d'"' -f2

# wget             The command
# -O -              Output the result to the screen, not a file
# -o /dev/null    Strip the progress wget progress bars
# http://192.168.1.1/Status_Router.asp    Use your appropriate router URL
# --user=myRouterUserName                 Router authentication
# --password=myRouterPassword 
# | grep 'var wan_ip' | cut -d'"' -f2           Extract the IP address from the returned page


```
Of course, the URL and grep string and formatting will vary by router.
And it breaks when you change your router.
And your router password is being sent in plain text.
But in some situations that's preferable to repeatedly querying foreign IP addresses.




Another approach to reduce your external bandwidth is to only check upon network-up (place a link to your script in /etc/network/if-up.d), though this only works if your external IP address doesn't change during your workday.

---

### Post by karthick87 on 2010-11-26
Why cant people use **ifconfig **to see their external ip?It takes only a couple of seconds.

---

### Post by Cheesehead on 2010-11-26
If you are behind a router, ifconfig will only return the IP address on that network, which may not be the one you want.

For example, if Uncle Claudio phones me and asks me to troubleshoot his problem, I must give him the IP address of my router in order to create the reverse-VNC connection. Ifconfig will give me the 192.*.*.* issued by my router, but he needs the public IP of my router, 75.*.*.*, issued by my ISP.

---

### Post by karthick87 on 2010-11-27
This is my output for** [COLOR=Red]ifconfig[/COLOR]** command it show's my public ip

```
karthick@Ubuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4956916 (4.9 MB)  TX bytes:1364829 (1.3 MB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:263899 (263.8 KB)  TX bytes:263899 (263.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:[COLOR=Red]117.206.91.236 [/COLOR] P-t-P:117.206.80.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:7522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4765234 (4.7 MB)  TX bytes:1183798 (1.1 MB)
```

---

### Post by rbishop on 2010-11-27
karthick87 that is all well and good, if you have a PPP connection setup on your machine.  Most users just have a router or modem that handle the login process for them.  Many ISP's will pre-configure modems to handle the PPP connection.  Many Cable company's don't even have logins for their network.

---

### Post by karthick87 on 2010-11-27
@rbishop Thank you i got it now.

---

### Post by scorp123 on 2010-11-27
> **karthick87 said:**
> Why cant people use **ifconfig **to see their external ip?  Good joke :D

> **karthick87 said:**
>  ppp0      Link encap:Point-to-Point Protocol  You know, in some regions of the world they have moved beyond PPP and dial-up like 12 or so years ago. ;)

You'd get a DSL or cable modem from your ISP (depending on your connection type) and that router/modem most of the time is also pre-configured to serve as DHCP server. So all you see via "ifconfig" is most likely that you got some RFC1918 private range address, usually 192.168.1.*-something, and that's it.

So in order to find out your external IP (= the one behind your router/cable modem) you have to be a bit more creative than just using "ifconfig" :D

---

### Post by karthick87 on 2010-11-27
@scorp123 Thanks for the information :)

---

### Post by scorp123 on 2010-11-27
> **Cheesehead said:**
> All the cron-based approaches are a bit troubling - it can be rude to add unecessary load to somebody else's server. Not if you do it right. And web sites such as whatismyip.com explictly don't mind if you query their site. They even give instructions on how to do it via scripting:

[http://forum.whatismyip.com/f14/our-automation-rules-t241/](http://forum.whatismyip.com/f14/our-automation-rules-t241/)

And I bet they have firewalls and what not in place to prevent anyone from overdoing it.

So if you follow their instructions and let your automated script hit this URL: [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp)

... then nothing bad should happen. That URL will only spit out your IP address and nothing more, so the traffic that a script would be causing is very very small.

---

### Post by alfplayer on 2011-02-08
Also,

> wget -qO - icanhazip.com

or

> curl icanhazip.com

I didn't find info on how often it can be used, but [*here*]("http://rackerhacker.com/icanhazip-com-faq/") it reads: "visitors can use the response in scripts or other applications very easily".

Supports IPv6 too.

---

### Post by bwallum on 2011-08-01
automation url is now:-

[http://automation.whatismyip.com/n09230945.asp](http://automation.whatismyip.com/n09230945.asp)

They request 300 seconds/5 minutes between automated enquiries.

---

### Post by SoFl W on 2011-08-01
Finding old threads I see!  Changes to the original code:

```
#!/bin/bash
#
#  From: http://ubuntuforums.org/showthread.php?t=526176
#
echo Your external IP Address is:
wget http://automation.whatismyip.com/n09230945.asp -O - -o /dev/null
echo 
exit 0
```

Posting that change is useful because my conky script no longer worked with whatsmyip.  This should fix it.

---

### Post by tension_ on 2011-08-03
Work for me too  ty all :)

---

### Post by kristianz on 2012-02-14
I added this to my crontab at a headless, remote server, so that I get confirmation once every morning that it's up and online, and how to reach it:

```
echo Internal `ifconfig eth0 |grep "inet addr" |awk '{print $2}'`, external addr:`wget http://automation.whatismyip.com/n09230945.asp -O - -o /dev/null` | mail myemail@example.com -s IP addresses
```

---

### Post by Khayyam on 2012-02-22
necromancy .. mia culpa!

I see alot of 'grep | cut | awk' etc .. all of this can by achieved with one command:

```
awk '/inet addr:/{print (substr($2,6,15))}' <(ifconfig eth0)
```

or similarly to preface it with 'eth0 IP:'

```
awk '/inet addr:/ {print "eth0 IP: "(substr($2,6,15))}' <(ifconfig eth0)
```

HTH ... khay

---

### Post by kitsaros on 2012-02-23
I have made a WAN IP Logger years ago for windows and for Linux (gtk2 is needed).
I know that it is not command line but you might fit at your needs.

[IMG]http://www.trustfm.net/GeneralTools/Images/WANIPLoggerKubuntu.png[/IMG]

The main page is here : 
[http://www.trustfm.net/GeneralTools/SoftwareWANIPLogger.php](http://www.trustfm.net/GeneralTools/SoftwareWANIPLogger.php)
And the download page is here : 
[http://www.trustfm.net/GeneralTools/SoftwareWANIPLogger.php?page=Download](http://www.trustfm.net/GeneralTools/SoftwareWANIPLogger.php?page=Download)

It is completely free for personal and commercial use. 

Let me know if you have problems.

---

### Post by jacobt777 on 2012-04-24
I see that this post has been answered in various replies, but I thought it wouldn't hurt to add another option.:p

You can also use wget with ipogre.com. 
```
wget -q -O - ipogre.com/linux.php|sed -e 's/.*IP Address: //' -e 's/<.*$//'
```

---

### Post by stinkeye on 2012-04-25
```
curl ifconfig.me
```

---

### Post by linuxball on 2012-11-20
> **Khayyam said:**
> necromancy .. mia culpa!

I see alot of 'grep | cut | awk' etc .. all of this can by achieved with one command:

```
awk '/inet addr:/{print (substr($2,6,15))}' <(ifconfig eth0)
```

or similarly to preface it with 'eth0 IP:'

```
awk '/inet addr:/ {print "eth0 IP: "(substr($2,6,15))}' <(ifconfig eth0)
```

HTH ... khay

Why invoking awk or any external command if plain POSIX shell already can do this:

```
ifconfig eth0|{ IFS=' :';read r;read r r a r;echo $a;}
```

or similarly to preface it with 'eth0 IP:'

```
ifconfig eth0|{ IFS=' :';read r;read r r a r;echo "eth0 IP: $a";}
```

Ciao - linuxball

---

### Post by stinkeye on 2012-11-20
> **linuxball said:**
> Why invoking awk or any external command if plain POSIX shell already can do this:

```
ifconfig eth0|{ IFS=' :';read r;read r r a r;echo $a;}
```

or similarly to preface it with 'eth0 IP:'

```
ifconfig eth0|{ IFS=' :';read r;read r r a r;echo "eth0 IP: $a";}
```

Ciao - linuxball
Just gives my LAN address.

---

### Post by linuxball on 2012-11-21
> **stinkeye said:**
> Just gives my LAN address.

You are right. My message was just a reply to message [#37]("http://ubuntuforums.org/showpost.php?p=11709741&postcount=37") (which admittedly was off-topic) of this thread.

My point was that the built-in features of the used POSIX shell mostly suffice to do post-processing. E.g. two examples which match the topic:
```
a=$(curl -s checkip.dyndns.org); a=${a##* }; echo ${a%%<*}
```
```
a=$(curl -s ipogre.com/linux.php); a=${a##* }; echo ${a%%<*}
```
The above examples will work in /bin/bash and /bin/sh (dash and other POSIX-compliant shells).

Instead of "curl -s" one can use "wget -qO -".

Ciao - linuxball

---

### Post by jacobt777 on 2012-12-18
IP Address:

```
curl ipogre.com 
```

Hostname:

```
curl ipogre.com/host
``` 

User-agent (browser information):

```
curl ipogre.com/ua 
```

Client Source Port (What port is the client using to access ipogre.com)

```
curl ipogre.com/port 
```

---

### Post by swajime on 2013-04-19
> **linuxball said:**
> You are right. My message was just a reply to message [#37]("http://ubuntuforums.org/showpost.php?p=11709741&postcount=37") (which admittedly was off-topic) of this thread.

My point was that the built-in features of the used POSIX shell mostly suffice to do post-processing. E.g. two examples which match the topic:
```
a=$(curl -s checkip.dyndns.org); a=${a##* }; echo ${a%%<*}
```
```
a=$(curl -s ipogre.com/linux.php); a=${a##* }; echo ${a%%<*}
```
The above examples will work in /bin/bash and /bin/sh (dash and other POSIX-compliant shells).

Instead of "curl -s" one can use "wget -qO -".

Ciao - linuxball

exquisitely elegant ... thanx for teaching me ## && %% :)

---

### Post by swajime on 2013-04-19
That is good for this:
```
a=$(curl -s checkip.dyndns.org); a=${a##*\.}; a=${a%%<*};color="\033[38;5;${a}m";plain="\033[0m";export PS1="\[${color}\]${PS1}\[${plain}\]"
```

---

### Post by cutesar on 2013-12-03
> **motin said:**
> I hope you know about the possibility to find out your IP Address by using visiting the site [http://www.whatismyip.com](http://www.whatismyip.com) . I needed a way to check this from the command line and this is what I came up with:

For this, you need the packages wget, grep and sed so make sure you have them by checking for them in Synaptic or running the following in a terminal:
```
sudo apt-get install wget grep sed
```

Then, as long as whatismyip.com prints out the IP-Address in the HTML page title, you can use this:

Create shell script:
```
cd ~
mkdir bin
nano  bin/whatismyip.sh
```

Insert this into nano (Copy, then paste into nano by pressing Ctrl + Shift + V):
```

#!/bin/bash

echo Your external IP Address is:
wget http://Www.whatismyip.com -O - -o /dev/null | grep '<TITLE>' | sed -r 's/<TITLE>WhatIsMyIP\.com \- //g' | sed -r 's/<\/TITLE>//g'

exit 0

```
(You can also use gedit instead of nano, but I chose to use nano above in case this is done through a remote text-based connection)

Press Ctrl + O, Enter, Ctrl + X, then run:
```
chmod u+x bin/whatismyip.sh
```

Now you can check your external IP Address by running:
```
~/bin/whatismyip.sh
```
...in a terminal.

Well ! the following code is used to find ip address : 

[COLOR=#000000]ifconfig  | **grep** -E 'inet.[0-9]' | **grep** -v '127.0.0.1' | **awk** '{ print $2}'[/COLOR][COLOR=#ff0000]

[/COLOR][COLOR=#000000]Usually, i use [/COLOR][[COLOR=#0000cd]Ip-details.com[/COLOR]]("http://www.ip-details.com/")[COLOR=#0000cd] [/COLOR][COLOR=#000000] to get extarnal ip address . 
[/COLOR][COLOR=#ff0000]



[/COLOR]

---

