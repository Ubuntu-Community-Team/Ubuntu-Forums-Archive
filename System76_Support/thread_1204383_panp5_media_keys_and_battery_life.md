---
title: "panp5: media keys and battery life"
date: 2009-07-04
forum: System76 Support
---

### Post by Sarai the Geek on 2009-07-04
First off, I want to just say that I LOVE my new Pangolin, and have had no problems whatsoever with it. Been very impressed with the way everything works out of the box (even after I replaced Ubuntu with Linux Mint), the construction feels solid, and the screen is easily the most gorgeous I have seen in all my years of computing.
I just have a few questions:

1.) How would I go about changing the programs that the three media keys in the top-left corner of the keyboard control? By default the 1st opens Thunderbird, the second opens the Thunderbird Calendar, and the last one opens Rhythmbox. I don't use any of these programs, so I would like to repurpose those keys. I tried using "keyboard shortcuts" but it would not recognize key-presses from those keys.

2.) is there an extended life battery available anywhere? I know sys76 offers an extra battery, but what I am looking for is a replacement battery that has a longer life- right now the computer does not stay alive very long on battery power, and as a college student dragging around that hulky ac/dc cord is, well... a drag. ;)

---

### Post by betrunkenaffe on 2009-07-05
1) Try changing preferred applications, maybe that will do it. System->Preferences->Preferred Applications.

2) Not that they have revealed.

---

### Post by miniyak on 2009-07-06
this works on my pangolin so i would have to assume that this is something that s76 drivers would take care of

did you have any luck getting the s76 drivers in mint? I read that it is possible but there is tweaking involved

You can also try changing the keyboard in the keyboard layout section of keyboard settings. Mine says "generic 105-key(intl)". I have a feeling that this is the default keyboard recognized. So you may want to find model# related info about the pangolin's keyboard and pick a similar/same model from the drop down list.

i would be more concerned about getting the drivers to work though because the "silent mode" button (provided by M key) is more useful then one would think. 

silent mode scales the cpu to 1.6ghz and turns down the fan, reducing noise and power consumption. Battery life still sucks but this feature does make getting those precious extra couple of minutes a little easier.

On the note of the battery, i going to have to say that the a extended life model will not be offered because of the lid is situated & the design of the latching system (too loose to be a foot). That is no official statement of course, just a joe smoe sticking his feet in to the shoes of the manufacturer. So a second battery is the way to go if you want more life. For some uses im going to have to say this would beet carting the power brick around and its what im going to do when i can justify spending 130$ on extra mobility.

---

### Post by Sarai the Geek on 2009-07-06
> **miniyak said:**
> this works on my pangolin so i would have to assume that this is something that s76 drivers would take care of

did you have any luck getting the s76 drivers in mint? I read that it is possible but there is tweaking involved.
Out of the box, they installed fine but the program refused to load, saying it only runs on Ubuntu 8.10 and older. I haven't put much effort into getting them to work with Mint. The webcam seems to work without them and I really care much about the fingerprint. My python skillz are fairly elementary, so I'm not sure I'd have much luck. 

> **miniyak said:**
> You can also try changing the keyboard in the keyboard layout section of keyboard settings. Mine says "generic 105-key(intl)". I have a feeling that this is the default keyboard recognized. So you may want to find model# related info about the pangolin's keyboard and pick a similar/same model from the drop down list.

i would be more concerned about getting the drivers to work though because the "silent mode" button (provided by M key) is more useful then one would think. 

silent mode scales the cpu to 1.6ghz and turns down the fan, reducing noise and power consumption. Battery life still sucks but this feature does make getting those precious extra couple of minutes a little easier.

On the note of the battery, i going to have to say that the a extended life model will not be offered because of the lid is situated & the design of the latching system (too loose to be a foot). That is no official statement of course, just a joe smoe sticking his feet in to the shoes of the manufacturer. So a second battery is the way to go if you want more life. For some uses im going to have to say this would beet carting the power brick around and its what im going to do when i can justify spending 130$ on extra mobility.


Bummer about the battery, but I can see what you are talking about with the extra space needed. I did see a computer (I believe it was a compaq) with a similar layout that had an extended life battery- instead of taking up more space horizontally, they went vertical with it, adding about half an inch to the back end of the computer. The result was that it was a little tilted on a flat surface and probably not the most comfortable on the lap.

---

### Post by miniyak on 2009-07-07
Just a test (failed see next post... i having a similar problem now that ive messed with things...)

open terminal, type gconf-editor

the select desktop, gnome, keybindings, then double click allowed keys

 *Im not sure if this will work, but you can just remove the entry if it fails, personally im trying to get the Esc key to close programs so that is how i found this. Still you need the right key value i think and in the case of the escape key i think there are other conflicts* 

click add ( in allowed keys dialogue) then type XF86Mail (this is the value of the button with the mail symbol on my pangolin)

after this test if it will work in the shortcut settings. If it does ill post the other values if needed.

---

### Post by miniyak on 2009-07-07
sorry, the allowed keys setting does something else.... the description say its for locking systems down so only a few keybindings are allowed which makes more sense, the name was deceiving... :|

