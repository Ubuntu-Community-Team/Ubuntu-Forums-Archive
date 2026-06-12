---
title: "vsftpd log question"
date: 2014-01-16
forum: Server Platforms
---

### Post by bob40 on 2014-01-16
Can anyone tell me what the log entry "CONNECT:Client "x.x.x.x" means?  I don't mean to sound dense, I know it means connect, but what is the difference between that and "[USER] OK LOGIN: Client "x.x.x.x"?

The reason I ask is that my vsftpd log has several CONNECT entries with no coresponding OK LOGIN entries.  I want to make sure I am not being hacked.  For the record, at least one of the recent IPs that connected but did not login was from Malaysia.  I don't know anyone who should be accessing my site from there.

Bob

---

### Post by TheFu on 2014-01-16
CONNECT is a TCP term.  Before anything can happen, there must be a connection. Login cannot happen without a connection first. Make sense?

If you run any FTP server, someone is trying to hack you. PERIOD.  The most popular FTP servers have been attacked for years, including having their source code modified in the main repository for the team.

Almost nobody should really run FTP servers anymore and definitely NOT with passwords.
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) explains. There are many, many other articles on the web that also have explanations why plain FTP is generally considered a bad protocol if security is a concern at all.

---

### Post by bob40 on 2014-01-16
I understand that people are trying to hack me.  I have set up fail2ban to help protect me.  I know nothing is foolproof.  

Can you tell me what it means if I get ONLY a CONNECT entry in the log?  I don't see the same IPs coming back over and over.

---

### Post by TheFu on 2014-01-16
People scan the internet looking for interesting services all the time.

Attacks these days seldom come from 1 IP. They use botnets to orchestrate attacks from many thousands of IPs to avoid IP-based tools from noticing the attack. It is only non-professional attackers who use fewer than 10 IPs.

Fail2ban cannot help encrypt a valid password that is transmitted without any encryption - like FTP does. Just sayin.

I don't know what those connects are - beyond some program making a connection. Could be accidental and it could be data gathering. Google found this: [http://tipstrickshack.blogspot.com/2012/12/how-to-exploit-vsftpd.html](http://tipstrickshack.blogspot.com/2012/12/how-to-exploit-vsftpd.html) and this [http://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html](http://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html)

---

### Post by bob40 on 2014-01-16
Thanks.  Looking into sftp now.

---

### Post by TheFu on 2014-01-16
sftp is built-into ssh. No other setup needed after installing the ssh-server beyond using port-translation on the WAN port of a router.  So for personal use or use by people that you trust on the internal LAN, it is fine. Be certain to disable passwords - only allow ssh-key-based connections from the internet. Also, disable root over ssh - security. fail2ban is useful for ssh/scp/sftp connection failures.
A few more ideas: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) to improve ssh/scp/sftp security.  It is possible to only allow sftp connections, preventing ssh/scp. Don't know how off the top of my head. Sorry. I know that question has been answered in these forums recently

ssh has the added benefit of using a pre-known port, so the firewall rules are much easier than with passive FTP. Since it does encrypted credentials AND data transfers, there is a small transfer performance hit.

---

