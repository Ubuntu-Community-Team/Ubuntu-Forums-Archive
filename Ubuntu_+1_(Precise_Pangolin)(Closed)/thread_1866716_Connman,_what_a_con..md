---
title: "Connman, what a con."
date: 2011-10-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by seeker5528 on 2011-10-21
I would prefer just to set my interface in the interfaces file, but since the Ubuntu devs don't seem to be too interested in getting resolvconf to do the right thing [Bug #448095](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/448095) and I don't want to apply a band-aid that seems likely to break/get overwritten periodically,  I figured I would give the GUI way a try.

So I figure pulling in the indicator-network doohickey would make sure I had the necessary stuff to display in the panel *and* configure the connection.

Hmmmm. Pulls in connman, pushes out network-manager. 

After fiddling with different options in the interfaces file, I finally got an indication that there was a network connection, but never was able to configure in the GUI, and network was blocked until I removed connman.

Also never saw any indication while messing with connman that there was an option in the GUI to enable static IP at bootup, as opposed to waiting until you log in, then bringing up the connection.

I did see some posts in the net that seemed to indicate it was possible, but just no indication that it is possible in the GUI. If it's not possible in the GUI I would prefer just to set up the connection in my interfaces file and use a cron job or some other trick to ifup the connection later in the boot after the rest of the network stuff is started.

Short story, I purged connman, installed networkmanager and networkmanager-gnome, commented the configuration lines for the ethernet connection in the interfaces file, did my static configuration, and made sure the 'enable for all users' box was checked and that seems to do what I want. 
After I rebooted, I switched to the VT while at the login screen so I could see if I could ping my router before logging in to the GUI, without first having to issue a command to bring the interface up, it worked.

So what's the deal with this connman thing? I have not seen it actually working, but from what I could see of the GUI it seems like a backward step.

I have not be a big fan of network-manager either since in the past it seemed to be borked a lot during development cycles, but does it really have that much baggage that it makes more sense to replace it with something that is less capable?

Don't let the thread title or contents of this post fool you, I don't really care if network-manager or connman is installed by default.

Mainly I am fishing to see what other peoples experience with connman are and what people for whom it actually works think of it's capabilities relative to network-manager and... Is there *really* no way in the GUI to create a static configuration that is enabled at boot time or did I just not see the option because it wasn't working correctly for me? And is it there a general preference of the people in this forum that one or the other should be the default for Precise?

Later, Seeker

---

### Post by cariboo on 2011-10-21
> **seeker5528 said:**
> I would prefer just to set my interface in the interfaces file, but since the Ubuntu devs don't seem to be too interested in getting resolvconf to do the right thing [Bug #448095](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/448095) and I don't want to apply a band-aid that seems likely to break/get overwritten periodically,  I figured I would give the GUI way a try.

So I figure pulling in the indicator-network doohickey would make sure I had the necessary stuff to display in the panel *and* configure the connection.

Hmmmm. Pulls in connman, pushes out network-manager. 

After fiddling with different options in the interfaces file, I finally got an indication that there was a network connection, but never was able to configure in the GUI, and network was blocked until I removed connman.

Also never saw any indication while messing with connman that there was an option in the GUI to enable static IP at bootup, as opposed to waiting until you log in, then bringing up the connection.

I did see some posts in the net that seemed to indicate it was possible, but just no indication that it is possible in the GUI. If it's not possible in the GUI I would prefer just to set up the connection in my interfaces file and use a cron job or some other trick to ifup the connection later in the boot after the rest of the network stuff is started.

Short story, I purged connman, installed networkmanager and networkmanager-gnome, commented the configuration lines for the ethernet connection in the interfaces file, did my static configuration, and made sure the 'enable for all users' box was checked and that seems to do what I want. 
After I rebooted, I switched to the VT while at the login screen so I could see if I could ping my router before logging in to the GUI, without first having to issue a command to bring the interface up, it worked.

So what's the deal with this connman thing? I have not seen it actually working, but from what I could see of the GUI it seems like a backward step.

I have not be a big fan of network-manager either since in the past it seemed to be borked a lot during development cycles, but does it really have that much baggage that it makes more sense to replace it with something that is less capable?

Don't let the thread title or contents of this post fool you, I don't really care if network-manager or connman is installed by default.

Mainly I am fishing to see what other peoples experience with connman are and what people for whom it actually works think of it's capabilities relative to network-manager and... Is there *really* no way in the GUI to create a static configuration that is enabled at boot time or did I just not see the option because it wasn't working correctly for me? And is it there a general preference of the people in this forum that one or the other should be the default for Precise?

Later, Seeker

The one time I tried conman, I almost immediately removed it and reverted to Network-Manager. I set a static ip address using network-manager, after I found that it didn't pay any attention to /etc/network/interfaces. Network-manager starts a lot earlier in Oneiric/Precise then it did in previous version, but it seems to me that it starts about 5 seconds into the boot process. I haven't installed bootchart yet, so I can't check. 

