---
title: "I can se my page with 192.168.1.102 but not with the router's ip   =(   help"
date: 2007-02-12
forum: Server Platforms
---

### Post by starbuck88 on 2007-02-12
I  installed apache (lamp) on my older computer and the http server seem to work becasue i can see the index.htm with the ip 192.168.1.102. I did port forwarding on my router and when i try to access my website with the real ip (the router's ip) , a access denied htm appear. 


Where is the problem....:confused: 

Thank you in advance!

-Starbuck :)

---

### Post by jtc on 2007-02-12
Are you trying to connect to your webbserver, by using the external ip, from another computer on the internal network? Have you tried accessing it from the outside?

---

### Post by starbuck88 on 2007-02-13
I tried from the inside of the server with 192.168.1.102 and Its WORKING
I did port forwarding on the router and tried 69,XX.XX.XX (real ip) and its not working, in fact i receive a access denied error!!!! ***

i tried from the outside and its not working.

Thank.

---

### Post by PetePete on 2007-02-13
try accessing it from a computer outside your network.. or run your brwoser through a proxy and see if it connects, should do if you've setup port fowarding correctly.

chances are its just connecting to your routers page.

---

### Post by Brazen on 2007-02-13
Yeah if you are connecting from a computer within your network to your router's IP, most routers don't handle that intelligently.  Even on a linux router it takes some creative configuration in order to do that.

As PetePete said, connect through a proxy server outside your network, or just connect from a computer outside your network.

---

### Post by v8YKxgHe on 2007-02-13
I had this problem, very simple to fix - it's just that your router is blocking the port, you'll need to open up port 80.

Edit: woops - didn't read that you already opened it up hehe, sorry!

---

### Post by starbuck88 on 2007-02-15
Thank everybody

quote - try accessing it from a computer outside your network - quote

I did, its not working..

and for the proxy.... i never did that...maybe i should read about it....


thank guy, i hope I will fix it soon.

---

### Post by v8YKxgHe on 2007-02-15
Are you sure you've set apache to allow connections from the outside world?

---

### Post by Nythain on 2007-02-15
and make sure your isp supports running servers... a lot of common ones block port 80 transmission... you can change the listen port and use a service similar to no-ip wich offers port 80 redirect

---

