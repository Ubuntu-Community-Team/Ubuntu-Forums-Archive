---
title: "Snort inline + mysql + base"
date: 2010-04-11
forum: Security
---

### Post by bell811 on 2010-04-11
Hello,
I am currently building a firewall for our network. I'm using ubuntu with shorewall and snort inline. And I'm also trying to get snort to use mysql for logging. 

My problems : 

1- Snort does not log anything in my database
2- When I look at snort output it doesn't seems to generate any alert even when I port scan my firewall
3- So I'm not sure if snort inline is actually working! 

What I did :
- I compiled snort with the inline and mysql option
- I created rules in my shorewall to send packet to queue, example :
```

QUEUE   net     $FW     tcp     80

```- I used oinkmaster to change alert to drop in snort rules
- I changed the output database line in snort.conf :
```

output database: log, mysql, user=root password=XXXXXX dbname=snort host=localhost

```And I started snort :
```

snort -Q -c /etc/snort/snort.conf -v  

...
database: compiled support for (mysql)
database: configured to use mysql
database: schema version = 107
database:           host = localhost
database:           user = root
database:  database name = snort
database:    sensor name = unknown:NULL
database:      sensor id = 1
database:  data encoding = hex
database:   detail level = full
database:     ignore_bpf = no
database: using the "log" facility
...
        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.5.3 (Build 124) inline 
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/snort/snort-team
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 7.9 2009-04-11

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.12  <Build 17>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 2>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 8>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 3>
           Preprocessor Object: SF_DCERPC  Version 1.1  <Build 5>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 12>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 2>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 3>
           Preprocessor Object: SF_Dynamic_Example_Preprocessor  Version 1.0  <Build 1>
Not Using PCAP_FRAMES
Initializing Inline mode 
building cached socket reset packets

```Seems to be working right.
I even get some output when I go on the Base webpage: 
```

04/11-15:48:55.400431 192.168.2.44:35307 -> 192.168.2.45:80
TCP TTL:64 TOS:0x0 ID:1265 IpLen:20 DgmLen:60 DF
******S* Seq: 0x24AEF3B8  Ack: 0x0  Win: 0x16D0  TcpLen: 40
TCP Options (5) => MSS: 1460 SackOK TS: 24770377 0 NOP WS: 6 

```But nothing is log in the database...
I attached a screenshot of BASE.
Any help would be great thanks

---

### Post by bodhi.zazen on 2010-04-11
From what you have posted everything seems to be working fine.

You changed "alert" to "drop", if you want to see alerts, change drop back to alert.

Unless you know what you are doing with snort, I would think snort inline is not such a great idea, snort generates a ton of false negatives and at a minimum you should tune your rules first.

---

### Post by bell811 on 2010-04-11
Thanks for your answer.
> **bodhi.zazen said:**
> 
You changed "alert" to "drop", if you want to see alerts, change drop back to alert.

Well at first I started snort with the alert setting and it never generated any alert when I port scanned it. 
And if I put drop instead of alert snort isn't going to log any alert? Is there a way to put both setting. I would like to know if it indeed dropped a packet. 

And snort did not log anything... not the alert not the regular log.

> **bodhi.zazen said:**
> 
Unless you know what you are doing with snort, I would think snort inline is not such a great idea, snort generates a ton of false negatives and at a minimum you should tune your rules first.

Thanks for the advice.I used snort many time in the past but never inline, and never with shorewall and never with mysql for the logs. This firewall is going to be in front of an email server/BlackBerry enteprise server. With very few open ports. The management of false positive will be, I think not to hard to handle (If again I have a log of those false positive!)

---

### Post by bodhi.zazen on 2010-04-11
There is nothing wrong with your snort installation, you can see for yourself in the output.

If you are not getting alerts you can wait or gnerate some of your own.

Logging a port scan would be dependent on your snort rules.

Hit snort with something else if you need to.

---

### Post by bell811 on 2010-04-11
But why is there no log at all in my database. As you can see in my base screen shot it looks like there as been no traffic at all... and there was.
Thanks

---

### Post by bodhi.zazen on 2010-04-11
> **bell811 said:**
> But why is there no log at all in my database. As you can see in my base screen shot it looks like there as been no traffic at all... and there was.
Thanks

