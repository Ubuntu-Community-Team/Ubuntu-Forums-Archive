---
title: "Live session can kill battery in a few seconds"
date: 2017-03-03
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-03-03
While looking at lack of internet here with some Intel wireless devices I broke out 2 add. laptops not in every day use. Typically I leave laptops at around 50-60% charge when not using so was surprised when both went to critical battery charge while in a live session for several minutes. (didn't actually look at charge status to start so thought maybe they'd discharged over time.) Was using them on battery power rather than ac

Tried again with a live session tonight on my latest laptop (windows only) as I knew it also had an Intel wireless device. On bootup to live session the laptop was at 55%. After a couple of minutes & _1 log out &  in_  it went to 5% in just a moment or two. 
Seems like rather poor/dangerous  behavior, not sure if I'll even bother with 17.04 again as don't want to put hardware at risk. So just thought I'd mention in case this arises for others.

2 screens attached that show, the line isn't as relevant as the data points in 1st. The 2nd has time frame expanded & also shows recharging as I needed to plug in to get screens.

---

### Post by VMC on 2017-03-03
Isn't linux distros in general notorious for burning thru battery life? I have read countless stories regarding battery drain. I have a desktop, so that is one issue I don't have.

---

### Post by mc4man on 2017-03-03
> **VMC said:**
> Isn't linux distros in general notorious for burning thru battery life? I have read countless stories regarding battery drain. I have a desktop, so that is one issue I don't have.
Not 45+% in about 30 secs or less, that's purely some Ubuntu bs. I do wonder where all that energy went but not too inclined to investigate further

---

### Post by ventrical on 2017-03-04
@mac

I did an install of ubuntu-mate 16.04 about a week ago on a Toshiba Satallite Centrino Mobile. After the install an indicator came up and told me my battery may be broken and that it was stuck on 5.4%. It was working swell with Ubuntu Unity 16.04. (this is just a laptop I use for testing). [s]ubuntu-mate killed the power somehow but is was a bs report (false positive)[/s]. I  booted into live-session 17.04 ubuntu-gnome and now it reports the battery is charging. I hope it is not busted in anyway. I'll get back to see if it gets fully charged. It appears that while installing ubuntu-mate that it put in some software to block the charging process even when the PC was off. This is scary. I wasn't going to report anything until I had seen your post.

regards

---

### Post by ventrical on 2017-03-04
Sure enough the indicator light for the battery is now green.

I'll pull the power cable and see how long it stays up in live mode.

Edit:

It took just a little over 8 minutes to drop to 12% capacity from 100% charge using ubuntu-gnome 17.04 live session.

Again:

Mate 16.04 'full install' reports broken battery and blocks it from charging when turned off.
gnome3 17.04 zesty 'live' reports it is charging , fully charged with green light indicator and takes 8 minutes for low battery warning.

will try ubuntu-unity stack.

Regards..

---

### Post by ventrical on 2017-03-04
I used older 14.04.1 and ran it down until it crash to black screen. Gave me 25 minutes.[s] I think mate really bricked the battery[/s] but I am trying some other tests.

---

### Post by ventrical on 2017-03-04
> **VMC said:**
> Isn't linux distros in general notorious for burning thru battery life? I have read countless stories regarding battery drain. I have a desktop, so that is one issue I don't have.

My lenovo thinkpad T61 has been going for an hour with 4 hours left on 16.04 ubuntu-desktop stack. That thing is a workhorse with an SSD drive. After macs' post I am reluctant to test on my solid , reliable harware because of how Mate apparently bricked my battery on my Toshiba. (I am only declaring an assumption at this point). I get three different readings from three different distros. I guess that says a lot but I am trying another method.

edit: @vmc
T61 ran 2 hours with some youtube time and I still have 1 and1/2 hours )so just saying that not all (linuxes) are battery killers.

@mac4man.. Thanks for the heads up on this!

Regards..

---

### Post by jbicha on 2017-03-04
The warning you saw in Ubuntu MATE is probably from [mate-power-manager]("https://github.com/mate-desktop/mate-power-manager/blob/master/src/gpm-manager.c#L1093")

That warning might not exist in GNOME or Unity any more.

How old is that computer? Batteries eventually do wear out.

---

