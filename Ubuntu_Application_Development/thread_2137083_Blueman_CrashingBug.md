---
title: "Blueman Crashing/Bug"
date: 2013-04-19
forum: Ubuntu Application Development
---

### Post by stevesy on 2013-04-19
Hi, hope its ok to post this here, thought you guys might be able to shed some light on why blueman keeps crashing on me.  I have a Dynamode dongle connected to my Dell Mini/Lubuntu 12.04.2 LTS and when I try to pair it with other bluetooth devices blueman hangs, as does the entire OS.  I tried to find support from developers on sourceforge but there's none available..  Not really sure where to go from here so if you guys have any idea what the problem is or could point me in the right direction that'd be great.  Can't wait to play with my new Logitech K810 keyboard! : /

Cheers : ]

---

### Post by stevesy on 2013-04-20
For newbies like myself who are experiencing similar difficulties have a look at:

[http://blog.projectnibble.org/2010/0...rt-came-to-be/]("http://blog.projectnibble.org/2010/08/08/how-ubuntus-broken-bluetooth-support-came-to-be/")
[ http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html]("http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html")

Might give you some ideas

---

### Post by stevesy on 2013-04-21
> **bkerensa said:**
> Why are you using Blueman versus the native Bluetooth settings in Ubuntu?

For whatever reason I thought blueman bluetooth manager was the native app.  Either way, whether I use it or bluetooth-applet both are crashing my system whenever I attempt to pair/connect devices.  Sometimes even the detection of my keyboard causes a black screen  with text output/crash.

---

### Post by bennypr0fane on 2013-04-21
Hello,

I have the same issue, posted here:
[http://askubuntu.com/questions/236188/why-do-i-only-hear-sound-from-the-speakers-with-a2dp-headset-connected](http://askubuntu.com/questions/236188/why-do-i-only-hear-sound-from-the-speakers-with-a2dp-headset-connected)
 Blueman crashes on me only whe I try to connect that headset with A2DP though, not with other devices. Maybe you wanna take a closer look at the event that triggers the crash? [Here]("http://bennypr0fane.trovebox.com/p/7/token-18134aab50")'s a screenshot of the apport notification that I get.
It would be helpful for someone to indicate how to get hold of a log file of a pairing attempt so we can post it here.
The reason I use blueman is because I have Lubuntu 12.04.
I do find it weird that the blueman homepage on sourceforge looks totally abandoned...

---

### Post by stevesy on 2013-04-24
> **bkerensa said:**
> Why are you using Blueman versus the native Bluetooth settings in Ubuntu?

I did a clean install of Lubuntu 12.04 and Blueman Device  Manager 1.23 is the only bluetooth software that comes with it.  I'm not sure what you mean by native bluetooth settings, as blueman is all I've got. Can you please explain? Also, gnome-bluetooth does not ship with Lubuntu so I was wrong about it/bluetooth-applet being native.

---

### Post by stevesy on 2013-04-27
Finally got bluetooth working!  I decided to return my Dynamode dongle   and swapped it for a slightly less cheapo dongle, a Hantol v2.0 which is   around &#8364;10/$13. This solved the system hang problem.  So, if you're   experiencing crashing like I was then from my experience it's most   likely the dongle you're using.  Maybe consider upgrading it.  

I  used blueman bluetooth manager 1.23 that ships with Lubuntu 12.04 to   pair/connect my bluetooth devices.  I'll tell you the process I went   through to get my K810 keyboard working..

Open a terminal (ctrl & alt & T) and enter in *blueman-manager* to open up the bluetooth manager.

Click "enable bluetooth" on the gui that pops up.

Make  sure your K810 keyboard is discoverable and then click on the  "search"  button.  When the keyboard is detected it'll appear on the  devices  list.  Once it does, highlight it and click on "setup" to  access the  setup assistant and get pairing set up

Click on custom  pin/passkey code and enter whatever you like (e.g.0000 )  then quickly  enter this same code into the K810 keyboard (and hit  enter).  You may  need to try this a few times before it works, I got  "pairing failed"  quite a bit before succeeding.  Power cycling the  keyboard and pc may  also be worth a go if you're having no luck  pairing.  Once paired and  the device added click on "input service" and  you're good to go.  If you  trust the device which I assume you will as  it's your keyboard, click  on the yellow star to add it as such. Done.   

If none of that works try another app e.g. gnome bluetooth and/or command-line workarounds like [http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html](http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html)

Just to mention, PC-Smartphone bluetooth works fine for me.
Still looking into Keyboard-Smartphone, devices pair but won't connect.

Hope this is of some help to those suffering from the same headache as i was.

---

