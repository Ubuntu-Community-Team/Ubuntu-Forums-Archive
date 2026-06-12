---
title: "Thoughts on Linux/Wireless"
date: 2009-03-20
forum: Testimonials &amp; Experiences
---

### Post by mpn_1990 on 2009-03-20
I've had Ubuntu 8.04 installed along side Windows XP for about 9-10 months now, and with the exception of one extremely frustrating internet connection sharing problem which I later resolved, I've found the user experience to be excellent, with solid design and implementation. 

But one minor detail that has kept me from moving over was the rather poor wireless support. I have to admit that with Ubuntu, and linux in general, wireless support is below average. Most solutions I've seen across multiple distros across multiple cards all eventually come back to installing ndiswrapper which based on what I've experienced with it is remarkably poor software. I've had a WUSB54G v1 running under ndiswrapper for a while, and one extremely frustrating problem I have is that every thirty minutes, the card stops working and the logs turn up "getting configuration failed (00010003)" every second until I unplug and re-insert the card. Google search doesn't yield any answers so I assume this is unfixable. The lack of native drivers or at the very least a version of ndiswrapper that actually works has for the most part kept me on security-hole-city Windows. I really, really want to switch to Ubuntu for everything, but I can't keep getting up every thirty minutes to reset my wireless card. 

From what I've seen in the linux wireless development community, there's too much of an emphasis on workarounds instead of fixes: getting wireless to work with ndiswrapper instead of focusing on development of better, native, open-source drivers for the chipsets these cards use. ndiswrapper shouldn't be the first line of action, it should be the last resort, because by its very nature it's a workaround that doesn't function as well as native drivers. 64-bit systems have virtually no wireless support at all. 

Linux performs excellent in almost every area, but I have to admit the wireless support is rather weak. And admittedly, this is partly the fault of manufacturers who will release neither linux drivers nor the data required to write them. But the issue has kept me from moving over and is probably keeping many others from switching over as well, because wireless networking is becoming more and more prevalent as a cheap, easy way to link together multiple computers and share an internet connection. If Linux is to thrive, it is utterly essential that manufacturers play their part in releasing linux drivers and/or chipset documentation.

---

### Post by wolfen69 on 2009-03-20
i think ubuntu's wireless support is actually pretty good. i've tried it on about 10 different laptops without issue. and no, they did not all use intel chipsets. how many have you tried it on?

i would not say it is weak, but just not on par with windows yet.

---

### Post by rmayer32 on 2009-03-20
Last year when I first switched my laptop to 7.10 I had all sorts of fun getting the wireless working. Since then however, the support has improved to the point where for me it is a non-issue.

One day maybe the hardware manufacturers will wake up and add some support to Linux, but at least we have an excellent resource in these forums and the wireless support just gets better with each release in my opinion.

---

### Post by stalkingwolf on 2009-03-21
starting with 7.04 ive kept a netgear wg111 usb wireless adapter at hand
when working with laptops.  Recently i addaed a DLink DWL G650 cadr to the arsenal.  Both have just worked every time, until 2 days ago.  Starting
with 8.04 the internal wireless on my laptops has just worked (2 HPs, 1Toshiba, and a 704 EEE) prior to that I had to make 1 adjustment and it worked on the HPs and Toshiba. The EEE always worked.

Due to a family situation i have recently started using Yahoo messenger after being free of it for about 5 years and windows independant for 2.

I found Gyachi and it is great except for 1 little thing.  cant get my web cam to broadcast.  works everywhere even in Gyachi to show me.  I read that this wasfixed in the 8.10 version so i did a test install of 8.10 and with a couple adjustments to the camera settings it works great.  upgraded my wifes computer , with in a few minutes she was good to go.

2 down 1to go.  2 nights ago i installed 8.10 on our HP nc8000.  then the hell began.  No wireless, none.  it sees the cards and the usb stick
but wont configure or connect.  No updates after install it tells me you system is up to dATE . Bull ive never had a fresh install that was up to date.
Install Gyachi, cant unfullable dependancy.  WTF it worked fine on the 2 previous installs.

Hell with it I reinstalled 8.04 and will work on the cam thing.

I think there is a problem with fixing things that aint broke.

---

### Post by wolfen69 on 2009-03-21
[Here]("http://in.dld.yahoo.com/i/in/messenger/linux/debian_sid/ymessenger_0.99.17-1_i386.deb") is an official yahoo messenger for linux.

---

### Post by armandh on 2009-03-21
It is the wireless manufacturer that is caught in the middle
they do not want to deliver the source code for an FCC approved device where code modification can create non approved modes of transmission.

we are lucky to get restricted drivers for current production equipment.

Equipment no longer in production or from a company no longer in business is like owning a Studebaker or Packard.

---

### Post by leclerc65 on 2009-03-21
AcerOne/HawkinG HWU8DD/Ubuntu 8.10
 in my backpack
A potent formula for free Internet on the go.:D

---

### Post by my window broke on 2009-03-22
The guy still has a point, wifi is one of the biggest issues of switching to linux. I was able to convince a friend to use linux and got stuck helping him get the wifi working on a sunday for several hours, (slow internet connection and switching back and forth for a windows computer driver access). The main thing though is its not Linux's fault, its the wifi companies. They don't want to support linux...

---

### Post by haemulon on 2009-03-22
I'm using FreeBSD.

When I installed it, I didn't have to configure anything at all.

It just recognized the wireless card, I don't even have to enter any ssid, it also connected.

So why can't Linux do that?

I don't get it, if FreeBSD is so simple to connect to wireless I'm sure Linux could do it also.

---

### Post by stalkingwolf on 2009-03-22
Wolfen, I tried your link and all i get is several pages of

