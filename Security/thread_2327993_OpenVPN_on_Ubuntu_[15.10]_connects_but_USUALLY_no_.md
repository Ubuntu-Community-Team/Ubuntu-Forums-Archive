---
title: "OpenVPN on Ubuntu [15.10] connects but USUALLY no Inter/Intranet"
date: 2016-06-16
forum: Security
---

### Post by vicmorrowshead on 2016-06-16
Hello Everyone:

For the record, I posted this exact post to the OpenVPN Connect forum - if I am violating some multi-post code of ethics, I plead ignorance and I apologize, but I honestly am not sure WHERE the problem actually exists.

The problem is that I cannot really say where the problem is. Although it appears to be an OpenVPN client issue on Android, after doing a lot of reading, I'm  not so sure anymore. People have had issues that were masked in certain ways and were totally not related to what they appeared to be. This may be the case here because it seems no one else is having this exact issue. If this was purely and Android + OpenVPN Connect issue, I would imagine there would be zillions of people having this issue.

Here is my issue:

What works ALWAYS:
1) OpenVPN on Unbuntu: no issue at all with Linux desktop clients. All VPN routing and forwarding for the LAN and for the Internet works beautifully.
2) Authentication/Connecting on Android and desktop.


What doesn't work:
Android client (SAME intermittent behavior with OpenVPN Connect, OpenVPN for Android [Arne S.], and OpenVPN Client).


When it doesn't work on Android (same behavior on Samsung Galaxy Note 4 [5.1.1], Samsung J7 [Marshmallow], Samsung Tab 3 [Jellybean]), it doesn't allow access to the LAN and to the Internet (which is contrary to tcpdump and the client packet counter [looks great]), however pinging works to LAN without any issue ALWAYS; but accessing services on LAN directly (via IP address - does not appear to be a DNS issue): times out or fails.


When it does work, it works perfectly. Everything is forwarded either to the Internet or the LAN, to and fro without any issues. Flawless, fast, and beautiful.


Configuration: tun; nothing dramatic. Basic configuration.


When it does work, it works repeatedly (can disconnect and reconnect), no issues. Then, at some point, it just stops. There are never any issues authenticating nor does it ever disconnect. Also, when it doesn't work, the sent/receive bytes increase as would be expected when trying to go to places on the network. tcpdump for tun0 also is responding as expected to the domains sought after and packets are clearly going in both directions - totally responds to actions on Android client; and client VPN software shows bytes going both ways, but it doesn't work. While it is not working, rebooting the device does not solve the problem: it just flat out stays not working. Then, after some time (without touching anything server or client side), after connecting, it just seemingly magically starts working. The only repeatable observation is this: when I need it to work, it never does. There is perhaps a hidden setting somewhere that is sensitive to my psychological state and responds accordingly. But I haven't found this flag anywhere. Also, Android clients are never in WIFI mode - just to be clear.


I am at a total loss. I see this on all Android devices I have tested with across 3 OpenVPN clients. Again, Linux desktop clients work flawlessly always even while Android clients are not working.


I am totally unable to find a pattern or anything that repeatedly triggers it to fail or succeed except for it being aware of my psychological state as mentioned earlier. When I am in a good mood, it destroys it; when I am in a bad mood, it works and uplifts me. But, this isn't an ideal use-case and I would like to not rely on this if at all possible. When I think I have some routine figured out, then it proves me wrong every time. SOMETIMES when it isn't working, connecting an Ubuntu client to the VPN will cause it to work for a while (regardless of whether or not the Ubuntu client stays connected or not).


What baffles me is that I have not seen forums inundated with this issue. I can't imagine I'm the only person in the universe experiencing this. I probably have one of the more lame and basic set-ups that there are.


Your help is greatly appreciated. Thanks in advance.

The OpenVPN Ubuntu system is not the firewall gateway. That is a separate box. The Ubuntu OpenVPN server has no iptables rules except for masquerade so that the packets from VPN clients from tun0 at 10.8.0.0/24 are handled and accepted properly on the main LAN and Internet when they leave eth0.

Client config:
```
[COLOR=#2E8B57][FONT=Monaco]client[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dev tun[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]proto udp[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]remote myplace myport[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]resolv-retry infinite[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]nobind[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]persist-key[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]persist-tun[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]<ca>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----BEGIN CERTIFICATE-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]...[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----END CERTIFICATE-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]</ca>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]<cert>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----BEGIN CERTIFICATE-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]...[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----END CERTIFICATE-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]</cert>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]<key>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----BEGIN PRIVATE KEY-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]...[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]-----END PRIVATE KEY-----[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]</key>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]remote-cert-tls server[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]comp-lzo[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]verb 3[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]auth-user-pass[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]reneg-sec 0[/FONT][/COLOR]
```

---

