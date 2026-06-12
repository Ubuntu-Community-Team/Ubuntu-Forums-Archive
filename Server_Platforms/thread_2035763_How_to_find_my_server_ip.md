---
title: "How to find my server ip?"
date: 2012-07-31
forum: Server Platforms
---

### Post by targett on 2012-07-31
I just installed 10.10 server and webmin but i dont know how to find what my server ip is so i can login to webmin from my desktop pc.
 
Thanks

---

### Post by Habitual on 2012-07-31
try ```
https://localhost:10000
```

---

### Post by LHammonds on 2012-07-31
So you setup a server and let it use DHCP?

If you can access the console, type "ifconfig" and it will show a summary of the network connections you have.  Typically, eth0 is your network card and "lo" is the local (internal only) loopback device.  Look at the eth0 (or whatever) device and see what the "inet addr" is set to.

I'd recommend changing your dynamic IP (DHCP) to a static IP so you always know where to access your server remotely (from your desktop PC).  The IP would need to be similar to what the DHCP server sends out but in a range where the DHCP server will not overlap.  For example, if your DHCP server hands out 192.168.1.2, 192.168.1.3, etc. addresses, use a high number such as 192.168.1.200 for your static IP.

LHammonds

---

### Post by targett on 2012-07-31
Thanks i will try these later, on my dlink router it let me set up a DNS for free. I chose targett.dlinkddns.com hopfully there is away i can set it up so i just type that address in to access my server from over the internet?
 
Thanks again

---

