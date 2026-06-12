---
title: "Ubuntu One not working...."
date: 2009-11-21
forum: Ubuntu One (CLOSED)
---

### Post by pizza-is-good on 2009-11-21
Hello,

I was interested to try Ubuntu One a while back, but decided to wait to try it until 9.10.

I am using 9.10 now, and there is just no way to get it to work...

When I copy files to my Ubuntu One folder in my computer, they are never uploaded online, and when I try to upload a file to the website, I always get the following error:
```
**Service Temporarily Unavailable**

 The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
  Apache/2.2.8 (Ubuntu) mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.8 OpenSSL/0.9.8g Server at files.one.ubuntu.com Port 443
```I have tried 'later' many times but it never works.


Any help will be appreciated.
Many thanks, and happy ubunting.

~pizza

---

### Post by andrea000 on 2009-11-22
Have you authorized your computer on the ubuntu one website?
There is a bug that prevents some people from doing this if
you can't authorize it open a terminal. 

applications->accessories->terminal
and copy and paste this command
> u1sync --authorize
Then the ubuntu one website should open asking you to authorize
your computer .Do that then click the ubuntu desktop app and click
connect.

---

### Post by scribbles on 2009-11-22
One of my machines wouldn't connect. This fixed it. Thanks!

---

### Post by pizza-is-good on 2009-11-23
> **andrea000 said:**
> Have you authorized your computer on the ubuntu one website?
There is a bug that prevents some people from doing this if
you can't authorize it open a terminal. 

applications->accessories->terminal
and copy and paste this command

Then the ubuntu one website should open asking you to authorize
your computer .Do that then click the ubuntu desktop app and click
connect.

I did that, and the terminal told me ```
The program 'u1sync' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-tools
```
So I did that, and then I authorised it.
I took me to the website and so I added some files on the UbuntuOne folder in my computer, and that didn't add them online. What now does work is if I add files online.

---

### Post by andrea000 on 2009-11-23
some people on the u1 forum say that Deleting everything
in ~/.local/share/ubuntuone/syncdaemon/ directory fixes
it.I'M not going to tell you to do that because i dont
know what it will do.The problem your having is a bug and
the u1 team has been working to fix it.sorry

---

### Post by raptortech97 on 2009-11-23
> **andrea000 said:**
> Have you authorized your computer on the ubuntu one website?
There is a bug that prevents some people from doing this if
you can't authorize it open a terminal. 

applications->accessories->terminal
and copy and paste this command

Then the ubuntu one website should open asking you to authorize
your computer .Do that then click the ubuntu desktop app and click
connect.

I did that, and it just showed a new line w/ a blinking cursor. Site still doesn't reflect my folder.

---

### Post by joshuahoover on 2009-11-24
> **raptortech97 said:**
> I did that, and it just showed a new line w/ a blinking cursor. Site still doesn't reflect my folder.

Sorry to hear Ubuntu One isn't working properly for you. Can you right-click on the Ubuntu One client and select "Report a Problem"? This will file a bug report with some logs. Also, please be sure to include any steps you've taken to get to this point so that we can better help get this problem addressed.

Thank you,

Joshua

---

### Post by pizza-is-good on 2009-11-28
I have submitted about 5 bug reports by now.

Anyway, I guess that I'll wait around for an update or maybe 10.04.

Thanks everybody for trying to help....

---

### Post by heatpumpcontrol on 2010-03-29
> **andrea000 said:**
> some people on the u1 forum say that Deleting everything
in ~/.local/share/ubuntuone/syncdaemon/ directory fixes
it.I'M not going to tell you to do that because i dont
know what it will do.The problem your having is a bug and
the u1 team has been working to fix it.sorry

> **pizza-is-good said:**
> I did that, and the terminal told me ```
The program 'u1sync' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-tools
```


These two worked for me. I had also installed Dropbox and it too wouldn't connect till I did the above.. Also, I opened port 443 in the firewall configuration. After I noticed they were both working, I deleted that port from the firewall config, logged off and back on and they are now both working still. 

Worked for me..

---

