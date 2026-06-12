---
title: "Can tor be used with network proxy?"
date: 2011-03-05
forum: Security
---

### Post by asdfghjkl67 on 2011-03-05
When i click preferences-network proxy a screen of comes up showing the system internet configuration. 

Is there a way to make all system connections got through tor?

---

### Post by wacky_sung on 2011-03-05
> **asdfghjkl67 said:**
> When i click preferences-network proxy a screen of comes up showing the system internet configuration. 

Is there a way to make all system connections got through tor?

Why all your network using TOR? Your internet speed will be clawed to snail.If privacy is your concern, then go for paid service as such VPN.

---

### Post by MechaMechanism on 2011-03-06
> **wacky_sung said:**
> Why all your network using TOR? Your internet speed will be clawed to snail.If privacy is your concern, then go for paid service as such VPN.
+1

Better to use surgical precision than wholesale proxing.  The cool thing about Ubuntu and Unix/Linux in general is that they don't have outbound connections by default.  In other words there is nothing to proxy.  The only connections would be those the user started.  Some examples of user connections would be, Firefox, bittorrent, email, music players sending data to last.fm and so on.  I would not worry about most user connections.  Just worry about web sites that need a username and password.

What I'm trying to say is only run web browsers and email through tor.  Although in many situations email programs will have problems due to unauthorized SMTP access to their ISP SMTP server.  But who use their ISP mail servers anymore.

All this said I will help you.

First install Tor
Open up System/Administration/Software Sources.
In other software tab click on add.
Enter the below:  Change REPLACE-ME with the name of the Ubuntu version your using, so if your using 9.10 you would put the name karmic in, Don't use the version number, we just want the name.  (karmic 9.10) (lucid 10.04) (maverick 10.10)
```
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) REPLACE-ME main
```
Do leave the space between the word deb and the start of the URL.

Open up terminal and paste in the following commands.
```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

Run: ```
apt-get update
apt-get install tor tor-geoipdb polipo
```

Grab the polipo config from here: [https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

Install the polipo.conf to /etc/polipo/  change the filename from polipo.conf to config, just config
```
sudo service polipo restart
```

In System/Preferences/Network Proxy  Select manual proxy.  In the HTTP proxy line enter 8118.  You can click apply system wide but I don't think that will work and at any rate you will not need it.

Most Gnome programs will honor the proxy setting.  For all other applications you will need to manually change the proxy.  Chrome is an example where it will honor the proxy setting.  Use chrome and go to [https://check.torproject.org/](https://check.torproject.org/) to see if your tor connection is working as it should.

Let me know if it works or not.  By the way I asked the very same question almost several weeks back, mine was piping everything through SSH, which I figured out how to do, sort of, meaning SSH is only socks and not http :(.

References I used for this: [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

---

### Post by wacky_sung on 2011-03-06
> **MechaMechanism said:**
> +1
Run: ```
apt-get update
apt-get install tor tor-geoipdb polipo
```

Grab the polipo config from here: [https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

Install the polipo.conf to /etc/polipo/  change the filename from polipo.conf to config, just config
```
sudo service polipo restart
```

In System/Preferences/Network Proxy  Select manual proxy.  In the HTTP proxy line enter 8118.  You can click apply system wide but I don't think that will work and at any rate you will not need it.


I do not encourge or stopping people who uses polipo which i find it too buggy and slow down the web surfing a lot.I will strongly recommend you to run Squid instead.

---

### Post by asdfghjkl67 on 2011-03-06
> **MechaMechanism said:**
> +1

Better to use surgical precision than wholesale proxing.  The cool thing about Ubuntu and Unix/Linux in general is that they don't have outbound connections by default.  In other words there is nothing to proxy.  The only connections would be those the user started.  Some examples of user connections would be, Firefox, bittorrent, email, music players sending data to last.fm and so on.  I would not worry about most user connections.  Just worry about web sites that need a username and password.

What I'm trying to say is only run web browsers and email through tor.  Although in many situations email programs will have problems due to unauthorized SMTP access to their ISP SMTP server.  But who use their ISP mail servers anymore.

All this said I will help you.

First install Tor
Open up System/Administration/Software Sources.
In other software tab click on add.
Enter the below:  Change REPLACE-ME with the name of the Ubuntu version your using, so if your using 9.10 you would put the name karmic in, Don't use the version number, we just want the name.  (karmic 9.10) (lucid 10.04) (maverick 10.10)
```
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) REPLACE-ME main
```Do leave the space between the word deb and the start of the URL.

Open up terminal and paste in the following commands.
```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```Run: ```
apt-get update
apt-get install tor tor-geoipdb polipo
```Grab the polipo config from here: [https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

Install the polipo.conf to /etc/polipo/  change the filename from polipo.conf to config, just config
```
sudo service polipo restart
```In System/Preferences/Network Proxy  Select manual proxy.  In the HTTP proxy line enter 8118.  You can click apply system wide but I don't think that will work and at any rate you will not need it.

Most Gnome programs will honor the proxy setting.  For all other applications you will need to manually change the proxy.  Chrome is an example where it will honor the proxy setting.  Use chrome and go to [https://check.torproject.org/](https://check.torproject.org/) to see if your tor connection is working as it should.

Let me know if it works or not.  By the way I asked the very same question almost several weeks back, mine was piping everything through SSH, which I figured out how to do, sort of, meaning SSH is only socks and not http :(.

References I used for this: [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)


Thanks for the detailed post

I just have one question-if i set up tor as the network proxy and then open up the tor browser bundle on on usb on the same pc will the two tor programs clash with one another? or would i get a 'double tor connection' as it were?

---

### Post by MechaMechanism on 2011-03-06
I don't think it will work.  This is what I got.  And even if you could I think you would have a port conflict.

$ ./start-tor-browser
tor is already running as PID 3940
vidalia is already running as PID 3937
polipo is already running as PID 29151

Please shut down the above process(es) before running Tor Browser Bundle.

Try doing the proxy with the browser bundle on usb and test with Chrome.

---

