---
title: "X10 Home Automation"
date: 2011-11-14
forum: The Cafe
---

### Post by whiskeylover on 2011-11-14
Any home automation geeks? I'm planning on buying a bunch of X10 modules for my home, and controlling them from an Ubuntu PC.

Anyone have any experience doing this? Has anyone done any interesting implementations of X10, like, maybe, turning on/off light bulbs to show the weather in binary format :D

---

### Post by Paqman on 2011-11-14
> **whiskeylover said:**
> I'm planning on buying a bunch of X10 modules for my home, and controlling them from an Ubuntu PC.


Trouble with this is you'll have to leave that PC running all the time. Unless it's very low power or it's going to be on anyway it could gobble up any efficiency savings through automation (assuming that's one of your goals, that is...)

I'm looking into X10 as the moment for some light home automation. Basically I want to monitor and automatically dump excess power from a PV array into either space or water heating. I've got an Arduino for the brains, and X10 has the advantage that it would avoid running extra wires around the house. The price is the main thing putting me off X10 though. X10 modules are pretty expensive for what they are.

---

### Post by whiskeylover on 2011-11-14
> **Paqman said:**
> Trouble with this is you'll have to leave that PC running all the time. Unless it's very low power or it's going to be on anyway it could gobble up any efficiency savings through automation (assuming that's one of your goals, that is...)

I'm looking into X10 as the moment for some light home automation. Basically I want to monitor and automatically dump excess power from a PV array into either space or water heating. I've got an Arduino for the brains, and X10 has the advantage that it would avoid running extra wires around the house. The price is the main thing putting me off X10 though. X10 modules are pretty expensive for what they are.

The PC is mostly on. Its a more of a geek toy than anything else, with a bunch of services running 24/7.

My objective isn't to save on electricity, but to do some geeky stuff and try to impress the wife.

---

### Post by sandyd on 2011-11-14
> **whiskeylover said:**
> Any home automation geeks? I'm planning on buying a bunch of X10 modules for my home, and controlling them from an Ubuntu PC.

Anyone have any experience doing this? Has anyone done any interesting implementations of X10, like, maybe, turning on/off light bulbs to show the weather in binary format :D
yup, but I don't use x10.

Each of the rooms has a keytag sensor that detects a signal from a keytag that all of the family members wear. As a result, lights turn on and off on their own without crappy infrared sensors, the garage doors close on their own, and no one needs to unlock/lock the back door.

The keytag itself is quite secure, it uses a PKCS#12 generated from a CA. As a result, each time the keytag is used, the PKCS#12 certificate is decrypted by the server. The signal is emitted via a bluetooth transmitter.

Its not particularly a long range signal, and its encrypted with the PKCS#12.

It was installed over a number of years, and by a datacenter technician (my sister), a brother who works for broadcom, and me, so don't expect it to be too easy.

---

### Post by whiskeylover on 2011-11-14
sandy, that sounds pretty awesome. Although I'm not sure I want to carry a keytag wherever I go. I'm usually in my boxers at home.

Also, X10 is pretty easy to implement by anyone. Its almost plug-n-play, and pretty well documented.

---

### Post by Paqman on 2011-11-14
> **whiskeylover said:**
> to do some geeky stuff and try to impress the wife.

In my experience those aren't necessarily complementary objectives ;)

---

### Post by sandyd on 2011-11-14
> **whiskeylover said:**
> sandy, that sounds pretty awesome. Although I'm not sure I want to carry a keytag wherever I go. I'm usually in my boxers at home.

Also, X10 is pretty easy to implement by anyone. Its almost plug-n-play, and pretty well documented.
:D
The system is integrated into the server monitoring / bandwidth monitering / power monitering core, so it takes extra effort. We added in the fun stuff afterwords.

---

### Post by whiskeylover on 2011-11-15
> **Paqman said:**
> In my experience those aren't necessarily complementary objectives ;)

Depends on the wife :)

> **sandyd said:**
> :D
The system is integrated into the server monitoring / bandwidth monitering / power monitering core, so it takes extra effort. We added in the fun stuff afterwords.

Geeky stuff is always fun, and worth the effort.

> **Paqman said:**
> The price is the main thing putting me off X10 though. X10 modules are pretty expensive for what they are.

Just bought a whole bunch of used X10 stuff on ebay (18 modules, 2 switches and two remotes) for US$65 including shipping. I think its a pretty good deal.

---

