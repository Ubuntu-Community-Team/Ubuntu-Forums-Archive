---
title: "unauthorised internet traffic??"
date: 2010-09-24
forum: Security
---

### Post by pretzel42 on 2010-09-24
Hi I've been using ubuntu for a while now, but am only very much an average desktop user. I've got a fairly fresh instillation of 10.04 on an old dell. I check my internet traffic with system monitor from time to time, and log files from time to time, as I am fairly security conscious, though not so savvy. After a system update the other day, I restarted and then logged on to regular desktop account. I noticed shortly after starting up, a 10mb download was going on, and yet I had not yet opened any applications.

I don't have any cron jobs I've written myself on the machine. And there were no other cron jobs logged in the log file viewer that had happened around that time either.

the only package updated prior to my restart was a recommended update for fglrx-modaliases - a package for ATI drivers. I don't have any graphic cards, just intel onboard, so I doubt there was a download for drivers initiated by the new package, or anything. 
 
The only other thing around that time I can find in my logfile viewer is an ntpdate 1393 log - but I assume that time syncing would not normally involve a 10mb download.

Prior to restarting the computer, as well as the update, I had also  run 'sudo freshclam' in terminal, and there was a bit of an unusual delay before it checked the servers. I remember reading there have been vulnerabilities with clamav relating to this recently.

Anyway, hope I'm not coming across paranoid (though I'm sure I probably am). So, what are the odds I've been cracked, and what could the download have been if not?

Any advice would be much appreciated

---

### Post by n~kf)}BW% on 2010-09-24
Try to find out what this download is all about by sniffing the traffic.

Use a tool like Wireshark. It has a nice interface and you will see the connections in real time. The odds that you've been cracked or it's malware are really small.

---

### Post by cariboo on 2010-09-24
It could be several things, Ubuntu usually checks for updates on start up. If you use the Me Menu, it could be checking for messages. Like slovenia said use wireshark to check network traffic.

When you install wireshark, run the following command in a terminal, so that you can use wireshark as a regular user:

```
setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap
```

---

### Post by The Cog on 2010-09-25
Justa  quick **netstat -t** will tell you what machines it is connected to. The names might give you a clue.

---

### Post by mr-woof on 2010-09-25
try sudo netstat -lnp and post the tcp/udp output

---

### Post by Codecaine_21 on 2010-09-25
i am having similar problems!! i installed a fresh copy of ubuntu  10.04 and during the installation i  opted to update my security updates  myself but everytime i start my  computer up an automatic security update comes up  even though i opted  to update myself. and it wants to update api  packages for perl and  install ssh servers... looks as to it might be a backdoor  or something  malicious!! i opened  up firestarter and my ip was calling  services  that i was not calling like i uninstalled ssh server and my ip  was  making calls to it but i wasnt running the server and it showed up  in  red i guess because its uninstalled. but i will recieve denial of   service updates and if i leave my computer on over night the computer is   on and running but my screen is detached. like the computer is on but   the screen is off even though i have all the wires plugged in. The   monitor works again if i restart my computer. i opened up my routers   server page for netgear and seen a few different ip's attached but when i   used nmap and fping it came back that they were not alive or the word   used was "Unreachable" any insight??

---

### Post by pretzel42 on 2010-09-25
Thanks guys. Much appreciated. I've installed wireshark incase I have any further problems, and I've run 'netstat -t' a few times in terminal to check for any odd connections and nothing unusual thus far. I'll try sudo netstat next time I'm in admin account. I doubt it was to do with the me menu - I do use gwibber for facebook and twitter, but I set it not to run on startup. I'll just keep an eye on things using your suggestions for a while, and if it doesn't happen again, I guess I'll just not worry about it. Thanks heaps for your help everyone. One quick question (possibly a dumb one). Is it possible that if someone temporarily got through my firewall that the traffic was a from a repeated, and probably unsuccessful attempt to crack my main admin (sudo) password. ie could an attack like that take up that much traffic? Just curious. Though there was nothing in my ufw log.

---

### Post by pretzel42 on 2010-09-25
I'll run sudo netstat -lnp and post the tcp/udp output when I get a chance

---

### Post by pretzel42 on 2010-09-26
Okay I've attached an odt file to this that has a copy of the tcp/udp output I got when I ran 'sudo netstat -lnp. Thanks for the suggestion. If anyone has got time to scan their eyes over it and see if there's anything suspect in there, it would be very much appreciated. I couldn't see anything overtly dodgey, but then I have little idea of what to look for. Thanks people.

---

### Post by Xeronix on 2010-09-26
Was this 10 mb file exactly 10 mb?

You said immediately after a update and reboot, so I'm starting to think it could be trying to update some backend stuff without you knowing.

It doesn't look like anything unusual is running, though you never know.

Do you have any idea where that file could have gone? You could have possibly been port injected via your router being compromised, do you have remote access enabled?

I'm starting to think that you've been added to a malicious botnet.

10 mb is simply enough for a client. Have another computer try running nmap on your system and check for other types of ports open that you aren't aware about.

---

### Post by OpSecShellshock on 2010-09-26
I had a look at the file. There's nothing unusual happening at all. I suspect that the network activity was general stuff like the system time being validated, the acquisition of a DHCP address, and the updating of the package repository cache. The services listed in the netstat output are the same as every other Ubuntu desktop installation I've seen, and are only listening on the LAN or localhost.

---

