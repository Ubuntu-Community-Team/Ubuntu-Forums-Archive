---
title: "Prevent using router dns"
date: 2019-05-01
forum: Security
---

### Post by crip720 on 2019-05-01
I am using ubuntu 16.04 with windscribe vpn.  I am having dns leaks which I think is from rental VDLS2 router, that I do not have root/admin password for.  Is there a way to prevent/stop using router's dns from ubuntu?  Did installed [COLOR=#000000]openresolv nscd unbound, but it is not preventing the leaks.  Do not want to do a reset to the router. Network manager is set to automaticDHCP with different than ISP's dns servers.  Thank you.[/COLOR]

---

### Post by DuckHook on 2019-05-01
Complex problem with no guarantee of success, but you can try a variation of the following:
[https://support.opendns.com/hc/en-us/articles/228007087-Ubuntu](https://support.opendns.com/hc/en-us/articles/228007087-Ubuntu)
&#8230;just use your preferred DNS server in lieu of OpenDNS. OpenDNS is itself also fine.

The problem is that router DNS will often take precedence over anything set locally. This is because the router is, and&#8212;if one thinks about it&#8212;*has* to be the boss in determining where and how a packet is routed since it's the end point that bridges your NAT to the big bad Internet. It all depends on how aggressively the router is configured. My DD-WRT firmware allows DNS bypass whereas the OEM firmware that it replaced did not.

The guaranteed way to circumvent any router setting is to VPN out of your local NAT. I don't know if you have a VPN provider that you can readily use, but a good selection can be found with a simple DuckDuckGo search.

EDIT

I obviously didn't read your original post carefully. You have a VPN.

How are you configuring your VPN? Is it encrypted (I don't know anything about yours)? What makes you think you are leaking DNS?

---

### Post by crip720 on 2019-05-01
The vpn is supposed to be encrypted and testing dns leaks with ipleak.  Leaks are not all the time, sometimes they show up and then don't.  The leak changes can happen with nothing else changing, same vpn servers as before.  I also am using webrtc leak limiters on browsers.

---

### Post by DuckHook on 2019-05-01
This is getting beyond my pay grade. However, I will move your post to "Security" where the real security gurus reside.

Do you have any apps that will bypass VPN? Torrenting for example?

---

### Post by crip720 on 2019-05-02
It is a system wide vpn, not just browser base, and torrent client set to only work though tun network.

---

### Post by crip720 on 2019-05-02
Have tried to use automatic addresses only in network manager before, but I seem to lose internet access when I do.

---

### Post by SeijiSensei on 2019-05-02
Does the VPN provider not maintain DNS servers visible only via the tunnel?  

[s]
Run the command

```
resolvectl status
```

The DNS servers in use appear at the bottom.  Is the "Current" DNS server inside the VPN?
[/s]

That's the command for current versions of Ubuntu.  On 16.04 you might start with running the command "nmcli dev show | grep DNS" or looking at the contents of /etc/resolv.conf.

Unless you overrode the servers manually, they should be specified by the router during the DHCP handshake.

---

### Post by DuckHook on 2019-05-02
> **crip720 said:**
> …torrent client set to only work though tun network.
As mentioned, I'm way out of my league here, but I'm not sure how that would work. As far as I know (which isn't very far), torrenting establishes dozens (sometimes hundreds) of direct peer to peer connections and bypasses all sorts of controls. That's why it is a known privacy/anonymity problem.

Anyways, hopefully a guru will see this thread and help you gnaw on the meat of your problem.

---

### Post by crip720 on 2019-05-02
Command [COLOR=#000000]nmcli dev show | grep DNS shows only my ISP DNS servers and the two DNS servers I added to network manager(1.1.1.1, 1.0.0.1).   [/COLOR][COLOR=#000000]/etc/resolv.conf gives me [/COLOR]127.0.1.1.  Would need help to changed resolv.  Using ipleaks the leaks only seem to be from webrtc, torrent leak detection does not show any leaks.  I am also using webrtc leak limiter and webrtc leak prevent extensions on browsers, chrome and opera.  Firefox also shows leaks with webrtc disabled.

---

### Post by SeijiSensei on 2019-05-03
Ask your provider if they maintain servers visible only over the VPN.

---

### Post by crip720 on 2019-05-03
I think you are talking about my Windscribe VPN provider, and their DNS servers suppost to start with 10.x.x.x, which shows up if I do ipleak test in Firefox plus also my ISP DNS.  This from vpn's website, [COLOR=#666666][FONT=lato]Yes, IPv6 connectivity is firewalled at the client, and all DNS requests get made through the tunnel, resolving domains at the VPN server. This overrides your ISP DNS so you cannot be snooped on by them.  I also have a ticket about this going with Windscribe.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2019-05-03
I'm not sure if this works on Ubuntu but, >>> Yes it seems it dose.
With the new network-manager command nmcli, do this:

```
nmcli --fields ipv4.dns,ipv6.dns con show <connection_name>
```

On newer versions of network-manager (such as in Ubuntu 16.04), the field names are slightly different:

```
nmcli --fields ip4.dns,ip6.dns con show <connection_name>

```
If you don't know the connection name, use:

```
nmcli -t --fields NAME con show --active
```
Example if needed:
```
nmcli --fields ipv4.dns,ipv6.dns con show tun0
ipv4.dns:                               --
ipv6.dns:                               --
```

---

### Post by crip720 on 2019-05-03
Out of the four active connections, nmcli only shows dns for wireless(1.1.1.1,1.0.0.1).  Four connections are, wired, wireless, tun0 and Windscribe.  Those dns addresses are what I have listed in network manager.  Wired connection shows error, no such connection profile.

---

### Post by crip720 on 2019-05-03
Was googleing around some more and found the extension/add-on called 'ScriptSafe'.  It seems to stop webrtc leaks so far, better than others or blocking the test sites from working well.  Test again tomorrow to see.

---

### Post by #&amp;thj^% on 2019-05-03
Firefox disable WebRTC:>>(See Screenshot) 
The &#8216;RTC&#8217; in WebRTC is an abbreviation for Real-Time-Communication, and is used for voice calls, video chats, and p2p file sharing. 
Type **"about:config" **in the address bar of Firefox.
Click on &#8220;I&#8217;ll be careful, I promise!&#8221; :p (or some security message similar to that) [the message depends on the version of Firefox you have]. 
A list will open with a search bar above. In that search bar, please type: 
```
media.peerconnection.enabled
```
 and hit enter. And click on that to toggle to "false"

For Chrome, Google has released a Chrome extension, " [WebRTC Network Limiter]("https://chrome.google.com/webstore/detail/webrtc-network-limiter/npeicpdbkakmehahjeeohfdhnlpdklia/related?hl=en-US")" that eliminates the fears of WebRTC. But your VPN should be your best bet at protecting you. Mine dose.

(Disabling  WebRTC by the user is not possible with Chrome and Chromium-based browsers, such as the Brave browser.)
browser add-ons and extensions are not 100% effective. Even with add-ons, the vulnerability still exists in the browser to reveal your true IP address with the right STUN code. **(Therefore don&#8217;t use Chrome.)**

---

### Post by crip720 on 2019-05-04
Have firefox webrtc disabled and have ext. webrtc limiter and webrtc prevent for a few years, they seem to not be working as well now.  Scriptsafe ext. seems to work, but also stopping some sites from working, might work too well.  I am also talking to vpn provider about this, but figured I should ask here if there was anything Ubuntu could do.

---

### Post by crip720 on 2019-05-06
I am marking this as solved, on another thread I open to get information on how to add these lines ```
[COLOR=#000000][FONT=&quot]script-security 2[/FONT][/COLOR]up /etc/openvpn/update-resolv-conf.sh
down /etc/openvpn/update-resolv-conf.sh
down-pre
``` and this line ```
setenv PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
``` and after three of four reboots, it is working.

---

