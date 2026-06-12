---
title: "Slow upload of blocklists through GUFW"
date: 2009-01-15
forum: Security
---

### Post by TTime on 2009-01-15
Hi All

I can see the benefits of Uncomplicated Fire Wall and IPtables ... so I thought I'd give it a go through the GUI (GUFW). Anywhoo I was also using IPBlock ( as you do when using Ktorrent ) and thought I could do away with the IPBlock if I uploaded the block lists through the GUI using the "Banning IP's" feature in GUFW...... but it is mind numbingly slow at uploading this information- 4hrs to upload 200kb and i've still got 1/2 a dozen other blocklists to go ( one is 12meg alone ).I should add that the lists are in .txt format (name:addresses)

Is there any faster way get the blocklists into this firewall ? Bear in mind i'm a Linux newbee... I can work the terminal but being a MS divorcee , still like the GUI for everyday use.

thanks for any help

---

### Post by uljanow on 2009-01-15
This is a known limitation. Having 200k rules in iptables is a bad idea. If you want to filter  blocklists you might want to try [iplist]("http://ubuntuforums.org/showthread.php?t=530183").

---

### Post by lovinglinux on 2009-01-16
UFW it is really freaking slow for ip blocklists. I don't know why they offer this feature, since most people will try to load large lists.

I recommend sticking with iplist or moblock, combined with ufw or firestarter for regular iptables rules.

I was in the same place as you a few months ago and I thought iptables were too complicated, but then I decided to learn the commands and I have no regrets. I'm currently using moblock with the inbuilt custom iptables scripts, so I don't need ufw or firestarter anymore. Moblock handles everything, starts at boot and works like a charm.

There is a GUI for moblock called mobloquer. You can do pretty much everything with it, but controlling moblock from terminal it's very simple.

---

