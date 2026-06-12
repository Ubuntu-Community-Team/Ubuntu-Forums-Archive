---
title: "Removed Firestarter, no internet"
date: 2011-10-01
forum: Security
---

### Post by laserman on 2011-10-01
A few years ago, I installed Firestarter for the reason of trying to wirelessly connect two computers, only to find out that failed miserably. I ended up using a router and performing the necessary transfer of files. Now, in trying to remove Firestarter, problems have risen in the internet connection being valid on boot.

I typed:

```
sudo apt-get purge -y firestarter
```

It seems to have removed Firestarter but the only way I can get internet is to manually activate UFW either by terminal or GUFW.

What can I do to "automate" the internet connection? Is there possibly still traces of Firestarter that is causing this issue? I have searched several threads on the removal of Firestarter and similar issues other people have experience, some stating even being successful in its removal and back to normal but I am not experiencing those same results. 

laserman

---

### Post by emiller12345 on 2011-10-01
Firestarter is just a frontend for iptables, which is the backend of the computers firewall.  For ubuntu desktop, the automatic network connections are usually handled by NetworkManager.  It might be that the service needs to be restarted...
```
sudo service network-manager restart
```This program uses DHCP to get all the networks information and register and ip address on the network.
Or firestarter may have left firewall rules behind after you uninstalled them, blocking traffic. You can see the current rules by ```
sudo iptables-save
```

---

### Post by laserman on 2011-10-01
> **emiller12345 said:**
> Firestarter is just a frontend for iptables, which is the backend of the computers firewall.  For ubuntu desktop, the automatic network connections are usually handled by NetworkManager.  It might be that the service needs to be restarted...
```
sudo service network-manager restart
```

I didn't identify this earlier but when the computer starts, I connect to the router. I can ping the router from now till the cows come home. It's getting to the internet that is the problem. In order for me to get access to the internet, I either have to enable ufw in terminal or enable through gufw. After that, all is fine, until I reboot and then I have to do it again.

> **emiller12345 said:**
> This program uses DHCP to get all the networks information and register and ip address on the network.
Or firestarter may have left firewall rules behind after you uninstalled them, blocking traffic. You can see the current rules by ```
sudo iptables-save
```

I can see a lot running this but I'm not sure what is or isn't in its correct state. I'm attaching two files, one with this command before ufw enabled and one after enabled.

---

### Post by emiller12345 on 2011-10-02
So it appears that you may have some rules left behind from firestarter, that look like is stored in ufw when you enable/disable it. If you want to remove all firewall rules (not advised for permanent use) you can ...```
sudo iptables -P INPUT ACCEPT && sudo iptables -P OUTPUT ACCEPT && sudo iptables -P FORWARD ACCEPT && sudo iptables -X && sudo iptables -F
```but its better to have some firewall then nothing.  I would recommend uwf

P.s. i don't know why UFW is not being enabled automatically, as it should, from session to session....

---

### Post by laserman on 2011-10-03
> **emiller12345 said:**
> 
P.s. i don't know why UFW is not being enabled automatically, as it should, from session to session....

I agree, I don't want to disable the firewall...and too, don't know why it isn't being enabled on startup. I don't think it is UFW though. IPTables would be my first guess, just don't know how to cure it now and don't want to perform a fresh install just to correct it either.

From here, will continue to dig, point towards iptables and see if this can be corrected.

:confused:

---

### Post by laserman on 2011-10-05
This was noticed on shutdown and the screen shot is attached. Would this "fail" have anything to do with it? It references dnsmasq.d and dhcp server failing.

John

---

### Post by rng on 2011-10-06
I am not sure if this would work. Add a line in /etc/rc.local file (before last line which should be 'exit 0') (using 'sudo gedit /etc/rc.local'): 

ufw enable

Then check if ufw is enabled at startup.

---

### Post by laserman on 2011-10-08
> **rng said:**
> I am not sure if this would work. Add a line in /etc/rc.local file (before last line which should be 'exit 0') (using 'sudo gedit /etc/rc.local'): 

ufw enable

Then check if ufw is enabled at startup.

Well I'll be...after as many months, been fighting this. Don't know if this is the norm but this did fix the problem. Now, when I boot up, yes, the firewall does enable but that command in rc.local does allow for access without any additional intervention.

