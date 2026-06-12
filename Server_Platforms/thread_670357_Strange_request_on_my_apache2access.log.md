---
title: "Strange request on my apache2/access.log"
date: 2008-01-17
forum: Server Platforms
---

### Post by h3rt3q on 2008-01-17
i get this request 30 minutes ago..

59.40.182.231 - - [18/Jan/2008:00:24:47 +0800] "CONNECT 66.135.214.176:80 HTTP/1.1" 200 614 "-" "-"
59.40.182.231 - - [18/Jan/2008:00:24:48 +0800] "GET / HTTP/1.1" 200 614 "-" "-"
59.40.182.231 - - [18/Jan/2008:00:24:49 +0800] "GET [http://www.ebay.com/](http://www.ebay.com/) HTTP/1.1" 200 614 "-" "Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)"

its starnge because im not ebay.com or i dont have any folder named that...
y isit giving 200 response? should it be 404??

---

### Post by MJN on 2008-01-17
It's just a client attempting to get you to download [www.ebay.com]("http://www.ebay.com") for it, i.e. it's trying to use you as a proxy.

The reason you are seeing a 200 response code is because your server is sending a 'successfull' response back to the client - it's not fetching [www.ebay.com]("http://www.ebay.com") but rather will have sent your default page from your default site (if you have more than one). Remember, a client can ask for whatever absolute URL it likes but if the Host-Header does not match one of your ServerName's then the default site will be used - hence [www.ebay.com]("http://www.ebay.com") was ignored and the client will have got <your site>/default.htm (or whatever your default pages are called).

(Note how when it asked **GET /** the page (actually your page plus some headers) returned was 614 bytes, and when it asked **GET [http://www.ebay.com/](http://www.ebay.com/)** the page returned was also 614 bytes - the same)

Does that help?

Mathew

---

### Post by h3rt3q on 2008-01-17
oh. so someone is trying to use me as a proxy server. thats weird... anyway thanx. coz i thought it was some security thing.

---

### Post by MJN on 2008-01-18
It's quite common. Don't take it personally though - they will likely have just 'stumbled' across your IP address whilst trawling through random addresses.
 
Mathew

---

### Post by x3roconf on 2008-01-20
> **h3rt3q said:**
> oh. so someone is trying to use me as a proxy server. thats weird... anyway thanx. coz i thought it was some security thing.

Maybe they are scanning for open proxies?

---

