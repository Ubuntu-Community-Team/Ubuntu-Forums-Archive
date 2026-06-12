---
title: "I have a beef about the networking solutions that I find here"
date: 2022-01-18
forum: Ubuntu, Linux and OS Chat
---

### Post by tobias-richards on 2022-01-18
Every time that I search for solutions to my wifi drivers, the solution is to apt-get install a bunch of drivers. Why does nobody realize that apt'ing anything is a non-solution: How can I apt-get install <network drivers> if I don't have network drivers? There are DOZENS of responses to questions about network drivers that say to apt-get install various packages without any thought to the fact that nobody can apt without first having network drivers. It's seriously starting to **** me off. I've got computers with Broadcom wifi. How the heck am I going to fix that by using networking to download the gosh darn drivers to fix the networking that I don't have? Of the dozens of "solutions" that I've read about this, NOBODY ever thinks about how to fix the network driver without having a network driver. UGH!

That is all. I had to get it off my chest.

---

### Post by guiverc on 2022-01-18
Having grown up in the days of *tapes* and *floppies*, I'm accustomed to needing to use the *sneaker *net.

ie. it's not difficult to go to another box (*across the room, elsewhere in the house/building, or nearby*) and execute a `wget` to download (*you can even use a web browser to do this*) the required file, copy to media (*floppy, tape, even USB thumb-drive*), then *walk* it back to the box that doesn't have working networking and perform the `dpkg -i` (*install*).  We've been doing that since the 1960s (or 70s in my case) so are you that much against *walking* ?

To me instructions to `apt install` something are not a problem; as I don't see it as a *burden* to use my mind & *walk *and use another box to do what I can't yet do on my new install. Why should the instructions be *dumbed* *down* to cover that too?  I see modern foods that tell you to heat before eating, then give the "*caution: contents maybe hot*" as unnecessary; but maybe you don't.

---

### Post by tobias-richards on 2022-01-18
I've tried that. I've done tech support having to say the autoexec.bat and config.sys settings letter-by-letter using the phonetic alphabet. I'm not old enough to remember 8" floppies, but I spent a lot of my later teenage years using the 5.25" floppies on my Commodore 64's 1521 disk drive. I have a buddy that remembers flatbed trucks delivering 8' high spools of punch-card data to his employer that were mainframe programs. They were using the same tech as player-pianos.

The problem with sneakernet is that it becomes difficult to know every single dependency of every single deb or rpm or (xBSD) package that I need for networking. Even if I did... right now I'm getting errors that ldconfig and start-stop-daemon aren't available when I try to use dpkg. How do I install the deb files to make dpkg work when dpkg is not working?

The catch-22's involved keep getting deeper no matter how much I try to use sneakernet and deb files.

---