Thanks rng!

:P

---

### Post by rng on 2011-10-08
Glad it worked.

Apparently, some firestarter configuration is still there and firestarter iptables rules are in place at startup (according to rules posted by you earlier). The rc.local command only automates ufw enabling at startup. 

You might try reinstalling firestarter, then choose "Mark for Complete removal" from synaptic package manager (rather than "Mark for removal"). That may remove firestarter configuration files and allow ufw to start at bootup even without rc.local command.

---

### Post by laserman on 2011-10-08
> **rng said:**
> Glad it worked.

Apparently, some firestarter configuration is still there and firestarter iptables rules are in place at startup (according to rules posted by you earlier). The rc.local command only automates ufw enabling at startup. 

You might try reinstalling firestarter, then choose "Mark for Complete removal" from synaptic package manager (rather than "Mark for removal"). That may remove firestarter configuration files and allow ufw to start at bootup even without rc.local command.

I performed the removal process in terminal with the listed command shown in my original post. What difference (if any other than one using terminal and the other using a GUI) exists between the two removal processes. Does one do more than the other in that regard? I will try this again as a test and list the results when I complete.

---

### Post by laserman on 2011-10-09
> **laserman said:**
> I performed the removal process in terminal with the listed command shown in my original post. What difference (if any other than one using terminal and the other using a GUI) exists between the two removal processes. Does one do more than the other in that regard? I will try this again as a test and list the results when I complete.

I removed "ufw enable" from rc.local and reinstalled firestater. Rebooted. Pinged 8.8.8.8 with no problem. Removed firestarter through Synaptic as a complete removal and rebooted. Pinged 8.8.8.8 again and came up with operation not permitted. Once I enabled ufw, I had no problem.

This stems back to the developer where removal does not replace the original state prior to the installation. The change made in rc.local has been THE BEST option offered so far. Puts an ease on the rest of the family who aren't as anxious to have to perform a terminal action or by GUI with GUFW, enable any firewall everytime the computer starts up.

Thanks again for the assist. Definitely made my breathing a lot easier.

---

### Post by rng on 2011-10-09
Obviously firestarter is making some changes that are not going away with its removal. Whatever these changes are, the entry 'ufw enable' in rc.local is reversing it. 

By the way, can you briefly tell me about 8.8.8.8 url.  Why did you try that rather than trying any regular website address? (I googled and found it to be 'google public dns'  but it is complicated to me).

---

### Post by The Cog on 2011-10-09
It is a DNS server operated by google. It's an easy to remember IP address that should pretty-much always be there and pingable so it's a good test of internet connectivity.

---

### Post by rng on 2011-10-09
Thanks for the info. But an iptables firewall can block ping while allowing web browsing.

---

### Post by emiller12345 on 2011-10-09
If you want to try and track down where those left over commands are located, they might be in the /etc/init.d directory.

```
find /etc/init.d/ -type f -exec grep -l -i "firestarter" '{}' \;
```This will look for the word firestarter in all of the init scripts.  Similarly, you could run,
```
find /etc/init.d/ -type f -exec grep -l -i "iptables" '{}' \;
```too look for any script that is directly setting iptables rules.

---

### Post by rng on 2011-10-09
I have firestarter installed and there is a file '/etc/init.d/firestarter' on my system.  It will be useful to know if laserman has this file on his system (where firestarter has been removed).

---

### Post by JKyleOKC on 2011-10-09
Is there some reason to make this problem so complicated? The iptables listings posted earlier hint that there may be stuff left over from firestarter. After removing firestarter with the "complete" or "-purge" option, issue the simple command ```
sudo iptables -F
```to completely flush all the rules. Then install ufw or gufw and see if things don't just work properly, even without ufw enabled.

Unless the OP has installed services that listen on external ports, all ports will be closed even with no firewall enabled. However, infections coming from drive-by downloads via browser vulnerabilities can still call home, so enabling the firewall is a good idea.

Both firestarter and ufw are simply front ends to the iptables netfilter that's built into the kernel, and they both define rules for it and install them in the system. You can also define your own and install them via the iptables utility, but ufw makes it much simpler. Note that the different front ends do very different things in their rules, so mixing them can create real trouble -- as it apparently did here!