### Post by ventrical on 2017-03-04
> **jbicha said:**
> The warning you saw in Ubuntu MATE is probably from [mate-power-manager]("https://github.com/mate-desktop/mate-power-manager/blob/master/src/gpm-manager.c#L1093")

That warning might not exist in GNOME or Unity any more.

How old is that computer? Batteries eventually do wear out.

Yes , I realize that batteries wear out. It was working fine with unity 16.04 until I hard installed Mate. I am still testing this case and will report back.

The warnings do not exist in gnome or unity - correct.

---

### Post by mc4man on 2017-03-04
> **jbicha said:**
> T
How old is that computer? Batteries eventually do wear out.
One laptop is 3.5 yrs, 1 2.5 yrs., 1 virtually new. In all cases the batteries perform well with 14.04, 16.04 & windows 10 respectively .

It seems hard to fathom how they could be discharged so quickly without obvious effects, it's 'slightly' possible that they actually weren't but - 
In all cases, if shutdown & not connected to ac then none of the laptops would power up until they were on ac.
In all cases the laptops spent an appropriate time recharging.

In an 'oddity' one laptop would not recharge until restarted on ac, i.e. after incident > shutdown > connect to ac it did not charge. (until restarted to 16.04.

I may try the oldest machine again, the newest one will not (the new one has a built-in battery which is becoming more popular.. & not easily replaced

The method here to reproduce is - 
Boot up to Ubuntu live session on battery.
Connect to wifi, check if internet access is available
If there is internet then log out/in to see if access survives (never does with 3 Intel wifi devices over last 6+ weeks or so, wifi connects fine, just no access
If 1st. ck. on access fails then configure network manually, often that provides access. Then log out/in to see if it survives (never does ...

The apparent draining of battery always occurs in the session's 2nd log in.

---

### Post by ventrical on 2017-03-04
> **mc4man said:**
> 

The method here to reproduce is - 
Boot up to Ubuntu live session on battery.
Connect to wifi, check if internet access is available
If there is internet then log out/in to see if access survives (never does with 3 Intel wifi devices over last 6+ weeks or so, wifi connects fine, just no access
If 1st. ck. on access fails then configure network manually, often that provides access. Then log out/in to see if it survives (never does ...

The apparent draining of battery always occurs in the session's 2nd log in.

Thanks for specific test case . will give it a whirl.

---

### Post by ventrical on 2017-03-04
HP 2000 non-IntelMobile

logout/login
Remembers wifi.
Got access.
Remembers key.
Remembers ff last page.

As I recycle videos through youtube the power indicator will oscillate between 3hrs:55mins and 4hrs:20mins.

ubuntu-gnome 17.04 live from yesterday.

Running over 1/2 hours now with 4hrs10mins left.

Regards..

---

### Post by ventrical on 2017-03-04
lenovo T61 Intel Wireless Pro


login/logout
Remembers Wifi
Remembers access
No power drain.
ubuntu-gnome 17.04 live session

failed to duplicate problem

---

### Post by mc4man on 2017-03-05
> **ventrical said:**
> lenovo T61 Intel Wireless Pro


login/logout
Remembers Wifi
Remembers access
No power drain.
ubuntu-gnome 17.04 live session

failed to duplicate problem

Just checked again on a lenovo y580
Booted up to live session at 54%
Set panel icon to show percentage
Connected to wifi, checked, had my 1 time internet access, did a little browsing, charge down to 51%
Open software sources, enabled repos, reloaded
Was about to install powertop, charge dropped from 50% to 5%
Shutdown, now laptop will not power on (ac not connected

I may see if the guy up the street can read the amount of charge left in battery as have hard time seeing how it can be discharged that much at once.
This is with thurs. image, will have to try fridays later.

---

### Post by ventrical on 2017-03-06
This happened to me on a Dell laptop during Oneric Ocelot testing.  It killed battery. I drained it out as much as I could and could only get 64%. The jury is still out on current problem with my Toshiba and why the battey got killed on that one.  I have  to do a couple more tests. There is a little motherboard in a lot of those batteries. They are contolled by software. If  a wrong firmware is used it can send a HID interrupt vector to block or malign the IRQ. So it has to be cleared by physically disconnecting the battery powerlines from the motherboard on the battey component and resoldering them back in.

> 
  I have  to do a couple more tests. There is a little motherboard in a  lot of those batteries. They are contolled by software. If  a wrong  firmware is used it can send a HID interrupt vector to block or malign  the IRQ. So it has to be cleared by physically disconnecting the battery  powerlines from the motherboard on the battey component and resoldering  them back in.

Did not work in this test case.

---

### Post by ventrical on 2017-03-07
I sent this link [https://www.maximintegrated.com/en/products/power/MAX1781.html](https://www.maximintegrated.com/en/products/power/MAX1781.html)

It is a eeprom/micorcontroller on my Tosshiba battey. Not sure if the forums are still being rebuilt.

---

### Post by ventrical on 2017-03-07
here is pic of eeprom/microcontroller.

---

### Post by ventrical on 2017-03-07
[s]So if there is a problem with MATE 16.04.2 it is because of this:[/s]

> 
 The 8-bit, RISC microcontroller core has an integrated 12k bytes of user programmable EEPROM, which provides battery-pack designers with complete flexibility in developing fuel gauging and control algorithms


As I keep working on my test case I find it only fair at this point to put this up concerning eeproms:

> 
There are two limitations of stored information; endurance, and data retention.
 During rewrites, the gate oxide in the [floating-gate transistors]("https://en.wikipedia.org/wiki/Floating-gate_transistor")  gradually accumulates trapped electrons. The electric field of the  trapped electrons adds to the electrons in the floating gate, lowering  the window between threshold voltages for zeros vs ones. After  sufficient number of rewrite cycles, the difference becomes too small to  be recognizable, the cell is stuck in programmed state, and endurance  failure occurs. The manufacturers usually specify the maximum number of  rewrites being 1 million or more.[SUP][[5]]("https://en.wikipedia.org/wiki/EEPROM#cite_note-5")[/SUP]
 During storage, the electrons injected into the floating gate may  drift through the insulator, especially at increased temperature, and  cause charge loss, reverting the cell into erased state. The  manufacturers usually guarantee data retention of 10 years or more.[SUP][[6]]("https://en.wikipedia.org/wiki/EEPROM#cite_note-6")

[/SUP][SUP]


So a laptop's eeprom in 2007 could be ready to regress in 2017.

 


[/SUP]

---

### Post by ventrical on 2017-03-07
> **mc4man said:**
> 
I may see if the guy up the street can read the amount of charge left in battery as have hard time seeing how it can be discharged that much at once.
This is with thurs. image, will have to try fridays later.


I ran my Toshiba to fail then took the battery out and cracked it open. It is full 12.57 volts. I  am running it down using a 12volt fan. Disconnecting the microcontroller board did not fix it. The geometry is still way off. When batt is dry I will boot up with 17.04 gnome-desktop and see whats happens. There may be a reset/fail when battery in null.If the eeprom is shot then not much that can be done.[s] I am making a second declaration that during the install of 16.04.2 MATE that it attempted to correct the data in the eeprom of the controller board unless it is just coincidence that the battery ready to fail just while I was occasioning to install 16.04.2 MATE.  I will also declare that IF the eeprom is proprietary AND has a proprietary failsafe AND Mate attempted to talk to proprietary software THEN failsafe FUNC engaged ELSE eeprom fail/batt-fail. This could be systemic in development as convergence tries to optimize power reduction but I can't document that specifically.[/s]

Update-edit
I ran  the 12 volt fan for over 6 hours and it was still ripping wind. (I may have to use bigger fan to drain these batteries).  The batteries are anything but bad. The Toshiba is currently charging. Draining the batteries somewhat did affect the geometry to some degree. I think I may still have to completely drain the battery using a larger motor.

Update-edit 2
The Toshiba laptop lasted 1 and 1/2 hours with screen always on. 
Now will find larger  fan motor, discharge completely and then try charging again.

---

### Post by ventrical on 2017-03-07
I seen this .. hmmmm.....

[https://ubuntuforums.org/showthread.php?t=2144463](https://ubuntuforums.org/showthread.php?t=2144463)

---

### Post by ventrical on 2017-03-07
Doing my second *full* drain test.  Lithium batteries are very resilient. 

edit: 2 fans quit .. the third ready to go. currently 2.56 volts. Thats the cut off point.

edit: bricked the battery.



[URL="https://www.youtube.com/watch?v=HhYbbSpi4Lg&feature=youtu.be"]https://www.youtube.com/watch?v=HhYbbSpi4Lg&feature=youtu.be
[/URL]

---

