---
title: "[HOWTO]: Use Pan with Stunnel4 Secure Sockets Layer (SSL)"
date: 2007-12-29
forum: Tutorials
---

### Post by 43moon on 2007-12-29
**Disclaimer:**
I didn't invent the wheel here, I am just condensing bits and pieces of information that I have learned from other people here in the forum.  It took me half of a day to finally figure this out.  I hope that I can save someone else the time and the effort by condensing the steps that worked for me.  I used Synaptic to install "Pan" and "stunnel4".  I am assuming that you already know how to do that.  I am not a pro so I may not know how to troubleshoot any issues that you encounter.  I am sharing what I have learned in an effort to begin to repay the community.


**Getting Stunnel4 to work:**
I am only insterested in SSL for my newsgroup reader.  I dont use an email client or anything else listed in stunnel so I commented-them-out in order to avoid any potential problems related to services that I don't use.  If you use any of the services, feel free to adjust them to fit your needs (remove the ";" in front of the various service level configurations).

Edit the stunnel config file:
```
sudo gedit /etc/stunnel/stunnel.conf
```

I have enclosed my stunnel.conf file. If you copy it, be sure to replace "YOUR.NEWSGROUP.HERE:PORT" with your required address and port as provided by your service provider.
```

; Sample stunnel configuration file by Michal Trojnara 2002-2006
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of chroot jail)

; Certificate/key is needed in server mode and optional in client mode
; cert = /etc/stunnel/mail.pem
;key = /etc/stunnel/mail.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[nntp]
accept = localhost:119
connect = YOUR.NEWSGROUP.HERE:PORT

; [pop3s]
; accept  = 995
; connect = 110

; [imaps]
; accept  = 993
; connect = 143

; [ssmtp]
; accept  = 465
; connect = 25

; [https]
; accept  = 443
; connect = 80
; TIMEOUTclose = 0

; vim:ft=dosini

```

Edit stunnel4:
```
sudo gedit /etc/default/stunnel4
```

Set "Enabled=" to "1" (without quotes):
```

# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0

```


**Getting Pan to work with stunnel4:**
Start Pan and enter the following settings for your secure newsgroup server:

Set the Location Address to: "localhost" (without the quotes).
Set the port to: 119
Enter your Login information if required by your service provider.

[B]
Start stunnel4:[/B]
```

/etc/init.d/stunnel4 start

```

Now start Pan and you should be able to access your newsgroup server through SSL.