To gain this simplicity of configuration, both front ends create some rather convoluted rules that route incoming packets around Robin Hood's barn to make their decisions. The single command I posted above will erase ALL of those rules and let you start with a clean slate.

---

### Post by laserman on 2011-10-19
> **emiller12345 said:**
> If you want to try and track down where those left over commands are located, they might be in the /etc/init.d directory.

```
find /etc/init.d/ -type f -exec grep -l -i "firestarter" '{}' \;
```This will look for the word firestarter in all of the init scripts.  Similarly, you could run,
```
find /etc/init.d/ -type f -exec grep -l -i "iptables" '{}' \;
```too look for any script that is directly setting iptables rules.

For the Firestarter code, nothing came up.

For the iptables code, /etc/init.d/arno-iptables-firewall came up.

laserman

---

### Post by laserman on 2011-10-19
> **JKyleOKC said:**
> Is there some reason to make this problem so complicated? The iptables listings posted earlier hint that there may be stuff left over from firestarter. After removing firestarter with the "complete" or "-purge" option, issue the simple command ```
sudo iptables -F
```to completely flush all the rules. Then install ufw or gufw and see if things don't just work properly, even without ufw enabled.


I will attempt this later this evening. Thanks for the input.
 
laserman

---

### Post by JKyleOKC on 2011-10-19
> **laserman said:**
> For the iptables code, /etc/init.d/arno-iptables-firewall came up.I'm not familiar with that file, but it may well be creating iptables rules that are causing trouble for you. Use "gksu nautilus" to launch a copy of your "places" browser running with root privileges, drill down to that file, right-click its icon and select its properties for viewing. There, uncheck the box that allows it to be executed as a program, and close down the file manager. That should prevent it from causing any problems.

