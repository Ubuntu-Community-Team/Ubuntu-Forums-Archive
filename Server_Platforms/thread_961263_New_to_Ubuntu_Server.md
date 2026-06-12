---
title: "New to Ubuntu Server"
date: 2008-10-28
forum: Server Platforms
---

### Post by cjwallace on 2008-10-28
Guys.

I have been playing around with Ubuntu the desktop version and have now major problems with doing what i need to do.

I want to take a look at the server version as i plan on installing Zabbix on it.

I do have a few questions to get me up and running. As the server version does not have a GUI can someone help me with the following.

1) How do i change my Network settings from DHCP to a static IP address?

2) How do i update the system will the latest patches etc 

3) How can i enable SSH from the command line so i can connect from my windows workstation with say putty.

That would get me up and running.

Thanks to anyone who can help

Cheers

Craig

---

### Post by peter_brewer on 2008-10-28
Google for most of them.

sudo apt-get update and then sudo apt-get upgrade will get you up to date.

---

### Post by cjwallace on 2008-10-28
Great thanks for the quick reply. Thats Q2 answered.

Can anyone else help me with the others.

Thanks in advance

---

### Post by conjur3r on 2008-10-28
1) [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

3) SSH should already be installed & running.  What happens when you try from Windows?

---

### Post by cjwallace on 2008-10-28
> **conjur3r said:**
> 1) [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

3) SSH should already be installed & running.  What happens when you try from Windows?

Thank you for the link for Q1 that is all sorted now.

Q2, when i try to use putty on port 22 or 222 i get a connection refused message.

Is there somewhere i need to enable it?

Craig

---

### Post by cjwallace on 2008-10-28
Not to worry guys. i had to install openssh-server and now i can connect to the server.

Cheers

Craig

---

### Post by Kellemora on 2008-10-28
Hi CJ

It would STILL be a server IF you installed a GUI on it, would it not?

TTUL
Gary

---

### Post by Iowan on 2008-10-28
Not in the eyes of a purist! [-(


Just kidding... REALLY!

---

### Post by canh_nguyen on 2008-10-29
> **cjwallace said:**
> Thank you for the link for Q1 that is all sorted now.

Q2, when i try to use putty on port 22 or 222 i get a connection refused message.

Is there somewhere i need to enable it?

Craig

Did you NAT port 22 or 222 in Router to your computer ip address?

---

### Post by jamesrfla on 2008-10-29
> **cjwallace said:**
> Thank you for the link for Q1 that is all sorted now.

Q2, when i try to use putty on port 22 or 222 i get a connection refused message.

Is there somewhere i need to enable it?

Craig

If you haven't already done this edit the SSH config file and tell it to listen on ports 22 and 222. To do this ```
gksudo gedit /etc/ssh/sshd_config
``` Then under What ports, IPs we listen for. Port 22 should be their by default. Under it just add Port 222. Then do ```
sudo nano /etc/ssh/sshd_config
``` After that you should be able to connect using port 22 and 222.

---

### Post by 080801jk on 2008-10-30
&#22320;&#19979;&#31649;&#36947;&#38271;&#26399;&#22788;&#20110;&#21322;&#23553;&#38381;&#30340;&#29366;&#24577;&#65292;[**&#28165;&#25972;&#21270;&#31914;&#27744;**](http://www.bjjjjgd.cn/qzhfc.htm)&#32570;&#23569;&#31354;&#27668;&#65292;&#27687;&#27668;&#26356;&#23569;&#12290;&#22240;&#27492;&#65292;&#21363;&#20351;&#22320;&#19979;&#26377;&#26131;&#29123;&#26131;&#29190;&#27668;&#20307;&#65292;&#20063;&#19981;&#20250;&#21457;&#29983;&#29123;&#28903;&#29190;&#28856;&#30340;&#29616;&#35937;&#12290;&#20294; &#24403;&#20117;&#30422;&#25171;&#24320;&#20197;&#21518;&#65292;&#26131;&#29123;&#26131;&#29190;&#27668;&#20307;&#19982;&#31354;&#27668;&#28151;&#21512;&#65292;&#24418;&#25104;&#29190;&#28856;&#24615;&#27668;&#20307;&#12290;&#27492;&#26102;&#22914;&#26524;&#36827;&#34892;&#31649;&#36947;&#32500;&#20462;&#21644;&#28938;&#25509;&#31561;&#20316;&#19994;&#65292;&#23601;&#20250;&#26377;&#29123;&#28903;&#29190;&#28856;&#30340;&#21361;&#38505;&#12290;&#22240;&#27492;&#65292;&#22312;&#20316;&#19994;&#21069;&#24517;&#39035;&#20808;&#29992;&#20108;&#27687;&#21270;&#30899;&#25110; &#27694;&#27668;&#36827;&#34892;&#32622;&#25442;&#12290;[**&#28165;&#25972;&#21270;&#31914;&#27744;**](http://www.bjjjjgd.cn/qzhfc.htm)&#32771;&#34385;&#20197;&#19978;&#20004;&#31181;&#27668;&#20307;&#20026;&#24816;&#24615;&#27668;&#20307;&#65292;&#32622;&#25442;&#20197;&#21518;&#65292;&#20026;&#38450;&#27490;&#22320;&#19979;&#20316;&#19994;&#20013;&#27602;&#20107;&#25925;&#30340;&#21457;&#29983;&#65292;[**&#28165;&#25972;&#21270;&#31914;&#27744;**](http://www.bjjjjgd.cn/qzhfc.htm)&#22312;&#20316;&#19994;&#21069;&#36824;&#24517;&#39035;&#36827;&#34892;&#36890;&#39118;&#12290;[**&#28165;&#25972;&#21270;&#31914;&#27744;**](http://www.bjjjjgd.cn/qzhfc.htm)&#36890;&#39118;&#26041;&#24335;&#26377;&#33258;&#28982;&#36890;&#39118;&#21644;&#24378;&#21046;&#36890;&#39118;&#20004;&#31181;&#12290;&#19968;&#33324; &#22320;&#19979;&#31649;&#36947;&#26816;&#26597;&#37319;&#21462;&#33258;&#28982;&#36890;&#39118;&#21363;&#21487;&#65292;&#24517;&#39035;&#25171;&#24320;&#38468;&#36817;3&#8212;4&#20010;&#20117;&#30422;&#65292;&#36890;&#39118;&#26102;&#38388;&#33267;&#23569;1&#23567;&#26102;&#12290;&#29305;&#27530;&#24773;&#20917;&#19979;&#65292;[**&#28165;&#25972;&#21270;&#31914;&#27744;**](http://www.bjjjjgd.cn/qzhfc.htm)&#31649;&#36947;&#30095;&#36890;&#21069;&#65292;&#36824;&#24517;&#39035;&#37319;&#29992;&#24378;&#21046;&#36890;&#39118;&#65292;&#21487;&#29992;&#40723;&#39118;&#26426;&#25509;&#19978;&#39118;&#31649;&#23454;&#26045;&#31649; &#19979;&#21561;&#39118;

---

