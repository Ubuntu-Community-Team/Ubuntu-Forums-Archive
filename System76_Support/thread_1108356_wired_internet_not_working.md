---
title: "wired internet not working"
date: 2009-03-27
forum: System76 Support
---

### Post by Brian_Newbie on 2009-03-27
I'm just now setting up my new computer from system 76. My wireless internet works perfectly but my wired internet is not working (eth0 is grayed out). 

When I connected to my home cable internet with my other acer computer, it showed my: IP address, submask, default route, primary DNS, secondary DNS and even my mac address when I right-clicked on the network icon. 

When I connect to the internet with my Pangolin Performance, It brings up only my mac address and nothing else. The "DHCP Client ID" box is blank.

What do I need from my cable provider to connect to the internet via a wired cable? 


Thanks

P.S how do I disable the auto-scrolling so I'm just using my mouse and not the palm of my hand. It's starting to drive me crazy.

---

### Post by thomasaaron on 2009-03-27
First, check this...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

---

### Post by Brian_Newbie on 2009-03-27
I tried this twice with no results. The only 2 entries that came up in the text editor were the 2: auto lo & iface lo inet loopback that I left untouched. 

When I clicked Save and rebooted my computer I connected automatically to the wireless network of the guy next door.

Is there anything else I can try?

---

### Post by thomasaaron on 2009-03-27
Whose your cable provider?

Are you connected like this: cable modem >> router >> laptop?

If so, try connecting directly to the modem.
Also, try re-setting your router.

It sounds like it is not seeing your ethernet at all. Make sure all cables are in tight, etc...

---

### Post by Brian_Newbie on 2009-03-27
I use Cogeco Cable in Ontario, Canada. On my acer I noticed that my IP address never changed. Whenever I go to Steve Gibson's grc.com shields up website on my acer I note that the account number and internet address are always the same and never vary. Maybe I do have a static IP address with Cogeco?

The "PC link" button on my cable modem (I don't use any external routers of any kind except for the cable modem itself) is the only one that is not lit up. 

I also use only the cable that came with my Pangolin and it fits snugly into my cable modem.

Am I forgetting something or should I call my cable company to manually enter their IP, submask, primary DNS etc info?

If this type of info/settings does not vary from computer to computer (both my acer and pangolin are running intrepid) then perhaps I can enter the same info into my Pangolin network manager manually?

---

### Post by thomasaaron on 2009-03-27
We don't ship an ethernet cable with the Pangolin. They do ship sometimes with a phone cord for a dial-up modem (which is only useful if you are running Windows on the computer) -- the dial-up modem is not supported in Linux.

Can you go from the ethernet port (the larger port) on the computer to the modem? An ethernet port looks like a phone port, but it is larger.

That doesn't sound like a cable modem. It sounds like a dial-up modem.

---

### Post by 3Miro on 2009-03-27
My IP address is dynamic, but varies very rarely. Unless you reboot your router you could have the same address for months.

Look at the settings of a machine that connects to your Internet and see how that happens. Is it some sort of protocol (poppe) or directly to DHCP. If you are using DHCP it might be that there is mac filtering installed and may have to manually let the system recognize your mac. Sometimes on local LAN networks (i.e. cable that goes right into the network card) I have seen it made so that you have to call the company every time you have a new computer (for the new mac).

---

### Post by Brian_Newbie on 2009-03-27
> **thomasaaron said:**
> We don't ship an ethernet cable with the Pangolin. They do ship sometimes with a phone cord for a dial-up modem (which is only useful if you are running Windows on the computer) -- the dial-up modem is not supported in Linux.

Can you go from the ethernet port (the larger port) on the computer to the modem? An ethernet port looks like a phone port, but it is larger.

That doesn't sound like a cable modem. It sounds like a dial-up modem.

Now I really feel dumb. I had the phone chord that came with the computer plugged into the right port. No wonder it didn't work!!

When I plugged the cable into the left port it connected me to my wired internet in about 3 seconds.

I promise to make sure my computer is hooked up correctly before posting questions to this forum. LOL.

Thanks very much

P.S. 

I LOVE my Pangolin. It's so much faster than my acer and even has a webcam that works under Linux.

Also: I received my laptop within 24 hours after your site said "shipping" from UPS. That is super-fast shipping!! Much faster than Canada Post. I look forward to enjoying my new Pangolin.

Brian

---

### Post by silvertuna on 2009-03-28
i'm at holiday inn with wired ethernet connection that my pangolin just acquired is not recognizing.  the eth0 checkbox is fuctional but connection is not successful.  no ip address shows up in ifconfig.  my etc/networkinterfaces shows 

auto lo
iface lo inet loopback

any ideas for what i should do or look for next?  i am in the lobby on wireless.

silvertuna 
intrepid 8.10

---

### Post by thomasaaron on 2009-03-28
If it doesn't just connect automatically, you may need to ask the hotel IT guys what is required. They may have some sort of protection in place.

---

### Post by silvertuna on 2009-03-30
Well i returned home and the ethernet wired connection worked fine on my network, just the way it should.  There wasnt anyone tech savvy at the Holiday Inn to look into it there, but employees there insisted all you had to do was plug in.  There must have been something odd there.  Dunno. 

silvertuna

---

