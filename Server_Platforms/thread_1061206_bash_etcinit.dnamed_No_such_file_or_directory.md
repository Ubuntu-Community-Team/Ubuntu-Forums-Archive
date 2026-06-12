---
title: "bash: /etc/init.d/named: No such file or directory"
date: 2009-02-05
forum: Server Platforms
---

### Post by Go_Big_Blue on 2009-02-05
I have been following the [www.howtoforge.com](www.howtoforge.com) website for setting up NAT, iptables, port forwarding, DNS and DHCP.  ([http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server))

About half-way through this whole setup up (at the point where it says to do a 'nslookup macpro') things start to get a little squirrely - actually a whole lot of squirrely!!! 

For example,
I typed in hostname -f at the command line and it returned: 'AOPserver1.AOP1.com'

So then I typed in the following:
[B]root@AOPserver1:/etc/bind/zones# nslookup 10.4.16.4
Server:		205.152.37.23
Address:	205.152.37.23#53

** server can't find 4.16.4.10.in-addr.arpa.: NXDOMAIN

root@AOPserver1:/etc/bind/zones# nslookup macpro
Server:		205.152.37.23
Address:	205.152.37.23#53

** server can't find macpro: NXDOMAIN

root@AOPserver1:/etc/bind/zones# cd
root@AOPserver1:~# host server
Host server not found: 3(NXDOMAIN)
root@AOPserver1:~# host 192.168.1.1
Host 1.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)
root@AOPserver1:~# host aop1.com
Host aop1.com not found: 3(NXDOMAIN)
root@AOPserver1:~# nslookup server
Server:		205.152.37.23
Address:	205.152.37.23#53

** server can't find server: NXDOMAIN

root@AOPserver1:~# nslookup 192.168.1.1
Server:		205.152.37.23
Address:	205.152.37.23#53

** server can't find 1.1.168.192.in-addr.arpa.: NXDOMAIN [/B]


So then I found on a forum on the web that I could try to edit the /etc/resolv.conf file.  So I did, and then I got the following:

**root@AOPserver1:~# pico /etc/resolv.conf ** (this is where I edited the file)
[B]root@AOPserver1:~# nslookup 10.4.16.4
Server:		10.4.16.42
Address:	10.4.16.42#53

4.16.4.10.in-addr.arpa	name = macpro.AOP1.com.

root@AOPserver1:~# nslookup 10.4.16.4
Server:		10.4.16.42
Address:	10.4.16.42#53

4.16.4.10.in-addr.arpa	name = macpro.AOP1.com.

root@AOPserver1:~# nslookup macpro
Server:		10.4.16.42
Address:	10.4.16.42#53

Name:	macpro.AOP1.com
Address: 10.4.16.4[/B]

So at this point my level of frustration is down (but only for a little while as we shall soon see).  So then I continue to follow the guide from [www.howtoforge.com](www.howtoforge.com).  It says to run the command 'named' to start named.  So I enter the following:

[B]root@AOPserver1:~# sudo /etc/init.d/named start
sudo: /etc/init.d/named: command not found[/B]

Then the tutorial says that if it doesn't start to check the /var/logs.  Okay - well the dang thing doesn't exist, so there is nothing in the /var/logs to check!!!!  But funny thing is ... earlier in the tutorial they had you edit the file /etc/bind/named.conf.

I am extremely frustrated at this point and ready to call off this whole setup!!! Ubuntu prides itself on being user friendly, but I find it to be more user frustrating than anything.  

Would one of you kind-hearted and intelligent individuals out there please help me get this problem fixed?  Thanking you in advance.

---

### Post by bluefrog on 2009-02-05
If you don't know how to use a saw on a log, you blame the log? The saw? or you?

Why should it be different with computers.

You are working with a server. It takes some time to learn, if you can learn.

End users do not play with windows servers either.

try bind9 instead of named

---

### Post by albinootje on 2009-02-05
> **Go_Big_Blue said:**
> 
[B]root@AOPserver1:~# sudo /etc/init.d/named start
sudo: /etc/init.d/named: command not found[/B]