### Post by Bandit on 2011-11-15
I was thinking about home automation when ever I build or buy my next home. It can be made into a power savor system, but you would need to run it on a efficiant CPU like the ones in netbooks and run linux in CLI only. Which isnt a biggy at all. Just use your main system to interface it and keep the other housed somewhere dry and cool year round. :popcorn:

---

### Post by whiskeylover on 2011-11-15
Power consumption isn't a big concern for me. I mean how much power does a computer that is on 24/7 (but with monitor off) use anyways? I read somewhere that it's around $100/year average in the US. I spend more than that in a month natural gas during winter.

My primary objective is to be able to be able to control the devices from the computer (even remotely) so as to switch on/off devices from outside the home, do cool things like glow the blue light bulb when it is about to snow and the red light bulb when it gets too hot outside, open the car garage door from the smart phone... you get the idea.

---

### Post by Paqman on 2011-11-15
> **whiskeylover said:**
> Power consumption isn't a big concern for me. I mean how much power does a computer that is on 24/7 (but with monitor off) use anyways? I read somewhere that it's around $100/year average in the US.

Assuming about 100W average power, you'd be looking at 876kWh per year, so just multiply that by whatever you pay per kWh. Here in the UK the average home uses 4500kWh per year, so 876kwh is about a 20% increase in consumption. Regular grid electricity is also quite dirty, so you end up paying a lot of external costs over and above the price of the actual electricity.

Home automation doesn't require much smash, it seems like overkill to to me to have a PC running constantly just for that. If you're going to leave it on just for X10 jobs I'd go further and set up MythTV/NAS/print server/torrent box/BOINC/whatever to make it worthwhile. Better yet, get yourself a nice little Atom box, install Ubuntu server and let it rip. Linux MCE is a good distro if you want an all-singing all dancing system that can do home automation. It's based on Ubuntu.

---

### Post by Bandit on 2011-11-15
> **whiskeylover said:**
> Power consumption isn't a big ................. you get the idea.

Yea I was thinking about in home coms system with video for the home much like a intercom, in home temp adjustment based on outside temp, humidity, and time. Plus window automation built around clocks wake-up alarm, with morning new.. Ya know.. All the cool stuff Bill Gates has in his home. I think there is a You Tube video on it somewhere.

---

### Post by whiskeylover on 2011-11-15
> **Paqman said:**
> Assuming about 100W average power, you'd be looking at 876kWh per year, so just multiply that by whatever you pay per kWh. Here in the UK the average home uses 4500kWh per year, so 876kwh is about a 20% increase in consumption. Regular grid electricity is also quite dirty, so you end up paying a lot of external costs over and above the price of the actual electricity.

Home automation doesn't require much smash, it seems like overkill to to me to have a PC running constantly just for that. If you're going to leave it on just for X10 jobs I'd go further and set up MythTV/NAS/print server/torrent box/BOINC/whatever to make it worthwhile. Better yet, get yourself a nice little Atom box, install Ubuntu server and let it rip. Linux MCE is a good distro if you want an all-singing all dancing system that can do home automation. It's based on Ubuntu.


As I mentioned in my earlier post, that PC is used to run a lot more stuff.

---

### Post by sandyd on 2011-11-18
> **Paqman said:**
> Assuming about 100W average power, you'd be looking at 876kWh per year, so just multiply that by whatever you pay per kWh. Here in the UK the average home uses 4500kWh per year, so 876kwh is about a 20% increase in consumption. Regular grid electricity is also quite dirty, so you end up paying a lot of external costs over and above the price of the actual electricity.

Home automation doesn't require much smash, it seems like overkill to to me to have a PC running constantly just for that. If you're going to leave it on just for X10 jobs I'd go further and set up MythTV/NAS/print server/torrent box/BOINC/whatever to make it worthwhile. Better yet, get yourself a nice little Atom box, install Ubuntu server and let it rip. Linux MCE is a good distro if you want an all-singing all dancing system that can do home automation. It's based on Ubuntu.
Oh, and make sure you have backup power. Then, no more dirty electricity as it goes through the battery ;) .

---

### Post by Bandit on 2011-11-19
> **whiskeylover said:**
> As I mentioned in my earlier post, that PC is used to run a lot more stuff.

LOL if your like me, my PC runs 24/7 unless their is a thunderstorm :D

In the end, I guess better habits about turning off lights and other appliances would be more efficient in the long run, but home automation can be a cool topic to show friends where as talking about how tight wadded you are with electricity by turning off everything may just make them think your a tight wad.. LOL

I will go with home automation :D

---

