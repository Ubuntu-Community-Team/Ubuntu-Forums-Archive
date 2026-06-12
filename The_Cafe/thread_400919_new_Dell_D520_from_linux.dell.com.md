---
title: "new Dell D520 from linux.dell.com"
date: 2007-04-04
forum: The Cafe
---

### Post by gradedcheese on 2007-04-04
Just a quick report:

I needed to buy a laptop for my grandmother (it's her first computer).  'went to linux.dell.com, ordered a D520 "n-series" (n = No Windows) laptop, and it arrived today.  I ordered it with Intel wireless and video, so everything worked out of the box.  

The D520 is actually quiet a nice laptop, very sturdy construction, very fast, and a good screen (no dead pixels).  It has little rubber standoffs on the screen casing to prevent marks from the keyboard from appearing when the lid is closed.  On first bootup, you'll need to press F2 to get to the BIOS and select CD-ROM as the first boot device.  'Strange that a "no OS" PC tries to boot off the hard disk unconditionally ;)

So, if anyone else is thinking about buying one of these, I just wanted to say that I am quiet happy with it.  Do order the Intel wireless (costs a little extra) because the default "Dell wireless" will have a Broadcom chipset which, ironically, is pretty worthless in Linux.  I am looking forward to them offering these with a distribution pre-installed, but for now this setup will do fine.

Also, a quick tip for those of us setting up a computer for family members:
- install openssh-server and put your public keys on their computer
- set up their DSL router (or whatever) to NAT port 22 for you
- also perhaps set up opendns.org as their DNS service

My logic with this is that I can then remotely log in and fix things (and run updates) as needed or install additional software that they may need.  Of course I also don't have to worry about stupid things like viruses and anti virus software, but that sort of comes with using Linux :)

---

### Post by user1397 on 2007-04-04
EDIT: I did a comparison between a system76 Gazelle Value (ubuntu preinstalled), a dell n-series latitude D520N (no OS preloaded), and a dell latitude D520 (windows preinstalled), all with the same specs.

The results are:

1) system76: $888

2) dell n-series: $757

3) dell D520 (with windows): $738 (but it has a free upgrade to a 60 GB hard drive, whereas the other 2 have a 40 GB)

---

### Post by gradedcheese on 2007-04-04
Yeah, I thought about buying from them and I kind of feel bad for not supporting them, but I have never liked the Asus 'whitebook' stuff that their laptops are based on (it just doesn't feel like a nice 'package', unlike what Dell and some others provide).  Also as someone who has repaired many ThinkPads and Dells to keep them running, I feel better about used and new replacement parts availability for a Dell than I do about chasing down various Asus OEM components in a few years.  All that said, the System76 laptops are indeed a great deal (though technically this Dell is slightly cheaper as it has a 15" screen).

By the way, those of you wanting fancy desktop effects, please note that Intel's 915 video (the default on most laptops) handles those just fine.  No need to order your laptop with ATI or NVidia crap and then have to deal with their idiotic closed-source drivers.

---

### Post by mips on 2007-04-04
Don't want to burst your bubble but you got suckered if you ask me.

If you purchased the windows version of the laptop you would have gotton a better deal.
60GB HD instead of 40GB
$728 vs $856


Your configuration:
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=blcwdn1&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=blcwdn1&s=bsd)

Identical configuration but with Windows:
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=blcwd1s&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&kc=6W300&l=en&oc=blcwd1s&s=bsd)


If i was you I would return it and get the windows version I listed above and save yourself $128 and get a bigger HD.

---

### Post by Engnome on 2007-04-04
> **gradedcheese said:**
> J
- set up their DSL router (or whatever) to NAT port 22 for you
- also perhaps set up opendns.org as their DNS service



You might wan't to use another port instead of 22 for security reasons.

I find opendns slower than my ISP:s dns server, don't just believe that opendns is faster do some testing.

