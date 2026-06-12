---
title: "setting up virtualbox for PIA (vpn)"
date: 2016-07-10
forum: Virtualisation
---

### Post by T_Jo on 2016-07-10
Hi 

I have received login details yesterday for PrivateInternetAccess access and want to start using it on virtualbox. 
Virtualbox is running Ubuntu and the host also. The guests connection continuously fails though. I have tried NAT and bridged connection in virtualbox. And both methods that are provided on the site - so  [https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn](https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn)
and this one [https://www.privateinternetaccess.com/installer/download_installer_linux](https://www.privateinternetaccess.com/installer/download_installer_linux)
Unfortunately connection fails every time - for both methods. 

There are a lot of forum posts / tutorials online that are or very old or incomplete answers, there doesn't seem to be a recent tutorial.

I don't even know where to start investigating the issue. No problem to post some log files or do some tests - any recent tutorial or post that will help me find solving it. If I can't solve it in Vitualbox I might install PIA in the host but I would rather use the virtual image. 
BTW. no problem to access the internet with the guest (NAT and Bridged)

---

### Post by TheFu on 2016-07-10
I've used PIA, but never on a virtual machine. Doubt that would matter.  I don't use NAT for VMs, preferring bridged.  Below is from memory and it has been a few months since I set this up.

* I didn't use any install package from them. Used the stock ubuntu openvpn.
* grabbed some file from PIA with settings inside - 
* manually created /etc/openvpn/ and dropped a few files into it from the PIA settings ZIP. These are: ca.crt  crl.pem  login.cf  update-resolv-conf - login.cf are my credentials for PIA (had to use some tool they have to generate L2TP/IPSec credentials) - it has 2 lines as specified in the notes.  
```
USERID
PASSWORD

``` - no labels, no comments, line 1 as my userid. line 2 has the L2TP credentials.
* Created a few exit node openvpn setting files: UK_London.ovpn  CA_Toronto.ovpn  - they provided an example, which I followed. I can post an example, if you like.
* Created a little script to start the VPN - 
```
$ more ~/bin/pia-toronto.sh 
#!/bin/bash
cd /etc/openvpn
sudo openvpn CA_Toronto.ovpn &

```
That's it.  Could either make a smarter script or more scripts for each exit-node location in the world.

I didn't want a GUI controlling this, since it runs on headless servers.  Don't have **any** idea how to do it with a GUI - plus I don't use network manager since my network setups usually have 3+ different subnets involved before adding the VPN.

Wish I knew where to find the initial ZIP package with the stuff needed inside it. Vaguely remember it was linked in some instructions for a 12.04 setup.  Old doesn't mean out of date, especially when NOT using the GUI.

I've done lots and lots of virtual machine stuff and cannot think of any reason why this PIA setup wouldn't work.

---

### Post by T_Jo on 2016-07-10
You might have followed this method [https://support.privateinternetaccess.com/Knowledgebase/Article/View/30](https://support.privateinternetaccess.com/Knowledgebase/Article/View/30) 

Will give that a try as well and let you know the result.

Yeah! According to the PIA site I am now protected by PIA :) 
Thanks for directing me in the right direction - might try the script later but more important is that it works now (and indeed used bridged) 

Is there any method to be sure openvpn is running? I want to prevent accidentally using the default ip
I am also interested in what ovpn config I should choose - is there a reason not to choose the one nearest by (and probably the fastest)?

---

### Post by mikodo on 2016-07-10
I only setup my desktop to use PIA. With that I can click on the "icon" it provides in my panel to configure it to not allow connection if PIA drops (has other settings like encryption to use and other settings). It has in rare instances dropped connection. Then, I cannot access the internet with that setting. Re-starting it has always connected it again. I don't know if you have that with your setup though, (the PIA icon that allows for settings).

When I first purchased PIA I tried the ovpn (if that is what is is called) it chose for me. Being from Western Canada it choose the Toronto one. That seemed slow and then I tried others state side and even Europe ones for fun. I have my favorite ones. But, conventional wisdom is to choose the closest or so I am told.

For me, it is not always the closest that is the fastest.

I used a Web-site to test the bandwidth of the different ovpn's. The only Web-site I saved the url for for doing this is below that uses HTML5, no flash, but I have to temporarily allow it to use java to work..

[http://www.bandwidthplace.com/](http://www.bandwidthplace.com/)

---

### Post by TheFu on 2016-07-10
It is vague to me, but I recall that if you didn't specifically generate new L2TP credentials, then it defaults to PPTP, which is useful to keep your little brother from spying, but not anyone else.  PPTP was cracked a long, long time ago and even MSFT has said not to use it the last 10 yrs.

Plus none of this prevents DNS leakage. More steps are necessary to prevent that based on my testing here. I'm still leaking.

---

### Post by T_Jo on 2016-07-11
If this is correct [https://www.privateinternetaccess.com/pages/client-support/](https://www.privateinternetaccess.com/pages/client-support/) then PPTP/L2TP/Socks is only needed if openVPN isn't working. But I could be totally misunderstanding your point.. 
I just did a DNS leak test and indeed there seems to be one address that is not my ip address but it is referring to my internet provider. 

Any suggestion how to improve this?

[https://www.dnsleaktest.com/how-to-fix-a-dns-leak.html](https://www.dnsleaktest.com/how-to-fix-a-dns-leak.html) unfortunately adding block-outside-dns to the ovpn file only seems to work on Windows. Will check again tomorrow..

---

### Post by TheFu on 2016-07-12
> **T_Jo said:**
>  Is there any method to be sure openvpn is running? I want to prevent accidentally using the default ip
I am also interested in what ovpn config I should choose - is there a reason not to choose the one nearest by (and probably the fastest)? 

a) Please don't screw around with fonts here.
b) Check the process table and the routing table.  Just like you'd do for any other process.
c) There are many reasons to use a VPN. Sometimes choosing the network-closest (not necessarily the distance closest) exit location is what you want for speed, but sometimes you'd like to exit from a different country to try out services only available in those other countries.  For example, Google is a little different depending on your exit node location - in some locations, you must sign in and agree to terms of use before they allow use. The typical use is for video streaming.

However, there is also often a desire to use a VPN that you might run from your home to provide access back to your network from anywhere in the world. A commercial VPN provider won't help with this at all.  Basically, we run an openvpn server from our home computer(s) for this reason and use the same openvpn client software to connect, just like we do with PIA.  Or there's the poor-man's VPN - ssh, sftp, sshfs, scp, x2go, .... which I use much more often to securely connect back home.

---

### Post by T_Jo on 2016-07-12
a - Didn't intentionally changed fonts - maybe because of some copy pasting from pia. Fonts look all the same in firefox.
b - I would rather have some widget that shows the few relevant details I am interested in but most of the tools are CLI only and are showing too much data... 
c - my main reason for using vpn is the tightening regulations on file sharing (the Netherlands is still pretty liberal but times are definitely changing)... also privacy in general worries me and especially the tons of data that is gathered by companies and governments linked to an ip address or email address. And as bonus it is just interesting technology.  

I chose Switzerland ovpn - works fine :) 
 
