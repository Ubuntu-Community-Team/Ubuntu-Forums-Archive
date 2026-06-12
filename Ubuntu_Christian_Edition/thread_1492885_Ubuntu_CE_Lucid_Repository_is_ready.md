---
title: "Ubuntu CE Lucid Repository is ready"
date: 2010-05-25
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2010-05-25
Good news, Ubuntu CE Lucid Repository is ready. 
Using this repository, you would be able to configure dansguardian easily, just use the dansguardian-gui and run autoconfigure.

I have added new feature as well on the dansguardian-gui (parental control), now you could block all internet access on certain times. This feature is usefull for example you want your kid to work on computer, but not allowed him to access internet on certain time, just use computer to do homework or project (that do not need to use internet offcourse). There are two time slots, you could block during day time (e.g. 13.00 - 17.00), or night time (e.g. 21.00 - 8.00). You could also block both time

Here is how to use the repositry and install ubuntu-ce:

For 64 bit Systems:
```
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

```

32 bit Systems:
```
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

```

Please help to test and give me feedback.

DK

---

### Post by stlsaint on 2010-06-20
Hello all, DK has had these repositories up for around 3 weeks now and we have not given him any feedback on this post on them. Please test out the repos and post your install procedures good or bad so that DK can move forward with production on the UCE lucid iso image. My install was a success as explained below.


I have just successfully converted a basic install of lucid to UCE using lucid repository's. All went well without errors but the dansguardian settings seemed to not have started dg but did start tinyproxy. I installed e-sword without issue and a fdew bibles. I ran an update and did a couple reboots. All seems to have went well on my end so as far as im concered the repos are ready for full production.:guitar:

---

### Post by RevJack on 2010-06-20
No issues here. I successfully converted Ubuntu 10.04 to UbuntuCE using the UbuntuCE repos. I don't use Dansguardian, so I can't really comment on it. Installed E-Sword without any problems.

---

### Post by stlsaint on 2010-06-20
> **RevJack said:**
> No issues here. I successfully converted Ubuntu 10.04 to UbuntuCE using the UbuntuCE repos. I don't use Dansguardian, so I can't really comment on it. Installed E-Sword without any problems.

nice...plus 2 for iso production on Lucid UCE!!!

---

### Post by Grunt-0341 on 2010-07-08
It worked great!:KS  I just copy and pasted your 32bit code in a terminal and it did all the work;)  I do think that you should mention that you need to reboot when the name and $ sign appear in the terminal.  I am new to linux and am clueless when it comes to alot of this computer stuff.  I found that in other topics I need to type sudo reboot in the terminal.  I did and everything went well:D  Also, it may be a good idea to teach us less tech savvy folks how to open a terminal.  I just thought I offer some constructive criticism as some of us are just learning :lolflag:I thank you very much for the work you did and all the time you put in.  Great job:guitar:

---

### Post by david_kt on 2010-07-08
> **Grunt-0341 said:**
> I found that in other topics I need to type sudo reboot in the terminal. 

If you are in gui environment, you just need to close the window or type exit. You do not need to reboot every time. Reboot only required if you are in command line only, no GUI.

DK

---

### Post by Grunt-0341 on 2010-07-12
Thanks Dave.  What is Gui?  What is command post?

---

### Post by david_kt on 2010-07-12
> **Grunt-0341 said:**
> Thanks Dave.  What is Gui?  What is command post?

GUI means gnome, KDE or other environtment. Sometime we boot on terminal only (command line), then we have to reboot to start in gui.

But in gui, we also could open terminal emulation, which is command line. But to go back to GUI, just close the windows or type exit.

DK

---

### Post by scottmuz on 2010-07-13
When I turn on web filtering it is extremely slow. So slow it is unusable. When I do a netstat it shows firefox connecting directly to port 80. I thought the iptables rules in ubuntu_ce_firewall are supposed to forward port 80 to 8080, but this doesn't seem to be happening

---

### Post by david_kt on 2010-07-13
> **scottmuz said:**
> When I turn on web filtering it is extremely slow. So slow it is unusable. When I do a netstat it shows firefox connecting directly to port 80. I thought the iptables rules in ubuntu_ce_firewall are supposed to forward port 80 to 8080, but this doesn't seem to be happening

What is the output of:

```
sudo iptables -t nat -L | grep 8080 
```

DK

---

