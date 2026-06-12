---
title: "panv3 wireless problems"
date: 2007-08-25
forum: System76 Support
---

### Post by octathlon on 2007-08-25
I am making a separate thread for this because it's (probably) unrelated to the "slowdown" issue in the other thread.

My panv3 successfully connects on startup, but within anywhere from 5 minutes to 2 hours, it drops the connection and won't reconnect, usually eventually timing out and saying "no network connection". There have been a few times that it did successfully reconnect, but not in the last couple of days.  I try clicking the network again to initiate the connection and it tries again, but can't connect. Logging out and back in doesn't help, only rebooting.  However one time, 30 minutes after losing the connection when it didn't seem to time out (the animated icon was still going), it suddenly asked for my keyring password again and reconnected.  Then lost the connection again later on. 

Meanwhile, my other notebook does not lose its connection during the whole time. 

I don't want to start messing around with settings too much until I hear what System76 suggests.

Overall I love this notebook - it's beautiful and fast, but when it comes down to it, wireless connectivity is THE most important thing to me.

Update: Just before posting this message, I tried setting my router to broadcast the network name; I had it set not to broadcast before.  After rebooting and connecting, the wireless connection was dropped in a few minutes; I restarted again, and since then, it has not dropped the connection! I have no idea whether changing that setting on the router could have anything to do with it, don't see why it would, but that's the only thing I have changed.  I have even put the machine to sleep and resumed twice and it continued to work perfectly.  I will keep monitoring it the rest of the weekend and see how it goes.

Update#2: Nope, it dropped the connection again, and I could not get it to reconnect without restarting the system. I tried "sudo /etc/dbus-1/event.d/25NetworkManager restart" and that did not work; it also didn't ask me for my keyring password again when I did that.  I think it is losing the network key somehow, because the one time it did successfully reconnect was the time it prompted me to enter my keyring password again.

---

### Post by thomasaaron on 2007-08-27
I can't seem to duplicate this on our shop panv3. Its connection is very stable.

Can you possibly try it out on a network other than your own and see if you experience similar problems. It sounds like something in your network is interfering with network manager.

I'm also wondering if it is a proximity issue. If you are closer, or further away from your router, do you have the same issue?

---

### Post by octathlon on 2007-08-27
I may be able to try our library's wireless connection or something.  I have a small house and the farthest I get from the router is about 30 feet; at that range the connection strength is around 75%.  

Dropping the connection occasionally is one thing, but the important thing is to be able to reconnect.  I just have a typical setup using WEP.  I considered turning off password protection for a while to see what would happen, but not sure if that would help figure out anything.

---

### Post by octathlon on 2007-08-27
Tonight I kept the laptop about 5 feet from the router; it reported 95% signal strength.  The same problem happened as before.  Should I send you the daemon.log file?  It seems very detailed about what all Network Manager is doing but it's greek to me.

---

### Post by thomasaaron on 2007-08-28
Yes, go ahead and post it. 

But I'd still like to know what it does on another network.

Whenever this sort of thing happens, I get suspicious of the home network. Network Manager has some connection difficulties here at System 76 due to some interference we've never quite been able to put our finger on. We believe it is due to the wireless router in a nearby office.

Sometimes it is very difficult for us to establish wireless connectivity; sometimes it kicks us off; Sometimes network manager disappears from the toolbar. Anywhere else, there is no problem whatsoever.

So, we really need to establish whether the problem is with the computer or the network.

---

### Post by octathlon on 2007-08-28
It is rather large so I am attaching a .tgz of it (had to give it a .tar extension for it to be accepted).
Aug 27 - 18:26 is when I booted up
20:49 is when it lost the connection and tried to reconnect
22:00 is when I tried to get it to reconnect by clicking the network name (xiexieni) in Network Manager.

There is another Linksys network in the area that shows up on the list sometimes, but it was not showing up last night at the times that I looked.  I'll try to find another network to connect to and test soon.  As I mentioned, I've used my Windows notebook on this network the last 2 years and it has not had any problems either dropping the connection or getting connected (other than that I have always had to manually restart the WirelessZeroConfig service every time after resuming from suspend).

Thanks,

---

### Post by thomasaaron on 2007-08-28
OK. 

Again, don't use another network in the immediate area.
You might try a coffee house or something. That way you can enjoy a hot brew while testing!

Best,
Tom

---

### Post by thomasaaron on 2007-08-28
This seems to stick out in the log:

