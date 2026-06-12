---
title: "Question about Apache Logs"
date: 2012-01-11
forum: Server Platforms
---

### Post by minorix on 2012-01-11
Hello,
I have a personal [COLOR=blue][/COLOR][FONT=inherit !important][/FONT]server setup on my home connection, mainly to increase my knowledge, but also to host a small website I have. I have been looking in the Apache logs and have noticed some strange entries that I am not completely sure about. Here are some examples:

67.43.228.238 - - [10/Jan/2012:20:54:26 -0600] "POST [http://216.86.158.122:6667/](http://216.86.158.122:6667/)HTTP/1.0" 301 340 "-" "-"

72.250.175.16 - - [10/Jan/2012:20:54:38 -0600] "CONNECT 72.250.175.12:6667 HTTP/1.0" 301 329 "-" "-"

212.27.60.46 - - [10/Jan/2012:20:54:40 -0600] "CONNECT 212.27.60.46:1025 HTTP/1.0" 301 328 "-" "-"
I understand that the returned 301 code is a "moved impermanently" indication, but I am a bit confused as to exactly what the client was trying to do. It seems like they were trying to do some sort of redirect? Port 6667 is something used for IRC apparently and 1025 is a MS RPC port. Does anyone know exactly what this is?
If I telnet to my server on port 80 and run this, I can duplicate the entry in the log. What exactly are they trying to do here though?


Ports 6667 and 1025 are not turned on on my server. 

Any help is appreciated. Thank you.

---

### Post by SeijiSensei on 2012-01-11
I think these are efforts to use your server as a proxy.  You can make sure this won't happen by disabling mod_proxy and friends in /etc/apache2/mods-enabled.  If you don't see any symlinks to proxy modules, which is the Ubuntu default, you should be okay.

---

### Post by minorix on 2012-01-11
Thank you for your help, I thought that was what was occurring, but was not entirely sure. 

If it was succeeding, it would return the website requested when I tried to telnet on port 80 in the web server, but instead it returns an error. This tells me it is not working as the hacker would expect.

---

