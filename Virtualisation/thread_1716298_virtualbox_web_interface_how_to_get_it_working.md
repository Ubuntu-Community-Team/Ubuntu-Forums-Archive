---
title: "virtualbox web interface how to get it working?"
date: 2011-03-28
forum: Virtualisation
---

### Post by warda on 2011-03-28
hi I installed virtualbox4 on my ubuntu10.10 and then phpvirtualbox4.
I have had already LAMP running with all needed modules.

I followed instructions from 2 sources:
[http://www.firstdigest.com/2010/08/manage-virtualbox-over-web-interface/](http://www.firstdigest.com/2010/08/manage-virtualbox-over-web-interface/)

[http://www.smilecouple.org/2011/01/19/install-virtual-box-4-0-on-ubuntu-with-phpvirtualbox42](http://www.smilecouple.org/2011/01/19/install-virtual-box-4-0-on-ubuntu-with-phpvirtualbox42)

I didnt get any errors during install and all seemed work fine but when am trying to access it from another machine on the url
[http://192.168.1.64:18083](http://192.168.1.64:18083)

i get following error:
```

This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
&#8722;
<SOAP-ENV:Envelope>
&#8722;
<SOAP-ENV:Body>
&#8722;
<SOAP-ENV:Fault SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<faultcode>SOAP-ENV:Client</faultcode>
<faultstring>HTTP GET method not implemented</faultstring>
</SOAP-ENV:Fault>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

anyone succeeded and possibly can tell me what am i doing wrong?

many thanks

---

### Post by CharlesA on 2011-03-28
You don't access the web server service directly. You access it thru phpvirtualbox.

You can find some better instructions over on [the phpvirtualbox page]("http://code.google.com/p/phpvirtualbox/").

---

### Post by warda on 2011-03-28
hi charlesA and thanks for tip. 
I didnt actually found the answer on the website you pointed but you saying 'You don't access the web server service directly. You access it thru phpvirtualbox.' made me thinking twice and I understood where was the problem :). Basically **_ALL_** instructions say: unzip folder to var/www and then you can access vb from any browser. what they don't say is YOU HAVE TO POINT IN YOUR BROWSER TO THAT FOLDER in my case it was: [http://192.168.1.64/](http://192.168.1.64/)**phpvirtualbox-4.0-5**

although now I run in another problem
I get to the interface and when enter user and password
i get error message:
```

Exception Object
(
    [message:protected] => Error logging in or connecting to vboxwebsrv.
    [string:Exception:private] => 
    [code:protected] => 64
    [file:protected] => /var/www/phpvirtualbox-4.0-5/lib/vboxconnector.php
    [line:protected] => 113
    [trace:Exception:private] => Array
        (
            [0] => Array
                (
                    [file] => /var/www/phpvirtualbox-4.0-5/lib/vboxconnector.php
                    [line] => 238
                    [function] => __vboxwebsrvConnect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )

                )

            [1] => Array
                (
                    [file] => /var/www/phpvirtualbox-4.0-5/lib/ajax.php
                    [line] => 109
                    [function] => connect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )

                )

        )

    [previous:Exception:private] => 
)

```

any ideas?

thanks!

---

### Post by CharlesA on 2011-03-28
Make sure that vboxsvr is running.

See [here]("http://code.google.com/p/phpvirtualbox/wiki/vboxwebServiceConfigLinux") for instructions.

---

### Post by warda on 2011-03-29
hi,

I am not able to start vboxweb service:
**sudo: /etc/init.d/vboxweb-service: command not found**
this are my settings for virtualbox 
in **/etc/default/virtualbox**
VBOXWEB_USER=myuser
VBOXWEB_HOST=192.168.1.64
VBOXWEB_PORT=18083

I also run  **su myuser -c '/usr/bin/vboxwebsrv'**
to see any errors and this is the output:

Oracle VM VirtualBox web service version 3.2.8_OSE
(C) 2005-2010 Oracle Corporation
All rights reserved.
2011-03-29 18:18:09 [ P ] #### SOAP FAULT: Address already in use [SOAP-ENV:Server]


how can i fix it?
... was thinking of reinstalling virtualbox but it seems be long way though...

any help please

thankyou

---

### Post by CharlesA on 2011-03-29
What does this return?

```
ps aux | grep vbox
```

---

### Post by zaktalanos on 2011-03-30
I am having this exact same problem.

the output of my ps -aux | grep aux

```
root      1314  0.0  0.1 115992  5016 ?        Sl   09:34   0:00 /usr/lib/virtualbox/vboxwebsrv --background -H localhost -p 18083 -t 0 -F /var/log/vboxweb.log
```

---

### Post by zaktalanos on 2011-03-30
I mean grep vbox. :D

I've just left it for now and got my machines running headlessly but it's a mission to go and set up the machines CLI style. sure it would save a lot of time to point and click through a web interface here so I will persist in trying to get the web service up and running. if I get anywhere will let you know.

---

### Post by CharlesA on 2011-03-30
Do either of you have any firewalls enabled?

---

### Post by warda on 2011-03-31
hi,

this is my output for ```
ps aux | grep vbox
```
```

myuser     1306  0.0  0.6  26440  6116 ?        Sl   17:42   0:00 /usr/lib/virtua        lbox/vboxwebsrv -b --logfile /dev/null
myuser     1500  0.0  0.0   4016   744 pts/0    S+   17:47   0:00 grep --color=au        to vbox

```

did you mean to replace vbox with the actual user? if yes the output would give more:
```

myuser     1306  0.0  0.6  26440  6116 ?        Sl   17:42   0:00 /usr/lib/virtualbox/vboxwebsrv -b --logfile /dev/null
myuser     1309  0.0  0.4  13976  3588 ?        S    17:42   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
myuser     1324  0.0  0.6  19840  6172 ?        Sl   17:42   0:00 /usr/lib/virtualbox/VBoxSVC --pipe 11 --auto-shutdown
root      1381  0.0  0.3   8932  3108 ?        Ss   17:43   0:00 sshd: myuser [priv]
myuser     1456  0.0  0.1   8932  1504 ?        S    17:43   0:00 sshd: myuser@pts/0
myuser     1457  0.0  0.6   8892  5528 pts/0    Ss   17:43   0:00 -bash
myuser     1590  0.0  0.1   4592  1064 pts/0    R+   17:51   0:00 ps aux
myuser     1591  0.0  0.0   4016   744 pts/0    S+   17:51   0:00 grep --color=auto myuse

```

there is no firewall on linux

and i disabled for testing firewall on windows and so the av software but the problem hasnt changed..

---

### Post by CharlesA on 2011-03-31
The server is running, Is virtualbox on a different machine then the web server?

---

### Post by warda on 2011-03-31
hi, 
no the whole setup is on 1 machine
I only added VBOXWEB_HOST=192.168.1.64 in hope to get it working :) but with or without makes no difference...

would you say is this problem with permissions on the folders? or maybe Im missing some extra modules for virtual box to make it talking to webservice?

thanks

---

### Post by CharlesA on 2011-03-31
Did you change anything in config.php ?

IIRC, it has to have the web server running as the same user as you are running virtualbox as.

---

### Post by warda on 2011-03-31
hi charlesA,

I eventually cracked it..
I have set no authentication = true and uncomment it. - I noticed that for my version of VB OSE authentication isn't supported.

now I can connect to the console. I get some error warning 
[B]
Method 'ns1:ISystemProperties_getInfoVDSize' not implemented: method name or namespace not recognized[/B]

I'll give it a try to see if I can create VMachine using this..
thanks for helping

---

### Post by CharlesA on 2011-03-31
Ah. I didn't think OSE worked with phpvirtualbox, but I'm glad you got it working. :)

---

