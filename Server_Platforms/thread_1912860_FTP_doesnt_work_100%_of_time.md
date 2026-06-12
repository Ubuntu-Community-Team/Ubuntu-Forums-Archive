---
title: "FTP doesnt work 100% of time?"
date: 2012-01-21
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-21
Hey everyone,
I recently installed vsftpd and had it working via LAN. But it doesnt work all of the time... Why is it doing this? :( I have both port 20 and 21 open on my router. I also cant get it to connect over the internet from another location. Can someone please help?!?

---

### Post by 2F4U on 2012-01-21
Probably no software works 100% of the time. What exactly are the symptoms when it doesn't work? Do you get an error message?

---

### Post by Rob_H on 2012-01-21
> **TFroehlich3 said:**
> Hey everyone,
I recently installed vsftpd and had it working via LAN. But it doesnt work all of the time... Why is it doing this? :( I have both port 20 and 21 open on my router. I also cant get it to connect over the internet from another location. Can someone please help?!?

FTP is a nightmare from a NAT/firewall perspective, particularly if you're dealing with a consumer-grade router. Depending on configuration, either the client or the server is expected to accept data connections to arbitrary ports. Its possible to configure vsftpd to use a constrained set of ports and then open those up on your firewall, but this makes your server susceptible to [hijacking attacks]("http://scarybeastsecurity.blogspot.com/2009/02/vsftpd-210-released.html"), especially if you don't use SSL or your clients don't support SSL session reuse.

My suggestion is to use SFTP (SSH File Transfer Protocol) instead of FTP if you can. It's easier from a firewall setup perspective and more secure than FTP. Although if you're running an anonymous FTP server, SFTP is probably not an option.

---

### Post by TFroehlich3 on 2012-01-21
> **Rob_H said:**
> FTP is a nightmare from a NAT/firewall perspective, particularly if you're dealing with a consumer-grade router. Depending on configuration, either the client or the server is expected to accept data connections to arbitrary ports. Its possible to configure vsftpd to use a constrained set of ports and then open those up on your firewall, but this makes your server susceptible to [hijacking attacks]("http://scarybeastsecurity.blogspot.com/2009/02/vsftpd-210-released.html"), especially if you don't use SSL or your clients don't support SSL session reuse.
 
My suggestion is to use SFTP (SSH File Transfer Protocol) instead of FTP if you can. It's easier from a firewall setup perspective and more secure than FTP. Although if you're running an anonymous FTP server, SFTP is probably not an option.
 
I am not running a anonymous FTP, I will just go ahead and try SFTP. Can you please direct me to a helpful guide that I can walk through?

---

### Post by TFroehlich3 on 2012-01-21
> **2F4U said:**
> Probably no software works 100% of the time. What exactly are the symptoms when it doesn't work? Do you get an error message?
 
 
I just can't connect to the FTP server, LAN or web. The connection just times out. But when I reboot the system multiple times it will work for awhile, but then the connections just start timing out and not letting me connect....

---

### Post by TFroehlich3 on 2012-01-21
Oh, and the router I am using is a Linksys WRT54G, flashed with DD-WRT firmware.

---

### Post by kevinthecomputerguy on 2012-01-22
+1 on sftp, NAT will break your ftp everytime

[http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)

---

### Post by aquarius18 on 2012-01-22
I have been using FileZilla with SFTP for 'ages' - never had a single problem. Worth a try.

---

### Post by kevinthecomputerguy on 2012-01-22
+1 Filezilla

---

### Post by HermanAB on 2012-01-22
Howdy,

It sounds like you have an underlying network problem.  FTP or any other service for that matter, requires that you have your network and routing under control, otherwise you are just wasting your time.

FTP *can* work with a firewall if you use either a demilitarized zone or a FTP connection tracker.  FTP is one of the oldest file protocols and has been around for about 40 or 50 years, so of course it can work reliably and securely, if you know what you are doing.

So, if you cannot connect to the FTP server, confirm that the service is actually running and that you are using the correct IP address etc.

---

### Post by TFroehlich3 on 2012-01-22
> **kevinthecomputerguy said:**
> +1 on sftp, NAT will break your ftp everytime
 
[http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)
 
How can I get that WebMin installed so I can have a GUI interface like that from another computer?

---

### Post by kevinthecomputerguy on 2012-01-22
try the homepage
[http://woodel.com](http://woodel.com)

---

### Post by Rob_H on 2012-01-22
> **TFroehlich3 said:**
> I am not running a anonymous FTP, I will just go ahead and try SFTP. Can you please direct me to a helpful guide that I can walk through?

If you have an SSH server installed, then you've already got SFTP available. If not, just install OpenSSH server with:

```

sudo apt-get install openssh-server

```

SSH listens on port 22 by default, but if you're going to access it over the Internet, I suggest you open a high numbered port on your router and forward it to port 22 on the server to help avoid drive-by attacks. But more importantly, make sure you have strong passwords on all user accounts that have shell access. (There are all sorts of ways you can configure SSH for even better security. Strong passwords are just the simplest.)

If yuou want a good GUI SFTP client, FileZilla is cross-platform and works well, as others have mentioned.

---

### Post by TFroehlich3 on 2012-01-22
> **kevinthecomputerguy said:**
> try the homepage
[http://woodel.com](http://woodel.com)

Alright, so I got everything setup, the Webmin and the SFTP, now, how can I access it from a remote location. I went in and opened port 22 on my router. At least I think I did it right. But I still can't connect via remote location. Any suggestions?

---

### Post by kevinthecomputerguy on 2012-01-23
host =
sftp://wan_name_or_wan_ip

port # = 22

---

### Post by TFroehlich3 on 2012-01-23
> **kevinthecomputerguy said:**
> host =
sftp://wan_name_or_wan_ip

port # = 22

I did that... Hmm... And all I do to open port 22 is go and name the Application anything I want, and then open from port 22 to port 22 along with the IP of the machine, correct?

---

### Post by kevinthecomputerguy on 2012-01-23
Those steps sound right to me

---

