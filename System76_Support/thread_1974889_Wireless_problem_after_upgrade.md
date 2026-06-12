---
title: "Wireless problem after upgrade"
date: 2012-05-06
forum: System76 Support
---

### Post by jml on 2012-05-06
I searched the forum and could not find reference to this type of problem. I have a Panp8 originally shipped with 11.04.  Everything worked.  Upgraded to 11.10 and everything worked.  Upgraded to 12.04 and a strange wireless problem occured.

Network manager sees my wireless access point (with WPA encryption) and supposidly connects with three out of four bars of signal strength.  But when I open FireFox and try to connect, the attempt times out saying that the server could not be found.  Things that I have tried:

1.  Reinstalled 12.04 as a clean install
2.  Turned the wireless card off then on with Fn F11
3.  System connects with a wired connection
4.  My Panp8 connects wirelessly with 11.10 Live CD
5.  Wireless works perfectly with all of my other wireless devices, (MacBook Pro, iPad, Acer Aspire One.)
6.  sudo lspci results in the following:  Intel Corporation Centrino Advanced-N 6230 (rev 34)

Since my network works perfectly with my other devises, and on my Panp8 with earlier versions of Ubuntu, I suspect that the problem lies with an obscure setting.  Any help would be appreciated. Thanks.

Joe

---

### Post by isantop on 2012-05-07
> **jml said:**
> I searched the forum and could not find reference to this type of problem. I have a Panp8 originally shipped with 11.04.  Everything worked.  Upgraded to 11.10 and everything worked.  Upgraded to 12.04 and a strange wireless problem occured.

Network manager sees my wireless access point (with WPA encryption) and supposidly connects with three out of four bars of signal strength.  But when I open FireFox and try to connect, the attempt times out saying that the server could not be found.  Things that I have tried:

1.  Reinstalled 12.04 as a clean install
2.  Turned the wireless card off then on with Fn F11
3.  System connects with a wired connection
4.  My Panp8 connects wirelessly with 11.10 Live CD
5.  Wireless works perfectly with all of my other wireless devices, (MacBook Pro, iPad, Acer Aspire One.)
6.  sudo lspci results in the following:  Intel Corporation Centrino Advanced-N 6230 (rev 34)

Since my network works perfectly with my other devises, and on my Panp8 with earlier versions of Ubuntu, I suspect that the problem lies with an obscure setting.  Any help would be appreciated. Thanks.

Joe

Try unplugging your wireless router for a few minutes, then plug it back in. We're sure there aren't any compatibility issues with 12.04 and any of our Wireless cards in Pangolins, so you'll want to try this.

---

### Post by jml on 2012-05-07
Will do, I will try this when I get home from work.

Joe

---

### Post by jml on 2012-05-07
Still no joy.  Powercycling the wireless router did not help.  I again tried a live CD version of Ubuntu 11.10 and both the wired and wireless connections worked perfectly.  All of my other devices connect.

When I enable wireless, I can connect to the wireless access point.  It simply cannot connect to the internet.  This Panp8 worked flawlessly until the upgrade to 12.04.  I do not think it is a hardware problem, but rather something in either the software settings or in the firmware.  Any further suggestions would reallly be appreciated.  Oh, I am connecting to a Trendnet wireless AP/Router.

Joe

---

### Post by ctsdownloads on 2012-05-08
> **jml said:**
> Still no joy.  Powercycling the wireless router did not help.  I again tried a live CD version of Ubuntu 11.10 and both the wired and wireless connections worked perfectly.  All of my other devices connect.

When I enable wireless, I can connect to the wireless access point.  It simply cannot connect to the internet.  This Panp8 worked flawlessly until the upgrade to 12.04.  I do not think it is a hardware problem, but rather something in either the software settings or in the firmware.  Any further suggestions would reallly be appreciated.  Oh, I am connecting to a Trendnet wireless AP/Router.

Joe

This may be nothing, but I'm curious.

Doing a iwconfig/ifconfig, are you seeing any excessive errors/retries? Second thought, you mentioned that you're connected okay to the access point. Is the admin area accessible when connected wirelessly? If so, does visiting 173.194.33.34 bring you to Google in Firefox?

Since isantop reports that the other models of that PC work fine with 12.04, I cannot help but wonder if there is some kind of blockage happening somewhere. Maybe an error with how DNS is being handled?

---

### Post by jml on 2012-05-08
Thanks for the suggestion.  I will try this when I get home from work.

Joe

---

### Post by shallowthought on 2012-05-09
Had same problem: have P8 with 11.04. First tried to do an upgrade to 11:10. Upgrade
failed. Then did a clean install to 12.04. Everything seems to work, except the wireless.
Then, following advice, unplugged everything, and when turned back on the wireless worked.

---

### Post by m90benaiah on 2012-05-09
I've also encountered a wireless problem after the upgrade. It says I'm connected but when I go to Firefox the load fails. I know it's not the connection; our Mac works just fine.

---

### Post by jml on 2012-05-11
ctsdownloads, I tried your suggestion butit did not work.  Typing in the address with a hardwired connection brought up Google, but even though the system indicated a wireless connection, Google did not load typing in the same address.

