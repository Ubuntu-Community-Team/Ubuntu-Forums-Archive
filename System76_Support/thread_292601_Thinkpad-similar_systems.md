---
title: "Thinkpad-similar systems?"
date: 2006-11-04
forum: System76 Support
---

### Post by tonyyarusso on 2006-11-04
I currently have an IBM/Lenovo Thinkpad T43 laptop, and I really like it.  However, now that the line is Lenovo rather than IBM, I'm not sure where things are going with them, and so would consider something like sytem76 for my next computer.  I was wondering if some people could tell me what  system76 models are most like the Thinkpad line.  The things I like about the Thinkpad that may be relevant for differentiating are size/portability, the keyboard layout, business/professional look (black and simple is good).  I like my computers to "feel like a machine, rather than a toy", if you know what I mean.  Any thoughts?

---

### Post by tonyyarusso on 2006-11-04
Oh, also, I like that there's the dual trackpoint/touchpad "UltraNav" system, although it doesn't look like any of the system76 machines offer a trackpoint as well..yet.

---

### Post by BlaineM on 2006-12-04
I have a t30 that I love... fast and sturdy as a titanium skyscraper... anyway, I wont be getting rid of it anytime soon.  I think that I will keep it at least for another 2 or 3 years.  Although I thought about getting a black Macbook a while back.

I love in a laptop the small size... 12 inch powerbook size.  I dont dig the huge screen laptops... or even the 15 inch "regular" sized ones for that matter.  I like the small ones, portable, fitting in my back pocket... not really.  Lightweight.  Strong processor that does not suck too much juice from the battery.  I like medium power video card, dedicated if at all possible.  But usually not possible in most laptops.

I like miniPCI wireless, even though I have a PCMCIA card.  DVD player.  I really dont care about cameras or any of that crap in a laptop...

The usual ports like usb and vga out.  I dont like the trackpoint device on the IBM laptops... useless in my opinion... so slow to use.  Mousepad is a must.  Backlit keys are cool, but not a must.  Thin laptops are great... apple all the way for that, and the core2duo is a great processor in any laptop.  great power.

anyway... my opinion about laptops.  they will never perform like a tower in my opinion.  my tower blows any laptop that I have ever used out of the water for performance.. even the macbookpro.  although that is a really great laptop.  unless in a year or so when the quad cores come out and...

Blaine

---

### Post by BroncoInCalifornia on 2006-12-07
At work I use a T42.  I think it is a great machine.  It is small, fairly light and fairly rugged.

For home use I just got a Pangolin.  This is a different sort of beast.  It is noticable larger than the Thinkpad.  But I love the screen on the Pangolin.  It is larger and seems brighter with a higher contrast ratio.  As I am over 50 and getting older so I really like having a big screen.  

I suspect the Gazelle series are closer in size to the Thinkpad. I think they are smaller and lighter.


By the way the delivery of the Pangolin was quick.  I received it before they said they would ship it.  It was shipped from Fremont CA.   They did a good job with the final assembly.  I am now setting it up the way I like it. My only complaint is that it does not yet automatically connect to our home wireless on startup.  But I will find ( or write ) a fix for this.

One thing that sold me on these Notebooks is the Common Building Blocks (CBB) program.  Many of the notebook parts are interchangeable with parts from other manufacturers.   This to me seems consistent with the spirit of open source.

---

### Post by josys36 on 2006-12-07
For now I am going to stay with my T60. I did like System/76, but they don't offer DVI connectors for their external monitors yet. And, only one model offers a port replicator, and to me it is not worth buying. At least when you buy one for the Thinkpad you can get DVI video. Folks may guff at this, but hey I bought an expensive monitor and I want the best connection for it.

The only issue I have had with my T60 is that the wireless stopped working on Edgy. For me this was not a huge issue as I did not use the wireless that often anyway. I always keep a 10 gig emergency windows partition anyway. 

Our whole company uses the IBM Thinkpad, and after a careful study of other companies, we have decided to stick with the Thinkpad. One of the main issues was support. IBM and Lenovo are huge. They will provide great support just as IBM has supported other products. Can you safely say the same for System/76? How much do we really know about System/76? 

Just food for thought, and my 2 cents.

Jason

---

