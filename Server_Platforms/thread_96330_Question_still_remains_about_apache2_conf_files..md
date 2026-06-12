---
title: "Question still remains about apache2 conf files."
date: 2005-11-28
forum: Server Platforms
---

### Post by exkalibur on 2005-11-28
[FONT=Arial]My "port 80 " issue has been fixed by remming a line out in ports.conf ( listen *:80) but I'm not satisfied that it's the way to do it...... To recap :

[/FONT][LIST=1]
[*][FONT=Arial]Could not connect to localhost due to an error " could not bind to port 80.....". This started after some package upgrades, but I can't prove it....[/FONT]
[*][FONT=Arial]Tried every command I knew and some that you suggested, to find what was tying up port 80.....nothing was found.[/FONT]
[*][FONT=Arial]Both httpd and ports conf files have a "listen *:80 " line. I rem the one in ports.conf and it fixed the problem.[/FONT]
[*][FONT=Arial]Apache2 version 2.0.54 and webmin ver. 1.230[/FONT]
[*][FONT=Arial]Webmin writes to ports.conf file.....what writes to httpd.conf file if it is supposed to be there for backward compatibility ?[/FONT]
[*][FONT=Arial]This issue has come back over and over, with lot of folks in this forum and others... I haven't seen one clear fix or common pattern...
    [/FONT][/LIST][FONT=Arial]Done lot of reading but some of these questions may be too "basic" for the manual or FAQ's. I find some of the documentation " obscure ", like, writen by and for, superduper admin gurus.....Sucks to be a newbie ..... :-))

Any sugestions or toughts....????
[/FONT]

---

### Post by LordHunter317 on 2005-11-28
There shuld be no ports directive in httpd.conf.

More likely, you already had an instance of Apache running.

---

### Post by exkalibur on 2005-11-28
> There shuld be no ports directive in httpd.conf.
[FONT=Arial]
I suspected that. Thanks for clarifying.
[/FONT] 
 >  More likely, you already had an instance of Apache running. 
[FONT=Arial]Well, we tried lots of different ways to find out what was running on port 80...Not even apache was showing up...But that's beside the point.It worked after the line removal in the conf. file...Still curious as for why it appeared there....anyway, I'll try new installs on spare drives, now that I'm a little bit more knowledgeable about ubuntu. And I'll make sure I track and document the changes this time.

Lots of good people helped with different suggestions and I really appreciated it.
Regards
[/FONT]

---

### Post by bfonseca on 2005-11-29
[QUOTE=exkalibur][FONT=Arial]
I suspected that. Thanks for clarifying.
[/FONT] 
  
[FONT=Arial]Well, we tried lots of different ways to find out what was running on port 80...Not even apache was showing up...But that's beside the point.It worked after the line removal in the conf. file...Still curious as for why it appeared there....anyway, I'll try new installs on spare drives, now that I'm a little bit more knowledgeable about ubuntu. And I'll make sure I track and document the changes this time.

Lots of good people helped with different suggestions and I really appreciated it.
Regards
[/FONT][/QUOTE]


Hi all, I am having a problem with Apache and it is similar to exkalibur. I would like to fix this problem. So that apache works and orbit. I think according to this: netstat -a | grep 80 theres alot running on port 80. for some reason apache doesnt show up. I am trying to get the server to work but this problem is preventing that. Can someone please help me with this problem

[SIZE="4"]Problem:[/SIZE]

/tmp$ netstat -a | grep 80
unix  2      [ ACC ]     STREAM     LISTENING     11898    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12330    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12315    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12296    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12280    /tmp/orbit-bfonseca/linc-1f27-0-33414e104f7eb
unix  3      [ ]         STREAM     CONNECTED     12255    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12217    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     12180
unix  3      [ ]         STREAM     CONNECTED     12042    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     11905    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  3      [ ]         STREAM     CONNECTED     11901    /tmp/orbit-bfonseca/linc-1eff-0-a3798b75807e
unix  2      [ ]         DGRAM                    10480

I can use all the help I can get. 
Thanks
brian

---

### Post by exkalibur on 2005-11-30
Brian.
The situation I was in was that I didn't set up the webmin apache module properly. Instead of redirecting to apache2.conf, I, due to lack of knowledge, left the httpd.conf as the main apache config file. I found a "listen *:80" line in the apache2/httpd.conf file. I rem it out and apache server was able to start.
 
Check that file first.....
regards

---

### Post by bfonseca on 2005-11-30
[QUOTE=exkalibur]Brian.
The situation I was in was that I didn't set up the webmin apache module properly. Instead of redirecting to apache2.conf, I, due to lack of knowledge, left the httpd.conf as the main apache config file. I found a "listen *:80" line in the apache2/httpd.conf file. I rem it out and apache server was able to start.
 
Check that file first.....
regards[/QUOTE]

Hi thanks for your quick response,  However unfortunatly it did not work.  Would you or anyone else have any other advice, to fixing my problem? Another problem I am having is I am unable to start and restart apache.

Problem:

bfonseca@12:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server (Apache2)...                                      [ ok ]
bfonseca@12:~$ sudo /etc/init.d/apache2 start
bfonseca@12:~$ sudo /etc/init.d/apache2 restart

Shouldn't there be a prompt like this
  *Starting web server (Apache2)...               [ok]

nothing appears when I try to start it...(wierd)
the same thing happens with restart.

---

### Post by exkalibur on 2005-11-30
OK ! First .....Are you running webmin ?

>  Shouldn't there be a prompt like this
  *Starting web server (Apache2)...               [ok] Yes, there should be. But I don't think you need the "restart" command after you used the "start" one.

Try this to find what processes are running and on which port.
```
sudo netstat -l -np -p
``` 
In the meantime, I'll dig up the rest of what I've tried.
regards

---

### Post by bfonseca on 2005-11-30
[QUOTE=exkalibur]OK ! First .....Are you running webmin ?

 Yes, there should be. But I don't think you need the "restart" command after you used the "start" one.

Try this to find what processes are running and on which port.
```
sudo netstat -l -np -p
``` 
In the meantime, I'll dig up the rest of what I've tried.
regards[/QUOTE]


Hi thanks alot for your help.... I have now fixed the problem, I got frustrated and just went on ahead and reinstalled the whole dist. It doesn't take long. But once installed I ran the apt-get apache2 and after that it has been working.  Thanks alot for taking the time to help me.
brian

---

### Post by exkalibur on 2005-11-30
You're welcome !!!!
Would've been interesting to find what was wrong.........

Regards

---