m90benaiah, your experience is the same as mine.  Network manager tellsme that I am connected to my wireless router, but it does not connect to the internet.

Very strange and frustrating, wireless worked perfectly with version 11.04 and 11.10.  Absolutely no problems.  All of my other devices still connect flawlessly to my wireless access point.  

I am temporarily giving up on Ubuntu on this laptop.  Unfortunately, not many of my preferred Linux distros are compatible with the Panp8's hardware.  I removed Ubuntu and am currently running Mint 12.  Wireless works perfectly, unfortunately without the benefit of S76's custom drivers, a lot of other functionality is not enabled.  Function keys for example.  I sent an e-mail to support at s76 several days ago, but I havenot heard back from them yet.  Will keep this thread posted if anything changes.

Joe

---

### Post by isantop on 2012-05-11
> **jml said:**
> ctsdownloads, I tried your suggestion butit did not work.  Typing in the address with a hardwired connection brought up Google, but even though the system indicated a wireless connection, Google did not load typing in the same address.

m90benaiah, your experience is the same as mine.  Network manager tellsme that I am connected to my wireless router, but it does not connect to the internet.

Very strange and frustrating, wireless worked perfectly with version 11.04 and 11.10.  Absolutely no problems.  All of my other devices still connect flawlessly to my wireless access point.  

I am temporarily giving up on Ubuntu on this laptop.  Unfortunately, not many of my preferred Linux distros are compatible with the Panp8's hardware.  I removed Ubuntu and am currently running Mint 12.  Wireless works perfectly, unfortunately without the benefit of S76's custom drivers, a lot of other functionality is not enabled.  Function keys for example.  I sent an e-mail to support at s76 several days ago, but I havenot heard back from them yet.  Will keep this thread posted if anything changes.

Joe

Just a note, we've actually dropped the old email support system in favor of a new system built-in to our website. Just log in to your account on our website to get to it.

---

### Post by Blatm on 2012-09-19
I seem to be having the same problem after upgrading from 11.04 to 12.04. Only WPA seems to be giving me trouble.

---

### Post by funicorn on 2012-09-20
try tracepath <url> and see what happens

---

### Post by Blatm on 2012-09-22
```
blatm@Bob:~$ tracepath google.com
gethostbyname2: Unknown host
```For some reason the wpa wireless at university now works, though my home network still doesn't. I'm sorry for the slow reply. Obviously without internet it's difficult.

I'm new to linux so I'm not sure what kind of information will be useful. Let me know what you need, and thanks for the help.

---

### Post by dbingham on 2012-09-29
I'm having the same problem.  I have a brand new Lemur Ultra and this has been an issue since I took it out of the box.   In my case, wireless connects fine but after some random amount of time I stop being able to load any websites.   I just get failed to contact server.  I am unable to connect to the admin page of my router.  It also happens while updating using the update manager.  The update manager claims the connection dropped.  The wireless claims to still be connected.  Logging in and out again does not fix the problem, but restarting my computer does.  At least, until the next random time drop occurs.  It's clearly on my laptop's end and not in the router.

Any suggestions would be thoroughly appreciated.  I'd like to actually be mobile with my new laptop instead of stuck to a chord.

---

### Post by Ubun2to on 2012-10-01
> **dbingham said:**
> I'm having the same problem.  I have a brand new Lemur Ultra and this has been an issue since I took it out of the box.   In my case, wireless connects fine but after some random amount of time I stop being able to load any websites.   I just get failed to contact server.  I am unable to connect to the admin page of my router.  It also happens while updating using the update manager.  The update manager claims the connection dropped.  The wireless claims to still be connected.  Logging in and out again does not fix the problem, but restarting my computer does.  At least, until the next random time drop occurs.  It's clearly on my laptop's end and not in the router.

Any suggestions would be thoroughly appreciated.  I'd like to actually be mobile with my new laptop instead of stuck to a chord.

Stuck to one chord? That must be one boring song.
Anyway, have you ever tried disabling and re-enabling networking from the networking menu?

---

### Post by a_m_100 on 2012-10-01
Hey everyone!

I guess my problem is very similar to yours...
I'm using Ubuntu 12.04 and have had a new wireless connection since about two weeks. Today afternoon my problem began. The laptop shows a healthy connection, and the torrents work, but the browser won't, I get the usual error page in Firefox. It's not the case of the torrents drowning out the browser because I've tried switching the client off and it still won't work. I've also tried to unplug the router and wait for the few minutes, but I get the same result. Now I'm at my uni and wireless works just fine. Any help would be appreciated!

edit: Just tried to rename /etc/resolv.conf as was suggested here: [http://askubuntu.com/questions/131004/wireless-connection-shows-up-but-cant-connect-to-internet-with-an-intel-wifi-li](http://askubuntu.com/questions/131004/wireless-connection-shows-up-but-cant-connect-to-internet-with-an-intel-wifi-li)

I hope this solution sticks! Also, would anyone be kind enough to tell me why this problem occurs and why this solution helps? If it's too noobish to answer then forget it! :)

---