### Post by Megaptera on 2010-07-13
All worked fine for me.

---

### Post by Cityscape on 2010-07-13
Doesn't work for me. :(

Terminal tells me > Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: e-sword-installer but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages


---

### Post by david_kt on 2010-07-13
> **Cityscape said:**
> Doesn't work for me. :(

Terminal tells me

Remove wine1.2 first:
```
sudo apt-remove wine1.2
```

DK

---

### Post by Cityscape on 2010-07-13
I now get this: > WARNING: The following packages cannot be authenticated!
  dansguardian dansguardian-gui e-sword-installer encfs-gui linbread trivia
  opensong ubuntu-ce-wallpapers wine-christian-repos ubuntu-ce-artwork
  ubuntu-ce
Install these packages without verification [y/N]?

Should I install these packages without verification? Is it dangerous or not?

---

### Post by david_kt on 2010-07-13
> **Cityscape said:**
> I now get this: 

Should I install these packages without verification? Is it dangerous or not?

Yes, please install them. I do not make verification yet for those packages.

DK

---

### Post by jkeeting on 2010-07-13
Hello, I am very new here, but have been reading along and trying this upgrade. Here is the error that I receive:

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have Ubuntu 10.04 installed. Any guidance would be appreciated.

---

### Post by david_kt on 2010-07-13
> **jkeeting said:**
> Hello, I am very new here, but have been reading along and trying this upgrade. Here is the error that I receive:

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have Ubuntu 10.04 installed. Any guidance would be appreciated.

You have two choices:
1. Put the cd you use to install ubuntu 10.04 in the cd drive
2. Remove cd rom from the repository, check below :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

DK

---

### Post by scottmuz on 2010-07-14
sudo iptables -t nat -L | grep 8080
returns
REDIRECT   tcp  --  anywhere            !localhost           tcp dpt:www ! owner UID match root redir ports 8080 

When I trace an outbound port from firefox with 'sudo netstat -tnp' I get :
tcp        0      0 127.0.0.1:8080          127.0.0.1:38213         ESTABLISHED 1280/dansguardian
tcp        0      0 10.1.1.2:38213          74.112.128.18:80        ESTABLISHED 3166/firefox-bin

Looks like one half of the socket is connected to dansguardian but the other half isn't. Is that normal?

As I said above firefox browsing is soooo slow when I have the ubuntu ce firewall activated, it unusable.

---

### Post by david_kt on 2010-07-14
> **scottmuz said:**
> sudo iptables -t nat -L | grep 8080
returns
REDIRECT   tcp  --  anywhere            !localhost           tcp dpt:www ! owner UID match root redir ports 8080 

As I said above firefox browsing is soooo slow when I have the ubuntu ce firewall activated, it unusable.

Looks like ok. What is the output of:

```
dansguardian --version
```

DK

---

### Post by scottmuz on 2010-07-15
~>dansguardian --version; dpkg -l | grep dans
DansGuardian 2.9.9.7

Built with:  '--mandir=/usr/share/man/' '--enable-clamav=yes' '--with-proxyuser=dansguardian' '--with-proxygroup=dansguardian' '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--enable-icap=yes' '--enable-commandline=yes' '--enable-trickledm=yes' '--enable-email=yes' '--enable-ntlm=yes' 'CXX=g++' 'CXXFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CC=cc' 'CFLAGS=-g -O2'
ii  dansguardian                              2.10.1.1-1really2.9.9.7-2ubuntu1                Web content filtering
ii  dansguardian-gui                          2.6                                             GUI frontend to setup and manage dansguardia

---

### Post by david_kt on 2010-07-15
> **scottmuz said:**
> ~>dansguardian --version; dpkg -l | grep dans
DansGuardian 2.9.9.7
ii  dansguardian                              2.10.1.1-1really2.9.9.7-2ubuntu1                Web content filtering
ii  dansguardian-gui                          2.6                                             GUI frontend to setup and manage dansguardia

Everything looks fine, not sure why it become very slow.

DK

---

### Post by scottmuz on 2010-07-16
Finally got some time to debug issue. Ended up that tinyproxy was the
issue.

Reverting to the karmic version of tinyproxy 1.6.5 fixed issue.

---

### Post by david_kt on 2010-07-16
> **scottmuz said:**
> Finally got some time to debug issue. Ended up that tinyproxy was the
issue.

