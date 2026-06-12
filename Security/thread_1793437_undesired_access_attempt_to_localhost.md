---
title: "undesired access attempt to localhost"
date: 2011-06-29
forum: Security
---

### Post by Phil Stone on 2011-06-29
While investigating my localhost access logs during an investigation to resolve locking myself out of my own server(!) I noticed this recent access attempt from a proxy referrer. I wouldn't expect this on a local server - currently set to listen on 127.0.01. The request was 403 forbidden, but surely the request should not have even reached this far? Is this an example of an unauthorised access attempt? I don't think it is me because all of my usual access requests are in moz 5 and im logged in to linux currently.

58.218.199.250 - - [29/Jun/2011:16:42:09 +0100] "GET ([http://www)      jpgdz.com/proxyheader.php]("http://www.jpgdz.com/proxyheader.php") HTTP/1.1" 403 217 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

Note please do not click this link as I do not know where it leads ^^^^! (and i dont know how to disable it on this forum)

Regards
Phil

---

### Post by e79 on 2011-06-29
[COLOR=Black][FONT=Arial][SIZE=2]Here is the result when clicking on the link...I don't know what it is for though...and I obviously removed the remote host and remote address to post this result.[/SIZE][/FONT][B][B]

> 
----------------------------------------
HTTP_ACCEPT=text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 HTTP_ACCEPT_LANGUAGE=en-us,en;q=0.5 HTTP_ACCEPT_ENCODING=gzip, deflate HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/20100101 Firefox/5.0 HTTP_CONNECTION=keep-alive REMOTE_PORT=23493 HTTP_REFERER=http://ubuntuforums.org/showthread.php?t=1793437  REMOTE_HOST=XXXXX REMOTE_ADDR=X.X.X.X
 ---------------------------------------- CS_ProxyJudge Result=ANONYMOUS ----------------------------------------[/B][/B][/COLOR]

---

### Post by Phil Stone on 2011-06-29
was the remote host you, me, or someone else?  One suggestion I'd think is that ff is attempting to reconnect after being denied by reverting into a previous version. Although this doesn't explain the user being on an NT OS.

---

### Post by Dangertux on 2011-06-29
The remote host is the IP who is accessing proxyheader.php

The logs are showing an automated scan : Is jpgdz.com your website?

---

### Post by e79 on 2011-06-29
> **Dangertux said:**
> The remote host is the IP who is accessing proxyheader.php

The logs are showing an automated scan : Is jpgdz.com your website?

Remote Host : FQDN to your modem
Remote Addr : Your actual external IP

---

### Post by Phil Stone on 2011-06-29
no my site has readable words for its title. I can accept it may be a port scan - ive been getting one lately - is an HTTP header incorrect rejection by my firewall followed a minute or so later by an incorrect TCP packets rejection. But like i say how is that even accessing my local system to get to my local server which as faik is not connected externally at least it shouldn't be.

---

### Post by Phil Stone on 2011-06-29
So I just posted a picture of my front door then.

---

### Post by Dangertux on 2011-06-29
> **e79 said:**
> Remote Host : FQDN to your modem
Remote Addr : Your actual external IP

That's correct , it's just using $_SERVER['REMOTE_ADDR'] and getbyhostaddr or $_SERVER['REMOTE_HOST']


You may wish to verify that apache is bound to localhost. sudo netstat -anlp would be helpful in this regard.

---

### Post by Phil Stone on 2011-06-29
I have listen on port localhost port 80. ok.

I have listen on port 631 not sure, but procces is cupsd and i see that when logging in so probably ok.

I have a servername which is a bristol ip so thats probably me and there's a foreign number by that too guessing that's international dialling code.

then tcp6 cupsd again short form (guess ipv6)
hen udp  - couple of "avahi-daemon r" and "dhclient.

So that looks fairly normal. - huge list after - notable entires:

unix  3      [ ]         STREAM     CONNECTED     3116     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     3114     435/upstart-udev-br 

The rest look like regular sys connections.

Re tcp listen on port 80 thtas litening on 0.0.0.0 wher the cupsd is listening on 127.0.0.1:631  im thinking the server lockout im experiencing is related to the port 80 tcp not being on 127.0.0.1 too. 

rgds
Phil

---

