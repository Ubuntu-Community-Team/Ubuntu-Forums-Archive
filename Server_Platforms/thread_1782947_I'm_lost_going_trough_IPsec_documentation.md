---
title: "I'm lost going trough IPsec documentation"
date: 2011-06-15
forum: Server Platforms
---

### Post by tapi0n on 2011-06-15
So I need to make an IPsec vpn. I've been told to use [Shrew Soft]("http://www.shrew.net/"). But I'm completely lost on where to begin. I've gone trough the documentation and stuff but I have no idea what to do next. 

I can't find anything on the site how to install or configure the shrewsoft shizzle. The only thing I could use is something about ipsec-tools because all the rest is using a graphical interface (which ofc I'm not seeing how I'm using a server edition).

Could anyone help me out?

---

### Post by SeijiSensei on 2011-06-15
To be honest, I never could figure out how to set up an IPSEC system.  That's why I opted for OpenVPN.  If this is a business application, I think you should give serious consideration to buying an appliance for this task.  A product like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124092) is probably going to cost less in the long run than having you configure something in Linux that you're not sure about.  There's also the issue of support if something doesn't work right, or you leave.

---

### Post by tapi0n on 2011-06-15
Although I completely understand your sentiment (it's a real pain in the knees), I have to admit the cisco thingy looks really nice but it's not an option.

Guess I will keep on tinkering :) Cheers anyway

---

### Post by koenn on 2011-06-15
> **SeijiSensei said:**
> To be honest, I never could figure out how to set up an IPSEC system.  That's why I opted for OpenVPN.  
Same here. IPsec is notoriously difficult and error-prone, partly because it acts at IP level, and thus interferes with 'normal" network troubleshooting tools.

Openvpn kinda fixed that. 


> **tapi0n said:**
> So I need to make an IPsec vpn. I've been told to use [Shrew Soft]("http://www.shrew.net/"). But I'm completely lost on where to begin. I've gone trough the documentation and stuff but I have no idea what to do next. 

I can't find anything on the site how to install or configure the shrewsoft shizzle. The only thing I could use is something about ipsec-tools because all the rest is using a graphical interface (which ofc I'm not seeing how I'm using a server edition).

Could anyone help me out?

Obviously, you'll have to set up a "server" or a "gateway" that your Shrew Soft clients can connect to. ipsec-tools is apparently just a set of tools (:)) so they'll be of no use unless you know ipsec and how to set it up.

I think the Openswan documentation  on the shrewsoft should give you an idea of what your aiming for, server-side  : a method to generate keys or certs, and a server config to accept connections from, authenticate, and push config to the clients.

If you don't want or can't install openswan (I think the project has been abandoned because everyone switched to openvpn, for reasons stated above), at least it can serve as a guideline for what you have to accomplish on the server, using ipsec-tools and possibly some other software (s.a. openssl).

---

### Post by tapi0n on 2011-06-16
Thing is, there are two firewalls I need to get trough. From what I get the certificates (keys) are generated on the firewalls. And I'm not quite sure how to interprit this. So compared to a normal vpn tunnel (say pptp) the tunnel is created between the two firewalls and not between two machines?

---