hard to guess. Either your rules do not generate alerts for the port scanner you are using, are you scanning from your local host ?

If you would like to see some error messages, stop your mysql server and start snort on the command line.

My point is from what you posted snort , mysql, and bare are functioning as expected.

Do you have your old rule set ? Use the old rule set that behaves as you expect to "test" snort. Assuming that works, you will have to debug your snort rules set.

---

### Post by bodhi.zazen on 2010-04-11
The only other consideration, snort can loose it's connection with mysql.

Log into base, clear the data base, then re-start snort.

---

### Post by bell811 on 2010-04-12
Thanks for your answers.
I have some more question. 

I want this machine to act as a firewall/gateway/IPS on my network. Lets say I want snort to process to packet I want to forward to a computer inside my local network ... How do I do that?

Example port 21 : 
For forwarding:

DNAT   
DNAT       net      loc:192.168.1.5  tcp      21

For sending to snort to process

QUEUE      net      loc      tcp      21

But the second one won't forward.
Thanks

---

### Post by bodhi.zazen on 2010-04-12
So I assume snort is working as you expect ?

As I indicated previously, you will probably need to write a few rules for snort. This is a very esoteric question for these forums and I suggest you ask on the snort forums.

google also has a few links to a few more detailed how-to's on snort inline, although it depends on how you are using snort (honeypot ?).

It seems to me you are going about this the hard way, I would simply use itpables (you can probably accomplish what you want with a few "simple" rules in iptables) + fail2ban (if for some reason iptables is not sufficient).

---

### Post by srinu.mca5 on 2011-03-08
Hello friends,

     I installed snort in my system ad IDS..Now I want to configure IPS in that same system..Is it possible with snort..

My doubt is : how can i change snort as snort inline and alert to drop.

_*I installed snort with apt-get install snort command*_

---

### Post by CNM on 2011-03-22
Hi ,

Actually i just started using snort
i followed this article which i found very useful :
[Installing SNORT on Ubuntu 10.04]("http://it.thelibrarie.com/weblog/2010/06/installing-snort-on-ubuntu-10-04/")
even though i am using ubuntu server 10.10

however at the end of the article they mentioned that if you ping your server something should appear on the "base" web interface 
however nothing is appearing there ... i have the same screen shot that exist at the beginning of the thread ... nothing detected ...

any help would be highly appreciated :)

Thanks

---

### Post by bodhi.zazen on 2011-03-22
> **CNM said:**
> Hi ,

Actually i just started using snort
i followed this article which i found very useful :
[Installing SNORT on Ubuntu 10.04]("http://it.thelibrarie.com/weblog/2010/06/installing-snort-on-ubuntu-10-04/")
even though i am using ubuntu server 10.10

however at the end of the article they mentioned that if you ping your server something should appear on the "base" web interface 
however nothing is appearing there ... i have the same screen shot that exist at the beginning of the thread ... nothing detected ...

any help would be highly appreciated :)

Thanks

It depends on your snort rules, but I doubt a simple ping will trigger an alert.

---

### Post by CNM on 2011-03-22
> **bodhi.zazen said:**
> It depends on your snort rules, but I doubt a simple ping will trigger an alert.

actually i just tweaked some stuff and it detected something ... not much of an alert though ...
i think i will try to use snort it in NIDS mode and use backtrack to simulate some attacks and see what i can get ...
any comments on that ? is there other scenarios i can try to get more revealing/interesting alerts ?

---

### Post by bodhi.zazen on 2011-03-22
> **CNM said:**
> actually i just tweaked some stuff and it detected something ... not much of an alert though ...
i think i will try to use snort it in NIDS mode and use backtrack to simulate some attacks and see what i can get ...
any comments on that ? is there other scenarios i can try to get more revealing/interesting alerts ?

If you have a personal or low traffic web server you will probably not see much action.

Give it time and you will see some interesting stuff or place your snort sensor on the other side of your router.

---

### Post by CNM on 2011-03-22
> **bodhi.zazen said:**
> If you have a personal or low traffic web server you will probably not see much action.

Give it time and you will see some interesting stuff or place your snort sensor on the other side of your router.

actually i am implementing it as a project 
so i have to force some interesting stuff to pop in any way i can :P lol
any idea on how to do that ?

---