I use the XFCE window environment, rather than Gnome or Unity, so the exact way of disabling the execute bit may be a bit different for you, but there's sure to be a way to turn it off. If all else fails, you can use the command line in a terminal window: ```
sudo chmod -x /etc/init.d/arno-iptables-firewall
```

---

### Post by emiller12345 on 2011-10-19
> **laserman said:**
> For the Firestarter code, nothing came up.

For the iptables code, /etc/init.d/arno-iptables-firewall came up.

laserman

By any chance did you install the 'arno firewall'? This is just a script to setup various iptables rules. If you have, then you can disable the script from executing by moving the symbolic link that will most likely be located in the /etc/rc2.d/ or /etc/rcS.d/ directories, so it doesn't begin with an 'S'.  For instance...
```
$ ls -l /*etc/rc2.d/S11arno-iptables-firewall*
lrwxrwxrwx 1 root root 20 2010-04-30 11:03 /etc/rc2.d/S11arno-iptables-firewall -> ../init.d/arno-iptables-firewall
$ sudo mv /etc/rc2.d/S11arno-iptables-firewall /etc/rc2.d/K89arno-iptables-firewall
$
```Then the next time you restart, the arno script will not execute.

---

### Post by laserman on 2011-10-19
> **emiller12345 said:**
> By any chance did you install the 'arno firewall'? 

When I first installed the netbook remix on this machine, I would have to say yes but looking at synaptic, it is not installed.

> This is just a script to setup various iptables rules. If you have, then you can disable the script from executing by moving the symbolic link that will most likely be located in the /etc/rc2.d/ or /etc/rcS.d/ directories, so it doesn't begin with an 'S'.  For instance...
```
$ ls -l /*etc/rc2.d/S11arno-iptables-firewall*
lrwxrwxrwx 1 root root 20 2010-04-30 11:03 /etc/rc2.d/S11arno-iptables-firewall -> ../init.d/arno-iptables-firewall
$ sudo mv /etc/rc2.d/S11arno-iptables-firewall /etc/rc2.d/K89arno-iptables-firewall
$
```Then the next time you restart, the arno script will not execute.

This is what I ran in terminal...

```

john@john-hpmini:~$ ls -l /etc/rc2.d/Sllarno-iptables-firewall
ls: cannot access /etc/rc2.d/Sllarno-iptables-firewall: No such file or directory
john@john-hpmini:~$ sudo ls -l /etc/rcS.d/Sllarno-iptables-firewall
ls: cannot access /etc/rcS.d/Sllarno-iptables-firewall: No such file or directory

```

I didn't get what was mention so I decided to look a bit further with this in terminal and this is what I found...

```

john@john-hpmini:~$ sudo find / -iname *iptables-firewall*
/var/log/arno-iptables-firewall
/var/log/arno-iptables-firewall.1
/var/lib/update-rc.d/arno-iptables-firewall
/var/lib/dpkg/info/arno-iptables-firewall.postrm
/var/lib/dpkg/info/arno-iptables-firewall.list
/etc/logrotate.d/arno-iptables-firewall.conf
/etc/init.d/arno-iptables-firewall
/etc/arno-iptables-firewall
/etc/rsyslog.d/arno-iptables-firewall.conf

```

So at this point, would you say that arno-iptables-firewall wasn't completely removed?

laserman

---

### Post by laserman on 2011-10-20
> **JKyleOKC said:**
> Is there some reason to make this problem so complicated? The iptables listings posted earlier hint that there may be stuff left over from firestarter. After removing firestarter with the "complete" or "-purge" option, issue the simple command ```
sudo iptables -F
```to completely flush all the rules. Then install ufw or gufw and see if things don't just work properly, even without ufw enabled.




First, I removed the entry from rc.local.

I performed your recommendation and the outcome was no different. I still have no interent without having to physically enable ufw.

As posted later, one asked me if I had previously installed arno-iptables-firewall and I believe that to be a true statement. There is evidence of these in folders on this machine as shown in post #22. Question is now, is THAT affecting everything where is it possible, even though I have removed that program, a script still doing something to iptables?

laserman
:(

---

### Post by emiller12345 on 2011-10-20
> **laserman said:**
> 
So at this point, would you say that arno-iptables-firewall wasn't completely removed?

the /etc/init.d/arno-iptables-firewall is the script that is probably responsible, although its not in synaptic you could have installed it directly, in which case it wouldn't show up in synaptic.

The results ...
> **laserman said:**
> 
```

john@john-hpmini:~$ sudo find / -iname *iptables-firewall*
/var/log/arno-iptables-firewall
/var/log/arno-iptables-firewall.1
/var/lib/update-rc.d/arno-iptables-firewall
/var/lib/dpkg/info/arno-iptables-firewall.postrm
/var/lib/dpkg/info/arno-iptables-firewall.list
/etc/logrotate.d/arno-iptables-firewall.conf
/etc/init.d/arno-iptables-firewall
/etc/arno-iptables-firewall
/etc/rsyslog.d/arno-iptables-firewall.conf

```
... show (i think) that /etc/init.d/arno-iptables-firewall shouldn't be executed at start-up.

looking at the source code for arno
```
$ find . -type f -exec grep  "ln -" '{}' \;
  ln -sv /usr/local/share/arno-iptables-firewall/plugins/traffic-accounting-show /usr/local/sbin/traffic-accounting-show
# ("ln -s /etc/init.d/arno-iptables-firewall script S99-arno-iptables-firewall script").   #
    ln -sv /etc/init.d/arno-iptables-firewall /etc/rcS.d/S41arno-iptables-firewall
    ln -sv /etc/init.d/arno-iptables-firewall /etc/rc2.d/S11arno-iptables-firewall
```the last two entries show how the init.d script starts up. if you don't have /etc/rcS.d/S41arno-iptables-firewall or /etc/rc2.d/S11arno-iptables-firewall then its probably not the cause.

you might try running the "uninstall.sh" script from the arno website.  It might do a better job of removing it.

---

### Post by laserman on 2011-10-20
> **emiller12345 said:**
> 
you might try running the "uninstall.sh" script from the arno website.  It might do a better job of removing it.

Executed and completed. Removed any and all existence of the arno files. 

Still have to perform 

```
sudo ufw enable
```

in order to get access to the internet.

---

### Post by emiller12345 on 2011-10-20
is ufw activating upon booting? Try this ...
```
sudo ufw status
```
... when if first boots.  If it says inactive, you might try and reinstall
```
sudo apt-get install --reinstall ufw
```
If it says ufw active, then some is changing iptables rules after UFW starts. 
It's probably just easier to band-aid and add the entry to the rc.local

---

### Post by laserman on 2011-10-20
> **emiller12345 said:**
> is ufw activating upon booting? Try this ...
```
sudo ufw status
```
... when if first boots.  If it says inactive, you might try and reinstall
```
sudo apt-get install --reinstall ufw
```
If it says ufw active, then some is changing iptables rules after UFW starts. 
It's probably just easier to band-aid and add the entry to the rc.local

The --reinstall wasn't recognized so I ran sudo apt-get purge -y ufw and re-installed it after that to only have the same issue.

I will agree that this is a band-aid to this problem. Invoking ufw enable in rc.local does get me up and running but it still doesn't hit the root cause. 

I have to agree with Jim on post #17. I should be able to boot this up without having to enable ufw and get online. Trying to even ping my router here in the house isn't even working (I get operation not permitted). Not until UFW is enabled. When I was trying to work between two computers and even try to share an internet connection, God only know what programs I may have dabbled and installed to make it happen, only to fail miserably. It's a moot point now but look what I've got to deal with. Hind sight is 20/20. Next time, I'll do it on a virgin machine where it won't matter what I mess up.

If someone wants to take a stab, I ran this in terminal

```
dpkg -l > installedprograms.txt
```

and have a listing of all of the programs installed. Unless there is another program that may pop into mind, I can search for and uninstall it.

John

---

### Post by JKyleOKC on 2011-10-20
With no "ufw enable" command in rc.local, try this right after startup, when you can't ping out or get to the internet: ```
sudo iptables -L >$home/rulesreport.txt
``` and then copy the report to a message (putting it inside CODE tags of course to preserve the formatting and make it easier to read).

It should be only a few lines long, and list the three built-in chains with their default policies of ACCEPT. If it contains other rules, hopefully one of us will recognize what is creating them and get more ideas of what to look for as a root cause.

You might run that same thing again after enabling ufw, but give the report file a unique name. That can show us exactly what changes ufw is making.

---

### Post by laserman on 2011-10-21
Jim, I did your test and before I post the results, let me throw this out there.

The recommendation that rng put in post #8 that was the band-aid to the fix where I put ufw enable in rc.local? Well, must have had blinders on. I do not know how this line got in rc.local. Note the iptables-restore line at the end. 

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#iptables-restore < /etc/iptables.sav
#ufw enable
exit 0
```

I put the ufw enable near the end just as instructed but never thought about why the iptables-restore line was there. So I # it out and rebooted. Now, in terminal, when I check the status of ufw, it is already enabled. Now, I have no idea what is activating ufw on boot. BUT, other than ufw already enabled, everything is working as it should without having to invoke a command in rc.local to make it happen.

John

---

### Post by emiller12345 on 2011-10-21
> **laserman said:**
> Now, I have no idea what is activating ufw on boot. 
once enabled, ufw should remember the status from boot to boot.

---

### Post by rng on 2011-10-21
@laserman: Interesting climax to a long detective story! But we still have not found the criminal. Why don't you post /etc/iptables.sav file so that we know whose rules are being used there (I think they would be same as before-ufw-enabling.txt that you posted earlier- which seem like firestarter rules). But iptables-restore entry in rc.local seem to be a manual entry by someone on your computer - maybe a long forgotten entry by yourself!

It is reassuring to note that there is no bug in any firewall programs.

---

### Post by laserman on 2011-10-21
> **rng said:**
> @laserman: Interesting climax to a long detective story! But we still have not found the criminal. Why don't you post /etc/iptables.sav file so that we know whose rules are being used there (I think they would be same as before-ufw-enabling.txt that you posted earlier- which seem like firestarter rules). But iptables-restore entry in rc.local seem to be a manual entry by someone on your computer - maybe a long forgotten entry by yourself!

It is reassuring to note that there is no bug in any firewall programs.

Here are the results and for what I know about this, looks like a program call Masquerade seems to be the culprit.

```
# Generated by iptables-save v1.4.4 on Thu Dec 23 14:35:22 2010
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [22:3229]
:OUTPUT ACCEPT [68:8957]
-A POSTROUTING -o ppp0 -j MASQUERADE 
-A POSTROUTING -j MASQUERADE 
COMMIT
# Completed on Thu Dec 23 14:35:22 2010
# Generated by iptables-save v1.4.4 on Thu Dec 23 14:35:22 2010
*mangle
:PREROUTING ACCEPT [2164:977493]
:INPUT ACCEPT [2164:977493]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2190:787063]
:POSTROUTING ACCEPT [2171:782885]
COMMIT
# Completed on Thu Dec 23 14:35:22 2010
# Generated by iptables-save v1.4.4 on Thu Dec 23 14:35:22 2010
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
-A INPUT -s 68.28.250.92/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 68.28.250.92/32 -p udp -j ACCEPT 
-A INPUT -s 68.28.242.91/32 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 68.28.242.91/32 -p udp -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
-A INPUT -d 255.255.255.255/32 -i ppp0 -j DROP 
-A INPUT -s 224.0.0.0/8 -j DROP 
-A INPUT -d 224.0.0.0/8 -j DROP 
-A INPUT -s 255.255.255.255/32 -j DROP 
-A INPUT -d 0.0.0.0/32 -j DROP 
-A INPUT -m state --state INVALID -j DROP 
-A INPUT -f -m limit --limit 10/min -j LSI 
-A INPUT -i ppp0 -j INBOUND 
-A INPUT -d 28.253.17.46/32 -i ppp0 -j INBOUND 
-A INPUT -d 28.253.17.46/32 -i ppp0 -j INBOUND 
-A INPUT -j LOG_FILTER 
-A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6 
-A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT 
-A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu 
-A FORWARD -i ppp0 -j OUTBOUND 
-A FORWARD -d 28.253.17.46/32 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -d 28.253.17.46/32 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -j LOG_FILTER 
-A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6 
-A FORWARD -s 192.168.0.0/24 -i eth1 -o eth0 -m conntrack --ctstate NEW -j ACCEPT 
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT 
-A OUTPUT -s 28.253.17.46/32 -d 68.28.250.92/32 -p tcp -m tcp --dport 53 -j ACCEPT 
-A OUTPUT -s 28.253.17.46/32 -d 68.28.250.92/32 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -s 28.253.17.46/32 -d 68.28.242.91/32 -p tcp -m tcp --dport 53 -j ACCEPT 
-A OUTPUT -s 28.253.17.46/32 -d 68.28.242.91/32 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -s 224.0.0.0/8 -j DROP 
-A OUTPUT -d 224.0.0.0/8 -j DROP 
-A OUTPUT -s 255.255.255.255/32 -j DROP 
-A OUTPUT -d 0.0.0.0/32 -j DROP 
-A OUTPUT -m state --state INVALID -j DROP 
-A OUTPUT -o ppp0 -j OUTBOUND 
-A OUTPUT -o ppp0 -j OUTBOUND 
-A OUTPUT -j LOG_FILTER 
-A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6 
-A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INBOUND -j LSI 
-A LSI -j LOG_FILTER 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP 
-A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p icmp -m icmp --icmp-type 8 -j DROP 
-A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -j DROP 
-A LSO -j LOG_FILTER 
-A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6 
-A LSO -j REJECT --reject-with icmp-port-unreachable 
-A OUTBOUND -p icmp -j ACCEPT 
-A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A OUTBOUND -j ACCEPT 
COMMIT
# Completed on Thu Dec 23 14:35:22 2010
```

@ rng, you are absolutely correct. I disabled ufw and rebooted and in fact, ufw was inactive with no problem accessing and pinging. 

Very true, what a detective story. NOW, I can rest assured that this is solved.

laserman

---

### Post by JKyleOKC on 2011-10-21
> **laserman said:**
> Here are the results and for what I know about this, looks like a program call Masquerade seems to be the culprit.

```
# Generated by iptables-save v1.4.4 on Thu Dec 23 14:35:22 2010
(clipped)
# Completed on Thu Dec 23 14:35:22 2010
```

@ rng, you are absolutely correct. I disabled ufw and rebooted and in fact, ufw was inactive with no problem accessing and pinging. 

Very true, what a detective story. NOW, I can rest assured that this is solved.

lasermanDo you remember just what you had going last December, two days before Christmas? Those dates scattered through the saved rules list tell exactly when the rules were set up, so if you remember how things were configured at that time, you'll know which program did it.

The references to "MASQUERADE" are not the name of the culprit, but rather are a target point within a chain that does the Network Address Translation (NAT) magic within the netfilter's processing. Using iptables-save and iptables-restore is an excellent way to retain a set of rules from one session to another, but as we've seen in this search can also be quite confusing. I use it myself to retain my rule set that I've developed over the years to meet some unusual requirements, since this machine is not only my main workstation but also serves as my router (with one NIC for my LAN and another for the outside world), and as a private FTP server. However I don't call iptables-restore from rc.local any more. Instead, I call it from the /etc/network/interfaces file as an "if-up" action so that it takes effect any time the network adapter that faces the outside world becomes active. This avoids any problems of timing, since the boot process changed from serial activation to parallel actions several releases back...

---

### Post by laserman on 2011-10-21
> **JKyleOKC said:**
> Do you remember just what you had going last December, two days before Christmas? Those dates scattered through the saved rules list tell exactly when the rules were set up, so if you remember how things were configured at that time, you'll know which program did it.

Respectfully, because I wear a ball cap and blue jeans everyday, I can tell you beyond a shadow of a doubt, I was wearing just that on December 23rd. Outside of that, no sir, could not even begin to think what I installed or removed that day.

> The references to "MASQUERADE" are not the name of the culprit, but rather are a target point within a chain that does the Network Address Translation (NAT) magic within the netfilter's processing. Using iptables-save and iptables-restore is an excellent way to retain a set of rules from one session to another, but as we've seen in this search can also be quite confusing. I use it myself to retain my rule set that I've developed over the years to meet some unusual requirements, since this machine is not only my main workstation but also serves as my router (with one NIC for my LAN and another for the outside world), and as a private FTP server. However I don't call iptables-restore from rc.local any more. Instead, I call it from the /etc/network/interfaces file as an "if-up" action so that it takes effect any time the network adapter that faces the outside world becomes active. This avoids any problems of timing, since the boot process changed from serial activation to parallel actions several releases back...

It is your wealth of knowledge and comments on this that helped me dig deeper into this issue. Now, my next lesson will be digging into learning iptables and how the firewalls work in Linux so I can be better educated. Everyday is a learning day.

---

### Post by JKyleOKC on 2011-10-21
> **laserman said:**
> Everyday is a learning day.Absolutely!

I'm probably one of the oldest folk active in this forum (being past 80), but I'm still learning new things every day -- and discussions such as these are what help me keep my mind sharp enough to accept new information even though I've been dealing with computers since the days of vacuum tubes.

Keep in mind that much of the information about iptables that you find on the net is confusing at best and sometimes woefully inaccurate also. The starting point for getting to know iptables and firewalls is to learn how TCP/IP works. Those initials stand for Transmission Control Protocol and Information Protocol, and they provide the framework within which all data moves across the Internet. To be more specific, they provide an "electronic form" with spaces for the sending address, the receiving address, the sending and receiving port numbers, a bit of other housekeeping data, and finally the data itself. That form is what we call a "packet" and the filtering software looks within each packet for specific items, processes its filter rules, and then either accepts the packet, rejects it, or moves on to the next rule.

These packets are each rather short; in most cases they're no more than 1500 bytes each, so it takes a lot of them to move even a short message.

To see individual packets sent or received by your machine, look into the program called WireShark. It can capture them and present them so you can study their layout and content. That's one of the most useful things you can do when trying to grok the netfilter actions! At first none of it will make much sense -- so many "housekeeping" packets move back and forth every minute that it's difficult to find those actually carrying your information. However with study it will eventually come together, and then the confusing material you see dealing with iptables will become much clearer.

Keep at it, and don't hesitate to yell here for assistance whenever you need to. Most of us believe in the idea of "paying forward" for all the help we've received over the years, by passing on any of it that we can.

---

### Post by rng on 2011-10-22
@JKyleOKC:  It is a pleasure to know about you. You may find following link about a recent news item interesting: 

A 100 year old man finished a marathon!    [http://newsfeed.time.com/2011/10/19/a-100-year-old-man-finished-a-marathon-what-have-you-done-today/#ixzz1bYUS91Az](http://newsfeed.time.com/2011/10/19/a-100-year-old-man-finished-a-marathon-what-have-you-done-today/#ixzz1bYUS91Az)
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by JKyleOKC on 2011-10-22
I saw that and find it remarkable. I'm not nearly mobile enough to even consider such a thing myself, but do appreciate anyone who can...

Thanks for the kind words and the tip!

---

