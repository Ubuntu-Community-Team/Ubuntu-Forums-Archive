---
title: "Dedicated firewall machine"
date: 2009-03-26
forum: Security
---

### Post by RFXCasey on 2009-03-26
Hey all,

I want to turn one of my old machines into a dedicated firewall/server. I'm having a little confusion as to which software would suit my needs best. Here is what I would like to get out of it. Firewall with stateful packet inspection, webfiltering of bad sites, print server, remotely managable, good activity reporting, a nice easy to use interface or gui. I also need it to all run off of a USB flashdrive as I will have no hardrive cdrom or floppy installed for power conservation purposes. 

The few I have looked at are Devil Linux, IPCop, Smoothwall, and Uncomplicated firewall but I am not sure if any or all of these will serve all of my needs. :confused:

---

### Post by Dngrsone on 2009-03-26
I use Smoothwall Express myself, though you might take a look at [ClarkConnect](http://www.clarkconnect.com/info/), as it's already set up to act as a print/file server, as I recall.

The Smoothwall forums have a few threads on using CF cards in place of a hard drive to run your firewall, BTW.

---

### Post by RFXCasey on 2009-03-26
So if I understand correctly both smoothwall and clarkconnect will do webfiltering natively or do you have to install some sort of module or 3rd party software to get that working?

---

### Post by Dngrsone on 2009-03-26
For Smoothwall you need to add DansGuardian, there's an easy-to-install mod for that you can get from the Smoothwall forums.

ClarkConnect has built-in filtering, don't know what engine it uses nor how good/bad it is.

I can tell you this-- the Smoothwall experts all recommend ClarkConnect to people who start asking questions about adding stuff to their Smoothies-- those guys are firewall purists who think that it should be a firewall and nothing else.

---

### Post by RFXCasey on 2009-03-26
Thank you so much for the information. Have you ever considered or heard anything about Devil Linux?

---

### Post by Dngrsone on 2009-03-26
Nothing.  I'm going to look it up right now, though.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by Dngrsone on 2009-03-26
Well, the idea is good-- no writeable storage means much fewer exploits to be used should someone get into the machine.

Personally, I'm not all that thrilled about using a floppy disc-- too unreliable for me.  I imagine making changes of any kind would be a pain, which means learning the system and getting it set up the way you want/like it might take more time and be very inconvenient.

But I like the minimalist take on it, and it should run well on a PII or PIII machine.

On a somewhat related note, hardware-wise: I like to wire my routers/switches right into the computer power supply, eliminating the bricks/wall warts and saving a little energy that way.  And since they are only really used when the firewall/DHCP server is on, when it is off, so are the routers.  It only works if the devices run on 5vdc or 12vdc.

---

### Post by Dr Small on 2009-03-27
> **RFXCasey said:**
> [...] webfiltering of bad sites, [...]

You'll need Squid and DansGuardian for that. The firewall doesn't do the filtering. I wrote a tutorial on how to do this (although, not exactly for the same situation) and you should be able to apply the same logic behind it, and get it setup.
[http://ubuntuforums.org/showthread.php?t=1078033](http://ubuntuforums.org/showthread.php?t=1078033)

Since the dedicated firewall will be what all traffic passes through, you install Squid, DansGuardian, and setup the Transproxy script to forward all OUTBOUND connections through the DansGuardian port. (This may be different though, if you're using a different firewall besides iptables, but it shouldn't be too difficult to figure out).

---

### Post by ktrnka on 2009-03-27
untangle or ebox might fit your needs.



[http://www.untangle.com/]("http://www.untangle.com/")

[http://ebox-platform.com/]("http://ebox-platform.com/")

---

### Post by lensman3 on 2009-03-27
I use Fedora Core 10.  

I have setup a forwarding sendmail, a local net dhcp, fetchmail for retrieving emails from my provider, a  very long iptables that also has the ability to forward ports to internal machines, a sftp server, a bind/named client that helps filter browser advertising.

At one time I setup two IP ranges /24 classes over just one wire and Ethernet card.

The only non-standard implementation I have now is the txqueuelen from ipconfig is set to 100 instead of 1000.  This has helped internal network response because the input/output Ethernet card queue is serviced by the interrupts more often than default.

My firewall script has close to 1000 lines.  Any Linux distribution will work just fine!

---

### Post by RFXCasey on 2009-03-28
Thanks guys I'll give it a shot. Will any Linux based OS work the same for setting up my firewall or are is there a real advantage to using something like Smoothwall? I imagine it is probably a little less complicated working with a distro designed specifically for firewalling.

---

### Post by Dngrsone on 2009-03-28
The advantage of a dedicated firewall OS is that the developers have tried to secure the software as much as possible against attack and exploitation.

Yes, just about any Linux is able to act as a firewall and filter, but having a secure OS is preferable over an accessible one.

---

