---
title: "My Laptop is Spoof Attacking my Router?"
date: 2010-03-31
forum: Security
---

### Post by mfdc1969 on 2010-03-31
For the past week I have been having trouble with my ADSL connection ... I thought it was the ISP but now I'm not sure. I can hardly ever connect to Google on the first click - "*Firefox can't find the server at [www.google.ca](www.google.ca)*" and now it's very difficult to use websites that require cookies to carry information to the next page (such as customizing a computer of the Dell site) ...

On a whim I checked the router logs (DLINK WBR-2310) and it shows my computer as a 'spoof attack' - see the attached screen shot.

The MAC listed is that of my own computer.

So I checked for rootkits using rkhunter/chkrootkit with nothing unusual listed. I recently added a switch (Linksys/Cisco EZXS55W) to connect my laptop to a file server in my crawlspace. The switch is also connected to the router. Disconnecting the switch seems to make no difference. 

My wife's computer is also suffering the same problems, running WinXP.

We both are using the latest Firefox versions as per automatic updates.

Is there a reason for me to be concenred that my laptop, running Ubuntu 9.10, is being listed in my router logs as "spoof attack"?

---

### Post by a.walker on 2010-03-31
Do you have MAC filtering enabled on your router? Did you start having these problems at approximately the same time you installed the switch? Have you tried configuring your computer to use opendns (to see if you are having some dns related problems)?

---

### Post by cdenley on 2010-03-31
It is hard to know what "spoof attack" means since there are many different forms of spoofing, and that log entry is too vague. My guess is your laptop isn't spoofing, but it is being spoofed to bypass your wireless routers MAC filtering. If someone else is using your MAC to gain wireless access, then a duplicate MAC address can certainly cause the intermittent network problems you describe.

---

### Post by dogdo on 2010-03-31
what wireless security you have up-wpa2 psk?

---

### Post by mfdc1969 on 2010-04-13
Well, after posting that first reply a friend suggested I check to see if my router had new firmware - it did. After updating that I have not had any such warnings in my router's logs. Nothing more than simply an accounting of lease granting/expiring in over 20 pages. And my web related problems have all disappeared. Google is back and it seems I can browse through sites carrying information/cookies etc. I guess that solved it?

I think the switch was coincidental but I will take the advice and use MAC filtering - that's a great idea as I know exactly who should be using my internet!

For wireless I am simply using WEP 128 ... I guess I should be using something stronger but I had troubles setting it up while using Hardy so I just avoided anything stronger than WEP. Now I use Karmic so I should just do it ...

Thanks for all your comments!

---

### Post by CharlesA on 2010-04-13
MAC Filtering is pointless since an attacker can just spoof the MAC address of an allowed client. All it does is provice a false sense of security and make it more of a pain in the *** for you to connect a legit wireless client to the AP.

Try to use WPA2 AES if you can, since WEP is terribly easy to crack.

---

### Post by mfdc1969 on 2010-04-13
Can anyone suggest some good Ubuntu related pages explaining more about wireless security from an Ubuntu point of view?

I know there are lots of pages in the Community Documentation but I would appreciate any links to blogs or other opinion/fact based writings from Ubuntu users.

Thanks!

---

### Post by CharlesA on 2010-04-13
Wireless security on Linux is no different from that on Windows or Mac.

What are you looking for exactly? "Wireless security" is a bit of a broad term.

---

### Post by mfdc1969 on 2010-04-13
Oh just some descriptions of the different types of security WEP, WPA etc...

I thought perhaps there might be some favourite sites (Lifehacker, Ubuntu Blogs etc.) that some one might want to recommend.

M

---

### Post by CharlesA on 2010-04-13
I see. 

There's a huge bunch of info here: [http://en.wikipedia.org/wiki/Wireless_security](http://en.wikipedia.org/wiki/Wireless_security)

Most of the sites I've seen talking about wireless security mention both MAC filtering and hiding the SSID.

MAC filtering is easily gotten around by spoofing the MAC of a known allowed host. A hidden SSID can still be found if someone is scanning for them, not to mention that it can allow someone to MitM (Man in the Middle) you, by making you connect to a rogue AP of the same name.

Overall there isn't much to wireless security, just use WPA2 AES, if all the devices on your network support it, with a long randomized key like the ones you can find here: [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

### Post by mfdc1969 on 2010-04-13
Thank you - as I said I have remained pretty much ignorant of security options, although I do hide SSID I have only been using WEP. That will change!

---