### Post by chili555 on 2022-01-18
You could tether your phone. You could use ethernet if your computer has it. If not, you could buy a very inexpensive USB-to-ethernet adapter. [https://www.amazon.com/AmazonBasics-Aluminum-Gigabit-Ethernet-Adapter/dp/B0898C73ZZ/ref=sr_1_4?crid=1LI36RCXQSHPP&keywords=usb+ethernet&qid=1642516678&sprefix=usb+ethernet%2Caps%2C111&sr=8-4](https://www.amazon.com/AmazonBasics-Aluminum-Gigabit-Ethernet-Adapter/dp/B0898C73ZZ/ref=sr_1_4?crid=1LI36RCXQSHPP&keywords=usb+ethernet&qid=1642516678&sprefix=usb+ethernet%2Caps%2C111&sr=8-4)

Of course, with care, you can do this: [https://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](https://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568) 

There is always a way.

---

### Post by TheFu on 2022-01-18
Drivers can be an issue for any hardware.  Over the decades, long-time Linux users have learned to buy hardware that has the best support for our loved OS. Basically, that means the drivers are high quality and included in kernel.  
A few months ago, I was upgrading a computer here and specifically picked the motherboard (B450) based on having an Intel NIC on-board that I knew had excellent Linux and BSD support.  $10 higher price than the other choices and 90% of the motherboards I looked at did NOT have an Intel NIC I knew would "just work".  I skipped the newer model of the motherboard (B550), which does have an Intel NIC, but one known with poor linux support.  I just didn't want the hassles.

It is sad that in 2021+ we still have to be very careful about the hardware we buy for our Linux computers.  But that is reality.  I've probably been disappointed at least 20 times with hardware that didn't support Linux easily.  Live and learn.

I do have a tiny USB wifi adapter that is *well* supported by Linux here somewhere. It has come in handy a few times. It isn't fast, just well-supported. Think it was $15.  I also have a few USB3-to-GigE adapters for laptops that don't have ethernet ports. That has been more useful, since I use it rather than wifi at home, almost always.

---

### Post by him610 on 2022-01-20
> I've got computers with Broadcom wifi.
Been there done that. When I completed the build of my first barebones (Shuttle) computer, I bought a Linksys wifi card that had a Broadcom chip in it. (Did not know any better then) Back then we had to tweak the Windows drivers to get them to work with Ubuntu. There was a suggested way to do it posted right here in Ubuntu Forum; however, my chip was a different model which required me to put my own modifications on it. I did get it to work though. The posted fix was my very first reply on this forum - must have been fifteen years ago.
Sometimes you gotta' do what ya' gotta' do to get things to work.

---

### Post by oldfred on 2022-01-20
In most cases you can use Ethernet to update a Wireless driver.
Did you boot live installer in live mode and see what works?

But now some small systems do not even have a default Ethernet port. Or a user cannot get to one.
Then sneakernet is about the only choice.

---

### Post by QIII on 2022-01-20
And then, of course, there are hardware models that are simply not supplied with drivers that support Linux ... which none of  us can do anything about unless someone is able to black-box a solution.

Point being:  If there isn't a driver to be included as a module in the kernel, you'll have to get it from elsewhere.  Not the fault of Linux developers.

---

### Post by jeremy31 on 2022-01-20
Since it is Broadcom, you can likely install the driver before installing Ubuntu, then be sure to select "Install third party software and drivers" during the installation and it works like magic when you reboot into the install

---

### Post by zebra2 on 2022-01-21
I had a Broadcom wifi in 2009 when I took my first Linux plunge.  The solution until I got drivers working was a USB Wifi and I used that fix for years. It is sad that you can buy a linux compatible usb wifi for $10 but you can't get a Broadcom chip in a new system that works. I personally think that Broadcom changes a single byte in their card with every edition just to keep the Linux OS from working. Over the years I have been careful to buy systems that support Linux. For me this was a learning experience.

---

### Post by tea for one on 2022-01-21
> **zebra2 said:**
> I had a Broadcom wifi in 2009 when I took my first Linux plunge.  The solution until I got drivers working was a USB Wifi and I used that fix for years. It is sad that you can buy a linux compatible usb wifi for $10 but you can't get a Broadcom chip in a new system that works.
Yes, I did exactly the same after purchasing a Netbook with Broadcom wifi. A cheap 'n' cheerful Edimax EW-7811Un ID 7392:7811 (Realtek RTL8188CUS) solved the issue.
I tried the Ubuntu Broadcom package but it proved to be an intermittent connection if you were too far from the router.
> **zebra2 said:**
> Over the years I have been careful to buy systems that support Linux. For me this was a learning experience.
I try to do this as well.
I recently bought a Lenovo laptop where the specification clearly stated Intel wireless. Excellent, should be fine with an Ubuntu flavour.
The device arrived with Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter - luckily the driver is in the kernel and the wifi worked without any effort on my part.
I know that I could have returned it because "not as advertised", but that is often a painful and clumsy process.
If it had not worked, I would have returned it.

Even with research, you can can still be tripped up by web information not being updated for every market.

---

### Post by zebra2 on 2022-01-21
@tea for one.
We are interestingly on the same page here. I have three Lenovo Laptops. They are dirt cheap on the inside, but all three work great. Especially with Linux. Hard to beat Intel.

---

### Post by chili555 on 2022-01-21
> **tea for one said:**
> I recently bought a Lenovo laptop *where the specification clearly stated Intel wireless*. Excellent, should be fine with an Ubuntu flavour.
The device arrived with Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter I would have returned it immediately.

I am saying this as a longtime Thinkpad fan going way back to the T23 with no built-in wireless at all! Break out the PCMCIA cards!

---

### Post by tea for one on 2022-01-21
> **chili555 said:**
> I would have returned it immediately.

I am saying this as a longtime Thinkpad fan going way back to the T23 with no built-in wireless at all! Break out the PCMCIA cards!

Would you have returned it because:-
[LIST]
[*]Not as advertised
[*]It uses Qualcomm Atheros QCA9377[/LIST]
The wifi is not 100% perfect and it seems to pause briefly every now and then if I am using it upstairs.
My router is downstairs and the wifi signal is fine there.

I wanted a 11.6" laptop and there was not a huge choice in late 2021 due to the oft quoted "global shortage of computer chips".
I am not disappointed bearing in mind the purchase price £180.00  (= USD240.00 approx)

---

### Post by chili555 on 2022-01-21
> **tea for one said:**
> Would you have returned it because:-
[LIST]
[*]Not as advertised
[*]It uses Qualcomm Atheros QCA9377[/LIST]
The wifi is not 100% perfect and it seems to pause briefly every now and then if I am using it upstairs.
My router is downstairs and the wifi signal is fine there.

I wanted a 11.6" laptop and there was not a huge choice in late 2021 due to the oft quoted "global shortage of computer chips".
I am not disappointed bearing in mind the purchase price £180.00  (= USD240.00 approx)Both not as advertised and because I am aware that the Atheros device, using the driver ath10k_pci is the source of many questions without dispositive answers here and at Ask Ubuntu. Your experience is just one more example.

Of course I could, as I have done several times before, because I love to tinker, replace the card with an Intel but why should I have to spend extra time and money to remedy the vendor's error?

---

### Post by tea for one on 2022-01-21
> **chili555 said:**
> because I am aware that the Atheros device, using the driver ath10k_pci is the source of many questions without dispositive answers here and at Ask Ubuntu. Your experience is just one more example.
Thank you for the info, the driver in use is indeed [COLOR="#0000FF"]ath10k_pci[/COLOR].

In the event of any future difficulty, I shall keep my eyes peeled on the relevant forum questions and answers.

---