### Post by targett on 2012-07-31
right even when i put in the ip 192.168.1.101 i still get nothing. Any ideas? or [https://localhost:10000](https://localhost:10000) dont work eather

---

### Post by ian dobson on 2012-07-31
Hi,

from the terminal type

ifconfig 

Regards
Ian Dobson

---

### Post by targett on 2012-07-31
> **ian dobson said:**
> Hi,

from the terminal type

ifconfig 

Regards
Ian Dobson

Hi, ive done that and it says 192.168.0.103 but when i type that in my browser i get nothing, so im a tad lost lol

---

### Post by nbetham on 2012-07-31
The address you need depends on whether you are trying to access it from your LAN or from the Internet. If it's from your LAN then the 192 address should work. If it's from the internet you will need the external IP of your router and the port forwarded on the router to the server for the service you are trying to access from the internet.

Regards,
Neil

---

### Post by targett on 2012-07-31
it is from my home pc i followed this guide [http://aminesoft.wordpress.com/2009/04/05/how-to-install-guidesktop-and-webmin-on-ubuntu-server/](http://aminesoft.wordpress.com/2009/04/05/how-to-install-guidesktop-and-webmin-on-ubuntu-server/)
Think im going to reinstall the server 10.10 and start again

---

### Post by nbetham on 2012-07-31
So just for clarification you are trying to access your server locally from a PC on the same network as the server?

---

### Post by targett on 2012-07-31
yes, when i type ifconfig i get the following

inet addr:192.168.0.103

---

### Post by nbetham on 2012-07-31
And you tried typing in [http://192.168.0.103:10000/](http://192.168.0.103:10000/) in your browser? If that doesn't work try typing netstat -l in the terminal on the server and look at the results for the "Active Internet connection (only servers)" section if there isn't a *:10000 listed in the local address list then it is likely that webmin isn't running or the install didn't finish properly. If it is listed you might have a problem with your firewall blocking outside connections to the server.

---

### Post by targett on 2012-07-31
> **nbetham said:**
> And you tried typing in [http://192.168.0.103:10000/](http://192.168.0.103:10000/) in your browser? If that doesn't work try typing netstat -l in the terminal on the server and look at the results for the "Active Internet connection (only servers)" section if there isn't a *:10000 listed in the local address list then it is likely that webmin isn't running or the install didn't finish properly. If it is listed you might have a problem with your firewall blocking outside connections to the server.

in local address i have the following...

tcp 0 0 *:ssh
tcp6 0 0 [::]:ssh
udp 0 0 *:bootpc

---

### Post by ubudog on 2012-07-31
Could you post the output of: 
```
ps ax | grep webmin
```

---

### Post by targett on 2012-07-31
> **ubudog said:**
> Could you post the output of: 
```
ps ax | grep webmin
```

936 tty1 S+ 0:00 grep --color=auto webmin

---

### Post by nbetham on 2012-07-31
Ok so judging by the looks of that netstat Webmin isn't running. If it was you should see an entry for *.10000 . I would try 'sudo service webmin restart' and try accessing the ip:10000 in the web browser again and check netstat again to see if it is actually listening on 10000.

---

### Post by targett on 2012-07-31
> **nbetham said:**
> Ok so judging by the looks of that netstat Webmin isn't running. If it was you should see an entry for *.10000 . I would try 'sudo service webmin restart' and try accessing the ip:10000 in the web browser again and check netstat again to see if it is actually listening on 10000.

When i type sudo service webmin restart i get webmin: unreconized service

---

### Post by Habitual on 2012-07-31
try "sudo service webmind restart"

---

### Post by targett on 2012-07-31
> **Habitual said:**
> try "sudo service webmind restart"

Same unrecognized service

Is there away to see if webmin is actually installed?

---

### Post by nbetham on 2012-07-31
> **targett said:**
> Same unrecognized service

Is there away to see if webmin is actually installed?

dpkg --get-selections

---

### Post by targett on 2012-07-31
> **nbetham said:**
> dpkg --get-selections

Thanks, next to webmin it says deinstall so i take it its installed.

Ive only installed openSHH so far on the server and webmin is there anything else i need to install to make webmin run?

---

### Post by nbetham on 2012-07-31
Deinstall means that the package has been selected to be removed. I'm not positive your webmin has been installed properly. I would go to [http://www.webmin.com/](http://www.webmin.com/) and download the latest version from there and use that to re install webmin. Something happened the first time the prevented it from completing properly.

---

### Post by targett on 2012-07-31
> **nbetham said:**
> Deinstall means that the package has been selected to be removed. I'm not positive your webmin has been installed properly. I would go to [http://www.webmin.com/](http://www.webmin.com/) and download the latest version from there and use that to re install webmin. Something happened the first time the prevented it from completing properly.

Ok ill give it ago but if i download it on my desktop pc how do i install it on to the server? sorry this is all new

---

### Post by ubudog on 2012-07-31
> **targett said:**
> Ok ill give it ago but if i download it on my desktop pc how do i install it on to the server? sorry this is all new

From the server, you can wget (download) the .deb from their site:
```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb
```

Then, to install it:
```
sudo dpkg -i webmin_1.590_all.deb
```

Hope that helps!

---

### Post by targett on 2012-07-31
thanks for that when i type dpkg --get-selections it now says install so i take it thats a good thing. But [https://192.168.0.103:10000/](https://192.168.0.103:10000/) still just shows...

Google Chrome's connection attempt to 192.168.0.103 was rejected. The website may be down or your network may not be properly configured.

Do i need to forward port 10000 in my router?

---

### Post by LHammonds on 2012-07-31
> **targett said:**
> thanks for that when i type dpkg --get-selections it now says install so i take it thats a good thing. But [https://192.168.0.103:10000/](https://192.168.0.103:10000/) still just shows...

Google Chrome's connection attempt to 192.168.0.103 was rejected. The website may be down or your network may not be properly configured.

Do i need to forward port 10000 in my router?
What is the IP address of your PC?  If it is on the same network, it will be something like 192.168.0.???

If it is on the same network, try pinging that IP address from your PC.

f your PC is Windows, open a command prompt and type "**ping 192.168.0.103**" and you can also get your IP from the command prompt by typing "**ipconfig**"

---

### Post by sandyd on 2012-07-31
> **ubudog said:**
> From the server, you can wget (download) the .deb from their site:
```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb
```Then, to install it:
```
sudo dpkg -i webmin_1.590_all.deb
```Hope that helps!
remember to do
```

sudo apt-get -f install
```
afterwords, as webmin has some requirements.

---

### Post by targett on 2012-07-31
> **LHammonds said:**
> What is the IP address of your PC?  If it is on the same network, it will be something like 192.168.0.???

If it is on the same network, try pinging that IP address from your PC.

f your PC is Windows, open a command prompt and type "**ping 192.168.0.103**" and you can also get your IP from the command prompt by typing "**ipconfig**"

reply from 192.168.0.103 bytes-32 time<1ms TTL 64 window dont stay open long enough to see the end bit of text.

cant get my ip from ipconfig as its open and closes the window in under a second. Although my router says its 192.168.0.102

---

### Post by nbetham on 2012-07-31
What are you using to run the command? Try opening up command prompt by running 'cmd' then ipconfig.

---

### Post by targett on 2012-07-31
> **nbetham said:**
> What are you using to run the command? Try opening up command prompt by running 'cmd' then ipconfig.

its 192.168.0.102

---

### Post by nbetham on 2012-07-31
Does 'service webmin restart' at-least work now? Or is it still saying unknown?

---

### Post by LHammonds on 2012-07-31
Now that you are in a command prompt, try the ping again.  Make sure it does not drop the pings and has zero % loss (in Windows, a ping command defaults to 4 pings, in Linux, it will continually ping until you press CTRL+C)

If you are getting zero % packet loss and your webmin service is running, you should be able to access webmin via a web browser on your PC.

If not, try a different browser.  You can use several different browsers without having to install them if you get them from portableapps.com

LHammonds

---

### Post by targett on 2012-07-31
> **sandyd said:**
> remember to do
```

sudo apt-get -f install
```
afterwords, as webmin has some requirements.

When i did that command it seemed to remove webmin
and now i type in the wget [http://blahblahblah](http://blahblahblah) i get unable to resolve host address
and now i get next to webmin it says deinstall after i type dpkg --get-selections and it wont let me redownload it now

---

### Post by targett on 2012-07-31
> **LHammonds said:**
> Now that you are in a command prompt, try the ping again.  Make sure it does not drop the pings and has zero % loss (in Windows, a ping command defaults to 4 pings, in Linux, it will continually ping until you press CTRL+C)

If you are getting zero % packet loss and your webmin service is running, you should be able to access webmin via a web browser on your PC.

If not, try a different browser.  You can use several different browsers without having to install them if you get them from portableapps.com

LHammonds

4 sent 4 recived non lost

---

### Post by targett on 2012-07-31
> **nbetham said:**
> Does 'service webmin restart' at-least work now? Or is it still saying unknown?

unreconized

---

### Post by nbetham on 2012-07-31
Could you attach a file of the output from dpkg so we can see what's happening when you try to install webmin?

---

### Post by targett on 2012-07-31
ive just reinstalled webmin and unpacked it etc
ureadahead will be reprofiled on next reboot
Errors were encounterd while processing:
 webmin
so i type sudo apt-get -f install and get...
reading package lists... Done
Building depensency tree
reading state info... Done
correcting dependencies... Done
The following packages will be REMOVED:
  webmin
0 upgraded, 0 newly installed, 1 to remone and 0 not upgraded.
1 not fully installed or removed.
After this op, 125MB disk space will be freed.
Do you want to continue [Y/n]?

do i click yes or no?

On a plus note if i just type the ip address in my browser i get this...

It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

So i know the LAMP install is working

---

### Post by nbetham on 2012-07-31
My guess is that the problem is that webmin has unmet dependencies, answering yes will only remove webmin. Try installing via this tutorial: [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

Also: lamp doesn't have anything to do with webmin. Webmin has it's own web server that runs independently of apache. Make sure when you try to access webmin it via [http://serveriphere:10000](http://serveriphere:10000)

---

### Post by targett on 2012-07-31
> **nbetham said:**
> My guess is that the problem is that webmin has unmet dependencies, answering yes will only remove webmin. Try installing via this tutorial: [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

Also: lamp doesn't have anything to do with webmin. Webmin has it's own web server that runs independently of apache. Make sure when you try to access webmin it via [http://serveriphere:10000](http://serveriphere:10000)

Followed the guide and rebooted server and tried [http://serverup:10000](http://serverup:10000) and still nothing

Firefox can't establish a connection to the server at 192.168.0.103:10000.
Oops! Google Chrome could not connect to 192.168.0.103:10000

Its baffled me been trying dif things for 5 hours lol

---

### Post by nbetham on 2012-07-31
Did the install report the same errors as the last time and try to uninstall webmin. Also does port 10000 show up in netstat -l and can you restart the webmin service?

---

### Post by targett on 2012-07-31
> **nbetham said:**
> Did the install report the same errors as the last time and try to uninstall webmin. Also does port 10000 show up in netstat -l and can you restart the webmin service?

it tried to uninstall webmin again if i typed sudo apt-get -f install.
cant restart webmin unreconized service.
cant see port 10000. 
other stuff is showing up ok though in netstat -l

---

### Post by nbetham on 2012-07-31
Try the installing from an apt repository section at the previous tutorial I gave you. Apt will help manage the dependencies for you.

---

### Post by targett on 2012-07-31
> **nbetham said:**
> Try the installing from an apt repository section at the previous tutorial I gave you. Apt will help manage the dependencies for you.

Thanks i will try that tomorrow, i did notice this if its any help,

The following packages have unmet dependencies:
webmin: Depends: linnet-ssleay-perl but is not installable
depends: libauthen-pam-perl but is not installable
depends: libio-pty-perl but is not installable
depends: apt-show-version but is not installable

---

### Post by nbetham on 2012-08-01
> **targett said:**
> Thanks i will try that tomorrow, i did notice this if its any help,

The following packages have unmet dependencies:
webmin: Depends: linnet-ssleay-perl but is not installable
depends: libauthen-pam-perl but is not installable
depends: libio-pty-perl but is not installable
depends: apt-show-version but is not installable

Any luck installing? Have you tried to apt-get install those missing dependencies? If so did they succeed or give an error as to why they failed?

---

### Post by targett on 2012-08-01
> **nbetham said:**
> Any luck installing? Have you tried to apt-get install those missing dependencies? If so did they succeed or give an error as to why they failed?
 
Yes tried apt-get -f install but it just tried to uninstall webmin, so im thinking of installing ebox control panel instead

---

### Post by nbetham on 2012-08-01
> **targett said:**
> Yes tried apt-get -f install but it just tried to uninstall webmin, so im thinking of installing ebox control panel instead

In order to install webmin you are going to need to fix those missing dependencies. You can do that by taking the name of each of those missing packages and then sudo apt-get install packageNameHere after that you should be able to install webmin.

I looked into ebox last night actually, and it looks like you need a license for to do more than just checking disk space and system usage.

---

### Post by targett on 2012-08-01
> **nbetham said:**
> In order to install webmin you are going to need to fix those missing dependencies. You can do that by taking the name of each of those missing packages and then sudo apt-get install packageNameHere after that you should be able to install webmin.
 
I looked into ebox last night actually, and it looks like you need a license for to do more than just checking disk space and system usage.
 
aahaaaa i see thanks, i will try that when i get home from work and post back weather it works or not.
I hope i dont need a license for ebox because if webmin still refuses to install on my server i may have no other option

---

### Post by targett on 2012-08-01
it didnt work just kept giving E: errors

---

### Post by targett on 2012-08-01
**Update** got halfway through installing Zentyal with this guide [http://pricklytech.wordpress.com/2011/03/24/ubuntu-server-installing-and-configuring-zentyal-openvpn/](http://pricklytech.wordpress.com/2011/03/24/ubuntu-server-installing-and-configuring-zentyal-openvpn/) and after i edited the file with nano and put the key in it updated webmin, god knows why but im happy webmin works fine now on [https://192.168.0.103:10000/](https://192.168.0.103:10000/) :D

Thanks for all the help from all the people that posted in this thread i appreciate it

---