Leakage seems to be solved after changing my connection from automatic dhcp to manual. Changed it to an opendns server.

---

### Post by TheFu on 2016-07-12
CLI output can be filtered to show exactly what you need, nothing more. Something like:
**ps -eaf |grep openvpn** ... plus you can put an "if" around the results and say "VPN is UP" or "VPN is DOWN" as the output, if you like.

I don't use file sharing (anything that includes uploading is especially illegal in my location), so don't know anything about that. Plus $100/yr gets me more streaming content than I can possibly watch. There really isn't any privacy on the internet anymore, but if you aren't the head of a criminal organization, when the feds break all the efforts at privacy you've put in-place (and they can already if they have patience), they won't bother coming after you for a few uploaded videos (assuming the videos aren't illegal on their own).  That doesn't mean we shouldn't be outraged by the invasion of privacy when we aren't doing anything wrong (like me), but that doesn't mean they should have complete access to all my "papers and effects" without a valid warrant actually signed by a judge.

I don't know much about the privacy laws in Europe, except that I cannot take photos of private homes or children in Spain and that northern European countries tend to have laws which are better for individual privacy than other parts of the world.

If you want a foolproof way to force VPN use or nothing, put the VPN control into the router (not the desktops) and continuously validate that the VPN is up (check the routing table) or bring the WAN interface down.

---