Reverting to the karmic version of tinyproxy 1.6.5 fixed issue.

Did you configure dansguardian manually or using auto-configuration in dansguardian-gui?

DK

---

### Post by scottmuz on 2010-07-18
auto-configured, until it didn't work then I started manually debugging.

---

### Post by david_kt on 2010-07-18
> **scottmuz said:**
> auto-configured, until it didn't work then I started manually debugging.

If you have solved it, than it is ok, But if you want to try, today I make dansguardian-gui-squid, the same as dansguardian-gui but using squid instead of tinyproxy. To use that:

```
sudo apt-get remove dansguardian-gui tinyproxy
sudo apt-get install dansguardian-gui-squid
```

The reason I try squid is it is caching proxy, might perform better for internet sharing on LAN with many computers.

DK

---

### Post by calebyong on 2010-07-22
I got a bug, facebook appears to be blank when i load the website, other websites are doing fine. I have facebook in my whitelist, and still the problem is not resolved, what should i do?

---

### Post by david_kt on 2010-07-22
> **calebyong said:**
> I got a bug, facebook appears to be blank when i load the website, other websites are doing fine. I have facebook in my whitelist, and still the problem is not resolved, what should i do?

Please terminal and check:

```
dansguardian --version
```

It should be DansGuardian 2.9.9.7.

You could also try to use squid to replace tiny proxy as follow:

```
sudo apt-get remove dansguardian-gui tinyproxy
sudo apt-get install dansguardian-gui-squid
```

Run autoconfigure again after installing it.
DK

---

### Post by calebyong on 2010-07-22
i've done all you suggested, and it make my filter broken, i really need that filter. I sinned just now because i didn't had the filter on. my dansguardian is 2.9.9.7.

---

### Post by david_kt on 2010-07-22
> **calebyong said:**
> i've done all you suggested, and it make my filter broken, i really need that filter. I sinned just now because i didn't had the filter on. my dansguardian is 2.9.9.7.

Make sure transparant proxy, Squid, and dansguardian status is on. If not, then try stop dansguardian, and then start dansguardian.

DK

---

### Post by calebyong on 2010-07-22
I've done all that. Still nothing.

---

### Post by david_kt on 2010-07-22
> **calebyong said:**
> I've done all that. Still nothing.

Are the indications on for all three?

DK

---

### Post by calebyong on 2010-07-25
No, only tinyproxy and transparent proxy is on. dansguardian is not on.

---

### Post by david_kt on 2010-07-25
> **calebyong said:**
> No, only tinyproxy and transparent proxy is on. dansguardian is not on.

That means you have not tried below yet:

```
sudo apt-get remove dansguardian-gui tinyproxy
sudo apt-get install dansguardian-gui-squid
```

Run autoconfigure again after installing it.

DK

---

### Post by calebyong on 2010-07-27
i have tried that too, made it even worst.

---

### Post by david_kt on 2010-07-27
> **calebyong said:**
> i have tried that too, made it even worst.

You mean the dansguardian could not start? Then try to open terminal and:

```
sudo /etc/init.d/dansguardian start
```

What is the output?

DK

---

### Post by calebyong on 2010-07-27
caleb@caleb-desktop:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as proxy and I am trying to open /var/log/dansguardian//access.log
[fail]

---

### Post by david_kt on 2010-07-27
> **calebyong said:**
> caleb@caleb-desktop:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as proxy and I am trying to open /var/log/dansguardian//access.log
[fail]

That means you do not do this step:

```
Run autoconfigure again after installing it.
```

Try to run that step, it should solve your problem.

DK

---

### Post by calebyong on 2010-07-27
still nothing is happening, still off. I have done all the steps you've told me to. Still its off.

---

### Post by rickyrockrat on 2010-08-01
I've got the same issue. I assume auto configure is chosen from the entry in the GUI:
"Autoconfigure/Reset Dansguardian and Squid".

I installed dansguardian-gui + tinyproxy, ran autoconfig as above. DansGuardian refuses to start:
"Error connecting to parent proxy"

Uninstall the above two, install dansguardian-gui-squid.
Run autoconfig as above, get access error:
"I am running as proxy and I am trying to open /var/log/dansguardian//access.log"

The double-slash is highly suspicious, but still unusable for non-geek users.