### Post by bodhi.zazen on 2011-03-22
Well, read the snort rules or fire up somethign such as OpenVAS.

[http://www.openvas.org/](http://www.openvas.org/)

The "problem" is much of the tools used by openvas are not going to be in the Ubuntu repos, but you can download the source code ...

---

### Post by CNM on 2011-03-22
> **bodhi.zazen said:**
> Well, read the snort rules or fire up somethign such as OpenVAS.

[http://www.openvas.org/](http://www.openvas.org/)

The "problem" is much of the tools used by openvas are not going to be in the Ubuntu repos, but you can download the source code ...


Openvas is included in BackTrack ...
The issue is : i have snort , a 3com switch and internet and i have to a way to apply snort in order to see interesting stuff or to try and protect a certain "Server" which can be a VM for instance ... since i'm also running snort on a VM ...
Currently i am reading Snort's manual ... yeah the 200 pages manual :P lol
Where does the rules reside though ?
in the /etc/snort/snort.conf there is the general config right ? not the rules ...
is it easy to write new rules ?
one last question ... dunno if you worked with snort before ... VRT signatures cannot be downloaded unless subscribed ? or does subscription allow them to be downloaded automatically while non subscribed users can download and apply them manually ?
i didn't quite get the way Snort's rules are updated ... :/
i heard of something called Oinkmaster ... didn't try it though ...

Thanks for the help mate :)

---

### Post by bodhi.zazen on 2011-03-22
> **CNM said:**
> Openvas is included in BackTrack ...
The issue is : i have snort , a 3com switch and internet and i have to a way to apply snort in order to see interesting stuff or to try and protect a certain "Server" which can be a VM for instance ... since i'm also running snort on a VM ...
Currently i am reading Snort's manual ... yeah the 200 pages manual :P lol
Where does the rules reside though ?
in the /etc/snort/snort.conf there is the general config right ? not the rules ...
is it easy to write new rules ?
one last question ... dunno if you worked with snort before ... VRT signatures cannot be downloaded unless subscribed ? or does subscription allow them to be downloaded automatically while non subscribed users can download and apply them manually ?
i didn't quite get the way Snort's rules are updated ... :/
i heard of something called Oinkmaster ... didn't try it though ...

Thanks for the help mate :)

Yes you have to subscribe for snort rules. They are available for free if you subscribe, read the web page carefully (there is a 30 day wait).

Yes you can then oinkmaster as once you subscribe they will give you an oink code.

---