```
&#65533;&#1091;&#65533;&#65533;9V&#65533;1&#65533;&#65533;s&#65533;&#65533;H&#65533;7i)&#65533;7&#65533;T&#65533;(&#1803;kqN&#65533;a&#65533;&#65533;^&#65533;.&#65533;V&#65533;"&#65533;f\&#65533;W&#65533;&#65533;&#65533;_]&#65533;{&#65533;8&#65533;b&#65533;&#65533;&#65533;E&#65533;T&#65533;&#65533;IZ&#65533;$b9&#65533;&#65533;n\&#65533;&#65533;&#65533;&#65533;.&#65533;?&#65533;&#65533;&#1537;A&#65533;P&#65533;l&#65533;&#65533;!&#1800;q>%&#65533;&#65533;a&#65533;&#65533;D|&#65533; )&#65533;&#65533;\&#1805;p      &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;vc=z&#65533;&#65533;7L&#65533;A&#65533;&#65533;!&#1806;kq&#65533;&#65533;K&#65533;b|¯&#65533;2&#65533;c;&#65533;&#1033;:&#65533;Q&#65533;L&#65533;&#65533;"&#65533;&#65533;&#888;?&#65533;&#65533;&#65533;&#65533;Z&#65533;G&#65533;&#65533;&#65533;&#65533;"&#65533;b3&#65533;&#65533;
?*aD*b0&#65533;`:.&#65533;&#65533;8_\C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l@&#65533;A9r&#65533;&#65533;e&#65533;&#65533;;p.D$N&#65533;'WS7&#65533;&#65533;&#1537;&#65533;&#65533;B&#65533; &#65533;&#65533;&#65533;\&#65533;&#65533;0G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;:~&#65533;&#497;&#65533;hC
&#65533;P&#65533;L&#65533;B&#65533;_&#65533;&#65533;`"&#65533;&#65533;
&#65533;c"&#65533;&#65533;r&#65533;c"&#65533;&#65533;2&#65533;c"p&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;&#1537;A&#65533;&#65533;*&#65533;&#65533;X<&#65533;q!Nç&#1327;&#65533;&#65533;&#65533;&#65533;&#1115;&#65533;&#65533;&#65533;$
&#137;2&#65533; &#65533;1wc:.&#65533;98
_&#65533;H&#65533;&#65533;}&#65533;&#65533;&#65533;&#65533;$vb&#65533;h&#65533;f&#65533;#&#65533;X&#65533;&#65533;q3&#65533;pN&#65533;'3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;`&#1098;XQ&#65533;5&#65533;&#65533;p&#65533;P>&#65533;+xC&#65533;&#65533;&#65533;&#65533;-SuX&#65533;&#344;&#65533;&#65533;p-d&#65533;x!&#65533;&#65533;&#65533;=|~3&#65533;&#65533;&#1836;&#65533;&#65533;^&}k&#65533;'&#65533;&#65533;&#65533;|&#1806;&#65533;&#65533;RN&#65533;kx[n&#65533;&#65533;q&#65533;Z_&#65533;&#65533;&#65533;!&#65533;&#475;xOb'&#65533;&#1099;FxaF>R&#65533;&#65533;7&#65533;*&#65533;g&#65533;|r;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;`&#1098;XQ&#65533;L&#65533;&#65533;<&#65533;&#65533;q.&#153;8_&#65533;F
{&#1032;r$b6&#65533;C$>&#65533;&#65533;&#65533;'&#65533;A&#65533;`5&#65533;U&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;q&#2018;&#65533;&#65533;&#65533;S &#65533;&#65533;&#632;&#65533;8&#65533;&#65533;B&#65533;GI;!&#65533;GV&#65533;&#65533; Kp&#65533;&#65533;pQ&#447;&#65533;&#1545;!&#1315;
9X&#65533;&#65533;&#65533;w&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;s&#65533;"
&#65533;&#65533;|&#65533;\&#65533;$&#65533;&#65533;\&#1802;Kq&#65533;&#65533;&#65533;:&#65533;W&#65533;$&&#65533;
?&#656;&#65533;&#65533;&#65533;&#65533;&#65533;\&#65533;t&#65533;&#65533;

```

> Equipment no longer in production or from a company no longer in business is like owning a Studebaker or Packard.  

There are a couple of them running around here as well as a few model A,
T, and even a Nash.


> The main thing though is its not Linux's fault


when hardware that has worked for 2-3 releases or more stops working in the new release I would have to say its ubuntus fault.

---

### Post by sidewinder12s on 2009-03-22
Ya, right now im fighting with my wireless card. i got the driver and its enabled but it cant connect to a network with a Pass on it. for the past to days ive had to just sit at the router doing things. I dont know what its problem is but ever time i try to connect it just tells me, You need to enter the Password and everytime it comes up the pass that is there is not the one i put in. I enter the right one and it doesnt connect. I can connect fine on XP, but i want to switch to ubuntu full time and this is the only thing holding me back. :(

---

### Post by 3rdalbum on 2009-03-23
Try putting in the key, rather than the passphrase. (the key is a hexidecimal string). Or the other way around - Ubuntu accepts my passphrase or my key, but my Wii and Vista both want the key and they won't accept the passphrase.

FreeBSD has a different set of drivers to Ubuntu. If Ubuntu comes with drivers for your wireless, then they will automatically work. What's probably happened is that a FreeBSD developer bought one of those cards and it didn't work, so he/she wrote a driver for it; but no Linux developers ever bought one of those cards.

---

### Post by stalkingwolf on 2009-03-23
I tried 9.04 yesterday on my HP.  wireless is still broke.  can see the con ections  but they are greyed out .

Is there an alternative network manager.  The setup in 8.10 and 9.04 sucks.

---

