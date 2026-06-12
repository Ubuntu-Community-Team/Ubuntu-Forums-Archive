---
title: "What's the real deal with wireless on Ubuntu?"
date: 2007-09-12
forum: The Cafe
---

### Post by aysiu on 2007-09-12
I've heard a lot of people saying wireless support on Ubuntu or Linux stinks. What have been your experiences?

---

### Post by regomodo on 2007-09-12
out of 4 chipsets used only 1 worked out of the box.

2 Ralinks didn't work and one of those requires 3rd party drivers (i go for serialmonkey, not ralink) to with it. An Atheros works perfectly although its efficiency  is giving me concern. The other is a prism chipset

Also, i'm all for replacing network-manager-gnome with WICD

---

### Post by 23meg on 2007-09-12
I've always had supported hardware, which unsurprisingly worked without configuration and caused no problems.

---

### Post by PmDematagoda on 2007-09-12
I have a Compaq with Intel wireless and have no problems in setting it up.:)

---

### Post by Phil Airtime on 2007-09-12
I tend to use a wired network, but on plugging a USB dongle labelled "Safecom" that was lying around into the computer, it appeared straight away in the network manager at the top-right of the screen.

---

### Post by dynamicv on 2007-09-12
I use the Broadcom 4306 chipset.  After a lot of trial and error I got it working with both WPA2 and WEP networks, but the range is nowhere near as good as when using the same hardware under OSX.  It also frequently drops for no apparent reason, leading to temporary routing errors, although when it does this it will suddenly pop back into play a minute or two later.  Under OSX the same connection will be completely stable.

Of course, I know the project team are doing their best, so don't want to be too critical since their work is appreciated.  However, there's a lot of work on the reliability to go before it's up to the standard it needs to be.

---

### Post by SuperDuck on 2007-09-12
I tried making it more difficult than it needed to be.  I was entering ip addresses, DHCP, so on and so forth for a few hours just trying to get the stupid thing to work.

Out of a lack of anything better to try, I clicked the "Roaming" button.

A few seconds later: "You are connected to wireless nework <blank>"  Doh!

---

### Post by FuturePilot on 2007-09-12
It worked out of the box. The Restricted Driver Manager had the driver for it.

---

### Post by mostwanted on 2007-09-12
Wifi on Linux lacks support for many typical school and workplace network authentication protocols. It's fine for home use here, but that's it.

---

### Post by asmoore82 on 2007-09-12
it worked out of the box, but changing locations does not...

nothing a little sudo vi /etc/networking/interfaces and
sudo /etc/init.d/networking {start,stop,restart} can't fix

---

### Post by aaaantoine on 2007-09-12
Had to use fwcutter for my Broadcom adapter, but there were no complications in doing this, and it has worked fine since.

---

### Post by macogw on 2007-09-12
mine worked out of the box because i have an ipw3945 (and i use wpa encryption at home).  i had to use ndiswrapper on 1 friend's computer and just install bcm43xx-fwcutter on my mom's and another friend's

---

### Post by logos34 on 2007-09-12
Feisty worked out of the box with my USB wireless-G adapter

Edgy 6.10 gave me some trouble but I eventually found a workaround.  If I'd been a noob I wouldn't have had a clue.  There would have ended my brief affair with Ubuntu linux.

---

### Post by epimer on 2007-09-12
I've had no problems at all (ipw3945) in Ubuntu. Arch is giving me a very odd, small problem, but not Ubuntu.

---

### Post by Sunflower1970 on 2007-09-12
Out of the box. But, I worked to find a router, and wireless cards that would work with no hassle.

---

### Post by hessiess on 2007-09-12
have this pci wireless card

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 

it will not work, followed alot of guides, ndiswrapper etc

---

### Post by forrestcupp on 2007-09-12
It's just like printers.  As long as you use one certain brand (atheros chipset), it will work without trouble.  If you happen to have any other kind, it will be a pain.

---

### Post by stalker145 on 2007-09-12
I originally had only an Atheros-based laptop and a RaLink-based laptop. Since then I've bought another Atheros-based laptop. All mini-PCI G.

The Atheros chips worked OOTB with WPA and absolutely no configuration needed. I could roam to any open wireless and it was simple to enter an access key to a secure spot as needed.

The RaLink is another story. I followed many of the tutorials for hours on end, banging my head against the floor (see sig) and came to the conclusion that the card (or the mini-PCI slot) was bad. Just for fun, I put in my Win2K HDD and, lo and behold, the card worked perfectly... We couldn't have that, so I dug up a Linksys USB G card. Many tutorials and a couple of hours later it was running... with WEP only. Doh! I should have read the specs.

