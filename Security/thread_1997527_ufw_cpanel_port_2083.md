---
title: "ufw cpanel port 2083"
date: 2012-06-05
forum: Security
---

### Post by g45lewis on 2012-06-05
I've set up ufw to deny incoming and allow outgoing on only selected ports (eg, 53,80,443/tcp and 53,67,68/udp). In order to access cpanel on the server hosting my website, I use the url [https://secureservername.com:2083/](https://secureservername.com:2083/). But unless I open 2083 in ufw, this will time out. This seems strange. Most likely I don't understand enough about how ports work. Does the port number in the https refer to my outgoing port or the server's incoming port? Thanks very much.

---

### Post by darkod on 2012-06-05
Usually the 2083 would refer to the port on the server you are accessing. The traffic leaves your computer on a random high number port and reaches the server on 2083.

You will need to allow outgoing traffic to port 2083 and allow the returning traffic (this should already be allowed, usually all RELATED and ESTABLISHED returning traffic is allowed back in.

---

### Post by g45lewis on 2012-06-05
Thanks!

---

