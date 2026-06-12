---
title: "Virtualbox, Exchange 2007/MAPI, and ZUNE"
date: 2009-06-11
forum: System76 Support
---

### Post by Futurian on 2009-06-11
I'm reluctant to post this, but I've searched a bunch of places, and found no definitive answers.

I want to avoid dual boot (Jaunty 64/XP Pro) on a Pangolin Performance if I can, but I need:

1.  Outlook connecting to Exchange Server 2007 via MAPI, with all functionality (calendar, etc.), 

2.  Full ZUNE functionality (synch, update, etc.) (for my kid).

Does anyone know if Virtualbox can do these things hosting XP Pro? If it can, I can install Virtualbox, and avoid dual boot.

Thanks!

---

### Post by thomasaaron on 2009-06-12
I've installed and used VirtualBox for cross-platform software testing. But never anything complicated.

My estimation is that it is very versatile. But I don't really have experience with the software you mentioned.

Let's see if some other 76ers have any insight on it.

---

### Post by bertmanphx on 2009-06-13
Hello,
I don't know anything about the sync function of a Zune.
I do use Virtualbox once in a while, when I wish to use AutoCad.  VB is a nice tool, and works well.  I keep an XP virtual machine, just for that purpose.

I'm quite sure you could run Outlook in a virtual machine just fine.  Although, I do think that the Evolution email client will now work with Exchange 2k7.

bertmanphx

---

### Post by Jozza The Wick on 2009-06-30
I haven't tried synching a Zune, but I have been able to sync my smartphone (Windows Mobile via ActiveSync) succesfully with my XP virtual machine. (I think it's actually quite impressive to watch!)

I would imagine that Outlook should be fine. It's certainly worth trying before you go with the dual boot option, since you can obviously use your Zune & MS Outlook while continuing to use your Linux apps. Plus the 'seamless' mode integrates the XP app windows into the Linux desktop pretty well!

Good luck with it!

---

### Post by Plecebo on 2009-06-30
I've used VB quite a bit to test different configuration and scenarios. It is great to do "what if" kind of testing, or for working out software setup tasks. Setup a base system, make a snapshot, change some configurations around... if it works make another snapshot, if not revert. Rinse, repeat. 
 
VirtualBox works great except for these scenarios IMHO: 
A) 3D applications. It is not really intended to run 3d game, look to other apps (like WINE) to do that
B) Things that need very specific access to your hardware. For example, a hardware raid scenario would probably be difficult to mimic in VB. 

That being said: 
1. I'm certain that VB will run Outlook and connect to exchange successfully. It shouldn't require specific hardware access (unless you have something like smart card authentication, in which case it may work... never hurts to try). 

2. The key that you are looking for in making the Zune sync is USB pass through support, which was added in one of the more recent releases of VB (not sure on version). Like anything new there are a few hiccups, but I know that this was key to getting things working with the iPhone & VB. 

Hope that was helpful.

---

### Post by Derath on 2009-06-30
I've used VB quite often, and it sounds like it would definitely suit your needs. There is one note: Make sure you get the Closed Source version rather than the Open Source Version. Last I heard, the OSE version did not enable USB pass through support, although that may have changed (or will soon). Using Outlook for Exchange only requires a net connection, you can use either the Bridged or NAT network setting for that, and as far as Zune is concerned, all you need is USB support for the device, easily done.

As a side note to the earlier post: VB has put in an OpenGL bridge to allow OpenGL to directly access the video card rather than using the virtual graphic driver. Word on the street is on the 3.0.2 beta version they are working on enabling DirectX capability for graphics (so you could run those games in VM rather than Wine), but this is still a work-in-progress beta version.

---

### Post by Jozza The Wick on 2009-06-30
Good point, Derath. Only closed-source supports USB pass-through. The feature has been implemented since at least v1.6 of VB. I v2.2.4 is the most recent stable version.

Thanks for the note on 3D support in v3.0! I'm gonna try that out!

---

### Post by ronaldprettyman on 2009-06-30
Virtualbox works great, I recommend using the official version, you can get the apt information off their website to add their repository to your system(/etc/apt/source.list). 

