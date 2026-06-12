---
title: "Finger Print Reader"
date: 2009-04-14
forum: System76 Support
---

### Post by sngltrk on 2009-04-14
I have been following the guide posted on the System76 site ([http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)) to install the finger print reader.  When I try to install libfprint the wget step fails to connect (wget [http://projects.reactivated.net/snapshots/libfprint/libfprint-20080810-6b8b17f5.tar.bz2](http://projects.reactivated.net/snapshots/libfprint/libfprint-20080810-6b8b17f5.tar.bz2)).  I tried installing libfprint-0.0.4 from the fprint project page with no success.  Have you created at deb file to install the fingerprint reader?  Any help you could provide would be appreciated.  I have a System76 laptop, model: panp4n.

Unrelated questions.  What battery life should I expect out of this laptop?  What can I do to extend the life beyond lowering lcd brightness and limiting CPU speed.

Thanks,
Sngltrk (Jack)

---

### Post by thomasaaron on 2009-04-14
The proper drivers are already installed on your computer. To be sure, go to System > Administration > System76 Driver > Install > Install.

Now, follow the instructions here...
[http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

Then go to Applications > Accessories > Fprint project.

---

### Post by sngltrk on 2009-04-15
Thanks that did the trick.  I was able to register and verify a fingerprint.  I'll try modifying PAM next.

The second question I had was on battery life a and ways to improve it.  Any thoughts?  See bottom of original post.

Thanks,

Jack

---

### Post by thomasaaron on 2009-04-15
Battery life is largely dependent on how you are using your computer. If you typically use programs that tax your cpu, your battery will be used up more quickly than it will if you are using lighter programs. For example, playing a DVD will use your battery much more quickly than, say, a word processing program.

Here are a few things I know of that can maximize your battery life.

1. SCREEN BRIGHTNESS
Go to System > Preferences > Power Management. Under the AC tab, set your brightness. Under the Battery Tab, select the checkboxes labled: "Dim Display When Idle" and "Reduce Backlight Brightness."

2. POWERTOP
Go to a terminal (Applications > Accessories > Terminal) and install powertop by running this command: sudo apt-get install powertop
Then start powertop by running this command: sudo powertop
Powertop will present you with opportunities to press keys that will kill un-needed services. You must leave the terminal open to keep powertop running, but you can minimize the terminal so that it isn't visible.

3. STARTUP PROGRAMS
Go to System > Preferences > Sessions > (Startup Programs Tab) and uncheck any startup sessions you do not need. It is not a good idea to uncheck startup programs unless you are sure you really do not need them. Some that are generally safe to remove are: Bluetooth Manger, Evolution Alarm Notifier, Remote Desktop, Tracker, Tracker Applet, and Visual Assistance.

4. SEARCHING AND INDEXING
Go to System > Preferences > Searching and Indexing and select the checkboxes labled: "Disable All Indexing When on Battery" and "Disable Initial Index Sweep When On Battery."

---

### Post by Vadi on 2009-04-15
I'd add the CPU frequency applet to that list.

---

### Post by thomasaaron on 2009-04-16
Yes, I would too! I thought I had it on there #-o

---

### Post by rabbit6667 on 2009-04-16
hey while running the tutorial it wont let me log on to the server to install any thing after the source forge anybody else have this problem? is there a different database now?

---

### Post by thomasaaron on 2009-04-16
If you have a newer System76 computer, you don't have to install anything. Just follow the instructions here...

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

---

### Post by rabbit6667 on 2009-04-17
ok so when i open the gui to input my finger prints it says error unable to find enrolled finger prints and simply wont let me enroll anything this is the last road block any thoughts?

---

### Post by thomasaaron on 2009-04-17
Hmmm... 

Try varying your... um... swipe speed. 

(Clarification: Are you saying you have been unable to enroll any fingerprints, or that you have some enrolled, but when you try to swipe a fingerprint to authorize something it says "can't find any"?)

---

### Post by TheBuzzSaw on 2009-04-17
What if you cut your finger, and it scars over???

---

### Post by thomasaaron on 2009-04-20
Then you will never be able to get into your account again. :popcorn:
That's the beauty of biometrics.

Actually, that's why you should register multiple fingers.

---

### Post by TheBuzzSaw on 2009-04-22
> **thomasaaron said:**
> Then you will never be able to get into your account again. :popcorn:
LOL! sux2Bme I guess...

I've never been big on the whole fingerprint reader technology gig. Bigger passwords for me!

---

