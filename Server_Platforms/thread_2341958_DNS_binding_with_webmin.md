---
title: "DNS binding with webmin"
date: 2016-11-02
forum: Server Platforms
---

### Post by waqarr on 2016-11-02
i want to help about DNS name server binding 

i've VPS with webmin. i setup DNS Binding Server correctly. now i want to know 2 questions

1: now is there need to add "A Record" to webmin DNS server ip in godaddy domain? 
2: is there forward sub domains ns1.domain.tld, ns2.domain.tld to my webmin server ip? or just add "A Record" only 

sorry my english is not high. try to understand what i want. expert help need 

i want to make a webmin hosting server. no need other open source panel. just help require on webmin

---

### Post by cariboo on 2016-11-02
Moved to server platforms.

---

### Post by darkod on 2016-11-03
Sorry, but I failed to understand what you are trying to do. To have your own dns nameservers?

First, webmin is not supported or recommended. You are better trying to administer the server on the command line using ssh session. And in any case make sure you do not open webmin to the whole world, only to your home/work public IP. You do have a firewall running on the VPS right?

For the dns part, you will need to create zones in bind for each domain you want to control dns for. After that, in the domain's registrar CP set the nameserver(s) to be your own nameservers. That way the domain.tld will use these nameservers.

It's not necessary to specify A records for the nameservers because they are usually configured by public IP, not by FQDN. But you can create A record for the VPS in one of your domains if you want to. That way you can also use FQDN instead of only public IP.

---

