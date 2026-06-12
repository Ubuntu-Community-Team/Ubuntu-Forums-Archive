---
title: "Can't connect to VPN on 14.04 LTS"
date: 2014-11-04
forum: System76 Support
---

### Post by jcllings on 2014-11-04
I spent some time at work last week extolling the virtues of Ubuntu and  System76 to my colleagues only to have a work-impacting issue soon  after.  The subject we were discussing at the time was switching to Macs. Pretty embarrassing.  Anyway, in a nutshell, my VPN connection from home no longer functions. 

Original post is here:

[http://askubuntu.com/questions/545312/cant-connect-to-vpn-on-14-04-lts](http://askubuntu.com/questions/545312/cant-connect-to-vpn-on-14-04-lts)

Sorry for the cross-post but I need help pretty badly and I've gotten no responses since yesterday.  The machine in question is a year (or two?) old System76 machine although the support contract may have expired. More than willing to renew if that will get me back to where I can work again.

Have done the following:
1. Called Comcast and had them check their end. They reset the modem poked around a bit and found no issues. 
2. Had work check the credentials. One issue found and corrected (I had one of the items wrong) but still can't get on. Reset the RSA key. Didn't help. 
3. Tried backing up versions of libgcrypt11 since some traffic suggested this might be the issue. Seemed plausible. Since both of my machines lost the ability to access the VPN, it might have been a bad update. Probably was but I've not been able to track it down.
4. Took my laptop off the local net and jacked directly into cable modem. No dice. Same issue. 
5. Also tried different clients. 

Error displayed is similar to "Connection Failed". Note that it says something to the effect that "Connection failed due to bad credentials" when I get them wrong. 

Haaaalp?! ;-) No, seriously. :-|

---

### Post by tonyr2k8 on 2014-11-04
You should look at this article, it's related to Comcast. [http://www.kvi.com/home/featured/281348241.html](http://www.kvi.com/home/featured/281348241.html)

---

### Post by jcllings on 2014-11-04
Thanks but this is not my issue. Comcast tried to "upgrade" me to that router they want everyone to use so they can perpetuate their phone service.  I had so much trouble with it, I took it back and got a strictly wired modem. Besides, we've now tested it onsite at work using my laptop. Same error.  The only place I can think of that something like that might have come from is an incoming update.  I'll get hard core on it this weekend and revert all updates since 22/23 Oct 2014 which is the last time it was known to be working.

---

### Post by jcllings on 2014-11-10
OK I think I understand this one now. I created a Windows VM, installed the Cisco client and configured it with my credentials. I got in to the VPN with no problems but I noticed some interesting behavior that perhaps is not handled by many Linux clients.  I had just changed my Windows password on the target desktop box inside the VPN, which is what I think triggered this.  When I logged in using Windows 7 and the official Cisco client it prompted me not once but twice for an RSA passcode. The second time I was specifically prompted for the NEXT passcode. Short term work-around then is to log in once from a Windows box at the remote side each time you change your Windows password.  I wonder how many headaches this has caused?

---