So someone should remove that double-slash, but the issue is that when re-installing, the script does not wipe out the log dir, so /var/log/dansguardian is owned by dansguardian.  Run this command:
```
sudo chown -r proxy:proxy /var/log/dansguardian
```

---

### Post by rickyrockrat on 2010-08-01
Now for the next issue. I run squid on my own server, and you have to re-direct port 80 to whatever squid is listening on (3128 in this case). iptables does not show that rule anywhere. Is there more required to install besides just dansguardian-gui-squid?  A side note: I am using Kubuntu with CE repos activated, so have not done a full install of UCE.

Please advise. Thanks. Hmmm. It seems to be working, and I was mistaken about the firewall rules.  I'm used to squidGuard doing URL filtering, so when I went to sites already filtered by my own system or OpenDNS I didn't get the expected error screen.  It appears DansGuardian does content, not URL filtering.

---

### Post by StuartPearson on 2010-08-21
Hi
I just upgraded my 10.04 

With tinyproxy I could not access the internet at all

After I'd done the switch to squid 
```
sudo apt-get remove dansguardian-gui tinyproxy
sudo apt-get install dansguardian-gui-squid
```
it all works fine.

---

### Post by Jordy_224 on 2010-08-30
I used to following steps to install [B]Dansguardian
[/B]

1.Installed ubuntu 10.04 using miniCD
```
https://help.ubuntu.com/community/Installation/MinimalCD
```
2.Update and Upgrade
 ```
sudo apt-get update | sudo apt-get upgrade
```
3.Installed the Repository per david_kt May25th post
```
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```
4.Followed Step by Step guide posed by John Yoon available at 
[HTML]http://ubundance.blogspot.com/2010/07/how-to-install-and-setup-dans-guardian.html[/HTML]
5.Within the guide I received an error at step #7 as seen below:  
```
localhost:/etc$ sudo /etc/init.d/dansguardian restart
```
Output:
[PHP]
Restarting DansGuardian:  * Restarting DansGuardian:                            Error opening/creating log file. (check ownership and access rights).

I am running as proxy and I am trying to open /var/log/dansguardian//access.log[/PHP]
6.Changed the ownership of the file: /var/log/dansguardian//access.log
```
sudo chown -r proxy:proxy /var/log/dansguardian
```
7.Auto restart dansguardian
```
sudo /etc/init.d/dansguardian start
```

8. use the Auto/configure option in dansguardian GUI

9. Manually edited the Firefox proxy: posed by gohsthb:

[HTML]http://ubuntuforums.org/showthread.php?t=812832[/HTML]

```
Lock specific preferences in Firefox so that users cannot edit them
lockPref("app.update.enabled", false);
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1, 192.168.1.0/24");
lockPref("network.proxy.share_proxy_settings", true);
lockPref("browser.startup.homepage", "http://www.desiredhomepage.com/");
```


10. Force Transparent on proxy status by restarting ubuntu_ce_firewall. 

 
a. create a cronjob or use rc.local

```
sudo cronjob -e 
```

or

```
Sleep 20 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```

b. The script is executed once when booting the system, even when booting directly into single user mode.


11. Added an updated *blacklist* of websites to dansguardian blacklist folder from the website: 

     [URL="http://dansguardian.org/?page=blacklist"]http://dansguardian.org/?page=blacklist
[/URL]

This step greatly improved the filtering results** ! **
[B]
a.[/B] It requires that the user manually include the **blacklist links** to the following files in the dansguardian folder.

   [B]/etc/dansguardian/lists/bannedsitelist
   /etc/dansguardian/lists/bannedurllist
   /etc/dansguardian/lists/exceptionsitelist
   /etc/dansguardian/lists/exceptionurllist[/B]



12. Setup fini !

---

### Post by vtamara on 2010-09-02
I have tested both versions and it has worked fine.

However today I could install a 32 bit machine, but not at all the 64 bit version in other machine, it reports:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
E: Broken packages

---

### Post by Jordy_224 on 2010-09-02
I did notice an error ...  
The transparent proxy returns to off by default.

For example...

If dansguardian gui options are: 
Transparent: **on**
Tinyproxy: on
Dansguardian: on
internet sharing: off
Current Filter: child
Filter Value: on

Then after reboot! the configuration changes to 
Transparent: **off**
 
If transparent is off then the filter no longer is functional. To restore the proxy a user must be use the autoconfigure/reset function which requires root privileges 

