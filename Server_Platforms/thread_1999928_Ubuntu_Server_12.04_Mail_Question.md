---
title: "Ubuntu Server 12.04 Mail Question"
date: 2012-06-08
forum: Server Platforms
---

### Post by rwslippey on 2012-06-08
Hello, 

I've got a file server setup at home here and it's running smoothly however I've got some different things going on and I'd like to be able to have the system email me different things. For instance I just setup clamscan to run on a schedule. I set the report up to send to my email address however I doubt it will get through due to my ip address being blocked by the other server. Is their any simple way to configure an smtp connection for the outgoing mail. I'd also like to see if this can function from the web server as well, so that the local sites can send mail as well (mostly everything I run on the web side is PHP based)

Thanks


Rob

---

### Post by rwslippey on 2012-06-08
Ok I'm in the right direction. Not sure I'm running into an issue but it's getting somewhere.

Here is what I've done:

Installed Postfix:
```
sudo apt-get install postfix
```

Modify .forward

```
sudo nano ~/.forward
```

Just add the address you'd like to forward TO in the file and save (F3 to save F2 to exit)

Now the mail being sent to root is being forwarded but it's being stopped somewhere along the line... I suspect due to domain name or host name and the reverse dns lookup. Not my department so I'll read up a bit more and see if I can figure out how that works.

here is the error I have as of now from postfix.


```
Jun  8 21:50:28 box postfix/error[11461]: 0B1CDE7: to=<myemail@domain.com>, orig_to=<superadmin@box.domain.net>, relay=none, delay=0.07, delays=0.03/0/0/0.03, dsn=5.0.0, status=bounced

Jun  8 21:50:28 wce1 postfix/qmgr[5389]: 0B1CDE7: removed
```


Again I assume this has something to do with my ip and the smtp host blocking the connection. Any ideas?

---

### Post by rwslippey on 2012-06-08
Got it working... Thanks to a port on this website 

[http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/](http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/)

It appears most ISPs block the dynamic range ip all together and haveing a domain name with a reverse lookup has nothing to do with it. 

So postfix has a work around.

Credit for below goes to the above websites:

```
sudo nano /etc/postfix/transport
```

Insert the following: be sure to change smtp.yourisp.com to your isp's actual smtp settings... For comcast I used smtp.comcast.net and its working.

```
gmail.com smtp:smtp.yourisp.com:25
googlemail.com smtp:smtp.yourisp.com:25
```

Save and close  F3 and F2 and Now run 

```
sudo postmap /etc/postfix/transport
```

Open /etc/postfix/main.cf

```
sudo nano /etc/postfix/main.cf
```

Start a new line at the bottom and enter

```
transport_maps = hash:/etc/postfix/transport
```
The above showes postfix where the transport list is

All should be good now... restart and test

```
sudo /etc/init.d/postfix restart
```

Good luck

Rob

---