Should be :
```

/etc/init.d/bind9 restart

```
See here :
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
> 
Then the tutorial says that if it doesn't start to check the /var/logs.  Okay - well the dang thing doesn't exist
Look in the /var/log directory.
> 
I am extremely frustrated at this point and ready to call off this whole setup!!! Ubuntu prides itself on being user friendly, but I find it to be more user frustrating than anything.

I've never read that the server edition of Ubuntu is suppose to be easy, where did you read that ?
And "more user frustrating than anything" ? Try Gentoo Linux, or LFS, or Arch Linux or Slackware Linux as a server, that will probably cost you more time and energy for setting up a server.

---

### Post by Go_Big_Blue on 2009-02-05
/etc/init.d/bind9 restart worked.  Thank you for the help.  I appreciate it.
I guess that what they had posted on the web was a typo.  

> **albinootje said:**
> 
I've never read that the server edition of Ubuntu is suppose to be easy, where did you read that ?
And "more user frustrating than anything" ? Try Gentoo Linux, or LFS, or Arch Linux or Slackware Linux as a server, that will probably cost you more time and energy for setting up a server.

I guess I haven't found it "written" anywhere.  It just seems to be the impression from the Ubuntu home page.  Maybe it should come with a disclaimer like "WARNING! Before you consider moving to the Ubuntu platform, please memorize the handy little Unix book "Unix is a Four Letter Word" written by Christopher Taylor because it is not for the faint of heart."

"About Ubuntu

Ubuntu is a community developed, Linux-based operating system that is perfect for laptops, desktops and servers. It contains all the applications you need - a web browser, presentation, document and spreadsheet software, instant messaging and much more."

---

### Post by Go_Big_Blue on 2009-02-05
> **bluefrog said:**
> If you don't know how to use a saw on a log, you blame the log? The saw? or you?

Why should it be different with computers.

You are working with a server. It takes some time to learn, **_if you can learn._**

End users do not play with windows servers either.

try bind9 instead of named

Bluefrog - you're an a$$.  Your insulting comments are neither helpful nor appreciated.  All you needed to put was the last line of your reply.:evil:  

Obviously the website had a typo.  However, not being familiar with the language of Unix or what was trying to be accomplished by what they had written, how are you supposed to figure it out.  I started this project to do just what you insinuated that I could not - LEARN.  I am learning this system, however, I did not feel that it would be this difficult to work through some of the details.

---

### Post by albinootje on 2009-02-05
> **Go_Big_Blue said:**
> /etc/init.d/bind9 restart worked.  Thank you for the help.  I appreciate it.
I guess that what they had posted on the web was a typo.  

I find bind sometimes a little annoying to work with, the package is called bind, the init script is called /etc/init.d/bind9, the  
process when started it called named I think, and the main config file is /etc/bind/named.conf.
Also.. RedHat, Fedora, Centos, and afair also Mandriva, use /etc/init.d/httpd for starting apache, which I've always found strange.
It is possible that those Linux distributions also use /etc/init.d/named for the init script name.
> 
I guess I haven't found it "written" anywhere.  It just seems to be the impression from the Ubuntu home page.  Maybe it should come with a disclaimer like "WARNING! Before you consider moving to the Ubuntu platform, please memorize the handy little Unix book "Unix is a Four Letter Word" written by Christopher Taylor because it is not for the faint of heart."

"About Ubuntu

Ubuntu is a community developed, Linux-based operating system that is perfect for laptops, desktops and servers. It contains all the applications you need - a web browser, presentation, document and spreadsheet software, instant messaging and much more."

I assume that "easy" for Ubuntu is meant for the desktop edition.
And I find Debian and Ubuntu pretty nice for servers, but DNS with bind is really not easy at all for beginners, and my own bind/named DNS knowledge is still pretty basic.

---

### Post by Go_Big_Blue on 2009-02-05
> **albinootje said:**
> 
I assume that "easy" for Ubuntu is meant for the desktop edition.
And I find Debian and Ubuntu pretty nice for servers, but DNS with bind is really not easy at all for beginners, and my own bind/named DNS knowledge is still pretty basic.

True - the desktop edition is fairly easy to use.  My 14yr old boys have already learned to use the Ubuntu Desktop Edition on their pc (as I burned over the Windows Edition entirely).  They are pretty happy with it, as well as I since I don't have to worry too much about viruses and the like.

Once again, thank you for the help.  Much appreciated.

---