Thanks to Badtothebone for this helpful post:
[http://ubuntuforums.org/showpost.php?p=3768783&postcount=7]("http://ubuntuforums.org/showpost.php?p=3768783&postcount=7")

And thanks to chrroessner for this very enlightening post:
[http://ubuntuforums.org/showpost.php?p=3569031&postcount=1]("http://ubuntuforums.org/showpost.php?p=3569031&postcount=1")

---

### Post by meekatron on 2008-02-03
ok i seem to have this working but a few things are confusing me. I am no expert on ssl stuff but what i am wondering is if the port on my news reader is 119 which is the port for my news server how is it encrypted. should it not be a different port number.

my conf file for stunnel looks like this 
[nntp]
accept = localhost:119
connect = news-europe.giganews.com:563

and my pan news reader is on localhost port 119.

does this mean it is bypassing stunnel and ignoring the encryption.
i got the 563 port number from giganews website would that be a special port for there ssl stuff.

is the ssl encryption for both upload and download? 

sorry if these questions sound a bit dumb just tryin to get my head round it.

---

### Post by jjb123 on 2008-02-08
Basically what you are doing is setting up a server on your computer, but only applications on your network can access it. So, in Pan it connected to your own computer and in turn stunnel connects via ssl to giganews on the port specified in the file.

---

### Post by djcronos on 2008-03-13
This is the de-facto standard for HOWTO's when it comes to setting up stunnel4 with pan in gutsy.  Thank you so much - I'm bookmarking this for future reference!

---

### Post by seraph47 on 2008-04-06
I am unable to get Pan working with stunnel4.
Here's my stunnel.conf:
```
; Sample stunnel configuration file by Michal Trojnara 2002-2006
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of chroot jail)

; Certificate/key is needed in server mode and optional in client mode
; cert = /etc/stunnel/mail.pem
;key = /etc/stunnel/mail.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[nntp]
[B]accept = localhost:119
connect = news.giganews.com:443[/B]

; [pop3s]
; accept  = 995
; connect = 110

; [imaps]
; accept  = 993
; connect = 143

; [ssmtp]
; accept  = 465
; connect = 25

; [https]
; accept  = 443
; connect = 80
; TIMEOUTclose = 0

; vim:ft=dosini
```

And my stunnel4:
```
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/stunnel.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
```

And pan is set to localhost/119 with my correct login info. 

Also, heres my log file :
```
2008.04.06 01:07:32 LOG5[15279:3083282112]: stunnel 4.18 on i486-pc-linux-gnu with OpenSSL 0.9.8c 05 Sep 2006
2008.04.06 01:07:32 LOG5[15279:3083282112]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2008.04.06 01:07:32 LOG6[15279:3083282112]: file ulimit = 1024 (can be changed with 'ulimit -n')
2008.04.06 01:07:32 LOG6[15279:3083282112]: poll() used - no FD_SETSIZE limit for file descriptors
2008.04.06 01:07:32 LOG5[15279:3083282112]: 500 clients allowed
2008.04.06 01:07:32 LOG7[15279:3083282112]: FD 7 in non-blocking mode
2008.04.06 01:07:32 LOG7[15279:3083282112]: FD 8 in non-blocking mode
2008.04.06 01:07:32 LOG7[15279:3083282112]: FD 9 in non-blocking mode
2008.04.06 01:07:32 LOG7[15279:3083282112]: SO_REUSEADDR option set on accept socket
2008.04.06 01:07:32 LOG7[15279:3083282112]: nntp bound to 127.0.0.1:119
2008.04.06 01:07:32 LOG7[15280:3083282112]: Created pid file /stunnel4.pid
2008.04.06 09:45:16 LOG5[4823:3083171520]: stunnel 4.18 on i486-pc-linux-gnu with OpenSSL 0.9.8c 05 Sep 2006
2008.04.06 09:45:16 LOG5[4823:3083171520]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2008.04.06 09:45:16 LOG6[4823:3083171520]: file ulimit = 1024 (can be changed with 'ulimit -n')
2008.04.06 09:45:16 LOG6[4823:3083171520]: poll() used - no FD_SETSIZE limit for file descriptors
2008.04.06 09:45:16 LOG5[4823:3083171520]: 500 clients allowed
2008.04.06 09:45:16 LOG7[4823:3083171520]: FD 4 in non-blocking mode
2008.04.06 09:45:16 LOG7[4823:3083171520]: FD 5 in non-blocking mode
2008.04.06 09:45:16 LOG7[4823:3083171520]: FD 6 in non-blocking mode
2008.04.06 09:45:16 LOG7[4823:3083171520]: SO_REUSEADDR option set on accept socket
2008.04.06 09:45:16 LOG3[4823:3083171520]: Error binding nntp to 127.0.0.1:119
2008.04.06 09:45:16 LOG3[4823:3083171520]: bind: Address already in use (98)
2008.04.06 09:49:32 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:36402
2008.04.06 09:49:32 LOG7[15280:3086601104]: nntp started
2008.04.06 09:49:32 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 09:49:32 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 09:49:32 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 09:49:32 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 09:49:32 LOG7[15280:3086601104]: Connection from 127.0.0.1:36402 permitted by libwrap
2008.04.06 09:49:32 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:36402
2008.04.06 09:49:32 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 09:49:32 LOG3[15280:3086601104]: No host resolved
2008.04.06 09:49:32 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 09:49:32 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 09:49:32 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 09:49:32 LOG6[15280:3083282112]: Child process 5027 finished with code 0
2008.04.06 10:06:14 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:35753
2008.04.06 10:06:14 LOG7[15280:3086601104]: nntp started
2008.04.06 10:06:14 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 10:06:14 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 10:06:14 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 10:06:14 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 10:06:14 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 10:06:14 LOG6[15280:3083282112]: Child process 5786 finished with code 0
2008.04.06 10:06:14 LOG7[15280:3086601104]: Connection from 127.0.0.1:35753 permitted by libwrap
2008.04.06 10:06:14 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:35753
2008.04.06 10:06:14 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 10:06:14 LOG3[15280:3086601104]: No host resolved
2008.04.06 10:06:14 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 10:06:14 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 10:26:46 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:60740
2008.04.06 10:26:46 LOG7[15280:3086601104]: nntp started
2008.04.06 10:26:46 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 10:26:46 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 10:26:46 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 10:26:46 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 10:26:46 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 10:26:46 LOG6[15280:3083282112]: Child process 6960 finished with code 0
2008.04.06 10:26:46 LOG7[15280:3086601104]: Connection from 127.0.0.1:60740 permitted by libwrap
2008.04.06 10:26:46 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:60740
2008.04.06 10:26:46 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 10:26:46 LOG3[15280:3086601104]: No host resolved
2008.04.06 10:26:46 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 10:26:46 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:23:44 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:57835
2008.04.06 17:23:44 LOG7[15280:3086601104]: nntp started
2008.04.06 17:23:44 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:23:44 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:23:44 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:23:44 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:23:44 LOG7[15280:3086601104]: Connection from 127.0.0.1:57835 permitted by libwrap
2008.04.06 17:23:44 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:57835
2008.04.06 17:23:44 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:23:44 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:23:44 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:23:44 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:23:44 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:23:44 LOG6[15280:3083282112]: Child process 2671 finished with code 0
2008.04.06 17:23:58 LOG5[2678:3083245248]: stunnel 4.18 on i486-pc-linux-gnu with OpenSSL 0.9.8c 05 Sep 2006
2008.04.06 17:23:58 LOG5[2678:3083245248]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2008.04.06 17:23:58 LOG6[2678:3083245248]: file ulimit = 1024 (can be changed with 'ulimit -n')
2008.04.06 17:23:58 LOG6[2678:3083245248]: poll() used - no FD_SETSIZE limit for file descriptors
2008.04.06 17:23:58 LOG5[2678:3083245248]: 500 clients allowed
2008.04.06 17:23:58 LOG7[2678:3083245248]: FD 4 in non-blocking mode
2008.04.06 17:23:58 LOG7[2678:3083245248]: FD 5 in non-blocking mode
2008.04.06 17:23:58 LOG7[2678:3083245248]: FD 6 in non-blocking mode
2008.04.06 17:23:58 LOG7[2678:3083245248]: SO_REUSEADDR option set on accept socket
2008.04.06 17:23:58 LOG3[2678:3083245248]: Error binding nntp to 127.0.0.1:119
2008.04.06 17:23:58 LOG3[2678:3083245248]: bind: Address already in use (98)
2008.04.06 17:25:18 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:41058
2008.04.06 17:25:18 LOG7[15280:3086601104]: nntp started
2008.04.06 17:25:18 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:25:18 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:25:18 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:25:18 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:25:18 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:25:18 LOG6[15280:3083282112]: Child process 2731 finished with code 0
2008.04.06 17:25:18 LOG7[15280:3086601104]: Connection from 127.0.0.1:41058 permitted by libwrap
2008.04.06 17:25:18 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:41058
2008.04.06 17:25:18 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:25:18 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:25:18 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:25:18 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:43:46 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:57064
2008.04.06 17:43:46 LOG7[15280:3086601104]: nntp started
2008.04.06 17:43:46 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:43:46 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:43:46 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:43:46 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:43:46 LOG7[15280:3086601104]: Connection from 127.0.0.1:57064 permitted by libwrap
2008.04.06 17:43:46 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:57064
2008.04.06 17:43:46 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:43:46 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:43:46 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:43:46 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:43:46 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:43:46 LOG6[15280:3083282112]: Child process 3698 finished with code 0
2008.04.06 17:44:06 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:57067
2008.04.06 17:44:06 LOG7[15280:3086601104]: nntp started
2008.04.06 17:44:06 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:44:06 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:44:06 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:44:06 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:44:06 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:44:06 LOG6[15280:3083282112]: Child process 3716 finished with code 0
2008.04.06 17:44:06 LOG7[15280:3086601104]: Connection from 127.0.0.1:57067 permitted by libwrap
2008.04.06 17:44:06 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:57067
2008.04.06 17:44:06 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:44:06 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:44:06 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:44:06 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:44:33 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:57069
2008.04.06 17:44:33 LOG7[15280:3086601104]: nntp started
2008.04.06 17:44:33 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:44:33 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:44:33 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:44:33 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:44:33 LOG7[15280:3086601104]: Connection from 127.0.0.1:57069 permitted by libwrap
2008.04.06 17:44:33 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:57069
2008.04.06 17:44:33 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:44:33 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:44:33 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:44:33 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:44:33 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:44:33 LOG6[15280:3083282112]: Child process 3738 finished with code 0
2008.04.06 17:45:45 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:51796
2008.04.06 17:45:45 LOG7[15280:3086601104]: nntp started
2008.04.06 17:45:45 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:45:45 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:45:45 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:45:45 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:45:45 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:45:45 LOG6[15280:3083282112]: Child process 3807 finished with code 0
2008.04.06 17:45:45 LOG7[15280:3086601104]: Connection from 127.0.0.1:51796 permitted by libwrap
2008.04.06 17:45:45 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:51796
2008.04.06 17:45:45 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:45:45 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:45:45 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:45:45 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:46:52 LOG5[3859:3083372224]: stunnel 4.18 on i486-pc-linux-gnu with OpenSSL 0.9.8c 05 Sep 2006
2008.04.06 17:46:52 LOG5[3859:3083372224]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2008.04.06 17:46:52 LOG6[3859:3083372224]: file ulimit = 1024 (can be changed with 'ulimit -n')
2008.04.06 17:46:52 LOG6[3859:3083372224]: poll() used - no FD_SETSIZE limit for file descriptors
2008.04.06 17:46:52 LOG5[3859:3083372224]: 500 clients allowed
2008.04.06 17:46:52 LOG7[3859:3083372224]: FD 4 in non-blocking mode
2008.04.06 17:46:52 LOG7[3859:3083372224]: FD 5 in non-blocking mode
2008.04.06 17:46:52 LOG7[3859:3083372224]: FD 6 in non-blocking mode
2008.04.06 17:46:52 LOG7[3859:3083372224]: SO_REUSEADDR option set on accept socket
2008.04.06 17:46:52 LOG3[3859:3083372224]: Error binding nntp to 127.0.0.1:119
2008.04.06 17:46:52 LOG3[3859:3083372224]: bind: Address already in use (98)
2008.04.06 17:47:01 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:51811
2008.04.06 17:47:01 LOG7[15280:3086601104]: nntp started
2008.04.06 17:47:01 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:47:01 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:47:01 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:47:01 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:47:01 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:47:01 LOG6[15280:3083282112]: Child process 3864 finished with code 0
2008.04.06 17:47:01 LOG7[15280:3086601104]: Connection from 127.0.0.1:51811 permitted by libwrap
2008.04.06 17:47:01 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:51811
2008.04.06 17:47:01 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:47:01 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:47:01 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:47:01 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:47:09 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:51814
2008.04.06 17:47:09 LOG7[15280:3086601104]: nntp started
2008.04.06 17:47:09 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:47:09 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:47:09 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:47:09 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:47:09 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:47:09 LOG6[15280:3083282112]: Child process 3872 finished with code 0
2008.04.06 17:47:09 LOG7[15280:3086601104]: Connection from 127.0.0.1:51814 permitted by libwrap
2008.04.06 17:47:09 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:51814
2008.04.06 17:47:09 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:47:09 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:47:09 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:47:09 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:47:10 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:51815
2008.04.06 17:47:10 LOG7[15280:3086601104]: nntp started
2008.04.06 17:47:10 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:47:10 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:47:10 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:47:10 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:47:10 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:47:10 LOG6[15280:3083282112]: Child process 3874 finished with code 0
2008.04.06 17:47:10 LOG7[15280:3086601104]: Connection from 127.0.0.1:51815 permitted by libwrap
2008.04.06 17:47:10 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:51815
2008.04.06 17:47:10 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:47:10 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:47:10 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:47:10 LOG7[15280:3086601104]: nntp finished (0 left)
2008.04.06 17:47:47 LOG7[15280:3083282112]: nntp accepted FD=10 from 127.0.0.1:51818
2008.04.06 17:47:47 LOG7[15280:3086601104]: nntp started
2008.04.06 17:47:47 LOG7[15280:3086601104]: FD 10 in non-blocking mode
2008.04.06 17:47:47 LOG7[15280:3086601104]: TCP_NODELAY option set on local socket
2008.04.06 17:47:47 LOG7[15280:3086601104]: FD 11 in non-blocking mode
2008.04.06 17:47:47 LOG7[15280:3086601104]: FD 12 in non-blocking mode
2008.04.06 17:47:47 LOG7[15280:3083282112]: Cleaning up the signal pipe
2008.04.06 17:47:47 LOG6[15280:3083282112]: Child process 3900 finished with code 0
2008.04.06 17:47:47 LOG7[15280:3086601104]: Connection from 127.0.0.1:51818 permitted by libwrap
2008.04.06 17:47:47 LOG5[15280:3086601104]: nntp connected from 127.0.0.1:51818
2008.04.06 17:47:47 LOG3[15280:3086601104]: Error resolving 'news.giganews.com': Neither nodename nor servname known (EAI_NONAME)
2008.04.06 17:47:47 LOG3[15280:3086601104]: No host resolved
2008.04.06 17:47:47 LOG5[15280:3086601104]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
2008.04.06 17:47:47 LOG7[15280:3086601104]: nntp finished (0 left)
```
I then start stunnel 4 with : **sudo stunnel4 /etc/stunnel/stunnel.conf**
I appreciate any help, thanks.

---

### Post by Gun_Smoke on 2008-06-22
Thanks.

---

### Post by darc on 2008-07-16
Thanks 43moon for the howto, and meekatron for mentioning the special port.

As meekatron said, if you use giganews, you need to set the connect to : 
news.giganews.com:563

-darc

---

### Post by leswgnr on 2008-07-16
I followed your (43moon) howto and have the error below. I have included below that my config file and default file. I don't seem to have any /stunnel4.pid file in my root directory.  Any help is quite appreciated. 
Thank you,
-----------------------------------------------------------------------------
dad@dad-desktop:~$ /etc/init.d/stunnel4 start
Starting SSL tunnels: 2008.07.16 22:15:40 LOG7[7690:3082667696]: RAND_status claims sufficient entropy for the PRNG
2008.07.16 22:15:40 LOG7[7690:3082667696]: PRNG seeded successfully
2008.07.16 22:15:40 LOG7[7690:3082667696]: SSL context initialized for service nntp
[Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file
------------------------------------------------------------------------------
; Sample stunnel configuration file by Michal Trojnara 2002-2006
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of chroot jail)

; Certificate/key is needed in server mode and optional in client mode
;cert = /etc/stunnel/mail.pem
;key = /etc/stunnel/mail.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[nntp]
accept   = localhost:119
connect  = news.newsguy.com:443 

;[pop3s]
;accept  = 995
;connect = 110

;[imaps]
;accept  = 993
;connect = 143

;[ssmtp]
;accept  = 465
;connect = 25

;[https]
;accept  = 443
;connect = 80
;TIMEOUTclose = 0

; vim:ft=dosini
---------------------------------------------------------------------------------
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
==================================================================

---

### Post by Gun_Smoke on 2008-07-16
do > sudo stunnel4

2008.07.16 22:45:02 LOG7[6802:3082888880]: RAND_status claims sufficient entropy for the PRNG
2008.07.16 22:45:02 LOG7[6802:3082888880]: PRNG seeded successfully
2008.07.16 22:45:03 LOG7[6802:3082888880]: SSL context initialized for service nntp


you can check your connection with wireshark.. 

Set a filter to tcp.port == "port number"

in my case it would be tcp.port == 443

"expression" is > tcp.port == 443

Looks like..... if working and a ton of them.... Something like this...... -
                                                                             |
                                                                              |
                                                                             |
                                                                            |
                                                                           |
                                                                           V
> 165335	339.081791	xxx.xx.xxx.xx	192.168.x.xxx	SSL	Continuation Data

So after "sudo stunnel4" 
start to grab some headers and then run wireshark with the expression or filter mentioned up there..


BOL

GS

---

### Post by Gun_Smoke on 2008-07-16
^^^^^^

Edited... this is for notification emails. 

GS

---

### Post by daladheri on 2008-07-19
I have successfully connected to my news with stunnel in between. Only question I have is that pan tells me that it tells me localhost connection reset by peer. here is a log. I get all my news though and it works but it gives me these errors occaisionally. 

```

Sat Jul 19 18:23:51 2008 - Error reading from localhost: Connection reset by peer
Sat Jul 19 18:23:51 2008 - Loaded 1345 articles for "alt.os.linux.ubuntu" in 0.1 seconds (22777 per second)
Sat Jul 19 18:23:51 2008 - Loaded 1617 articles for "comp.lang.ruby" in 0.1 seconds (24094 per second)
Sat Jul 19 18:23:51 2008 - Loaded 16 articles for "comp.os.linux.powerpc" in 0.0 seconds (1552 per second)
Sat Jul 19 18:23:52 2008 - Loaded 247 articles for "linux.debian.ports.powerpc" in 0.0 seconds (34936 per second)

```

---

### Post by bennich on 2008-09-23
Hey - Thanks a bunch for the guide.

Bookmarked for future reference - it worked like a charm ;-)

---

### Post by fbnewtz on 2008-11-04
I think it is important (obvious to most) point to run the /etc/init.d/stunnel4 start with sudo.

sudo /etc/init.d/stunnel4 start

This resolves any PID problems.

Thanks,

Fred

---

### Post by finer recliner on 2008-11-08
I also was getting the error:
You should check that you have specified the pid= in you configuration file


it was solved when i realized that i forget to uncomment the "client = yes" line.

just double check your .conf file to make sure it matches the OP's settings.

thanks!

---

### Post by gutsy goober on 2008-11-20
**update**  I made this work by simply stopping stunnel, ie "sudo /etc/init.d/stunnel4 stop" and restarting it. So there you go.

Hi.  I am also getting the pid error.

Stunnel worked great when I set it up yesterday, but today I ran it again and got the error--I am not able to connect.

I ran the file as "sudo" and have "client=yes" in my config file.

I read a couple things about permissions and stuff but I'm not well versed in this.

TIA for any help.

---

### Post by somking95 on 2009-02-21
> **43moon said:**
> 
```

/etc/init.d/stunnel4 start

```


I was able to get stunnel4 working with PAN. However, does the above command set stunnel4 to run at startup or do I need to run it every time before running PAN?

P.S. Thanks for the How-To. Very good and very use useful.

---

### Post by mrfargoreed on 2009-04-02
A HUGE thanks to everyone here for this advice, especially 43moon's original post.  I've been trying everything to get Klibido/PAN working with Stunnel4 and getting to the point of smashing the keyboard with a large kitchen utensil, but thanks to this thread I seem to have it working!  

I have a couple of questions though:
1 - Do I actually have to stop Stunnel4 when I close my newsreader?
2 - How do I check that Stunnel4 is actually working properly and encrypting my data?

MANY thanks.

---

### Post by Gun_Smoke on 2009-04-02
you can check your connection with wireshark..

Start grabbing some headders...

Set a filter to tcp.port == "port number"

in my case it would be tcp.port == 443

"expression" is

```
tcp.port == 443
```
Looks like..... if working and a ton of them.... Something like this...... -
|
|
|
|
|
V
```

165335 339.081791 xxx.xx.xxx.xx 192.168.x.xxx SSL Continuation Data 
```

---

### Post by mrfargoreed on 2009-04-02
Many thanks for your reply, Gun_Smoke.  The headers have downloaded ok, I just wanted to make sure everything was 'secure'. I've installed Wireshark, too.  

Cheers!

---

### Post by Gun_Smoke on 2009-04-02
I believe you understood me correctly, but just to clarify for those who might find this thread in the future. 

Have wireshark running with the filters in place *while* downloading headers, as wireshark is a 'live' application.  So amongst many things it does very well is watch what type of packets are going to and from where.  In a very very small nutshell.   

See the documentation included with WS and the tons of information on the web.  There are people in ##wireshark on freenode to help you better understand what your reading should you get lost. (might be #wireshark)

---

### Post by norcal on 2009-04-14
thank you for the How to, very helpful. Question: Does stunnel4 provide me anonymity like tor when i access a newserver? if not can it be configured to go through proxy servers?

---

### Post by mikezila on 2009-05-04
> **norcal said:**
> thank you for the How to, very helpful. Question: Does stunnel4 provide me anonymity like tor when i access a newserver? if not can it be configured to go through proxy servers?

It doesn't make you anonymous, but it makes is very, very difficult for anyone to see your traffic, or rather to make out what it is.  They can still intercept it, and tell it's yours, but they won't really be able to do anything with it.

---

### Post by mikezila on 2009-05-04
Edited because it was probably wrong.

---

### Post by mikezila on 2009-05-05
Having some trouble.  Everything is setup correctly (or it seems to be), it's just that wireshark is still seeing a bunch of plain TCP packets, with no "SSL Continuation Data" at all, leading me to believe that it just isn't working.  Here's some details.

I'm using giganews, and I have SSL enabled on my account.  Diamond plan baby!

I'm using Pan, and Pan is connecting to localhost at port 119

stunnel is configured exactly as in OP's post, save for my nntp section, which is:
```

[nntp]
accept = localhost:119
connect = news.giganews.com:563

```

stunnel is also ENABLED=1, so I know that's not it.

Pan connects and works correctly, but when I fire up Wireshark to monitor my tubes, they're clogged with normal TCP traffic!  What gives!  I need my tinfoil headgear!

---

### Post by killabee44 on 2009-06-24
Guys, 

Thanks to the OP for this helpful post. I got stunnel going with Astraweb. Had to use:

secure.news.astraweb.com:563

for some reason ssl.astranews.com:563 didn't work.

Anyhow, since stunnel requires sudo to start, is there a way to automatically start it at boot? I thought programs that required sudo could not be started without password. Im new to Linux, so that might be a very simple thing..

Thanks.

---

### Post by russetaylor on 2009-11-20
> **killabee44 said:**
> Guys, 

Anyhow, since stunnel requires sudo to start, is there a way to automatically start it at boot? I thought programs that required sudo could not be started without password. Im new to Linux, so that might be a very simple thing..

Thanks.

You can do this
```
export EDITOR=gedit && sudo visudo
```
Add the following line at the end of the /etc/sudoers file (use down arrow to move cursor down to bottom)
```
johndoe ALL= NOPASSWD: /etc/init.d/stunnel4 restart
```
Replace "johndoe" by the name of the user or the group which can use sudo and do the modification.
Finally you need to add stunnel to the startup programs list from [System] [Preferences] [Startup Applications] [Add]
**Name:** stunnel4
**Command:** bash -c "sleep 45; sudo /etc/init.d/stunnel4 restart --start-hidden"
**Comment:** whatever

Note the 45 seconds is the pause before the stunnel starts.  You may want to adjust this pause or not have one at all.  I don't jump right into using pan after boot so I set a long pause.

---

### Post by GavinP on 2009-11-26
I set the local port listening for stunnel to 11900 instead of 119 and this seems to get around the sudo problem.

I can now boot the PC, logon on as a non-sudoer user and it just works when starting pan without any command line instructions.

I had to change the server setup in Pan to also point to localhost 11900.

Thanks

Gavin

---

### Post by RickKnight on 2010-04-07
Great HOWTO. I'm using PAN to connect to UsenetMonster. Configuring Stunnel and PAN together was simple and worked first time. 

Thanks!

---

### Post by kevpatts on 2012-02-09
Hey guys,

I can't seem to get past the "You should check that you have specified the pid= in you configuration file" error. My config file is:```
; Sample stunnel configuration file by Michal Trojnara 2002-2009
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of the chroot jail)

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/ssl/certs/stunnel.pem
;key = /etc/ssl/certs/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside the chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = zlib

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
;debug = 7
;output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