There is no linux.dell.se for Sweden :(  Only americans can order the n series?

---

### Post by mips on 2007-04-04
> **Engnome said:**
> 
There is no linux.dell.se for Sweden :(  Only americans can order the n series?

Why would you want to anyway ? It's a US$128 more expensive than the windows version, or do you just like throwing money away ?

Sometimes I really wonder about people & their logic or should I say their lack there of.

---

### Post by Engnome on 2007-04-04
> **mips said:**
> Why would you want to anyway ? It's a US$128 more expensive than the windows version, or do you just like throwing money away ?

Sometimes I really wonder about people & their logic or should I say their lack there of.

I wouldn't :D I don't like dell at all and even if there was a linux.dell.se with ubuntu loaded laptops cheaper than windows machines I wouldn't buy one.

But not having the n series (in Sweden) shows that Dell doesn't care. Not that I care what Dell cares about but some do and if Dell showed that they cared maybe more would.

Sometimes I really wonder about people & their logic or should I say their lack there of. :P

---

### Post by maniacmusician on 2007-04-04
> **mips said:**
> Why would you want to anyway ? It's a US$128 more expensive than the windows version, or do you just like throwing money away ?

Sometimes I really wonder about people & their logic or should I say their lack there of.
:) yeah. What's best about this particular situation is that, as ubuntuman pointed out, the system76 laptop, that comes with warranties and actual ubuntu-based support, is actually cheaper as well.

---

### Post by Oki on 2007-04-04
System76 laptop don't ship to my country(yet), but Dell do. 
Engnome; I believe Dell will ship n series to Sweden if you call them, I remember one from Norway did that.

---

### Post by maniacmusician on 2007-04-04
> **Oki said:**
> System76 laptop don't ship to my country(yet), but Dell do. 
Engnome; I believe Dell will ship n series to Sweden if you call them, I remember one from Norway did that.
Yeah, that's a big bummer....I hope they fix that soon.

---

### Post by Oki on 2007-04-04
And if they do; then I would rather do business with them, and not Dell! Personally I find it strange that System76 have not started to sell to other countries. I mean; the Dell ideastrom shows us that there is a big marked for Linux desktops around the world. Thanks to Internet people are shopping from all places, I have already bought a lot of photo equipment form US, and I am not alone.

---

### Post by ssam on 2007-04-04
you should disable password logins for ssh. if you have ssh server exposed to the internet expect to get regular log on attempts from with common usernames and passwords, as well as brute force attacks.

from my /etc/ssh/sshd_config
```
PasswordAuthentication no
```

a typical chunk from my /var/log/auth.log
```

Apr  2 12:53:08 localhost sshd[10206]: Connection from 216.180.225.106 port 48749
Apr  2 12:53:09 localhost sshd[10206]: Invalid user d@rk\r from 216.180.225.106
Apr  2 12:53:10 localhost sshd[10208]: Connection from 216.180.225.106 port 48942
Apr  2 12:53:11 localhost sshd[10208]: Invalid user dark\r from 216.180.225.106
Apr  2 12:53:11 localhost sshd[10210]: Connection from 216.180.225.106 port 49679
Apr  2 12:53:12 localhost sshd[10210]: Invalid user dark123\r from 216.180.225.106
Apr  2 12:53:13 localhost sshd[10212]: Connection from 216.180.225.106 port 49802
Apr  2 12:53:14 localhost sshd[10212]: Invalid user testuser\r from 216.180.225.106
Apr  2 12:53:14 localhost sshd[10214]: Connection from 216.180.225.106 port 50004
Apr  2 12:53:15 localhost sshd[10214]: Invalid user t3stus3r\r from 216.180.225.106
Apr  2 12:53:16 localhost sshd[10216]: Connection from 216.180.225.106 port 50216
Apr  2 12:53:17 localhost sshd[10216]: Invalid user testuser123\r from 216.180.225.106

```

---

### Post by mips on 2007-04-04
> **Engnome said:**
> I wouldn't :D I don't like dell at all and even if there was a linux.dell.se with ubuntu loaded laptops cheaper than windows machines I wouldn't buy one.



Same here. Good choice.

---

### Post by mips on 2007-04-04
> **Oki said:**
> And if they do; then I would rather do business with them, and not Dell! Personally I find it strange that System76 have not started to sell to other countries. I mean; the Dell ideastrom shows us that there is a big marked for Linux desktops around the world. Thanks to Internet people are shopping from all places, I have already bought a lot of photo equipment form US, and I am not alone.

Oki,

Why not simply buy the eaxact same model laptop locally that System76 sells in the US ? In the process you will save yourself some money. Is it that hard to install Ubuntu or whatever yourself ? Last time I checked they used Asus whitebook laptops which can be brough anywhere in the world where Asus has a presence/distributor.

---

### Post by gradedcheese on 2007-04-04
About the pricing:

The "cheaper" Windows laptops have the following problems for me:
1) MS earns something off them and the purchase will be logged as another Windows license that someone bought
2) their price is offset by all the craplets that Dell preloads, otherwise they would indeed be much more expensive than the n-series version.  Dell and other PC sellers have basically admitted to this in the past.  With Linux or no-OS there are no craplets to preload.
3) I'm kind of an idealist and I will actually pay more for the non-craplets-funded, no-Windows-license version, especially if it registers on Dell's radar as someone people are interested in and gets them to move in the right direction...

---

### Post by user1397 on 2007-04-05
> **maniacmusician said:**
> :) yeah. What's best about this particular situation is that, as ubuntuman pointed out, the system76 laptop, that comes with warranties and actual ubuntu-based support, is actually cheaper as well.my bad, if you look at my post again, you will find that it has been edited...I had meant to say the system76 laptop was *cheaper* than the n-series dell, but none of that really matters, if the dell preloaded with windows is actually cheaper than all of them...

---