When starting in recovery mode, I seem to recall that it uses dhcp, and ignores static ip settings.

---

### Post by buzzmandt on 2011-10-22
am i to assume from this thread that ubuntu has decided to use conman instead of network-manager?

---

### Post by jbicha on 2011-10-22
No, indicator-network was specifically written for connman which was proposed at UDS Maverick in May 2010 to replace network-manager in Ubuntu. I didn't think it was a particularly good idea and it's looking less and less likely that network-manager will go away any time soon. network-manager does pretty well now.

---

### Post by zika on 2011-10-22
Just as NM got polished enough to be of use and that You could rely on it... I hope that decision will be reconsidered...
Never mind, I'll just be going back to /etc/network/inetrfaces and ifupdown... Old school...

---

### Post by masgeeks on 2011-10-22
Is nm-connection-editor in 11.10 not sufficient to setup network connections...???  Just curious.  Has worked well for me for all type of connections, even VPN...  :-|

---

### Post by seeker5528 on 2011-10-24
> **cariboo907 said:**
> When starting in recovery mode, I seem to recall that it uses dhcp, and ignores static ip settings.

Since it's probably generally expected that many people will not use the 'for all users' setting' combined with the minimal things being started, I would guess that in recovery mode network manager probably is not used.

If network manager forces it's configuration in spite of the fact that you set the connection up in '/etc/network/interfaces', you probably need to change the setting in the network manager configuration file '/etc/NetworkManager/NetworkManager.conf'... ```
[ifupdown]
  managed=true/false
```

If set to 'true' NetorkManager will always manage the interface, if set to 'false' NetworkManager will manage the interface if it is not defined in '/etc/network/interfaces' and will leave it alone if it is defined there.

In the past the default was 'false', but I think it was changed to true somewhere along the way.

Later, Seeker

---

### Post by zika on 2011-10-24
The quickest way to turn NM off and not un-install it is:
```
:~$ cat /etc/init/network-manager.override 
manual
```
Creating such file prevents automatic start of NM, and all candidates in /etc/init in a silmilar manner...
No radical changes but a smooth way to turn it of or on...
Of course, You can turn it on, after boot with ```
service network-manager start
```
By having &#8222;false&#8220;, as is it was mentioned in a previous post, in a right place, keep /etc/network/interfaces and NM in cohabitation with override-file as a nice prevention of NM taking the scene unwantedly...

---

### Post by seeker5528 on 2011-10-24
> **masgeeks said:**
> Is nm-connection-editor in 11.10 not sufficient to setup network connections...???  Just curious.  Has worked well for me for all type of connections, even VPN...  :-|

At the beginning NetworkManager was only targetted at home use and to try to always maintain a connection.

Generally speaking NetworkManager provides a good range of options these days, some bridging and other advance usage is not handled, but people that *really* have a reason to use those advanced configurations I would expect probably configure their stuff a different way.

Previously I did nave NetworkManager installed, but since I defined my configurations in the interfaces file, it wasn't managing anything, so I did no have indicator-network installed.

When I installed indicator-network and it wanted to pull in connman and push out NetworkManager, I figured 'OK, since I am investigating I might as well take a look at that' and did not look to see if connman was a 'depends' or 'recommends'. Apparently it's a recommends, since I removed connman and re-installed NetworkManager, and the indicator-network still shows men the network connection in the tray. All the indicator stuff seems to do the right thing in NetworkManager as far as it's display of network status and access to configuration.

I think the big thing against NetworkManager is that it seems like there have consistently been people that have problems getting it to work, but I think not consistently the same people. As a result you have a lot of people recommending WICD or other GUI tools, but I don't know that the evidence is there to support that they really have less problems than NetworkManager. I think to some extent the reliability issues are due to the changing situation with drivers as they advance their capabilities and hardware coverage, which sometimes results in regressions with hardware that previously worked fine.

As for connman it was designed with embeded use in mind, phones, netbooks, etc... so I don't really know what the arguments for using it in a more general purpose OS environment. 

I did not investigate connman that heavily, googled to see if I could find something about static configurations and tried to use it with and without the interface being defined in my interfaces file. Without the interface being defined in my interfaces file, poking at the network configuration through the 'configuration' option on the indicator-applet or in gnome-control-center did not allow me to enable and without being enabled did not provide access to any settings. With the interface being defined in my interfaces file, it showed a connection being enabled and gave me some access to configuration, but no matter what I tried in the configuration GUI, which does show some different options than when NetworkManager was being used, nothing made the connection work, which I think was due to the 'Airplane Mode' which looks to be a toggle intended for completely blocking network communication on all but the 'lo' interface so your portable device/computer won't connect to random available networks or allow random people connect to you while traveling.

Later, Seeker

---