user@localhoast$dansguardian -version 

```

DansGuardian 2.9.9.7

Built with:  '--mandir=/usr/share/man/' '--enable-clamav=yes' '--with-proxyuser=dansguardian' '--with-proxygroup=dansguardian' '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--enable-icap=yes' '--enable-commandline=yes' '--enable-trickledm=yes' '--enable-email=yes' '--enable-ntlm=yes' 'CXX=g++' 'CXXFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CC=cc' 'CFLAGS=-g -O2'
```


How to making Transparent proxy: &#8220;on&#8221; as the default option rather than relying on autoconfigure.Any suggestions?



In addition: 
I did notice that Firefox proxy remains unlocked even after selecting for locked status in the gui. By default it starts as unlocked. 

For example...

If dansguardian gui options are:
Transparent: on
Tinyproxy: on
Dansguardian: on
internet sharing: off
Current Filter: child
Filter Value: on
**Firefox proxy is unlocked **

---

### Post by Jordy_224 on 2010-09-13
Problem fixed. 

The solution was to manually lock firefox proxy. 

To do so I used the following guide, by gohsthb here: 

[http://ubuntuforums.org/showthread.php?t=812832](http://ubuntuforums.org/showthread.php?t=812832)

but for xubuntu edit the apturl.js file with gedit. 

```
sudo gedit /etc/firefox-3.0/pref/apturl.js

```

Next, 
After restart the firefox proxy setting were still reserved.  Tinyproxy remained connected, even after restart dansguardian blocked access. 

works fine. 

keep up the good work dansguardian!

---

### Post by rykel on 2010-09-21
I tried to install Ubuntu CE from Lucid, but received the following error! I have official WINE 1.2 from WineHQ but am not sure if that is causing the "conflict".

> [B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: e-sword-installer but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages
[/B]

---

### Post by david_kt on 2010-09-21
> **rykel said:**
> I tried to install Ubuntu CE from Lucid, but received the following error! I have official WINE 1.2 from WineHQ but am not sure if that is causing the "conflict".

Ubuntu CE is using wine stable, so as wine beta from wineHQ will cause problem. Please remove wine and remove WineHQ repository.

DK

---

### Post by rykel on 2010-09-21
> **david_kt said:**
> Ubuntu CE is using wine stable, so as wine beta from wineHQ will cause problem. Please remove wine and remove WineHQ repository.

DK

I have noticed that... when I tried to install wine1.2, it tries to remove ubuntu-ce and e-sword... are you able to make a version of e-sword/ubuntu-ce that CAN work with the beta wines?

Thank you so much so far!

---

### Post by david_kt on 2010-09-22
> **rykel said:**
> I have noticed that... when I tried to install wine1.2, it tries to remove ubuntu-ce and e-sword... are you able to make a version of e-sword/ubuntu-ce that CAN work with the beta wines?

Thank you so much so far!

Yes, but it is very difficult to support as wine continue upgrading and might cause problem with e-sword installer and wine christian repository. Means, I have to continually try e-sword installer and wine christian repository and fix any bug introduced by new package of wine.

By the way, you do not need e-sword installer/ubuntu-ce after you install e-sword. So, you could just proceed to install wine1.2 and remove e-sword installer and ubuntu-ce. It would not affect anything, you still have all ubuntu ce packages neccesary for daily use.

DK

---

### Post by rykel on 2010-09-24
> **david_kt said:**
> Yes, but it is very difficult to support as wine continue upgrading and might cause problem with e-sword installer and wine christian repository. Means, I have to continually try e-sword installer and wine christian repository and fix any bug introduced by new package of wine.

By the way, you do not need e-sword installer/ubuntu-ce after you install e-sword. So, you could just proceed to install wine1.2 and remove e-sword installer and ubuntu-ce. It would not affect anything, you still have all ubuntu ce packages neccesary for daily use.

DK

oic! Hmmm, what do you think about this idea then... let ubuntu-ce autoremove wine1.2 (or any beta wine for that matter), install e-sword installer and then autoremove wine stable plus install back the wine beta?

This would then cause no confusion to newbie ubuntu-ce users like me, who initially could not figure out the error message, until I came to this thread. Thank you so much!!

p/s. btw, does anyone know if there is a Ubuntu Muslim Edition?

---

### Post by david_kt on 2010-09-24
> **rykel said:**
> oic! Hmmm, what do you think about this idea then... let ubuntu-ce autoremove wine1.2 (or any beta wine for that matter), install e-sword installer and then autoremove wine stable plus install back the wine beta?

This would then cause no confusion to newbie ubuntu-ce users like me, who initially could not figure out the error message, until I came to this thread. Thank you so much!!

p/s. btw, does anyone know if there is a Ubuntu Muslim Edition?

The wine stable is meant for two packages: e-sword installer and wine Christian repository. So, if it is upgraded to beta, the wine Christian repository might have problem as well, depending on the beta wine. So, it is better to keep it stable so as if you want to use e-sword installer or wine Christian repository, you could re-install ubuntu-ce. If you want to use wine beta after that, install wine beta.

DK

---

### Post by jonathonblake on 2010-09-25
> **rykel said:**
> does anyone know if there is a Ubuntu Muslim Edition?

It is currently known as Sabily, and can be downloaded from [http://www.sabily.org](http://www.sabily.org). 

There also is a Buddhist remix whose name changes at nearly every release. The current version is zenix, obtainable from 
[http://zenix-os.net/](http://zenix-os.net/) . Prior remixes included Buddhabuntu and Ubuntu Bhuddist Edition.

Ubuntu Jewish Edition has not been updated since version 7.10 was released.

Ubuntu Satanic Edition is obtainable from [http://ubuntusatanic.org/](http://ubuntusatanic.org/) .

I think that covers the extent of other religiously orientated Ubuntu remixes.

jonathon

---

### Post by rykel on 2010-09-26
> **jonathonblake said:**
> It is currently known as Sabily, and can be downloaded from [http://www.sabily.org](http://www.sabily.org). 

There also is a Buddhist remix whose name changes at nearly every release. The current version is zenix, obtainable from 
[http://zenix-os.net/](http://zenix-os.net/) . Prior remixes included Buddhabuntu and Ubuntu Bhuddist Edition.

Ubuntu Jewish Edition has not been updated since version 7.10 was released.

Ubuntu Satanic Edition is obtainable from [http://ubuntusatanic.org/](http://ubuntusatanic.org/) .

I think that covers the extent of other religiously orientated Ubuntu remixes.

jonathon

I guess there is no "Atheist-buntu" right? hehe, thank you man!

---

### Post by cowlitzron on 2010-10-27
Works fine on Ubuntu 10.10 Maverick except Danguardian doesn't allow sites to get through on Firefox unless you tweak it like the directions given in another thread.  I don't use Dansguardian because I do not have any young children.  I usually use the Epiphany browser.  Dansguardian might possibly work on Epiphany if tweaked, since Epiphany does have a Lockdown feature.

---

### Post by ArgusVision on 2010-10-28
Hi. Probably a little late on the response, but I just added CE repo successfully. I'm just excited to see CE is still around. Last time I had any dealings with CE was in 2007. God Bless, and keep up the good work!

---

### Post by PhawKhrua on 2010-11-07
Oops!  Just went to the download page for CE, grabbed the torrent and started to download what the page says is the latest and greatest, but now I discover it's Ubuntu 9.10, not 10.10.

Is there an actual ISO of the TRULY latest, or is it not possible to perform a completely new installation of CE directly?

Thanks.

---

### Post by Cityscape on 2010-11-30
I'm getting this on a fresh install of Lucid:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
E: Broken packages


---

### Post by david_kt on 2010-11-30
> **Cityscape said:**
> I'm getting this on a fresh install of Lucid:
You probably use wrong architecture. Please check what do you use, 32 bit or 64 bit.

DK

---

### Post by Cityscape on 2010-12-01
> **david_kt said:**
> You probably use wrong architecture. Please check what do you use, 32 bit or 64 bit.

DK
I use the i386 architecture (32 bit). CE Jaunty and Lucid have both worked on this computer in the past. But this time it's not installing smoothly. :???:
Any help is much appreciated.

---

### Post by david_kt on 2010-12-01
> **Cityscape said:**
> I use the i386 architecture (32 bit). CE Jaunty and Lucid have both worked on this computer in the past. But this time it's not installing smoothly. :???:
Any help is much appreciated.

MAke sure you use below for 32 bit:

```
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

DK

---

### Post by Cityscape on 2010-12-02
Well, that worked. I must have been using the 64 bit instructions.
Now I feel so foolish (but I guess this kind of thing happens sometime to everyone).

Thanks a lot for your help. ;)

---

### Post by Jordy_224 on 2010-12-05
Hey,  

Dansguardian is running fine and is a big improvement over other software however.
 The session time-limit function is problematic. I think it has to do with the transparent proxy option. If transparent proxy is **on** session limiter works if **off** it doesn't

 After reboot the transparent proxy randomly switches to off. 

```
transparent proxy = **off**. 
```

Of course, I used to **auto-configure **option to restore settings, but I don't want to have to do this at every restart. 

I think there is a setting in my firehol/tinyproxy  proxy that conflicts with dansguardian.



> Ubuntu 10.04
> i386 architecture (32 bit)
> dansguardian -v 

```
DansGuardian 2.9.9.7


Built with:  '--mandir=/usr/share/man/' '--enable-clamav=yes' '--with-proxyuser=dansguardian' '--with-proxygroup=dansguardian' '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--enable-icap=yes' '--enable-commandline=yes' '--enable-trickledm=yes' '--enable-email=yes' '--enable-ntlm=yes' 'CXX=g++' 'CXXFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CC=cc' 'CFLAGS=-g -O2'
```

---

### Post by david_kt on 2010-12-05
[QUOTE=Jordy_224;10201015

I think there is a setting in my firehol/tinyproxy  proxy that conflicts with dansguardian.[/QUOTE]

You should remove firehol and any other firewall and see if it solve the problem.

DK

---

### Post by Jordy_224 on 2011-03-07
Thanks for you work with UCE. Do you have any suggestions for blocking online web proxies that use the glype format? 

Currently, I've set a keyword filter of anonymous proxy. This removes access most online proxies but not all. 
 

Thanks again

---

### Post by andrew5859 on 2011-03-10
Ubuntu CE repository doesn't exist.....it can't be found....Error Code 404.  And yes, I'm using the right one....I've tried several times, copying and pasting and/or typing into terminal the exact line code for the appropriate 32bit, unless you have the ppa address or code to put into the repository list of update manager.....it doesn't work...so any suggestions would be greatly appreciated...thank you in advance....I also see, not to many people come on this thread.


Andrew

---

### Post by david_kt on 2011-03-10
I don't own the repos:
Your website has been suspended!

I will setup another repository on my own web server if I have time.

DK

---

### Post by Jordy_224 on 2011-03-12
dansguardian.deb pagkage : Ubuntu 10.10
 
[http://pkgs.org/ubuntu-10.10/ubuntu-updates-universe-i386/dansguardian_2.10.1.1-2ubuntu0.1_i386.deb.html]("http://pkgs.org/ubuntu-10.10/ubuntu-updates-universe-i386/dansguardian_2.10.1.1-2ubuntu0.1_i386.deb.html")

- Jordy

---

### Post by tumelo on 2011-03-13
Ya danguardian isn't working on my machine anymore for some reason. It says it's running, but it's not blocking anything. I tried to reinstall the gui to take a look at it, but it did't work because it fetches it from the website that's down. I don't understand why dansguardian is directly attached to ubuntuce. It's just a web filter, nothing directly Christian about it.

---

### Post by Jordy_224 on 2011-03-13
tumelo,

Is the transparent proxy status **on** | **off**.? 

I had a similar issue. I suggest making sure firefox is running through the proxy first. This is done by checking the firefox preferences | networking. Change the manual configuration:

Http Proxy: 127.0.0.1 port **8080**
use proxy all protocols :** yes.** 

Second, try restarting the firewall using the command line:  
**/etc/init.d/ubuntu_ce_firewall restart**


I found that a transparent proxy conflict would disable dansguardian. This may or maynot be your problem, but its a worth trying first.


-Jordy

---

### Post by tumelo on 2011-03-13
Thank you so much Jordy. Changing my network preferences on chrome worked.

---

### Post by Jordy_224 on 2011-04-16
to any blacklist expert, 

Is dansguardian able to restrict  [https://foo.bar](https://foo.bar) sites based on **key word**? 

In a custom phrase-list file, I entered words directly from [COLOR="Blue"][https://camolist.com]("http://camolist.com")[/COLOR] for example. 
Then I blacklisted the site in a custom **blacklist.txt**. 
Both attempts **failed**. 

any recommendations? 

Here is an example of my custom PhraseList to block a camolist site.
```

me@localhost: nano ./mybanned_phraselist 

./mybanned_phraselist:
< Browse >,< anonymously >,< bypass >,< your >,< workplace >

me@localhost:/etc/init.d/dansguardian restart 

```

Update: 
Dansguardian does not filter https. However using the url blocker is effective. One can blacklist https websites. Or its possible to blanket blacklist all http, and draw specific exceptions.

-Jordy

---

### Post by Jordy_224 on 2011-05-18
Hello, 

All my attempts to block the following "proxy" site have
failed. So, far I have used keywords to edit (urlblock, weighted-phraselist, and bannedphrase site) Do you have any suggestions? This proxy seems to be a really tricky one.

```

```

---

### Post by nysnsweet on 2011-06-27
Hello,


I installed Ubuntu CE with Ubuntu 10.04 and have a few problems:


1. When I tried to download the bibles in e-sword, I have an error message pop up that says:
 

Esword_installer error: Note: command 'uget -nd --read-timeout=300 --retry-connrefused --header Acept-Encoding: gzip,deflate [http://www.e-sword.net/files/setup960](http://www.e-sword.net/files/setup960)
 

I pressed okay.  Then the 2nd error came up that says:
Esword_installer error: Note: command 'env WINEPREFIX=/homestephen/.wine_Esword wine /home/stephen/.wineeswordcache/setup960.exe' returned status 2.  Aborting.
 
The following is what the terminal said:

fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e3cd9b8, overlapped 0x7e3cd99c): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/stephen/.wine' has been updated.
Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/stephen/.wine_Esword wine regedit /home/stephen/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e3cd9b8, overlapped 0x7e3cd99c): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/stephen/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/stephen/.wine_Esword wine /home/stephen/.wineeswordcache/setup960.exe
wine: cannot find '/home/stephen/.wineeswordcache/setup960.exe'
Note: command 'env WINEPREFIX=/home/stephen/.wine_Esword wine /home/stephen/.wineeswordcache/setup960.exe' returned status 2.  Aborting.

How can i fix this?

2. How do you turn on Dansguardian?  I did a quick internet search, and did not find anything blocked.

3.  How do you use OpenSong?  I tried to use the program, but it just goes straight to Open file...but I thought program would open up itself to display songs?

Sorry for lots of questions.. Please help if you can.  Thanks so much for reading/helping.

---

### Post by jonathonblake on 2011-06-27
> **nysnsweet said:**
> 
wine: cannot find '/home/stephen/.wineeswordcache/setup960.exe'
Note: command 'env WINEPREFIX=/home/stephen/.wine_Esword wine /home/stephen/.wineeswordcache/setup960.exe' returned status 2.  Aborting.

That attempts to install e-Sword 9.6.0.
The minor problem is that e-Sword 9.6.0 is no longer supported, and is no longer available.  The current version is e-Sword 9.9.1.

> How can i fix this?

Use the current installation script found in the first post of the thread at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

jonathon

---

### Post by nysnsweet on 2011-06-27
> **jonathonblake said:**
> That attempts to install e-Sword 9.6.0.
The minor problem is that e-Sword 9.6.0 is no longer supported, and is no longer available.  The current version is e-Sword 9.9.1.



Use the current installation script found in the first post of the thread at [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

jonathon

Thanks for your help Jonathon...On the first post, it says:
WARNING: DO NOT run below installer with sudo or as root
but the first or 2nd command is with sudo?  So i dont understand why that would be in red if it is a warning?  Confused....

---

### Post by david_kt on 2011-06-27
> **nysnsweet said:**
> Thanks for your help Jonathon...On the first post, it says:
WARNING: DO NOT run below installer with sudo or as root
but the first or 2nd command is with sudo?  So i dont understand why that would be in red if it is a warning?  Confused....

Some people run the INSTALLER with sudo (i.e. sudo ./e-sword_installer ), that would cause file ownership problem.

DK

---

### Post by Jordy_224 on 2011-07-19
Dansguardian experts, 

 I am using dansguardian to filter all **ssl **traffic. That means, sites such as _[https://www.shopping.com](https://www.shopping.com)_ are blocked. It works, but **only in Firefox** not in other bowsers. Why is this the case? 

The following is a print-screen showing that a https proxy site is blocked in Firefox but not in opera browser.



-Jordy

---