### Post by emiller12345 on 2011-03-22
A while back I came across this to test my ids/ips, its okay for what it does
IDSwakeup
[http://www.securityfocus.com/tools/1803](http://www.securityfocus.com/tools/1803)

---

### Post by CNM on 2011-03-23
> **bodhi.zazen said:**
> Yes you have to subscribe for snort rules.  They are available for free if you subscribe, read the web page  carefully (there is a 30 day wait).

Yes you can then oinkmaster as once you subscribe they will give you an oink code.

I'm still not sure how to use oinkmaster ...
i just registered and waiting for the confirmation email from snort ...

> **emiller12345 said:**
> A while back I came across this to test my ids/ips, its okay for what it does
IDSwakeup
[http://www.securityfocus.com/tools/1803](http://www.securityfocus.com/tools/1803)

Thanks a lot for the tip :)
will the packets generated have different IP source addresses , different MAC addresses ...
it similuates what kinds of attacks  ? 
web server attacks ? email attacks ?

---

### Post by CNM on 2011-03-23
> **bodhi.zazen said:**
> Yes you have to subscribe for snort rules. They are available for free if you subscribe, read the web page carefully (there is a 30 day wait).
 
Yes you can then oinkmaster as once you subscribe they will give you an oink code.
 
I'm a bit confused ...
after registering i can download any of these :
 
**_Snort v2.9_**
 
snortrules-snapshot-2904.tar.gz
17 Feb, 2011
 
 
snortrules-snapshot-2901.tar.gz
17 Feb, 2011
 
 
snortrules-snapshot-2902.tar.gz
17 Feb, 2011
 
 
snortrules-snapshot-2903.tar.gz
17 Feb, 2011
 
 
 
 
what's the difference ? 
since all of them have the same release date ... :/

---

### Post by bodhi.zazen on 2011-03-23
> **CNM said:**
> I'm a bit confused ...

Snort does have a bit of a learning curve and I am not sure how much or how little you know about penetration testing. You keep mentioning backtrack, which is a live CD, but I am not sure you know how to use these tools.

Google is your friend, you need to search and read. If you have a specific question, ask, but you are asking very broad questions and writing a response would look like this:

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

[http://ubuntuforums.org/showpost.php?p=9265804&postcount=6](http://ubuntuforums.org/showpost.php?p=9265804&postcount=6)

[http://www.snort.org/assets/166/snort_manual.pdf](http://www.snort.org/assets/166/snort_manual.pdf)

etc ...

---

### Post by CNM on 2011-03-23
> **bodhi.zazen said:**
> Snort does have a bit of a learning curve and I am not sure how much or how little you know about penetration testing. You keep mentioning backtrack, which is a live CD, but I am not sure you know how to use these tools.

Google is your friend, you need to search and read. If you have a specific question, ask, but you are asking very broad questions and writing a response would look like this:

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

[http://ubuntuforums.org/showpost.php?p=9265804&postcount=6](http://ubuntuforums.org/showpost.php?p=9265804&postcount=6)

[http://www.snort.org/assets/166/snort_manual.pdf](http://www.snort.org/assets/166/snort_manual.pdf)

etc ...

loooooool
i already read those :P
and i'm half through the manual :)
what was confusing me is the naming of the update packaged i can download
regardless if i will use oink or not , why is there different snapshots for the updates although all done the same day ...
which one to choose ? i just go with the one that has the highest number ? there must be something i'm missing ...

---

### Post by bodhi.zazen on 2011-03-23
Those are versions of snort. Your rule set should match your version of snort.

[http://www.snort.org/vrt/docs/ruleset_changelogs/changes-2011-03-22.html](http://www.snort.org/vrt/docs/ruleset_changelogs/changes-2011-03-22.html)

---

### Post by CNM on 2011-03-23
> **bodhi.zazen said:**
> Those are versions of snort. Your rule set should match your version of snort.

[http://www.snort.org/vrt/docs/ruleset_changelogs/changes-2011-03-22.html](http://www.snort.org/vrt/docs/ruleset_changelogs/changes-2011-03-22.html)


ahhhh ok ok 
so by 2904 they meant version 2.9.0.4 ... etc
thanks mate :)

---

### Post by emiller12345 on 2011-03-23
> Thanks a lot for the tip :)
will the packets generated have different IP source addresses , different MAC addresses ...
it similuates what kinds of attacks  ? 
web server attacks ? email attacks ?You'll need to look through it, and from what I can remember, I think the script is broken, but it has ideas how you can set off alerts on your IDS.
If I had to guess how this is done manually, I might try 
```
echo -ne "GET /cgi-bin/ HTTP/1.0\r\n\r\n" | nc xxx.xxx.xxx.xxx 80
``` where xxx.xxx.xxx.xxx is an IP address of where you'd like to send this data.

---

### Post by CNM on 2011-03-23
> **emiller12345 said:**
> You'll need to look through it, and from what I can remember, I think the script is broken, but it has ideas how you can set off alerts on your IDS.> **emiller12345 said:**
> 
If I had to guess how this is done manually, I might try 
```
echo -ne "GET /cgi-bin/ HTTP/1.0\r\n\r\n" | nc xxx.xxx.xxx.xxx 80
``` where xxx.xxx.xxx.xxx is an IP address of where you'd like to send this data.
 
broken ? why you say so ?
as i recall using IDSakeup u can try :

```
 ./IDSwakeup <src addr> <dst addr> [nb] [ttl] 
```

A nice example would be :

```
 ./IDSwakeup  0  127.0.0.1  1  
```

i ran this from the local VM while launching snort in sniffing mode
then i ran the same command from another VM on the same network and changed the 127.0.0.1 to the snort server's IP with snort in sniffing mode 

However nothing significant is shown on BASE ...

any ideas ? :/

---

### Post by emiller12345 on 2011-03-23
You may want to run wireshark or some other network sniffer to make sure that your actually creating the packets that IDSwakeup says it is making.  IDSwakeup requires hping2 or hping3 so make sure you have it.  Also a scriptable way to download snort rules (once you have your oinkcode) is ```
#!/bin/bash
wget http://www.snort.org/reg-rules/snortrules-snapshot-2900.tar.gz/OINKCODEHERE -O snortrules-snapshot-2900-$(/bin/date +%Y%m%d%H%M).tar.gz -U "Mozilla/4.0"
``` Also, check the "alert" file that snort generates first, before you look into base. Second, check the mysql database to make sure the alerts are making their way there, lastly they should be showing up in BASE.

---

### Post by CNM on 2011-03-24
> **emiller12345 said:**
> You may want to run wireshark or some other network sniffer to make sure that your actually creating the packets that IDSwakeup says it is making. IDSwakeup requires hping2 or hping3 so make sure you have it. Also a scriptable way to download snort rules (once you have your oinkcode) is ```
#!/bin/bash
wget http://www.snort.org/reg-rules/snortrules-snapshot-2900.tar.gz/OINKCODEHERE -O snortrules-snapshot-2900-$(/bin/date +%Y%m%d%H%M).tar.gz -U "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)"
``` Also, check the "alert" file that snort generates first, before you look into base. Second, check the mysql database to make sure the alerts are making their way there, lastly they should be showing up in BASE.

> **emiller12345 said:**
> You may want to run wireshark or some other network sniffer to make sure that your actually creating the packets that IDSwakeup says it is making. IDSwakeup requires hping2 or hping3 so make sure you have it. Also a scriptable way to download snort rules (once you have your oinkcode) is ```
#!/bin/bash
wget http://www.snort.org/reg-rules/snortrules-snapshot-2900.tar.gz/OINKCODEHERE -O snortrules-snapshot-2900-$(/bin/date +%Y%m%d%H%M).tar.gz -U "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)"
``` Also, check the "alert" file that snort generates first, before you look into base. Second, check the mysql database to make sure the alerts are making their way there, lastly they should be showing up in BASE.

will double check on the hping3 thingy ...
another thing , i edited the /etc/oink.conf and added this :
url = http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz

then i did :

```
sudo bash -c "/usr/share/oinkmaster/makesidex.pl /etc/snort/rules/ >/etc/autodisable.conf"
sudo oinkmaster -C /etc/oinkmaster.conf -C /etc/autodisable.conf -o /etc/snort/rules/
```

i am getting :
Loading /etc/oinkmaster.conf
Downloading file from http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz... 
/usr/local/bin/oinkmaster.pl: Error: could not download from http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz. Output from wget follows:

--2011-03-24 09:46:24--  http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz
Resolving [www.snort.org](www.snort.org)... 68.177.102.20
Connecting to [www.snort.org|68.177.102.20|:80](www.snort.org|68.177.102.20|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-03-24 09:46:25 ERROR 404: Not Found.


isn't the url correct ?
i have the version 2.9.0.4 and i am registered not subscribed


P.S
i also added oinkmaster.pl to /usr/local/bin and did :
```


oinkmaster.pl -o /etc/snort/rules

```

same error ...

---

### Post by EJeanmaire on 2011-03-24
You could also use inundator to generate fake snort alerts.

---

### Post by EJeanmaire on 2011-03-24
Did you log into snort.org and generate an oinkmaster code? Paste that code in the <code> section in the oinkmaster config, athen run oinkmaster under sudo, and you are all set.

> **CNM said:**
> will double check on the hping3 thingy ...
another thing , i edited the /etc/oink.conf and added this :
url = http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz

then i did :

```
sudo bash -c "/usr/share/oinkmaster/makesidex.pl /etc/snort/rules/ >/etc/autodisable.conf"
sudo oinkmaster -C /etc/oinkmaster.conf -C /etc/autodisable.conf -o /etc/snort/rules/
```

i am getting :
Loading /etc/oinkmaster.conf
Downloading file from http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz... 
/usr/local/bin/oinkmaster.pl: Error: could not download from http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz. Output from wget follows:

--2011-03-24 09:46:24--  http://www.snort.org/sub-rules/<code>/snortrules-snapshot-2904.tar.gz
Resolving [www.snort.org](www.snort.org)... 68.177.102.20
Connecting to [www.snort.org|68.177.102.20|:80](www.snort.org|68.177.102.20|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-03-24 09:46:25 ERROR 404: Not Found.


isn't the url correct ?
i have the version 2.9.0.4 and i am registered not subscribed


P.S
i also added oinkmaster.pl to /usr/local/bin and did :
```


oinkmaster.pl -o /etc/snort/rules

```

same error ...

---

### Post by CNM on 2011-03-24
> **EJeanmaire said:**
> Did you log into snort.org and generate an oinkmaster code? Paste that code in the <code> section in the oinkmaster config, athen run oinkmaster under sudo, and you are all set.
 
yeah of course

---

### Post by bodhi.zazen on 2011-03-24
That and snort limits the rate you can download the rule set. I think they have a 15 minute or so time out after each download.

---

### Post by CNM on 2011-03-24
> **bodhi.zazen said:**
> That and snort limits the rate you can download the rule set. I think they have a 15 minute or so time out after each download.

Yeah i know that
and it's not because of that ...
any suggestions ?
cause i want it to work with oinkmaster i don't want a manual update

---

### Post by emiller12345 on 2011-03-24
> **CNM said:**
> will double check on the hping3 thingy ...
another thing , i edited the /etc/oink.conf and added this :
url = [http://www.snort.org/sub-rules/code/snortrules-snapshot-2904.tar.gz](http://www.snort.org/sub-rules/code/snortrules-snapshot-2904.tar.gz)


 first off, "sub-rules" is if you paid for your rule set, "reg-rules" is non-paid.
second you should try flipping "snortrules-snapshot-2900.tar.gz" and "code"
*thirdly, I think I ran into this problem before, in order to download the rules for 2.9.0.4, you'll need the 2900.tar.gz file, I don't know wht *<--- This is wrong ignore it 
try from the commandline first with wget first to get the url right.

---

### Post by CNM on 2011-03-24
> **emiller12345 said:**
> first off, "sub-rules" is if you paid for your rule set, "reg-rules" is non-paid.
second you should try flipping "snortrules-snapshot-2900.tar.gz" and "code"
thirdly, I think I ran into this problem before, in order to download the rules for 2.9.0.4, you'll need the 2900.tar.gz file, I don't know wht
try from the commandline first with wget first to get the url right.

i switched to reg-rules it didn't work (both 2904 and 2900)
when i switched code and snortrules... i got a message telling me that the url is wrong
i tried it via wget with 2904 and 2900 and i got the error message (404)

---

### Post by emiller12345 on 2011-03-24
> **CNM said:**
> i switched to reg-rules it didn't work (both 2904 and 2900)
when i switched code and snortrules... i got a message telling me that the url is wrong
i tried it via wget with 2904 and 2900 and i got the error message (404)

So here's the real tedious part. The 404 error is a sign that you'll need to wait 15 minutes just to try again.  And its a slow process, you'll just need to be patient, wait 16 minutes in between tests. once you get the url correctly formated, I think you'll be good to use it in oinkmaster.conf.  I never really liked oinkmaster cause it kept overwriting my custom rule sets and was a little fussy in general.  let me know if it works for you.

---

### Post by bodhi.zazen on 2011-03-24
> **emiller12345 said:**
> I never really liked oinkmaster cause it kept overwriting my custom rule sets and was a little fussy in general.  let me know if it works for you.

I was going to mention the same thing. I usually simply manually download the rules manually.

---

### Post by CNM on 2011-03-25
> **emiller12345 said:**
> So here's the real tedious part. The 404 error is a sign that you'll need to wait 15 minutes just to try again.  And its a slow process, you'll just need to be patient, wait 16 minutes in between tests. once you get the url correctly formated, I think you'll be good to use it in oinkmaster.conf.  I never really liked oinkmaster cause it kept overwriting my custom rule sets and was a little fussy in general.  let me know if it works for you.

i already waited more than 15 minutes many times ... no luck !

> **bodhi.zazen said:**
> I was going to mention the same thing. I  usually simply manually download the rules manually.

i think i'm dropping oinkmaster and going back to do this manually ...
i'll give 2 or 3 more tries and if it doesn't work i'm going manual ;)

---

### Post by CNM on 2011-03-25
i updated them manually i followed the [link]("http://ubuntuforums.org/showthread.php?t=1477696") you sent

however there is no doc folder 

i only did this : 
```
sudo cp rules/* /etc/snort/rules
```
i downloaded the 2904 package ...

is there anything else i should do ?

---