Needless to say, I went to my local computer store and bought an open box Atheros card ($16US), plugged it in, and it worked straightaway. Now my network consists of one hardwired desktop and three Atheros-based wireless laptops.

The lesson of my tale is to always research the gear you intend to purchase.

---

### Post by eentonig on 2007-09-12
Intel and Cisco wireless cards. Worked right out of the box.

Except some authentication and security parameters.

---

### Post by crimesaucer on 2007-09-12
I recently tried to use my wireless for the first time, and it was difficult. I have a BCM4318 and I used this guide: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)


Plus I used the wifi-radar app because I wasn't sure on how to configure the Network Settings Manager.

 
I had problems with wifi-radar the first few times I tried to use it, then I figured it out, and I still had problems with wifi-radar not being able to detect and connect to the wireless networks that were available on Windows Xp. And it seemed slower and seemed to drop the connection a lot when it would finally connect...then it would have difficulty reconnecting and detecting the different wireless streams available if it disconnected.


I also tried to just use the Network Settings Manager and it was a bit of a hassle connecting it to random coffee shop ip addresses that I didn't know. Maybe I was just too used to the ease of the Windows Xp wireless app. 


So, I have done a little research and I have found the wireless app called Wicd, and it seems like it might be better than wifi-radar...but I won't know until I go to a coffee shop again and give it a try.

---

### Post by dca on 2007-09-12
I have the new Atheros in my Acer laptop...  Not quite a mini-PCI card, something else.  I just used ndiswrapper and the Vista driver(s) from Acer's PanAm website...

---

### Post by lisati on 2007-09-12
Wireless worked pretty much straight away out of the box, the only "tweak" I've done is to prevent the keyring manager asking for the password at logon.

Occasionally it doesn't connect, mostly after changing to a different user - no big deal as clicking on the configuration icon & then the ESSID seems to get the connection going again.

---

### Post by rolnics on 2007-09-12
I have a Netgear wn311b so had to use ndiswrapper to get it working along with the drivers from XP. I found this pretty difficult, but remember I've only been using Ubuntu 5 months now!

---

### Post by Billy_McBong on 2007-09-12
[COLOR="Blue"]my router is right next to my computer so i don't use wireless[/COLOR]

---

### Post by Kingsley on 2007-09-12
My Intel 3945 wireless card worked out of the box with Ubuntu. 

A couple of months ago I tried with no success to get wireless on Fedora 7. I tried tutorials that dealt with ndiswrapper and changes to the kernel but none worked. I think the problem lied with Fedora 7's 2.6.22 kernel.

---

### Post by aysiu on 2007-09-13
So it seems as if about 50% of people still around (those who haven't given up completely) have either automatically working or effortless wireless.

That's encouraging, but it also shows we have a long way to go...

---

### Post by LowSky on 2007-09-13
mine is a funny story...

when I first installed ubuntu, my wireless usb didnt work, then i upgraded the kernel and now it does

---

### Post by saxuntu on 2007-09-13
For my HP laptop with Intel wireless it worked out of the box. For the Buffalo wireless i have in my Desktop i have yet to figure out anything.

---

### Post by PurposeOfReason on 2007-09-13
For my laptop, it just worked. On my parents computer with a netgear WG121, not so much.

---

### Post by nonewmsgs on 2007-09-13
my wireless cards (3 laptops and one desktop) would not work in linux.  it was a big headache.  there were multiple versions of the same card that were radically different (with a choice finger towards d-link).  they apparantly did not contain firmware and after about 30 hours i gave up and replaced them all with netgear atheros carsd and those worked out of the box.

---

### Post by PartisanEntity on 2007-09-13
I chose 'other':

I guess it depends on your hardware, I started off my Ubuntu wireless experience with a broadcom card. I nearly gave up on Linux and Ubuntu because of this, it took me at least a week of trying out all kinds of tutorials and reinstallations to finally get it working.

Later I decided to make life easier for myself and so I bought an intel wireless card and replaced the broadcom, now it works right out of the box :)

---

### Post by psiu on 2007-09-14
The laptop with 2 different Cardbus cards has been troublesome....has to be Ndiswrapper and Wicd to get it to work, just connecting to a standard wireless network with WPA2.

Just upgraded the Wicd version last night, hoping that it would help with start up times (there is about a 30 second delay during boot with the network process), instead it led to about an hour of tinkering and then uninstalling and reinstalling.

Have a USB wireless widget also, it works fine on the laptop with Wicd installed already, and on a desktop build it works fine using Wicd (but not the horribly useless default Network Mgr).

So I picked the middle poll option.

---

