---
title: "WOW dropping wireless"
date: 2010-12-14
forum: Wine
---

### Post by sydbat on 2010-12-14
I usually do not have a problem running things in WINE. They just work. However, I have a friend who is house sitting for us over Christmas and I want to set up WOW on our HTPC so he can play it without having to bring his own computer. 

I have installed the basic WOW.exe fine, but as it goes to download the updates, it drops the wireless after 5 or so minutes. I have searched this forum and Googled alot, but to no avail. No one seems to have the same problem (similar ones, yes, but I cannot find a solution).

My box - Intel quad core, 3GB RAM, NVidia GT220, latest stable repo WINE (1.2).

I have also noticed that SimCity 4 causes wireless to drop as well, but I have never seen that as a problem (because I don't play SimCity online).

In order to get my wireless connection back after it drops, I have to reboot. No other solution works.

Suggestions? Need more info?

Thanks.

---

### Post by cwwilson721 on 2010-12-14
What wireless module does it use? (lsmod, lspci will tell you)

Odds are, it's a wireless module issue (I get the dropped wireless myself from a cheap usb dongle), with the driver dropping things.

Best bet would be to run a cat5 cable to your box until you get it sorted.

wine itself has NO 'power' over the network connection. It's all modules run from the kernel.

---

### Post by sydbat on 2010-12-14
> **cwwilson721 said:**
> What wireless module does it use? (lsmod, lspci will tell you)

Odds are, it's a wireless module issue (I get the dropped wireless myself from a cheap usb dongle), with the driver dropping things.

Best bet would be to run a cat5 cable to your box until you get it sorted.

wine itself has NO 'power' over the network connection. It's all modules run from the kernel.When I boot that box, I'll let you know specifics. I do know it is a pci (pci-e??) wireless card. 

And there is no way I can run it wired, due to it's placement in the living room.

---

### Post by sydbat on 2010-12-15
Sorry for the delay in responding. Life.

According to lshw, the wireless card is an AR5008 Wireless Network Adapter (Atheros, rev 01).

lsmod - two are listed, both for ath9k (mac80211, ath).

And, at the moment, it seems that the connection is strong. I wonder if that is because I am on another desktop...might be a different story if I were on the one with wine running?

---

### Post by rette7mich on 2010-12-15
have you opened all of the WOW ports in your router?

3724
6112
6881-6999

also i'd check your firewall

```
sudo ufw status
```

if it's enabled then open the ports above with 

```
sudo ufw allow 3724
sudo ufw allow 6112
sudo ufw allow proto tcp to any port 6881:6999
```

for me when i play/install WOW with wine, i install and update everything via virtual box XP machine, then i drag the folder to my wine directory. Works Wonders!

WowWiki has a great wine help page too!

---

### Post by dslreports_snakeoil on 2010-12-15
I have that problem as well, but not with WOW. My PC in the living room will turn off the wireless network card.
But I know the reason for my "problem". I have a wireless phone. So if a call comes in, it interfers with the wireless network and the network is shut down for as long as the phone is in use. A fix is to get a different phone that uses a different broadcast freq.

Maybe you have something in your home that is interferring with your wireless signal. The Wii or PS/3 or the wife's laptop don't have an impact on my network, just the wireless telephone handset.

---

### Post by sydbat on 2010-12-15
> **dslreports_snakeoil said:**
> I have that problem as well, but not with WOW. My PC in the living room will turn off the wireless network card.
But I know the reason for my "problem". I have a wireless phone. So if a call comes in, it interfers with the wireless network and the network is shut down for as long as the phone is in use. A fix is to get a different phone that uses a different broadcast freq.

Maybe you have something in your home that is interferring with your wireless signal. The Wii or PS/3 or the wife's laptop don't have an impact on my network, just the wireless telephone handset.Ya...the cordless phone...was interfering until I found a channel that does not conflict. YAY! And the Wii doesn't seen to interfere.

Today, no problems running WOW - yet. I'll keep you guys informed.

---

### Post by sydbat on 2010-12-15
> **rette7mich said:**
> have you opened all of the WOW ports in your router?

3724
6112
6881-6999

also i'd check your firewall

```
sudo ufw status
```

if it's enabled then open the ports above with 

```
sudo ufw allow 3724
sudo ufw allow 6112
sudo ufw allow proto tcp to any port 6881:6999
```

for me when i play/install WOW with wine, i install and update everything via virtual box XP machine, then i drag the folder to my wine directory. Works Wonders!

WowWiki has a great wine help page too!All ports seem to be open. I'll keep an eye on it to make sure.

---

