---
title: "Help! Wi-fi not working."
date: 2011-03-12
forum: Ubuntu Studio
---

### Post by Shreger on 2011-03-12
I'm absolutely and completely new to Linux in general, but since most of the art programs I use are Linux ports, and tend to run slowly on Windows, I decided to try installing Ubuntu Studio on my Laptop. Just to see if they ran any faster in their 'native environment'.

Regretfully, I broke my ethernet port some years ago, and can only access the internet (to get driver updates, or, well, anything) via Wi-fi. I cannot for the life of me figure out how to do this.

In theory, I should be able to use the "network" tool under "System->Administration." Once there, I *should* be able to use the "connections" tab to acces the wireless connection properties, enter the network name, password, IP address, Subnet mask, and Gateway address manually, thus solving my problem (that would seem the logical solution to my Windows-based frame-of-reference). However when I do this the only significant change is that Firefox takes ten minutes to give me a "cannot find page" error, rather than the one second it did before.

I've just spent the last 6 hours trying to find a solution to my problem, and I'm starting to become rather frustrated (understatement). Can anyone help me before I snap and throw my computer across the room?

Thanks,
Jesse.

P.S. I can still access the net via my desktop (ie. How I'm posting this), so if there's something I need to download, I can do it with this, and transfer it over manually.

---

### Post by Pablo_F on 2011-03-12
Hi,

Wireless in ubuntustudio seems to be a problem. Imho, the best thing you can do is installing a generic ubuntu, which hopefully will detect your wireless out of the box.

You can install every package included in ubuntustudio via Synaptic or the Software Center, so don't feel like you are missing anything. 

Cheers, Pablo.

---

### Post by Shreger on 2011-03-16
So are you saying there's no hope whatsoever for Ubuntu Studio when it comes to Wi-fi? I really don't want to go to the regular Ubuntu to be honest. I've heard that Studio has a "low-latency kernel" (devotes 95% of CPU cycles to primary artistic application), and I *really *like the idea....

...A lot.

So unless there's some way to make regular Ubuntu have the same thing, I'd rather not give up on Studio just yet.

Surely there's some way.

Thanks,

Jesse.

---

### Post by Shreger on 2011-03-16
Ah! Problem solved!

Apparently, when the makers of Ubuntu Studio got rid of all the non-art software, they got rid of the network manager too.

For anyone who has a similar problem, here is how to fix it:

1. Acquire a USB Ethernet adapter.
2. Re-install Ubuntu Studio with Ethernet hooked up through the adapter. (yes, you have to, otherwise it won't have been able to make the necessary updates during install to get online afterward, adapter or not)
3. System -> Administration -> Synaptic Package Manager
4. Scroll down to, and select "Networking" (_***NOT***_ "multiverse" or "universe")
5. In the search box, enter "Network manager"
6. Click the check box on "network-manager-gnome," and select "mark for install"
7. Click "Apply."
8. Accept everything it wants to install, download, etc.
9. Restart.
10. Make sure Wi-fi is turned on, then select your network of choice.

Done! 

Special thanks to: My tech (my dad (who *is *a certified and practicing computer specialist (who I mooch help from regularly))), for lending me the adapter.

---

### Post by corestorm on 2011-03-16
:popcorn:i love posts like this

---

### Post by russ218 on 2011-03-18
Ubuntu studio seems to be a great catch there are really some areas that they need to improve such as things like this. I would love it if they have a customer support avaialble 24/7. Overall I would still go for ubuntu. :)

---

