---
title: "Bizarre Apache/Tomcat redirect"
date: 2012-11-06
forum: Server Platforms
---

### Post by Number6 on 2012-11-06
Hi,

I've got a LAMP/Tomcat Ubuntu Server install running, and I also installed Railo and Mura CMS. I performed all of this installation at home with the server on my home network. Everything worked great including the Apache proxying to the Tomcat instance running Mura.
Then I took the server to it's new home at work and changed the IP on the NIC to its new public IP. Now when I try to browse to the test website it tries to redirect to the IP the server had in my home network which, of course, fails to load the site!!

Why on earth is it doing that?? I can't find anywhere in the configs where there's even a reference to that IP address.

Any help would be much appreciated as this is a serious roadblock to putting it in production.

Thanks

---

### Post by SeijiSensei on 2012-11-06
I'd start by looking at the ProxyPass and ProxyPassReverse directives in your Apache configuration.

Nice bike, by the way.  Watch out for those weather balloons.

---

### Post by Number6 on 2012-11-06
Thanks for the response,
Don't think it's that, they're just: 

ProxyPass / [http://localhost:8080](http://localhost:8080)
ProxyPassReverse / [http://localhost:8080](http://localhost:8080)

and localhost points to 127.0.0.1 like it should.

It seems to be the Tomcat side of things as if I try to browse to the server using the IP address and port 8080 (bypassing Apache) I still get redirected to 192.168.0.113:8080!

Yea those balloons just choke me up everytime :)

---

