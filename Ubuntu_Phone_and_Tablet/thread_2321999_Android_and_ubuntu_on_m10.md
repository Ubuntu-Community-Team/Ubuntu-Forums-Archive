---
title: "Android and ubuntu on m10"
date: 2016-04-25
forum: Ubuntu Phone and Tablet
---

### Post by NiksaVel on 2016-04-25
ARe there any tuturials on flashing android on ubuntu m10? How about on flashing ubuntu back? ANy chance for something like dual boot?


Something likehttp://www.mibqyyo.com/en-articles/2015/09/16/ubuntu-android-installation-process-for-bq-aquaris-e4-5-and-e5/#/vanilla/discussion/embed/?vanilla_discussion_id=0

---

### Post by Jon_Thomas on 2016-04-25
I would think you would need a boot loader would let you choose which one to boot first. 

 I know it has been done before a year or two ago with multiple Android ROM's on one device with some varied success. Do a search on XDA Developer's site for details.

---

### Post by NightCrawler on 2016-04-25
Yes, it's doable. I did it with mine since I find the thing unusable at the current state.

1. Downlaod Flash tool from here: [http://spflashtool.com/](http://spflashtool.com/)
2. Download firmware from here (1.3 is the actual version): [http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/](http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/)
3. Unzip the firmware into a separate folder.
4. Put the tablet into a fastboot mode
5. Start the flashtool (sudo ./flash_tool)
6. Select scatter file (MT8163_Android_scatter.txt)
7. Select the option Firmware Upgrade
8. Click on Download and be patient.
9. When flashing has completed, exit the Flash Tool and disconnect the tablet.
10. First boot might take 10 - 15 minutes so don't panic. As long as boot screen says 'powered by Android' and the boot animation hasn't frozen, things are OK.

Disclaimer: I am not responsible for any damaged hardware or software arising from this process, so proceed at your own risk.

---

### Post by Jon_Thomas on 2016-04-25
> **NightCrawler said:**
> Yes, it's doable. I did it with mine since I find the thing unusable at the current state.

1. Downlaod Flash tool from here: [http://spflashtool.com/](http://spflashtool.com/)
2. Download firmware from here (1.3 is the actual version): [http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/](http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/)
3. Unzip the firmware into a separate folder.
4. Put the tablet into a fastboot mode
5. Start the flashtool (sudo ./flash_tool)
6. Select scatter file (MT8163_Android_scatter.txt)
7. Select the option Firmware Upgrade
8. Click on Download and be patient.
9. When flashing has completed, exit the Flash Tool and disconnect the tablet.
10. First boot might take 10 - 15 minutes so don't panic. As long as boot screen says 'powered by Android' and the boot animation hasn't frozen, things are OK.

Disclaimer: I am not responsible for any damaged hardware or software arising from this process, so proceed at your own risk.

Well, hopefully it will work better for you.

---

### Post by NiksaVel on 2016-04-26
> **NightCrawler said:**
> Yes, it's doable. I did it with mine since I find the thing unusable at the current state.

1. Downlaod Flash tool from here: [http://spflashtool.com/](http://spflashtool.com/)
2. Download firmware from here (1.3 is the actual version): [http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/](http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/)
3. Unzip the firmware into a separate folder.
4. Put the tablet into a fastboot mode
5. Start the flashtool (sudo ./flash_tool)
6. Select scatter file (MT8163_Android_scatter.txt)
7. Select the option Firmware Upgrade
8. Click on Download and be patient.
9. When flashing has completed, exit the Flash Tool and disconnect the tablet.
10. First boot might take 10 - 15 minutes so don't panic. As long as boot screen says 'powered by Android' and the boot animation hasn't frozen, things are OK.

Disclaimer: I am not responsible for any damaged hardware or software arising from this process, so proceed at your own risk.


Thanks,  I'll definitely give it a try since this thing is really unusable for anything but casual web surfing...   there really should be a sticky or an "official" way to switch back and forth between ubuntu touch and android...  at least a sticky on this forum...   I could also imagine an app that would do it automatically...

---

### Post by NightCrawler on 2016-04-26
> **Jon_Thomas said:**
> Well, hopefully it will work better for you.

My mistake was that I bought it based on hype around it and hoping that it will be in usable state for my media consumption needs and some light document editing, ssh into my server etc.
The flaws have been documented in other threads so I will not repeat them here. Unfortunately, I think, as it currently stands, the tablet is simply not ready. I was expexting beta quality but it's actually alpha quality. Too much functionality is missing.

With that being said, I would like to clarify that I use Ubuntu on my desktop, laptop, on a couple of servers and all those machines are rock solid. I bought a Meizu MX4 and I can live with occasional flaw on that one, since the stuff I do on the phone is fairly simple and limited compared to the plans I had for the tablet. However, convergence is simply not there yet and as media consumption device it has some pretty big flaws. 

In any case, I'm keeping the tablet and will be observing how Ubuntu touch develops and I will be flashing it back to Ubuntu (probably around OTA 14~15 :wink: ).

Currently, it's on Android and it's just so much faster (pdf opening, ebooks, streaming music and videos, etc.). I use Juice SSH for my server admin stuff and life is good again :)

---

### Post by NiksaVel on 2016-04-26
> **NightCrawler said:**
> My mistake was that I bought it based on hype around it and hoping that it will be in usable state for my media consumption needs and some light document editing, ssh into my server etc.
The flaws have been documented in other threads so I will not repeat them here. Unfortunately, I think, as it currently stands, the tablet is simply not ready. I was expexting beta quality but it's actually alpha quality. Too much functionality is missing.

With that being said, I would like to clarify that I use Ubuntu on my desktop, laptop, on a couple of servers and all those machines are rock solid. I bought a Meizu MX4 and I can live with occasional flaw on that one, since the stuff I do on the phone is fairly simple and limited compared to the plans I had for the tablet. However, convergence is simply not there yet and as media consumption device it has some pretty big flaws. 

In any case, I'm keeping the tablet and will be observing how Ubuntu touch develops and I will be flashing it back to Ubuntu (probably around OTA 14~15 :wink: ).

Currently, it's on Android and it's just so much faster (pdf opening, ebooks, streaming music and videos, etc.). I use Juice SSH for my server admin stuff and life is good again :)

Exactly my thoughts...  this is really alpha...   all I can do is some light surfing and opening some documents, but I see that if development continues this could really be something worth using.  Just the fact that I can convert the tablet to android and than switch back is actually a good selling point, and I really think that this should be streamlined with some simple app like rom switcher for rooted android phones. With this option I do not regret one bit purchasing this tablet even though at it's current state it can not serve what I expect of it. I will happily switch back to ubuntu occasionally to see how it's developing and to provide some hands-on reviews.

---

### Post by grahammechanical on 2016-04-26
If you flash the BQ Android image to that device then you get into the situation that all android users are in. Relying on the OEM to upgrade Android. Stick with Ubuntu and Canonical will send out Over the Air (OTA) updates to the OS every six weeks or so.

[https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1](https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1)

Regards

---

### Post by Helsvell on 2016-04-26
> **NightCrawler said:**
> Yes, it's doable. I did it with mine since I find the thing unusable at the current state.

1. Downlaod Flash tool from here: [http://spflashtool.com/](http://spflashtool.com/)
2. Download firmware from here (1.3 is the actual version): [http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/](http://www.mibqyyo.com/en-download/categorias/aquaris-m10-fhd/)
3. Unzip the firmware into a separate folder.
4. Put the tablet into a fastboot mode
5. Start the flashtool (sudo ./flash_tool)
6. Select scatter file (MT8163_Android_scatter.txt)
7. Select the option Firmware Upgrade
8. Click on Download and be patient.
9. When flashing has completed, exit the Flash Tool and disconnect the tablet.
10. First boot might take 10 - 15 minutes so don't panic. As long as boot screen says 'powered by Android' and the boot animation hasn't frozen, things are OK.

Disclaimer: I am not responsible for any damaged hardware or software arising from this process, so proceed at your own risk.

This just sits at "Search usb, timeout set as 3600000 ms".  I guess I am missing the drivers package in ubuntu?

---

### Post by NiksaVel on 2016-04-26
> **grahammechanical said:**
> If you flash the BQ Android image to that device then you get into the situation that all android users are in. Relying on the OEM to upgrade Android. Stick with Ubuntu and Canonical will send out Over the Air (OTA) updates to the OS every six weeks or so.

[https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1](https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1)

Regards

Don't get me wrong, I love ubuntu and the idea of the ubuntu mobile convergance....   but I am not a developer and I can get more use even from an old Ipad...  this device is little more than a paperweight for a regular user at this point...   in this state I could never recommend this device to anyone, but I hope that will change over time...   ATM I feel like the early days of Android while iOS was on a whole different level...   my hands are tied to do anything I want...  and that is read occasional pocket article and some web and email... I use mobile gmail page on the browser, youtube web app works so so and pocket has no offline articles...    everything is so much slower and less than android at this point.  I will gladly return and revisit ubuntu in a month or so...  and report back here with my thoughts as well as any possible bug reports and such...

---

### Post by NiksaVel on 2016-04-26
> **Helsvell said:**
> This just sits at "Search usb, timeout set as 3600000 ms".  I guess I am missing the drivers package in ubuntu?

Have you tried ```
sudo apt-get install phablet-tools
``` ?

btw, how do you put tablet in fastboot mode?
Is this process the same for flashing ubuntu firmware?

---

### Post by NiksaVel on 2016-04-26
BTW...   here is another confirmation that it works okay to flash to android and back to ubuntu: [http://askubuntu.com/questions/761070/cant-install-ubuntu-touch-on-bq-aquaris-m10]("http://askubuntu.com/questions/761070/cant-install-ubuntu-touch-on-bq-aquaris-m10")

And more in depth tutorial: [http://a25.co/ubuntu-phone-how-to-install-android/]("http://a25.co/ubuntu-phone-how-to-install-android/")

---

### Post by NightCrawler on 2016-04-26
> **grahammechanical said:**
> If you flash the BQ Android image to that device then you get into the situation that all android users are in. Relying on the OEM to upgrade Android. Stick with Ubuntu and Canonical will send out Over the Air (OTA) updates to the OS every six weeks or so.

[https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1](https://wiki.ubuntu.com/Touch/ReleaseNotes/OTA-10.1)

Regards

I know that. But I bought the device in order to do certain tasks on it and currently Ubuntu does not deliver. I need certain things now, not in two months. As I mentioned earlier, I do plan to re-flash back to Ubuntu in the future, but for now, the device will work with Android. Additionally I could probably go for pure AOSP and compile it myself. I already replaced recovery with TWRP so, the updating point is getting kind of moot.

---

### Post by NightCrawler on 2016-04-26
> **NiksaVel said:**
> Have you tried ```
sudo apt-get install phablet-tools
``` ?

btw, how do you put tablet in fastboot mode?
Is this process the same for flashing ubuntu firmware?

Press Power + Volume Up for 10 seconds. When it vibrates it should reboot to fastboot. There will be a line at the bottom of the screen stating that it's in fastboot mode. Alternatively, if you enable developer mode in Ubuntu, you can connect it to your PC and execute 'adb reboot fastboot' to put it in fastboot mode.

---

### Post by NiksaVel on 2016-04-28
> **Helsvell said:**
> This just sits at "Search usb, timeout set as 3600000 ms".  I guess I am missing the drivers package in ubuntu?

Flashed mine to android as well....  was hanging on this too... my device had to be turned off. Than plugged in to USB after pressing "download" in the flash tool.

Works great, compared with the ubuntu android on the same device is incredibly fluid and responsive....   so it's not a hardware limitation...

---

### Post by NightCrawler on 2016-04-28
> **NiksaVel said:**
> Flashed mine to android as well....  was hanging on this too... my device had to be turned off. Than plugged in to USB after pressing "download" in the flash tool.

Works great, compared with the ubuntu android on the same device is incredibly fluid and responsive....   so it's not a hardware limitation...

Yes... It makes you understand how much optimization is still required in Ubuntu. Hardware is more than capable.

---