```
Aug 27 20:50:22 PANG-LT2 NetworkManager: <information>^Iwpa_supplicant(9566): Authentication with 00:00:00:00:00:00 timed out. 
```

This line occurs numerous times in the log.

It means that Network Manager is seeing your access point but is unable to complete the authentication process with it. My initial thoughts are that you do not have Network Manager configured correctly with your router. Perhaps you have WPA confused with WEP. Perhaps your router is listening for a 64 bit code and you have NetworkManager sending a 128 Bit code. Perhaps Your Router is set to open system and your router is set to shared key. Perhaps your router is set to static ip and NetworkManager to dhcp. I don't know. But if it is a mismatch, you'll need to use a sharp eyeball to figure it out. Sometimes you can actually get a poor connection with mismatched settings, but there are always performance consequences and instability.

My guess is that this is the problem.

This link sounds very much like your issue:
[http://www.nabble.com/Frequent-Disconnects-t4082069.html](http://www.nabble.com/Frequent-Disconnects-t4082069.html)
It offers some thoughts on interference which I found interesting (and have experienced myself with Network Manager).

I'm pretty sure the problem boils down to:
1. Settings

-or-

2. Interference that is screwing up network manager 


One last detail: You've never downloaded madwifi, have you? It often shows up when googling issues similar to yours.

---

### Post by octathlon on 2007-08-28
Great, I will check my settings carefully tonight.  The one that jumps out at me as a possibility is open system vs. shared key -- I didn't verify that setting on my router when I set up NM.  I hope it's that simple, and not an interference thing.

No, I haven't downloaded madwifi.

Thanks a lot,

---

### Post by palintheus on 2007-08-28
Not sure, but this could be a bug in NM, I often experience lots of disconnects throughout the day, and sometimes it will reconnect in ~30 sec other times it will not reconnect and I have to go in and re-select my network. I use WPA, and there is a WEP and a Open network within range. 

You also mention interference, could this be caused by other modems and non-wifi routers in the same area as the wifi area?

```

Aug 28 08:06:24 darter ntpd_initres[5755]: ntpd returns a permission denied error!

```

The above error in the log also occurs in my log, and this is the only other line that pops out at me and it occurs a lot. 

This is on a Daru2

---

### Post by octathlon on 2007-08-28
All my settings seem to be ok; DHCP, WEP 128-bit encryption, with the correct key stored in Keyring Manager. The router's Authentication type is set to "Auto", which is supposed to accept either open or shared key, so theoretically it shouldn't matter which way I set it on the laptop.  
One good thing is, ever since I enabled broadcasting the SSID the other day, whether a coincidence or not, the connection is a lot more stable, though it does eventually get disconnected sooner or later.  

Question: On Network Manager, if I want to change from Shared Key to Open system, how do I edit those settings?  I entered them the first time I connected to my network.  The only options given are Connect to Other, Create New, or Manual configuration. Manual config just opens the System |Administration |Network  GUI, which I should NOT do, right?

---

### Post by thomasaaron on 2007-08-29
I've found on my Linksys router that using the "Auto" option did not work well for me. That is one of the things that convinced me that Network Manager is VERY picky. You're definitely OK if you set it EXACTLY the same on your router and network manager.

Also, I've had much more luck with Open System than Shared Key.
I'd recommend you change that as well.
To set it to open key, you can always set a new WEP key with your router. Then Network Manager will prompt you again for your key. At that point, you can choose Open System from a drop down menu.

---

### Post by octathlon on 2007-08-29
OK.

On my Linksys router, the only two options are Auto or Shared Key.  So I guess first I'll try setting Network Manager to Open system and if that doesn't help, I'll try setting both of them to Shared Key.  

thanks!

---

### Post by octathlon on 2007-08-29
Update:  I have not changed any settings yet.  For the last two evenings, Network Manager has been playing nice and not lost the connection.  I figure as long as it's working, I won't do anything to jinx it!

---

### Post by octathlon on 2007-09-04
Update:  Network Manager now seems to be able to reconnect after a disconnect.  Here's what I did:
Keyring Manager had both a default and a session Keyring.  I had tried deleting the session keyring before which didn't seem to affect anything.  The default keyring had only the key to my wireless stored there.  I deleted the default keyring.

I restarted.  I then had to re-enter my wireless key and I made sure to select Open System.  I got prompted to enter the Keyring password and this time I entered the same password as I use for my login.   I've only had a disconnect once since then, but NM quickly reconnected, and without asking me to enter the keyring password.

As I mentioned in an earlier post, after I set my network to broadcast the SSID, I have had very few disconnects, though I don't know if that's why.  I'll have to wait to see if it continues to successfully reconnect but it looks promising.

---

### Post by Zxaos on 2007-11-26
I'm having a similar issue, and it has just started since installing gutsy.

I'm using a local d-link router which broadcasts the SSID and is running WEP.  However at variable intervals, usually longer than 5 hours of runtime, the network manager applet will display that there is no signal strength (it usually sits at around 89%)  The windows laptop I have continues to work on the wireless connection, though. Sometimes, I will get a prompt to re enter the WEP key, but not always. In most cases, the wireless will refuse to connect to any network after this point, even other visible networks in the area.  Eventually, the applet icon will freeze and the system will stop responding normally - programs will open but many of the gnome components like nautilus will stop responding, and I am unable to shutdown or restart the system from either gnome or doing it through a console command. The only way to regain normal operation is to hard reset the system, at which point the wireless resumes working normally.

This occurs at various signal strenghts (I've left the machine 3 feet away from the router and still had this happen).

Any suggestions?

---

### Post by thomasaaron on 2007-11-26
We probably need to have a look at /var/log/messages just after it disconnects.

cat /var/log/messages

---

### Post by Zxaos on 2007-12-09
Here are the lines that I get from messages:

```
Dec  9 02:43:19 Baldr dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Dec  9 02:43:19 Baldr dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Dec  9 02:43:21 Baldr kernel: [ 5743.116000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

At this point I got a popup requesting the the network's WEP key again. I canceled the dialog which changed the network applet to the disconnected symbol.

I then clicked on the network applet again, and it brought up the list of all wireless networks in my area. I selected my network and the applet changed into the trying to connect icon. After that it just sat there.  Any applications I already had open continued working normally, but I was unable to open any new ones, or bring up any system dialogs (like the normal gnome save file dialog in gedit).

I dumped the messages log to another file after I had tried to reconnect, but it doesn't look like it added anything to it apart from the entries right around the disconnect.

Any ideas?

---

### Post by thomasaaron on 2007-12-10
Zxaos (not sure how to pronounce that... :lolflag:),

Are you using a PanV3. While at first glance your problem sounds like it might be a networking problem, you mentioned applications freezing. 

What computer do you have? Is it a PanV3 too?
Also, is hibernate/resume a part of your equation?


If your answers to the above are Yes and No respectively, though, you might be experiencing a bug similar to the one we have here at the System 76 office. We've never quite been able to nail it down, but the symptoms are definitely similar and it seems to be related to the collage of routers and wireless traffic that fill our office building. We know it is related to this building becuase it doesn't happen anywhere else. Does your problem occur elsewhere?

---

### Post by Zxaos on 2007-12-11
Yes, it's a PanV3, and no I haven't used hibernate or suspend before this occurs. (There are seperate suspend/hibernate issues currently, though).

There *are* a large number of wireless networks in the area where I normally run the machine. Still, having said that I had no problems before Gutsy was installed.

I can try it in an area with fewer APs but more clients, but that's probably going to have to wait until the new year (only one reachable access point on most of campus). I haven't had the problem there so far, but it's an intermittant problem anyway, so maybe I just haven't been connected for the long period required for it to happen.

Also, it's not so much applications freezing as gnome.  Any *open* applications continue to work just fine, but you can't shutdown, restart, launch new applications, or use the gnome file-chooser (for saving files, for example).  Even if you switch to a console and try to shutdown from there, nothing happens. It's very odd.

---

### Post by thomasaaron on 2007-12-11
Just FYI, if you get into that situation and need to do a hard shut-down. Don't do it with the power switch.

Hold down that Alt and SysRq keys and, while holding them down, press these keys: RSEIUB

Think:
R-aising
S-kinny
E-lephants
I-s
U-tterly
B-oring

Less chance of hosing your fs that way.

---

### Post by Zxaos on 2007-12-11
SysRq (Fn+Del) brings up the printscreen prompt on my system, bizarrely.
Edit: Nevermind. Apparently that's normal.

---

### Post by thomasaaron on 2007-12-12
Try it without pressing the function key.

Just Alt+SysReq (+ the keys I mentioned above one at a time)

-----------------------------------

EDIT: Actually, I just tried that, and it didn't work. Tried several other combinations too. No dice.
So much for that idea on the Pangolin.

---

### Post by Zxaos on 2007-12-13
It worked for me!  You just have to ignore the multitude of screenshot dialogs that start popping up.  I did Alt + Fn + SysRq (So Del on the panv3) + (in sequence) RSEIUB

It worked just fine.

Now, if only the system would stop needing this procedure...

---

### Post by octathlon on 2007-12-13
I have never heard of anything like this. Is it a generic Linux thing?  
Alt+Fn+SysRq+RSEIUB !? I'm not sure I can even get my fingers to do such a thing!

---

### Post by Zxaos on 2007-12-14
It's built into many kernels in various linuxes.

Fn is really only necessary because otherwise it's the delete key on the pavn3, not the SysRq key.

R - change keyboard from raw mode
s - sync filesystem to write outstanding buffers
e - send term to all processes
i - send kill to all processes
u - unmount all file systems and mount in read only
b - reboot

It's a shortened version of the sequence you'd normally do automatically in a regular shutdown.

---

### Post by aarondrich on 2007-12-14
I just started having similiar issues with my panv3.  I experience very similiar behavior, after a reboot the wireless works for some undetermined amount of time, and then it disconnects and I loose my connection.  If I reboot it will connect again, but as the machine is going down it hangs after the ubuntu splash screen with the reverse status bar and spits out a 

Network Manager Error: nm_mananger ...... Received a Signal Type 15

When this occurs I have to do a hard reboot, I'll try your little shortcut mentioned above but don't think that will help.

When I get home I can put up the exact text.  I just got my laptop and absolutely love it, however wireless is a pretty integral piece that must work.  Hopefully you all can help.  I did notice that the System76 repo was just updated right before I started having my issues.  Do I need to reinstall the System76 software every time I get an update or does that occur instantly?  Just a thought.

Thanks for the help ahead of time.

---

### Post by thomasaaron on 2007-12-14
What kind of wireless configuration are you guys using? DHCP? Static IP? Other?

We've got a bunch of these babies out there, and I'm not hearing anything about this problem other than this thread. So, I'm wondering if there is some common ground here somewhere?

Are we all running 32-bit Ubuntu?
Does it do it anywhere?
Also, the full text of the error would be helpful.

---

### Post by Zxaos on 2007-12-14
The only specific error messages are what I posted earlier. The network I'm using is with DHCP, although I have my router set up to always assign the same IP address to this machine with DHCP.

I am running 32 bit Ubuntu.

Like I mentioned, I've only observed it happening at one location, however that's likely because it seems to have to be on for quite some time before it occurs usually. The other network that I use has gaps between its APs so I'm constantly disconnecting and reconnecting as I move around.

---

### Post by aarondrich on 2007-12-14
I believe I'm running 32-bit Ubuntu, it's the version of Gusty that came with the pangolin value 3.  Also, I have a DLINK router, using DHCP, no WEB encription, but I don't broadcast my wireless network name.

Also, I have had no issues until this last week, and as I mentioned before it seemed to start after I updated the system 76 software from the repository.  When that is updated do I need to execute the software from the admin menu again?

Thanks

---

### Post by thomasaaron on 2007-12-14
I'm sure it has nothing to do with the System 76 driver -- since the System 76 driver has nothing to do with the Wirless on any of our computers. That is supported out of the box by Ubuntu.

Yes, once you've downloaded the driver update, you need to run it again. Just run the install tab/button.

---

### Post by octathlon on 2007-12-14
@Zxaos: Thanks for that info about the "rseiub" actions :)

@Tom, et. al.: I finally got sick of network manager and removed it and installed Wicd instead.  That solved the problems I was having.  Now, the interference or whatever it is that causes my signal strength to drop to 0% every so often still happens, but wicd doesn't freak out like nm would.  Nm would say "disconnected" and go into its endless attempt to reconnect.  Wicd just calmly keeps trying to reconnect until the signal strength comes back, then goes on and continues with what it was doing, never interfering with anything else on the system.  

Also, Wicd doesn't make you enter your keyring password every time you log on like nm did.  Personally I think nm's problems are related to its using the keyring manager, and not being able to get the password from it again when it tries to reconnect.

edit: BTW, I had to add the command "/opt/wicd/tray.py" to my Session preferences so wicd would start automatically.

edit again:  OK I just made a liar out of myself.  Just as I had started up Open Office, the wireless signal strength dropped to zero, and although the whole system didn't freeze (I could switch between windows), Open office just sat there at the splash screen, not doing anything for about 30 seconds, then suddenly it continued and started up.  I looked back at the icon and the connection was back.  So I guess the same thing is happening to me after all!

---

### Post by aarondrich on 2007-12-15
Thanks for the help.  My problem has stopped for now, I did update the System76 Driver, but it seems that shouldn't matter.  I also rebooted the machine after it came up, but before I lost my network connection to the wireless router and it shut down fine after that.  I don't know if my hardware was in a wacky state or what.

---

### Post by Tomone on 2007-12-19
It looks like I have the exact same problem as Zxaos. I think it only happens at one location, but it's hard to tell since I'm never at any other location long enough to give the problem a fair chance of happening. I've spent the last few days trying to figure out the cause, mostly just seeing if closing all unnecessary applications would solve it, but none of that seems to affect it.
One big change though, is that I've started using Wicd for network management, which seems to stop the freezing. My network connection will still cut out (when I try to reconnect, Wicd gets stuck on "Obtaining IP address...") and I won't be able to reconnect until rebooting, but I will be able to open and close programs with no problem.

Update: I just woke up and, to my surprise, found my network still connected. My computer's been up for over 17.5 hours so I think (cross your fingers) that I've figured out the problem. The only thing I've changed from the last time the network quit was Bluetooth. I just turned off the "Bluetooth device management" in the "Services settings." I'm optimistic, about 92% sure that this is the problem, so hopefully I won't have to update this again saying that my network just quit again.

---

### Post by Zxaos on 2007-12-20
Well I'm at a different location for the holidays and I should have the occasion to leave the machine connected here for quite a while. It's a DHCP WPA-TKIP network with not much else in the way of networks around.  So if it happens, we've changed just about every variable there. :)

---

### Post by Tomone on 2007-12-21
Okay, turns out I was wrong about both things. My connection dropped at about 30 hours. Also, once I tried to reconnect, I couldn't open any other programs or shutdown the normal way. So now I guess I'm back to having no ideas.

---

### Post by thomasaaron on 2007-12-21
TomOne:

Do you have the logs from when it dropped the connection?
/var/log/messages

---

### Post by Tomone on 2007-12-23
I had a hard time remembering when I restarted the computer because of the problem and when I restarted for other reasons, so I had to wait for it to happen again to get the messages. Also, I know someone mentioned that the problem might have to do with a lot of interfering wireless networks, but where I am now (where the problem is happening), there are only two other wireless networks I can see. And those two networks are usually too weak for me to see at all.
Log (I know it was good at midnight, but sometime between then and 8:30 the connection was lost):
Dec 22 23:59:07 pangolin -- MARK --
Dec 23 00:08:22 pangolin syslogd 1.4.1#21ubuntu3: restart.
...
Dec 23 05:41:50 pangolin kernel: [30183.988000]          res 50/00:08:a7:32:f1/00:00:0e:00:00/40 Emask 0x2 (HSM violation)
Dec 23 05:41:50 pangolin last message repeated 13 times
Dec 23 05:41:50 pangolin kernel: [30184.300000] ata1: soft resetting port
Dec 23 05:41:51 pangolin kernel: [30184.476000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 05:41:51 pangolin kernel: [30184.476000] ata1.00: configured for UDMA/100
Dec 23 05:41:51 pangolin kernel: [30184.476000] ata1: EH complete
Dec 23 05:41:51 pangolin kernel: [30184.476000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 23 05:41:51 pangolin kernel: [30184.476000] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 05:41:51 pangolin kernel: [30184.476000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
Dec 23 07:00:06 pangolin kernel: [34879.988000]          res 50/00:08:7f:e6:6f/00:00:04:00:00/40 Emask 0x2 (HSM violation)
Dec 23 07:00:06 pangolin last message repeated 13 times
Dec 23 07:00:06 pangolin kernel: [34880.300000] ata1: soft resetting port
Dec 23 07:00:07 pangolin kernel: [34880.476000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 07:00:07 pangolin kernel: [34880.476000] ata1.00: configured for UDMA/100
Dec 23 07:00:07 pangolin kernel: [34880.476000] ata1: EH complete
Dec 23 07:00:07 pangolin kernel: [34880.476000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 23 07:00:07 pangolin kernel: [34880.476000] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 07:00:07 pangolin kernel: [34880.476000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
Dec 23 07:42:53 pangolin kernel: [37446.988000]          res 50/00:08:df:32:f1/00:00:0e:00:00/40 Emask 0x2 (HSM violation)
Dec 23 07:42:53 pangolin last message repeated 13 times
Dec 23 07:42:53 pangolin kernel: [37447.328000] ata1: soft resetting port
Dec 23 07:42:54 pangolin kernel: [37447.500000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 07:42:54 pangolin kernel: [37447.500000] ata1.00: configured for UDMA/100
Dec 23 07:42:54 pangolin kernel: [37447.500000] ata1: EH complete
Dec 23 07:42:54 pangolin kernel: [37447.500000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 23 07:42:54 pangolin kernel: [37447.500000] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 07:42:54 pangolin kernel: [37447.500000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
Dec 23 08:32:36 pangolin kernel: [40429.968000] nfsd: last server has exited
Dec 23 08:32:36 pangolin kernel: [40429.968000] nfsd: unexporting all filesystems
Dec 23 08:32:36 pangolin kernel: [40429.968000] RPC: failed to contact local rpcbind server (errno 5).
Dec 23 08:32:36 pangolin exiting on signal 15

---

### Post by thomasaaron on 2007-12-24
Tomone,

Are you using the PanV3 too? Your logs look more like a Gazelle or old Darter having a firmware problem. Please confirm your computer model, and we'll take it from there. (Actually, if you have a Gazelle Value or White Darter, just email me for the fix/directions.)

Best,
Tom

---

### Post by Tomone on 2007-12-25
Tom, 
I am using the panv3. Although, I switched back to the gnome wireless manager and after 30 hours haven't had a problem (yet).

Update:
After it going strong for over 60 hours, I thought the problem might be gone. So I started up kTorrent and left my computer for a few hours. I came back and the network connection was lost and I couldn't do anything on the computer. Here's the log message from that one (it's a little different from the other messages):

Dec 26 14:06:32 pangolin kernel: [244682.900000]          res 50/00:08:7f:45:20/00:00:04:00:00/40 Emask 0x2 (HSM violation)
Dec 26 14:06:32 pangolin last message repeated 3 times
Dec 26 14:06:32 pangolin kernel: [244683.212000] ata3: soft resetting port
Dec 26 14:06:32 pangolin kernel: [244683.384000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 26 14:06:32 pangolin kernel: [244683.384000] ata3.00: configured for UDMA/100
Dec 26 14:06:32 pangolin kernel: [244683.384000] ata3: EH complete
Dec 26 14:06:32 pangolin kernel: [244683.384000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 26 14:06:32 pangolin kernel: [244683.384000] sd 2:0:0:0: [sda] Write Protect is off
Dec 26 14:06:32 pangolin kernel: [244683.384000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 26 14:28:57 pangolin -- MARK --
Dec 26 14:48:57 pangolin -- MARK --
Dec 26 14:52:21 pangolin kernel: [247431.548000]          res 50/00:08:c7:14:f0/00:00:0e:00:00/40 Emask 0x2 (HSM violation)
Dec 26 14:52:21 pangolin last message repeated 6 times
Dec 26 14:52:21 pangolin kernel: [247431.864000] ata3: soft resetting port
Dec 26 14:52:21 pangolin kernel: [247432.036000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 26 14:52:21 pangolin kernel: [247432.036000] ata3.00: configured for UDMA/100
Dec 26 14:52:21 pangolin kernel: [247432.036000] ata3: EH complete
Dec 26 14:52:21 pangolin kernel: [247432.036000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 26 14:52:21 pangolin kernel: [247432.036000] sd 2:0:0:0: [sda] Write Protect is off
Dec 26 14:52:21 pangolin kernel: [247432.036000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 26 14:56:40 pangolin dhcdbd:  dhclient 11798 down (9) but si_code == 0 and releasing==0 !
Dec 26 14:56:42 pangolin kernel: [247692.896000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Update #2:
Okay. It just happened again, but I think I learned something. It looks like all that stuff about "HSM violation" and "soft resetting port" happens all the time. The only message I have this time when the connection was lost is:
Dec 31 10:44:23 pangolin kernel: [62416.892000] ADDRCONF(NETDEV_UP): eth1: link is not ready

That looks like the same message that Zxaos has, but the difference between mine and his and the sys76 office problem is that there aren't a lot of wireless networks around here. In fact, I usually can't see any other networks besides the one that's in my house.

---

