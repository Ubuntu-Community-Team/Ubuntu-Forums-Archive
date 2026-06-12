---
title: "accessing lan via SSH in a restricted firewall"
date: 2010-05-05
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-05
Hi,
I have a computer  which  has a public IP.My ISP has allowed only port 22 for my machine to be accessed outside from internet.I want rest of my computers which are connected to this  machine be accessible via SSH on internet.I can configure IPTABLES to route different ports to internal machines but since ISP has given only one port for the gateway how can I go for it any guesses.
I came across some thing reverse SSH tunneling but that has to keep the connection alive all the time at gateway I want my trusted people to be directly able to access the machines on LAN to which they have account to login in this scenario.

---

### Post by ghost_ryder35 on 2010-05-05
have the box on lan be the bastion host, and then ssh from that host to whatever internal boxes you want

---

### Post by tapas_mishra on 2010-05-05
Thanks for the idea.I looked at [http://en.wikipedia.org/wiki/Bastion_host](http://en.wikipedia.org/wiki/Bastion_host)
and [http://www.google.co.in/search?hl=en&client=firefox-a&hs=9B1&rls=com.ubuntu%3Aen-US%3Aunofficial&q=bastion+host&meta=&aq=f&aqi=g7g-m3&aql=&oq=&gs_rfai=](http://www.google.co.in/search?hl=en&client=firefox-a&hs=9B1&rls=com.ubuntu%3Aen-US%3Aunofficial&q=bastion+host&meta=&aq=f&aqi=g7g-m3&aql=&oq=&gs_rfai=)
can you give some more hint/idea?

---

### Post by ghost_ryder35 on 2010-05-05
for example you would have bastion.yourwork.com
bastion would only run openssh-server.  It would be locked down so any attempts from unauthorized users would fail.  bastion.yourwork.com has a public IP address.
server1.yourwork.com is an email server and server2.yourwork.com is a proxy server.  both server1 and server2 would have private IP address' that bastion.yourwork.com would route to via a second network interface.  these private ip's for server1 and server2 could nat to 1 public IP or seperate public ip's depending on your accessiblity to public addresses.  
this would enable your users on the internet to be able to access bastion.yourwork.com via ssh and then they could ssh to server1.yourwork.com.

in this situtation it is common to setup the users .ssh/config file to use an ssh proxy so they can just ssh server1.yourwork.com instead of sshing to bastion and then server1.

```

Host server1.yourwork.com
user foomaster
ProxyCommand ssh bastion.yourwork.com nc server1.yourwork.com 22

```

this command uses nc to connect to server1 from bastion.  

bastion.yourwork.com - 8.8.8.8
bastion-int2.yourwork.com - 192.168.1.1
server1.yourwork.com - 192.168.1.2
server2.yourwork.com - 192.168.1.3

---

### Post by tapas_mishra on 2010-05-05
Wow thanks a lot for sharing this information.It really helped.
Is the above configuration to be done at server config or client who wants to connect from internet.


Just to test it I did from internet (I did not configured any thing at bastion host while testing)
From a machine on internet 
```
ssh user@bastion.yourwork.com nc server1.yourwork.com 22
```It did asked me password of user at server1.yourwork.com
but after that after it accepts password I have a blank screen.
If I type then some command then I get a message protocol mismatch.
Did I do some mistake.

I looked here [http://blog.chmouel.com/2009/02/08/proxycommand-ssh-bastion-proxy/](http://blog.chmouel.com/2009/02/08/proxycommand-ssh-bastion-proxy/) it confused me.
If possible give some link which you feel I should read.

---

### Post by koenn on 2010-05-05
ghost_ryder35's idea should work, but here's a different idea:

set up a vpn server to listen on port 22
set up that computer with a static route to the other hosts on your LAN, and enable IP forwarding on it

This should give you unlimited access to your entire LAN
(didn't try it myself, YMMV)

downside : you loose (internet) ssh access to the internet-connected computer (because port 22 is in use by openvpn). You can probably work around that by having openssh-server listen on a different port, and access it through the tunnel. This might require a bit of work.

---

### Post by tapas_mishra on 2010-05-05
> **koenn said:**
> ghost_ryder35's idea should work,
Yes it did worked.I was about to edit the message but then checked your message.Thanks for the information .The mistake I was doing was I created .ssh/config on the Bastion host itself then I tested it failed.Then I removed this and thinking that I need to create a user at bastion host I added a user and in its .ssh/config I added that.Third time it did not connected I edited the .ssh/config of client on internet which he pointed and voilla I was able to connect.
You will be asked for 2 passwords first the client will connect to Bastion host and you need to have a first password ready for that.
> **koenn said:**
> 
downside : you loose (internet) ssh access to the internet-connected computer (because port 22 is in use by openvpn). You can probably work around that by having openssh-server listen on a different port, and access it through the tunnel. This might require a bit of work.
I got your point.You mean to say connect via VPN to some machine on LAN from internet and then this machine which I am using as Bastion do an SSH or like that from the LAN since on internet it lost ssh connection.
Actually configuring client to use .ssh/config will not be easy not difficult for me but some may be using Putty.

---

### Post by ghost_ryder35 on 2010-05-05
> **tapas_mishra said:**
> Wow thanks a lot for sharing this information.It really helped.
Is the above configuration to be done at server config or client who wants to connect from internet.


Just to test it I did from internet (I did not configured any thing at bastion host while testing)
From a machine on internet 
```
ssh user@bastion.yourwork.com nc server1.yourwork.com 22
```It did asked me password of user at server1.yourwork.com
but after that after it accepts password I have a blank screen.
If I type then some command then I get a message protocol mismatch.
Did I do some mistake.

I looked here [http://blog.chmouel.com/2009/02/08/proxycommand-ssh-bastion-proxy/](http://blog.chmouel.com/2009/02/08/proxycommand-ssh-bastion-proxy/) it confused me.
If possible give some link which you feel I should read.

you cant run the proxy command like that.   if you want to run it on the command line you must run it like this.

```

foo@ubuntu:~$ ssh bastion.yourwork.com -o 'ProxyCommand nc server1.yourwork.com 22'

```

and yes you would do this from the client side.  running from the command line is a pain, so i recommend adding it to your .ssh/config in the manner i described in previous post.

---

### Post by tapas_mishra on 2010-05-05
That line user no where came into picture.I am confused for that.
From my client when I connect with .ssh/config as mentioned above 
it asks me to enter a password for a username which does not exist on Bastion host in fact it asks me to enter password of username that I am having on the client machine on internet which is obviously not present on Bastion host.
For the time being I want to use from command line 
since user may be using SSH to their machines it will otherwise always use Bastion Host as proxy when not required also.
I read man page of SSH after this post
```

ssh dummy@bastionhost.myserver.com -o 'User Bob ProxyCommand nc internal1.myserver.com 22'


```
Got following error
```

command-line line 0: garbage at end of line; "ProxyCommand".
```
I tested that config file it worked well.Want to test command line.
It is two way I mean first I authenticate at Bastion Host then authenticate inside also.
Can't it be reduced to one.
Want to test VPN also as** koenn** said.

---

### Post by koenn on 2010-05-05
> **tapas_mishra said:**
> 
I got your point.You mean to say connect via VPN to some machine on LAN from internet and then this machine which I am using as Bastion do an SSH or like that from the LAN since on internet it lost ssh connection.
Actually configuring client to use .ssh/config will not be easy not difficult for me but some may be using Putty.
that would be one way of doing it. It might also be possible to connect, from internet, through the tunnel, to the LAN-interface address of the 'bastion'/vpn server (on a different port than 22), if it's set up to route between the tunnel interface and the LAN interface, and openssh-server is configured to accept connections on that address & port. I see how that would work, theoretically, but I've never tried it.

---

### Post by tapas_mishra on 2010-05-05
I found useful 
[http://www.mind-download.com/2009/05/setting-up-ssh-to-create-transparent.html](http://www.mind-download.com/2009/05/setting-up-ssh-to-create-transparent.html)
The problem is Gateway does have a public IP but only port 22 is opened at a firewall which is by ISP.So any one who has to connect has to do an SSH.Is it not possible to have some PHP website running on gateway at port 22 which logs in and after login gives a bash shell on desired machine on LAN.If yes then how ?

---

### Post by ghost_ryder35 on 2010-05-05
> **tapas_mishra said:**
> That line user no where came into picture.I am confused for that.
From my client when I connect with .ssh/config as mentioned above 
it asks me to enter a password for a username which does not exist on Bastion host in fact it asks me to enter password of username that I am having on the client machine on internet which is obviously not present on Bastion host.
For the time being I want to use from command line 
since user may be using SSH to their machines it will otherwise always use Bastion Host as proxy when not required also.
I read man page of SSH after this post
```

ssh dummy@bastionhost.myserver.com -o 'User Bob ProxyCommand nc internal1.myserver.com 22'


```
Got following error
```

command-line line 0: garbage at end of line; "ProxyCommand".
```
I tested that config file it worked well.Want to test command line.
It is two way I mean first I authenticate at Bastion Host then authenticate inside also.
Can't it be reduced to one.
Want to test VPN also as** koenn** said.

usually you "remove it" by setting up SSH keys on the client and server.  so when you login from client you have your ssh private key open with a tool like kde-wallet or pageant, then when you ssh in to bastion, it uses ssh-key auth instead of password auth, then when you nc to server1 it will also use the ssh-key auth so no password is needed other than to open your ssh-private key on the client one time.

---

### Post by tapas_mishra on 2010-05-06
Ya even the same idea came to my mind having keys.There may be some users who may not understand this.Is it possible to generate rsa keys on a SSH client like Putty and doing .ssh/config etc.

---

### Post by windependence on 2010-05-06
So port 22 is the ONLY port open to the outside? Is port 443 open for ssl connections? You could always run your ssh daemon on 443 and go out through that port.

-Tim

---

### Post by tapas_mishra on 2010-05-06
Yes only 22 is open for outside no 443.Any other port is not open.
If some how I can give my team a web based access to internal lan like some thing [http://myserver.com:22](http://myserver.com:22) (using DynDNS ) then SSH to LAN and command prompt working in browser that will help.I just have the idea may be you people can point me what should I look in or search.

---

### Post by spynappels on 2010-05-06
Can I just clarify, is it only inbound connections which are firewalled with port 22 open, or are all outbound connections also blocked? Are Related and Established connections allowed inbound on other ports?

If the above is the case, setting up a VPN server to listen on port 22 would be the only reasonable option I think. 

If the above is not the case, have SSH listening on that port, SSH into the server listening there and SSH from there to other servers on the LAN, in one of the ways suggested earlier.

---

### Post by tapas_mishra on 2010-05-06
> **spynappels said:**
> Can I just clarify, is it only inbound  connections which are firewalled with port 22 open, or are all outbound  connections also blocked? 


Blocked.

---

### Post by ghost_ryder35 on 2010-05-06
> **tapas_mishra said:**
> Yes only 22 is open for outside no 443.Any other port is not open.
If some how I can give my team a web based access to internal lan like some thing [http://myserver.com:22](http://myserver.com:22) (using DynDNS ) then SSH to LAN and command prompt working in browser that will help.I just have the idea may be you people can point me what should I look in or search.

this is what you are looking for.  You will obviously have to change SSH to listen on another port on bastion.yourwork.com since this web service will be running there.  I recommend using SSL when implementing this.
[http://blog.thebartels.de/2006/12/11/howto-ajax-based-ssh-client-for-your-debianplesk-setup-ajaxterm/](http://blog.thebartels.de/2006/12/11/howto-ajax-based-ssh-client-for-your-debianplesk-setup-ajaxterm/)

---

### Post by tapas_mishra on 2010-05-06
Thanks for the link.It did help. I have a doubt any connection coming from internet is to go through port 22 only so if I install AjaxTerm on the SSH server I make SSH listen on some other port but when the ISP has blocked all ports but not port  22 then wouldn't all this fail.

---

### Post by ghost_ryder35 on 2010-05-06
> **tapas_mishra said:**
> Thanks for the link.It did help. I have a doubt any connection coming from internet is to go through port 22 only so if I install AjaxTerm on the SSH server I make SSH listen on some other port but when the ISP has blocked all ports but not port  22 then wouldn't all this fail.

nothing will fail if you make bastion.yourwork.com openssh server listen on localhost:2222 and then configure apache to listen on public_interface:22.
Then user would connect like this
firefox -> [https://bastion.yourwork.com:22/whereverAjaxTermlives](https://bastion.yourwork.com:22/whereverAjaxTermlives)

---

### Post by CharlesA on 2010-05-06
I don't know if it will help, but I've got only one port open on my gateway and SSH in thru it, then tunnel over to the other machines: RDP, VNC, SSH, whatever.

Haven't had any problems with that, but I don't know what exactly you are trying to accomplish.

---

### Post by ghost_ryder35 on 2010-05-06
> **CharlesA said:**
> I don't know if it will help, but I've got only one port open on my gateway and SSH in thru it, then tunnel over to the other machines: RDP, VNC, SSH, whatever.

Haven't had any problems with that, but I don't know what exactly you are trying to accomplish.

touché

---

### Post by CharlesA on 2010-05-06
Could probably connect via SSH then tunnel AJAX over it on a different port, perhaps.

I don't know if that would be too much of a pain or not.

---

### Post by tapas_mishra on 2010-05-06
> **CharlesA said:**
> I don't know if it will help, but I've got only one port open on my gateway and SSH in thru it, then tunnel over to the other machines: RDP, VNC, SSH, whatever.

Haven't had any problems with that, but I don't know what exactly you are trying to accomplish.

I am trying to give some one on internet access to one specific IP on my machine which is on LAN and the authentication should not be twice only one time they should not know that they first logged in to bastion host and then they are redirected to some other IP on LAN.This using a web interface so that if they are behind some proxy or firewall they do not need to bother at least they always have http access.My gateway has public IP but only port 22 is opened by ISP .So I am trying to have some thing that runs on my bastion host or you can call it as a gateway and it redirects the incoming SSH to a machine on LAN but it should not be a two times authentication only once.
As some one suggested above to open port 443 by ISP it seems a good idea.I would like to try that too by talking with ISP.
Then they can do an FTP the machine they are connected or what ever shell command they want to use.

---

### Post by ghost_ryder35 on 2010-05-06
> **tapas_mishra said:**
> I am trying to give some one on internet access to one specific IP on my machine which is on LAN and the authentication should not be twice only one time they should not know that they first logged in to bastion host and then they are redirected to some other IP on LAN.This using a web interface so that if they are behind some proxy or firewall they do not need to bother at least they always have http access.My gateway has public IP but only port 22 is opened by ISP .So I am trying to have some thing that runs on my bastion host or you can call it as a gateway and it redirects the incoming SSH to a machine on LAN but it should not be a two times authentication only once.
Then they can do an FTP the machine they are connected or what ever shell command they want to use.

You have wrong assumptions here.

since you would have to configure this service on 22, it does not matter whether they use putty or firefox, if they are behind a firewall and that firewall does not allow port 22 out they wont be able to get to bastion.yourwork.com no matter what.

Also while they are using the Web interface say the Ajax solution I provided they would not be able to ftp or whatnot to their client machine from the server.

If they need to be able to ftp you are looking at a much more complicated setup, you would be better off with scp since 22 is already open.

---

### Post by tapas_mishra on 2010-05-06
> **ghost_ryder35 said:**
>  since you would have to configure this service on 22, it does not matter whether they use putty or firefox, if they are behind a firewall and that firewall does not allow port 22 out they wont be able to get to bastion.yourwork.com no matter what.Ok thanks for pointing that out.
> **ghost_ryder35 said:**
> 
Also while they are using the Web interface say the Ajax solution I provided they would not be able to ftp or whatnot to their client machine from the server.Ya that I understand while experimenting ajax just this idea came.Which I feel will be possible some how.


> **ghost_ryder35 said:**
> 
If they need to be able to ftp you are looking at a much more complicated setup, 
Since you pointed it out any ideas as to how to make this possible.
 I do not have port 80 open by my ISP
and what about shellinabox
[https://help.ubuntu.com/community/shellinabox](https://help.ubuntu.com/community/shellinabox)
is it any way helpful in my scenario assuming I configure a reverse proxy at port 22 using Apache.

---

### Post by ghost_ryder35 on 2010-05-06
> **tapas_mishra said:**
> Ok thanks for pointing that out.
Ya that I understand while experimenting ajax just this idea came.Which I feel will be possible some how.



Since you pointed it out any ideas as to how to make this possible.
 I do not have port 80 open by my ISP.So...

you are limited with your abilities since you only have 22 open by the ISP.  i'd recommend home brewing an  apache mod_jk setup that looks at packets coming in and then using mod_proxy to send them to their final destination, that way you can kind of have multiple services running on port 22.  but this is getting into a huge hodge podge of a mess and very hard to support/troubleshoot.  i'd just stick with having SSH running on that port and educating your users how to use it, otherwise work with your ISP to get other ports open.

---

### Post by CharlesA on 2010-05-06
> **ghost_ryder35 said:**
> you are limited with your abilities since you only have 22 open by the ISP.  i'd recommend home brewing an  apache mod_jk setup that looks at packets coming in and then using mod_proxy to send them to their final destination, that way you can kind of have multiple services running on port 22.  but this is getting into a huge hodge podge of a mess and very hard to support/troubleshoot.  i'd just stick with having SSH running on that port and educating your users how to use it, otherwise work with your ISP to get other ports open.
This would probably be the best thing to do.

It might be possible to have muliple services running on port 22, but it would just be a huge mess to support and configure.

---

### Post by tapas_mishra on 2010-05-06
> **ghost_ryder35 said:**
> otherwise work with your ISP to get other ports open.
Not possible :(

---

