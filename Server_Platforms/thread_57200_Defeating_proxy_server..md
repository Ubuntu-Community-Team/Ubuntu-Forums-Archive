---
title: "Defeating proxy server."
date: 2005-08-15
forum: Server Platforms
---

### Post by s0c0 on 2005-08-15
I'm looking for a method to defeat a rather tenacious proxy server.  The server will not allow any connections to websites unless the web browser is set to communicate with the proxy server.  The proxy server is such a bastard that it prevents any non-http/https traffic.

I am look at a solution that would allow me to connect to my home linux box from a remote location via HTTP.  My home computer would then iniate the website request (based on a url I entered intoa text field) and then relay it back to the remote machine somehow.  Perhaps this could be done through an HTML frame and covered by SSL.

Is this possible or fairly complex?  I haven't been able to find much documentation on something like this.  Though I haven't had a change to dive in Squid a lot.  Thanks.

---

### Post by PeP on 2005-08-15
you want to do is http tunneling:
[http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=%22http+tunneling%22+ssh&btnG=Rechercher&lr=lang_en](http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=%22http+tunneling%22+ssh&btnG=Rechercher&lr=lang_en)


Are you sure that it is not safer for you to contact your network administrator? If you activity is detected and not allowed you might have some troubles.

Also, the admins may either have already set up an ssh gateway or a socks proxy to allow this.

---

### Post by btdown on 2005-08-16
I would appreciate some help with this as well.
 
I've found a couple tutorials using putty for an ssh connection to my home machine, but none of them worked. ;(
 
Thanks,
BT

---

### Post by A-star on 2005-08-17
In putty you can specify a proxy (your proxy) and then specify which port you want to redirect with it (for ssh port 22 if I'm not mistaken).

To surf the web the best thing to do is install a proxy server at home and in your browser at work (I suppose you want to connect from there), specify as proxy server 127.0.0.1 port whatever you choose in putty.

I would say try to experiment a little bit, and you will see that everything is easier then it looks.

---

### Post by Aussiein on 2005-08-19
Hi,

Another option could be to make IPSEC based tunnel to your friends router and then   route all your traffic via the tunnel.

Similar situation was faced by me when I was in middle east as most of ISP's do filtering.

Regards

Aussiein

---

### Post by gabizu on 2006-04-07
hi!!
 i have the same problem! i am student in Romania  and a cant pass my http proxy. the only port open is 80! in windows i used freedom but now i dont know what should i do?
if you can answer me i'll be very tanksfull!!!

---

### Post by ice60 on 2006-04-12
[http://www.jmarshall.com/tools/cgiproxy/](http://www.jmarshall.com/tools/cgiproxy/)
[http://kryptonian-x.blogspot.com/2005/05/proxy-bypasser.html](http://kryptonian-x.blogspot.com/2005/05/proxy-bypasser.html)
[http://www.oreillynet.com/pub/h/4807](http://www.oreillynet.com/pub/h/4807)
Torpark might work 
[http://www.fastandloud.com/uncategorized/blocked-school-work-filter-bypass-myspace-facebook-friendster-google-orkut-yahoo-360/](http://www.fastandloud.com/uncategorized/blocked-school-work-filter-bypass-myspace-facebook-friendster-google-orkut-yahoo-360/)

---

