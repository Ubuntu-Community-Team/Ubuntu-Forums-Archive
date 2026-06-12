---
title: "SendEmail problem"
date: 2014-06-18
forum: Server Platforms
---

### Post by Carlos Pena on 2014-06-18
Hello guys,

I need some help.

I use sendemail command to send emails from my ubuntu 12.04 server with no problem at all. Recently i installed a proxy server(in separated windows machine) to control internet access. In order to access internet from the ubuntu server for apt-get I use the environment variables http_proxy="user:pass@proxyserverip:port". Every works fine with the apt-get and proxy, but i can not send emails with the sendemail.  Is there any way to be able to send an email when i am using the proxy server?

sendEmail -f "fromemailaccount" -t "toemailacount" -u "test" -m "test message" -s "isp_smtp_server" -o -xu "ispUserId" -xp "ispPassword"

Any help will be appreciated.

Regards,

Carlos
Santo Domingo, 
Dominican Republic

---

