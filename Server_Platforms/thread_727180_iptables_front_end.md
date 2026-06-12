---
title: "iptables front end"
date: 2008-03-17
forum: Server Platforms
---

### Post by netlogic on 2008-03-17
I am a fan of Shorewall. It has been around for a long time and it works for me. Now, to increase more security, we want various rule sets to manage for all workstations, laptops, and servers. I know I can easily manage iptables with basic commands, but working with large rule sets, it seems like different front ends for different roles of the machines feel more logical. Fwbuilder seems more logical for top layer firewalls. Shorewall seems very quick and dry for all the data servers, but it might be too feature rich for others to quickly adjust. It seems like other front end options are lokkit, ipkungfu, firehol, uif, fiafif, ferm, urkuk, and webadmin. 

Webadmin is out of question. New rules are slower to roll out, because it has a graphical interface. Also, Firestarter is definitely no for the workstations. We don't want users to touch or adjust the firewall. I tried Lokit many years ago. It seems like it doesn't offer an ip range blocking, so that is out of the question.  Fiaif, Ferm, Urkuk, and Uif, I haven't bothered to research them. They don't seem to be very active with releases. So, it seems like it is down to Ipkungfu and Firehol for data servers and workstations. Have anyone has an active usage and feeling about these two products? Such as pros and cons? We only want certain workstations talk to certain networks. Also, constantly readjusting the traffic or re-designing the back end traffic may lead into more cost than most people would like. I would like to hear your inputs. Thanks again.

---

