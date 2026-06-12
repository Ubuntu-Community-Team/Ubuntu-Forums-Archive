---
title: "Ubuntu 9.10 UEC Store images"
date: 2010-03-19
forum: Ubuntu One (CLOSED)
---

### Post by Richaa on 2010-03-19
Hi,

I have successfully register cluster/node on Ubuntu 9.10 server. :)

I am trying to run the image from UEC browser but when I click on **store tab and click on search button **I get the following error [COLOR=Blue]**"error 28 connect() timed out"**[/COLOR]. 

Please help as I am not able to figure out where am I going wrong/ what am I missing?

Any help is appreciated.

Thanks in advance. :)

---

### Post by Sivaa on 2010-03-20
Hello Richaa
I think I know the reason for the problem. You may want to try out the following. This should mostly fix the issue
 
1) Open /etc/default/image-store-proxy file
2) There will be 2 proxy variables http_proxy and https_proxy.
3) You need to set the proxy server details (ip and port) in these variables.
I guess you would not have set the values and it would be still [http://your-proxy:port](http://your-proxy:port) and [https://your-proxy:port](https://your-proxy:port) respectively.
 
Let me know the results. Good Luck ;)
 
Cheers
Siva

---

### Post by vgokulakrishnan on 2011-03-04
Hello,
What if i get this error,
" ERROR 35: gnutls_handshake() failed: A TLS packet with unexpected length was received."
I tried purging and reinstalling python-image-store-proxy too, But didn't help.. [IMG]http://ubuntuforums.org/_3DLJna5PMuA3Kh92Lc9lpyyToc12piZKMaSJoc9lMl9zYm1Jql9zM1Eao1WJqi8vBp1[/IMG]
Any 1 has a solution, please say me asap..

---

