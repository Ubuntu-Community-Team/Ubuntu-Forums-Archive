---
title: "How install virtualbox on ubuntu server 16.04 and using it as provider virtual machin"
date: 2016-06-03
forum: Virtualisation
---

### Post by sed_faster on 2016-06-03
hello everyone,

I need the article or mentoring about how should I install and set the Ubuntu server to receive the virtual box and phpVirtualBox to management virtual machines. What should I know about these topics?
I share this article: [https://www.unixmen.com/install-oracle-virtualbox-and-manage-it-using-phpvirtualbox-on-ubuntu-15-10-headless-server/](https://www.unixmen.com/install-oracle-virtualbox-and-manage-it-using-phpvirtualbox-on-ubuntu-15-10-headless-server/)

I did all steps but after make the credentials appear the pop-up with this message:

```
Exception Object
(
    [message:protected] => Could not connect to host (http://127.0.0.1:18083/)
    [string:Exception:private] => 
    [code:protected] => 64
    [file:protected] => /var/www/html/phpvirtualbox/endpoints/api.php
    [line:protected] => 134
    [trace:Exception:private] => Array
        (
        )

    [previous:Exception:private] => 
)
```


Thanks and best regards

---

### Post by MAFoElffen on 2016-06-04
You had note that the article's title includes the verbiage "headless" right?

Headlesss would imply that the server, even if it has display, and keyboard, that your visualization services will be accessed remotely. Standard VirtualBox has a GUI. Using it as headless, you are running the CL Management util from the commandline, in a headless server mode so that it never invokes the GUI management toolset.

Being you are accessing it remotely implies the you keep to virtual networking conventions in either implementing a bridge so that ou can access them from your own network or a route path to the virtual NAT network. 

Your error has a link local /home address, which your VM Guests would not be accessible from.

To help us help you. Describe your server and how you set it up. Tell us how you are trying to use it ... then tell us what you did to get that error.

Also... Could you clarify what "provider virtual ma" means. Just seems like there was more, but got cut off?

---