Note that when using the official version you have to recompile or download a new kernel module after each kernel update so I recommend using the official version. They just released 3.0 today. So I highly recommend adding the official repository to your source list. Or keeping the deb handy.

Your want to forward USB ports to the xp system and make sure to install the guest services for full support.
Zune and exchange work great from my experience with XP Pro sp3 in VirtualBox 3.

The new version of virtualbox is suppose to have some experimental directX support as well, but I haven't tested it yet.

---

### Post by Derath on 2009-06-30
NP Jozza, I am eagerly awaiting the actual release of v3, as it would resolve my wife's issue of not being able to play some games. although I may have to give her a 30-40G virtual drive for that one :) As soon as it's released I'll be trying some of the hidden object games that she likes. Blasted ActiveX and DirectX requirements... :mad:

---

### Post by ronaldprettyman on 2009-07-01
> **Derath said:**
> NP Jozza, I am eagerly awaiting the actual release of v3, as it would resolve my wife's issue of not being able to play some games. although I may have to give her a 30-40G virtual drive for that one :) As soon as it's released I'll be trying some of the hidden object games that she likes. Blasted ActiveX and DirectX requirements... :mad:

They Officially announced v3 on their face-book yesterday.
You have to manually install it, it won't upgrade 2.X to 3 automatically
if you have the offical repositories
```
sudo apt-get install virtualbox-3.0
``` 

then run 
```
sudo echo "deb http://download.virtualbox.org/virtualbox/debian jaunty non-free" >> /etc/apt/source.list
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get install virtualbox-3.0

```

Source: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by 4heid on 2009-07-16
outlook in vb wont connect, now no net connection

Postby 4heid » 16. Jul 2009, 00:55
I am running Ubuntu 9.02 with VB 3.0.2 with Vista.
I installed vista and outlook 2007 successfully. The first attempt showed a local and internet connection in vbox and I rebooted after installing outlook.
After attempting to setup my exchange in outlook, it would not connect to the server so I checked my net connection inside the box and it shows now local only.

In the settings in vbox I have the network connect attached as Host only adaptor.I tried NAT and the Bridge with Eth1 (the working net connection on my host), all other network options and that didnt work either.

With the Bridge, I get internet service when first booting but it always disappears after 30 secs thus I cant connect to OUtlook and finish setting up exchange.


Anyone have any thoughts to get the connection back to vbox and then what to do about outlook?

TIA,
Chris

---

### Post by Futurian on 2009-08-13
Outlook 2007 is connecting with Exchange 2007 via MAPI for me; everything seems to work. I'm running XP pro in VB 3.0.4, and have made no changes to the default settings for anything related to networking. I installed VB 3 via Synaptic after using Synaptic to unistall VB 2.

I haven't had a chance to test syncing a Zune, and probably won't get that chance in the near future.

Sorry, I don't know what is going on with others' networking problems.

---

### Post by jdmelton on 2009-08-14
4heid,

Outlook will work properly once the networking issue is solved. Zune, I do not know.

My use of networking is mainly through the wireless on my laptop. I travel a lot, so much of the time I am attaching to some hotel or coffee shop WiFi. I use network manager on the laptop.

I do not know if you have looked at the help files. There is some good information there. In regards to networking, try Help -> Contents -> Sun xVM VirtualBox -> Virtual networking.

In my case, I tried to get my wireless working directly under VirtualBox (Windows XP Professional Service Pack 2 32 bit). That did not work so I tried to get my Ethernet card to work directly also. That did not work, either. Then I read sections 6.1 and 6.4 in the help, and changed to the PCnet-FAST III adapter type and NAT as the attached to type. I left the MAC address alone (my laptop wireless was active at the time). That did not work either! Then I went back and checked the Cable Connected box. After this, the networking worked properly.

On the Windows side, I use obtain an IP address automatically and obtain DNS server address automatically for the Internet Protocol. The adapter is labeled AMD PCNET Family PCI Adapter which became available after I made the selection in the VirtualBox Settings for the virtual machine.

