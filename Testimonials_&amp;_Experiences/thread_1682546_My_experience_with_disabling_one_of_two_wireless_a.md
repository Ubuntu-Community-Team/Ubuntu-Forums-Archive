---
title: "My experience with disabling one of two wireless adapters in Ubuntu"
date: 2011-02-06
forum: Testimonials &amp; Experiences
---

### Post by diablo75 on 2011-02-06
It all started with my uncle who was looking for a new computer.  He stumbled across the Zotac Mini MAG, which is a micro-ATX form factor PC that comes with no operating system pre-installed.  I installed Ubuntu on for him using the Live CD and an external drive he already happened to have.

I was happy to see that his wireless adapter was working immediately in the Live environment but quickly discovered that, for some strange reason, could barely communicate with his router.  I blame poor signal integrity or bad antenna design on the part of Zotac.  But it just so happened that he had a USB wireless adapter that worked immediately after plugging it in.

We now had a new computer with a fresh install of Ubuntu running on it that now had two wireless adapters attached to it.  Now here's the rub:

For some reason, Ubuntu wanted to auto-connect to the wireless network using the internal wireless adapter and not the external one.  Getting the external connected and the internal disconnected was a matter of clicking on the Network Management (nm-applet) icon at the top and clicking on the appropriate ESSID name under the USB adapters list, and clicking the same ESSID name (which was in bold, indicating an active connection) under the internal adapters list.  This was a nuisance and didn't help to make my uncle feel impressed by the otherwise very capable Ububnu Linux Operating System.

So I went out to find a solution, posting two threads on Ubuntu forums a few days apart from each other and in different forums.

The [one that got picked up]("http://ubuntuforums.org/showthread.php?t=1662244") boiled down to three solutions being proposed for me:

1.  Dismantle this brand new computer, attempt to locate the on-board wireless adapter and remove it (fortunately someone else let me know that the actual adapter is embedded in the motherboard and can't be removed, so this BRILLIANT suggestion had to be left out).

2.  Blacklist the appropriate modules related to the internal adapter so it would effectively be disabled.

3.  Create a script that would autorun and evoke the "iwdown" command in some way.

Based on popularity of the second solution I followed the instructions given by others (to use lsmod, lspci and lsusb to determine the module name and then edit the appropriate blacklist find in /etc/modprobe.d/).  This hit a couple bumps along the way, one of which was discovering that there were in fact multiple blacklist files here and not just any file would do and this took a little experimentation; you had to edit the correct file.  The other, much larger speedbump was this entire experience before it even began to play out.

At first my instinct was to check the System>Preferences>Network control panel, expecting to find some button or menu or check mark that would allow me to disable one specific network interface.  I was surprised to find that, for an operating system rooted in the existence of the Internet and computer networking in general, the Network settings panel doesn't provide the desired option I was looking for.

Not being very savy with the vast wealth of commands that are out there in the world of Linux, I decided it was time to hit the forums and ask the experts for their suggestions.  I was surprised to not hear a simple "Use this one command and it will disable the interface" or "Click on this, this and this to do the same thing and you're all done".  I didn't think I was trying to do anything complicated by todays standards, and I say that with the gravity of the fact that you could do exactly what I wanted to do in Windows 2000 using just a couple clicks in the control panel or one command in the CLI.  I hate to draw up this comparison, as I know everybody hates to see people complain that Linux would be better and more popular if only it did things the way they've been done in some other more-popular operating system... and for the most part it's not a fair argument to make against Linux.

However, this is the year 2011 and I personally don't understand much about this whole approach as far as blacklisting modules go.  What would one do if, say, they had two wireless adapters that both used the same chipset?  What then?

End rant.

---

### Post by coffeecat on 2011-02-06
You can, in fact, do exactly what you want using Network Manager in Maverick. It's ever so slightly more complex than a couple of clicks, but definitely doable. 

First, obtain the MAC code of the device you want to connect. Then right-click on the NM applet icon > Edit connection > Wireless tab > highlight your connnection > edit > Wireless tab > add the MAC address to the 'Device MAC address' field > click apply button. Then, when you start up, network manager will only use the wireless device with that MAC address.

I won't say any more for now because this forum is not for technical support. If you do need any more help, this will have to be continued in another subforum.

---

### Post by diablo75 on 2011-02-06
If you don't mind I'd like to copy and paste your tip into the thread that instructed me to blacklist the appropriate modules as it would seem that, from the beginning through the end, nobody really had a "good" idea about how to do what I was trying to do.  Your suggestion makes the most sense because:

1.  You can do it with the GUI
2.  It targets specific interfaces rather than their modules

As many views as the thread has gotten I can't help but think people will reference to it in the future trying to find "the best" solution.  Thanks.

---

### Post by coffeecat on 2011-02-06
Make sure you can get it to work first! :)

I simulated your situation with two USB devices, ending up with two connections in the wireless tab (I named them 'auto <SSID> <device>' so as not to get confused). I ticked the autoconnect box in one and not in the other and when I swapped devices around, NM behaved as I would expect - autoconnecting one but only connecting with the other if I clicked on my network in the drop-down. All of which is useful to know.