### Post by BlaineM on 2006-12-09
> **BroncoInCalifornia said:**
> 
My only complaint is that it does not yet automatically connect to our home wireless on startup.  But I will find ( or write ) a fix for this.

Do you use any programs like Wifi-Radar?  I like this program... it stores the profiles and then allows you to choose which to use.  And when you boot up, chooses the profile for the wireless network that is present, and logs you on.  I use it everywhere that I go with the laptop... school, coffeeshops, my apartment...

---

### Post by BroncoInCalifornia on 2006-12-09
> **BlaineM said:**
> Do you use any programs like Wifi-Radar?  I like this program... it stores the profiles and then allows you to choose which to use.  And when you boot up, chooses the profile for the wireless network that is present, and logs you on.  I use it everywhere that I go with the laptop... school, coffeeshops, my apartment...

I finally have the wireless thing sorted out. I ended up with the NetworkManager applet.  I think it was what was originally installed.   The original toobar applet gave a message "No network devices have been found".

After trying some other things including WiFi Radar I ended up with the NeworkManager (again I think) -- with the same error message!  After searching the Internets I discovered I needed to comment out the lines from /etc/network/interfaces relating to eth1 -- the wifi interface. I also commented out the eth0.  Booting is now a lot faster because it is not trying to dhclient on an interface that is not communicating.

My final /etc/network/interfaces:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo

iface lo inet loopback

#iface eth0 inet dhcp

#iface eth1 inet dhcp
#wireless-txpower on
#wireless-essid RicePort
#wireless-key a8b0fc1b2b

#auto eth0

#auto eth1


If the Network Manager was installed ( I think it was), then these lines should have been commented out.  I think this was an error in the original configuration.

I love the Network manager.  If I click on the icon I get a display of all the networks around us with the relative signal strength. It is great!!!

-----------------------------------

I also installed Beryl.  This was painless.  I followed these intructions:
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX) 

I then added a menu item for /usr/bin/beryl-manager so I can turn it on.  I also had to enable window resizing using the Beryl setting manager GUI.

The Intel 950 graphics in the 945GM chip seems to have all the graphics power I need for this super eye candy.

---

### Post by crichell on 2006-12-11
Hi Broncolin - We install Network Manager by default and configure it to work with the network devices.  What has been happening with some customers is that they go to System > Administration > Networking to configure their network card which then wipes out network manager because it wrights to the /etc/network/interfaces file.  

I've been trying to come up with a good way to avoid the problem.  Maybe remove Networking from the Administration menu but that can cause a problem if a customer wants to use static addresses or more advanced setup.  Our quick start guide that comes along with the machines shows to connect using NetworkManager but I think most people put it aside and jump right in (I would).  Does anyone have any suggestions?

---

### Post by newlinux on 2006-12-11
anyway you can have a message pop up on the computer screen when it is first booted up explaining the issue? It could have an option to say "don't show me again" so that the user can get rid of the message...

---

### Post by crichell on 2006-12-11
that's not a bad idea - maybe a popup that's similar to the software update popup.  Have it display only on first boot.

---

### Post by BroncoInCalifornia on 2006-12-12
> **crichell said:**
> Hi Broncolin - We install Network Manager by default and configure it to work with the network devices.  What has been happening with some customers is that they go to System > Administration > Networking to configure their network card which then wipes out network manager because it wrights to the /etc/network/interfaces file.  

I've been trying to come up with a good way to avoid the problem.  Maybe remove Networking from the Administration menu but that can cause a problem if a customer wants to use static addresses or more advanced setup.  Our quick start guide that comes along with the machines shows to connect using NetworkManager but I think most people put it aside and jump right in (I would).  Does anyone have any suggestions?

Was was going to write to say that I thought the computer was mis-configured.  I am glad that you are shipping units with the proper configuration. I did not look at the quick start guide until after I fixed the problem.  

I also like the suggestion by newlinux. 

By the way, I really like the computer (Pangolin).  My daughter really likes it too. I have a hard time getting it away from her. She has started to use it to do her homework.  It did not take her long for her to figure out how to use Gaim for instant messaging.  I do not know how teenagers get any homework done between all those messages.

---

### Post by crichell on 2006-12-13
I'm glad to hear you and your daughter are enjoying the laptop.  --and all that great free software!

---

### Post by newlinux on 2006-12-13
I'm 6 months in to loving my laptop - My wife calls it my "baby."

---