I wrote a post for VirtualBox 3.0.4, it may be of some help. I use Hardy 8.04.3 AMD64. [http://ubuntuforums.org/showthread.php?t=1231646](http://ubuntuforums.org/showthread.php?t=1231646)

---

### Post by HotShotDJ on 2009-08-14
> **bertmanphx said:**
> Although, I do think that the Evolution email client will now work with Exchange 2k7.Yes.  Evolution (version 2.26.1 with Evolution Exchange Connector version 2.26.0)  email works flawlessly with Exchange 2k7 and OWA.  But the server must have OWA enabled for this to work. I have not tried the MAPI plug-in. In my case, if I am connected to the server from within my university's network, everything works, including GAL dependent functions such as shared mail boxes, shared calendars, shared contact lists, etc.  However, the firewall prevents connection to the GAL from outside the network and breaks shared mailboxes, calendars, etc. when off-campus.  If you can VPN into the network, GAL dependent functionality should be restored (I can't test this, because my university inexplicably uses a proprietary VPN and does not allow Linux clients to connect, even though a Linux client is available).

My normal, day-to-day needs (calendar, contact lists, email, out-of-office settings, etc.) are still fully functional through Evolution when off-campus.  When I need the additional GAL dependent functionality, VirtualBox 3.0.* with Outlook works well.

---

### Post by Futurian on 2009-08-14
HotShotDJ,

Can  you say what values you entering in setting up Evolution to work with OWA? I use OWA via Firefox, but can't get it working in Evolution. Neither can one of my friends,

Thanks,

Futurian

---

### Post by HotShotDJ on 2009-08-14
> **Futurian said:**
> Can  you say what values you entering in setting up Evolution to work with OWA? I use OWA via Firefox, but can't get it working in Evolution. Neither can one of my friendsIt took some experimenting for me, as well.  Here is what got mine working:

Server Type: Microsoft Exchange
Username: domain\username
OWA URL: [https://webmail.yourschool.edu](https://webmail.yourschool.edu)
Specify the mailbox name: checked
Mailbox: username

My university has separate domains for Faculty/Staff and Students, so we need to specify the domain as part of the username field.  In my case, it is "facstaff\username" -- a corporation might have different domains set for different departments, for example, Accounting, Sales, Administration.  I know I have to do the same thing when I enter my username in Outlook, so my guess is that if you don't need a domain name when you use Outlook, you won't need it in Evolution.

The OWA URL server is the same URL that I enter into Firefox to get to the web interface (without all the /exchg/fac/login that gets tagged on after Firefox connects).  I've seen some that look something like "https://webmail.yourcorp.com/exchange" -- in any case, it should be the same as the OWA URL that you enter into Outlook.  And you do need the "https://" or "http://" preface.  If you leave it off, nothing will work.

You can probably leave the "Specify the mailbox name" and "Mailbox" fields blank.  When I clicked the "Authenticate" button, they were filled in automatically.  The same with "Authentication Type" -- it was set by the server after I clicked "Authenticate."

On the Receiving Options tab, I set it to check for new messages every 1 minute.  Important -- leave the "Global Catalog server name" field blank for now.  It is usually a different server than the OWA, and, from my searching and reading, it usually does not work from outside the corporate network.  In my case, the server name is the same as the root domain of my university (myuniversity.com) and works perfectly from within the network, but it crashes Evolution when I try it from outside the network.  Apparently, the GAL is handled differently in Evolution then it is in MS Outlook, since Outlook does not have any issue with the GAL when I'm off campus.  Hopefully, the developers of the exchange and/or MAPI plugins will work out the magic to make this work in the future.

Once you get connected, you will want to make some changes to the Defaults tab so that your Drafts Folder and Sent Messages Folder are set to you exchange account rather than local folders.  I'm pretty sure everything else is self explanatory.

I hope this helps you out.

---

### Post by Futurian on 2009-08-14
Thanks, HotShotDJ!
I tried some different combinations, based on your report, but I still get a message that Evolution can't connect to the server. I wonder if something could have been  done on the  server end  to not allow applications other than browsers to connect.

Thanks again. I really do appreciate your willingness to take time to  help.

---

