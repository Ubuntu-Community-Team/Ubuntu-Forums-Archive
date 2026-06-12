---
title: "Remote Desktop used from Internet"
date: 2010-03-21
forum: Security
---

### Post by brumac on 2010-03-21
Today I noticed my Desktop was being controlled remotely from over the Internet even though I had it set for 'local network only'. Foolishly I relied on this setting and hadn't specified a password or other security.

The remote user had opened my Firefox passwords page and was perusing this when I pulled the plug.

All external checks confirmed that my router/firewall is actively blocking correctly.

How could this happen? How can I prevent this in the future?

I had recently install the Firefox extension for Weave Sync and wonder if that had anything to do with it?

Any suggestions, clues will be gratefully received.

---

### Post by uRock on 2010-03-22
[SIZE="5"]First, change your online passwords![/SIZE]

Second, Password protect your remote desktop.

Third, Enable UFW. With UFW enabled nothing connects unless it is started from your system.

Fourth, Go into your router and change the routing table, if possible. If your internal network IPs start at 192.168.1.1, change them to start at a random number such as 192.168.33.1. If you didn't know, you can change the last two sets after the 192.168.x.x. Some home routers even allow 10.0.0.1.

To enable UFW run this in a terminal: ```
sudo ufw enable
```
If you want a GUI to alter the firewall, install GUFW via the terminal with: ```
sudo apt-get install gufw
```or install it via Synaptic Package Manager.

You may also be able to go into your router's settings and have it request a new IP.

This person may already have enough info about your common passwords to break in again.

I hope this helps.

---

### Post by Keith1212 on 2010-03-22
wow that crazy! Do i need to take precautions? I mean i don't use remote desktop at all. I have a router with a firewall on and wep security on my wifi. Plus i got mac addy filtering enabled on it. I should be good right? lol

---

### Post by uRock on 2010-03-22
> **Keith1212 said:**
> wow that crazy! Do i need to take precautions? I mean i don't use remote desktop at all. I have a router with a firewall on and wep security on my wifi. Plus i got mac addy filtering enabled on it. I should be good right? lol

If you haven't enabled Remote Desktop with the Internet menu, then you have nothing to worry about with this particular program. If you do, then password protect it.

---

### Post by brumac on 2010-03-22
Thanks iRock, You Rock. Thank you for your clear and succinct instructions. 

Yes, then first thing I did was to change all my online passwords and disabled Remote Desktop. The rest I will do when I stop shaking :o.

Do you know where I can discover how this happened in the first place? My (3) computers here are supposed to be invisible from the outside world behind my firewall.

Regards, Bruce.

---

### Post by a.walker on 2010-03-22
> **Keith1212 said:**
> wow that crazy! Do i need to take precautions? I mean i don't use remote desktop at all. I have a router with a firewall on and wep security on my wifi. Plus i got mac addy filtering enabled on it. I should be good right? lol

You should probably change your router's settings so that it is using WPA or WPA2 instead of WEP. WEP is better than no encryption, but not a whole lot better. Mac filtering is usually a bigger headache for you than for someone with nefarious intent. 

You also might want to go ahead and copy your files onto an external drive and reinstall ubuntu just to be safe.

Also start wearing tinfoil hats and put one on your dog too. :p

---

### Post by Gregorybekkers on 2010-03-22
Disable the portforwarding on your router or change it to another port...
Update all your passwords and if u don't use it disable remote desktop and enable your firewall

---

### Post by cdenley on 2010-03-22
When enabling "remote desktop" if you check the checkbox about "configuring your network", then upnp will be used to configure port forwarding on your router automatically if your router supports upnp.

---

### Post by uRock on 2010-03-22
> **brumac said:**
> Thanks iRock, You Rock. Thank you for your clear and succinct instructions. 

Yes, then first thing I did was to change all my online passwords and disabled Remote Desktop. The rest I will do when I stop shaking :o.

Do you know where I can discover how this happened in the first place? My (3) computers here are supposed to be invisible from the outside world behind my firewall.

Regards, Bruce.

Your welcome.:) I think it was a matter of luck for the hacker running port scans to find that service open and unsecured. Finding the culprit is a really tedious task, which is why most sites don't report it when they have been hacked.

You may want to check in your router and make sure NAT is enabled.

Regards,
Ronnie

---

### Post by HermanAB on 2010-03-22
Congratulations, you are the millionth Ubuntu user to get his computer hacked via VNC.

Don't use VNC.  Use SSH.

---

### Post by OpSecShellshock on 2010-03-22
Disable UPnP in your router. Disable the remote desktop, and only enable ssh if you have a specific need to access your computer remotely. Use a strong password that isn't the same as your user account password on the desktop, or better yet use keys. Disable ssh whenever you aren't going to be using it. Basically, if you ever do anything that requires accepting incoming connections from outside your home network, only have it enabled while you're using it, and shut it off both on the computer and in the router the rest of the time.

---

