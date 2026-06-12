---
title: "phpvirtualbox error"
date: 2014-09-20
forum: Virtualisation
---

### Post by allen7 on 2014-09-20
I have been using phpvirtualbox on my host server to run two virtualbox guests for a LAMP stack and a Media server. Up until now it has been working fine. I just began to install the virtualbox guest additions and when I rebooted the system I could no longer access the phpvirtualbox web ui. I am prompted for my login, then get an error as follows: Could not connect to host ([http://127.0.0.1:18083/](http://127.0.0.1:18083/))

I click on the details and it shows the following:
Exception Object
(
    [message:protected] => Could not connect to host ([http://127.0.0.1:18083/](http://127.0.0.1:18083/))
    [string:Exception:private] => 
    [code:protected] => 64
    [file:protected] => /var/www/phpvirtualbox/lib/ajax.php
    [line:protected] => 128
    [trace:Exception:private] => Array
        (
        )

    [previous:Exception:private] => 
)


I have tried restarting vboxweb-service multiple times without success. I have also seen elsewhere online to try vboxwebsrv >nul which results in : 
Oracle VM VirtualBox web service Version 4.3.10_Ubuntu
(C) 2007-2014 Oracle Corporation
All rights reserved.

Also, I have tried running vboxwebsrv -H 127.0.0.1 which resulted in:
Oracle VM VirtualBox web service Version 4.3.10_Ubuntu
(C) 2007-2014 Oracle Corporation
All rights reserved.
VirtualBox web service 4.3.10_Ubuntu r93012 linux.amd64 (Apr  7 2014 03:37:47) release log
00:00:00.000105 main     Log opened 2014-09-20T19:01:24.965301000Z
00:00:00.000106 main     Build Type: release
00:00:00.000108 main     OS Product: Linux
00:00:00.000109 main     OS Release: 3.13.0-35-generic
00:00:00.000109 main     OS Version: #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014
00:00:00.000125 main     DMI Product Name: To Be Filled By O.E.M.
00:00:00.000129 main     DMI Product Version: To Be Filled By O.E.M.
00:00:00.000168 main     Host RAM: 7653MB total, 7346MB available
00:00:00.000170 main     Executable: /usr/lib/virtualbox/vboxwebsrv
00:00:00.000170 main     Process ID: 2352
00:00:00.000171 main     Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.005167 SQPmp    #### SOAP FAULT:  [SOAP-ENV:Server]

If anyone could help get me back up an running it would be great. Thanks

---