I take your point about people searching and referencing your thread. It's an inevitable fact that people comfortable with fiddling around in system configuration files will sometimes be unaware of ways of doing the same task in the GUI, and will post the fiddly system fix. Just look at the number of instructions to open the terminal in the Beginner's Section. But I'd better say no more about that; I've been guilty of that myself!

---

### Post by 3rdalbum on 2011-02-06
> **diablo75 said:**
> 

However, this is the year 2011 and I personally don't understand much about this whole approach as far as blacklisting modules go.  What would one do if, say, they had two wireless adapters that both used the same chipset?  What then?

Option 3: Create a startup script that turns off the adapter using the "iwconfig" command; I'd have to look up the man page for iwconfig but I'm sure you can disable an adapter using this (resets at reboot, which is why you'd need to put it into a startup script).

Blacklisting is the cleaner approach, but if you don't know how to do it then obviously it's not an option :-)

---

### Post by coffeecat on 2011-02-07
> **3rdalbum said:**
> Option 3: Create a startup script that turns off the adapter using the "iwconfig" command; I'd have to look up the man page for iwconfig but I'm sure you can disable an adapter using this (resets at reboot, which is why you'd need to put it into a startup script).

Blacklisting is the cleaner approach, but if you don't know how to do it then obviously it's not an option :-)

I believe you're missing the point of the OP's first post - at least if I'm reading the situation correctly - that he/she could find no straightforward GUI way of disabling one wireless adapter. I think there's a secondary point, that in a thread of no less than 37 posts, **no one** suggested a GUI solution, despite the fact that there is the one that I found.

Having said that, I wouldn't say that utilising the NIC MAC code in network manager is particularly user-friendly. OK for you and I, and the OP, but impossible for the ordinary computer user who has probably never heard of a MAC code. If, as the OP says, this can be done with a couple of mouse clicks in Windows (Windows 2000 no less!) then this is one up to Windows. Since this is the Testimonials forum, not a technical support forum, that is a relevant observation.

And I would suggest that in a 37-post long thread about a networking problem, no one even thinking of looking at network manager is also an eloquent testimonial about this forum. Don't get me wrong. I enjoy being a member of this forum, I learn a lot from it and I too enjoy rummaging around in the deeper recesses of this operating system. But I sometimes wish people would get their heads from under the bonnet (=hood!) from time to time, wipe their oily hands and get their feet firmly upon the ground again. :wink:

---

### Post by rocksockdoc on 2011-04-25
I was referred over to this thread here from this thread over there:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

In my situation, I have two related problems:

[LIST]
[*]I need to tell Ubuntu 10.04 to use the external USB WiFi radio (wlan1) and not the internal WiFi radio (wlan0)
[*]I also need to set the MAC address of the external WiFi radio to a specific MAC address because my WISP uses MAC-address filtering
[/LIST]
I'm going to summarize (what I can figure out) about this referenced thread:
- [**My experience with disabling one of two wireless adapters in Ubuntu**]("http://ubuntuforums.org/showthread.php?t=1682546")

**Options listed in this thread (some good, most bad):**

[LIST=1]
[*]Locate the on-board  wireless adapter and remove it (i.e., this is a bad idea)
[*] Blacklist the appropriate modules in  /etc/modprobe.d/
[*] Create a script that would autorun and evoke the "iwdown" command in some way
[*]Create a startup script that turns off the adapter using the "iwconfig" command
[*]Manually disconnect the internal wlan0 in the "Network Manager" each time you connect to WiFi
[*]Edit Connections in the Network manager to only use a single adapter with a specific MAC address
[/LIST]
Looking at that suggested last (i.e., best) option above:

[LIST=1]
[*]Right click on the Network Manager icon in the main Ubuntu 10.04 top menu bar
[*]Left click on Edit Connections -> Wireless tab
[*]Left click to highlight your desired connection & press the "Edit" button
[*]Left click on the "Wireless" tab & enter the desired MAC into the "MAC address" field
[LIST]
[*]This option locks this connection to the network device specified by the MAC address entered here. Example: de:ad:be:ef:ca:fe
[/LIST]
 
[*]Left click the "Apply" button
[*]Then, when you start up, the Network Manager should only use the wireless device with that MAC address.
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190003&stc=1&d=1303756770[/IMG]

My question:

I can set the MAC address of the external USB WiFi radio to DEADBEEFCAFE using this procedure:
```

$ sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
$ sudo ifconfig wlan0 up

```QUESTION: 
How do I get that manual setting to be automatic upon reboot?

QUESTION:
But, which MAC address do I put in the "Network Manager" "Wireless" tab "MAC Address" field?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by Peter09 on 2011-04-28
Just a quick thought, can you disable the onboard wireless card via set up in the Bios of the machine?

---

### Post by MarcusW on 2011-04-28
I agree it's a bit harder than it should be. I did the same thing once, but I added:

"modprobe -r ath9k"

(ath9k was the module name) in /etc/rc.local.

---

### Post by armandh on 2011-04-28
+1 to turn off in bios

the zotek micro ATX board I have came without the add on wifi that [when installed] used the 19V power cord to the power brick as the antenna

but there was some sort of a mini PCIE connection for it.

---