;[pop3s]
;accept  = 995
;connect = 110

;[imaps]
;accept  = 993
;connect = 143

;[ssmtp]
;accept  = 465
;connect = 25

;[https]
;accept  = 443
;connect = 80
;TIMEOUTclose = 0

; vim:ft=dosini

[Eucalyptus for Landscape]
accept  = landscape.canonical.com:443
connect = localhost:8773
```
and ls -al /etc/ssl/certs/stunnel.pem returns:
```
-rw-r--r-- 1 root root 3432 2012-02-09 11:41 /etc/ssl/certs/stunnel.pem
```

any idea what I'm doing wrong? Using Lucid server by the way, trying to get [this]("https://help.ubuntu.com/community/UEC/Landscape") working.

Kevpatts

---

### Post by robby8550 on 2012-04-05
Is it possible to set up stunnel4 for multiple servers? I would like to add gmane.org to the news-server I already have set and working.

pan 0.136 with stunnel4 operational on Mint 11 AMD64

---

### Post by Trebacz on 2012-11-03
This post was real helpful in getting me up and running (Pan and Astraweb). I consolidated all of it here (and a couple other articles) in a blog post (partly so I can remember):

[http://blog.trebacz.com/2012/03/installing-stunnel-to-enable-ssl.html]("http://blog.trebacz.com/2012/03/installing-stunnel-to-enable-ssl.html")

To the most recent poster. Yes you should be able to set stunnel up for multiple servers. I'd just use a different local port for each server when you set up your stunnel configuration.

---

