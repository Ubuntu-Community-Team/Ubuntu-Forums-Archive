---
title: "[problem] Proxy on ubuntu"
date: 2010-04-02
forum: Sudan Team
---

### Post by abdoamcig on 2010-04-02
Dear all,

In windows Xp i had using Hotspot for accessing my accounts in PayPal and in Google Adsense ..

and sense that time when i applied Ubuntu in my computer, I'm still searching for Proxy program, That allowing me to access these websites ..

Regards,
Abdo

---

### Post by zero-n on 2010-04-02
try TOR

---

### Post by abdoamcig on 2010-04-03
Thanks Zero-n for your reply .. 

i have did all the instructions but it doesn't work, i had try to remove Polipo and change it with privoxy .. But Polipo still appear in the Tor preferences

---

### Post by Malta paul on 2010-04-03
Try this its great, if you can access?
[http://anonymous-proxy-servers.net/de/](http://anonymous-proxy-servers.net/de/)

---

### Post by zero-n on 2010-04-03
The link specified by [Malta paul]("http://ubuntuforums.org/member.php?u=166032") will help but try to change page language to English

---

### Post by Malta paul on 2010-04-03
Just click the UK flag for English, top right corner, ;)

---

### Post by zero-n on 2010-04-03
This programs used to be JAP am i right ?

---

### Post by Malta paul on 2010-04-03
Yes correct

---

### Post by zero-n on 2010-04-09
hey [abdoamcig]("http://ubuntuforums.org/member.php?u=802676") you can try [**THIS**]("http://www.linuxac.org/forum/entry.php?63-%D4%D1%CD-%CA%E4%D5%ED%C8-%C8%D1%E4%C7%E3%CC-tor-%C7%E1%E3%D4%E5%E6%D1-%DA%E1%EC-%C7%C8%E6%E4%CA%E6-%21%21-%E1%E1%C8%C7%CD%CB%ED%E4-%DA%E4-%C7%E1%CE%D5%E6%D5%ED%E5-%C7%E1%E3%D8%E1%DE%E5-%21") link.

---

### Post by abdoamcig on 2010-04-21
Unfortionately all these methods failed to work with me, Can any one give me any other easy method ?

---

### Post by yasir.elsharif on 2010-04-22
Hello [abdoamcig]("http://ubuntuforums.org/member.php?u=802676"), 
I am using vidalia (GUI) with tor/polipo and all are working just fine.
So you can just add tor repository and install tor polipo vidalia 
and you're done.
```
deb     http://deb.torproject.org/torproject.org karmic main
```
Then add the gpg key used to sign the packages by running the followingcommands at your command prompt:
```
gpg --keyserver keys.gnupg.net --recv 886DDD89gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```
Now refresh your sources and install Tor by running the followingcommands at your command prompt:
```
apt-get updateapt-get install tor tor-geoipdb vidalia 
```

you can also check this [link]("http://www.torproject.org/docs/debian.html.en") for more details.
enjoy surfing anonymously :)
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

remember to remove tor from autostart when the system starts.

---

### Post by Y2J on 2010-04-25
itshidden.com ;)

---

### Post by yasir.elsharif on 2010-05-14
hello [abdoamcig]("http://ubuntuforums.org/member.php?u=802676"),
is it still not working?
Tor + Vidalia + Polipo work just fine with me
you should give it another try

---

### Post by todd1049 on 2010-05-15
Salam 'Alaykum Yasir,

I tried your suggestion, using the instruction on the tor page you linked to as well.  But when I tried downloading the key, I got the following result:

the command was -- $ gpg --keyserver keys.gnupg.net --recv 886DDD89

the result was:
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Can I find it elsewhere?  Thanks for your help.

---

### Post by yasir.elsharif on 2010-05-16
Hello todd1049,
You may try this web page:
[https://www.torproject.org/docs/debian.html.enor](https://www.torproject.org/docs/debian.html.enor) 

There is a launchpad ppa packages:
[https://launchpad.net/~sevenmachines/+archive/tor]("https://launchpad.net/%7Esevenmachines/+archive/tor")

---

