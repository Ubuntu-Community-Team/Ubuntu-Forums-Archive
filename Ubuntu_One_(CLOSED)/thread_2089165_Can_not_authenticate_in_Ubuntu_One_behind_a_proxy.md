---
title: "Can not authenticate in Ubuntu One behind a proxy"
date: 2012-11-28
forum: Ubuntu One (CLOSED)
---

### Post by mme oscar on 2012-11-28
Hi everyone,

After installing it at home without any problem, I'm trying to install Ubuntu One at work (Ubuntu 12.04, must use proxy). Apparently it can not connect to the server: I can't sign in of course, can't use the "forgotten password" form either (address not recognized), and if I open the dialog to create an account I get a message "There was a problem downloading the captcha, reloading...".

I tried installing ubuntuone-client-proxy, following
[http://askubuntu.com/questions/7081/ubuntu-one-behind-a-proxy-how-to-make-it-work](http://askubuntu.com/questions/7081/ubuntu-one-behind-a-proxy-how-to-make-it-work)

and resinstalling the certificates, following [https://one.ubuntu.com/help/faq/why-am-i-getting-an-the-authentication-failed-error-on-windows-225/](https://one.ubuntu.com/help/faq/why-am-i-getting-an-the-authentication-failed-error-on-windows-225/) (though actually this does not apply to my case)

... without any success.

Does someone has any idea what I am doing wrong? What I could try?

Thanks!

Remark: I had previously posted this question on askubuntu but didn't get any answer:
[http://askubuntu.com/questions/219444/can-not-authenticate-in-ubuntu-one-behind-a-proxy](http://askubuntu.com/questions/219444/can-not-authenticate-in-ubuntu-one-behind-a-proxy)
I also saw that similar questions were asked here with limited success:
[http://ubuntuforums.org/showthread.php?t=2007988&highlight=proxy](http://ubuntuforums.org/showthread.php?t=2007988&highlight=proxy)
[http://ubuntuforums.org/showthread.php?t=1997809&highlight=ubuntu+proxy](http://ubuntuforums.org/showthread.php?t=1997809&highlight=ubuntu+proxy)

---

### Post by mme oscar on 2012-12-05
For anyone who faces the same problem: after contacting Ubuntu One support, they told me that

> Unfortunately, Ubuntu One does not work properly behind auto proxy configurations. That appears to be the reason why it's not working for you since your proxy is set to be auto-configured by a server (via the URL in the proxy settings).


I also tried to configure the proxy manually in the Network settings but it does not work either (I suspect there is something wrong with the way Ubuntu One uses the https proxy).

See also bug report
[https://bugs.launchpad.net/ubuntuone-client/+bug/1002862](https://bugs.launchpad.net/ubuntuone-client/+bug/1002862)

So it seems that currently I can only switch back to Dropbox.

---