---

### Post by Sarai the Geek on 2009-07-07
> **miniyak said:**
> sorry, the allowed keys setting does something else.... the description say its for locking systems down so only a few keybindings are allowed which makes more sense, the name was deceiving... :|

Indeed the name is a little decieving... :(

---

### Post by thomasaaron on 2009-07-08
This thread is becoming a little murky and difficult to follow. But if you're wanting to assign the key to do something particular, you can use System > Preferences > Keyboard Shortcuts and assign it to do any of the listed functions.

If you want it to do a customized command, you can open gconf-editor and go to apps > metacity > keybinding commands. In the right column enter the command you want it to perform. For instance, let's say you've entered the command "gedit" to the right of command_1. Gedit is the default text editor in Ubuntu.

Then go to apps > metacity > global keybindings. Find command_1. To the right of it, assign a key combination.

You should be cautions while doing this. It's possible to hose your existing keybindings.

---

### Post by miniyak on 2009-07-09
*"You should be cautions while doing this. It's possible to hose your existing keybindings."*

 lol, yup, that is what happened to me, I would stay away from gconf until you find a more definite solution presents its self, unless you have no keybindings to lose. I thought mistakes would be easily fixable but im still figuring out how to get my keybindings back. (for me, In the desktop area the custom keys say they have no schema. All other shortcuts are still working however)

---

### Post by thomasaaron on 2009-07-09
miniyak, exactly what keys have lost their bindings. I'll try to help you get them back.

---

### Post by miniyak on 2009-07-09
i had crl + alt + *x*(variable letters) set up for my most used programs like firefox for instance was set up as "crl alt u" and Miro "crl alt m"

only these customizations disappear when i added and entry to the "allow keys" function in gconf. i have since removed the entry and my key bindings are still missing.

---

### Post by Sarai the Geek on 2009-07-09
Well, I got the first two keys to do what I wanted them to, the third one is a little more stubborn, apparently it's wired a little differently (keytouch showed it to be part of a separate input device) perhaps because it's supposed to talk to the hardware instead of the software. Dunno. In any case, I'm satisfied with it the way it is, and don't have any real desire to do much more because I also use a lot of other keybindings and don't want to lose them!

---

### Post by miniyak on 2009-07-10
the third key is supposed to put the laptop into silent mode. so i would be surprised if it is wired to a controler for cpu and fan speed.

Have you checked you cpu's clock speed after holding down the third key?

---

### Post by Sarai the Geek on 2009-07-10
> **miniyak said:**
> the third key is supposed to put the laptop into silent mode. so i would be surprised if it is wired to a controler for cpu and fan speed.

Have you checked you cpu's clock speed after holding down the third key?

Well, I didn't check the clock speed, but when I push it my cpu usage by percent jumps significantly (40% to 80-90%) even though I haven't done anything on the computer. I will go and check the clock speed now to be sure but I'm guessing the button does have some effect. It also explains why sometimes my cpu usage is way higher than it should be- it never occured to me that pushing that button would have that sort of effect. There should be an indicator to show whether the cpu is in silent mode.

---

### Post by miniyak on 2009-07-10
I was unaware of silent mode the first couple of weeks after i got my pangolin. Until I went back and read through the manual for info on battery usage. lol

I agree about the idea of an indicator, in the form of discrete physical switch (also ones for bluetooth and wifi). The idea of more LED indicators defeats the purpose of stringent power conservation in my mind even though they barely take up any power. 

your cpu should clock at 1.6ghz in silent mode. This would make your cpu usage look higher then normal

---

### Post by Sarai the Geek on 2009-07-10
> **miniyak said:**
> I was unaware of silent mode the first couple of weeks after i got my pangolin. Until I went back and read through the manual for info on battery usage. lol

I agree about the idea of an indicator, in the form of discrete physical switch (also ones for bluetooth and wifi). The idea of more LED indicators defeats the purpose of stringent power conservation in my mind even though they barely take up any power. 

your cpu should clock at 1.6ghz in silent mode. This would make your cpu usage look higher then normal

How do you check the clock speed? According to a google search, hwinfo --cpu | grep Clock is supposed to show it, but that value is always at 1000mhz, which is less than you indicated even for silent mode clock speed?

---

### Post by miniyak on 2009-07-10
right click on a panel from the desktop (in mint or ubuntu, bottom or top will work all the same) 
select add to panel
select cpu frequency scaling monitor

that should give speeds and allow control of cpu governor

---

### Post by Sarai the Geek on 2009-07-10
> **miniyak said:**
> right click on a panel from the desktop (in mint or ubuntu, bottom or top will work all the same) 
select add to panel
select cpu frequency scaling monitor

that should give speeds and allow control of cpu governor

Nice! When I set it to 1.67GHz, it goes down to 1.33GHz when I push the button! Now I've got it set on 2.17GHz and when I hit the button it goes down to 1.67. I think I'm going to add a monitor to my conky so I can tell when powersave is on. :)
I wonder why it was set so low out of the box?

---

