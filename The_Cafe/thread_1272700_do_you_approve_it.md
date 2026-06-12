---
title: "do you approve it?"
date: 2009-09-22
forum: The Cafe
---

### Post by cosine352 on 2009-09-22
I am sitting here at JFK international airport. The wireless internet connection is free only for first 20 mins after you connect. They must be restricting the time by accessing the mac address. So I changed my mac address and I connect to the internet again. Now I have made a script for all this and running every 19 minutes. So I am always connected. Do you guys think I am doing something really wrong?

---

### Post by The Toxic Mite on 2009-09-22
Well, you are kinda "dodging the fare", as a trainspotter would say, but the script sounds neat.
 
So half yes/half no for me :P

---

### Post by SunnyRabbiera on 2009-09-22
Well how much is it after 20mins?
20minutes for free is pretty good, more time then I get at the library computer.

---

### Post by bodyharvester on 2009-09-22
kudos for the script and the creativity :D

care to share the script? id love to see it :)

at my local library you get an hour free, and after that you just ask for another hour and they give it to you

---

### Post by cosine352 on 2009-09-22
well the cost is around $8 for 24 hour. I am just killing time here (2 hour more. Have been for 90 minutes).

---

### Post by The Toxic Mite on 2009-09-22
Why are you at JFK by the way? Going somewhere exotic??? :P

---

### Post by Mobil1 on 2009-09-22
Yep I agree with bodyharvester that's just damn cool and I'd love to see the script too :)
[URL="http://ubuntuforums.org/member.php?u=869539"]
[/URL]

---

### Post by SunnyRabbiera on 2009-09-22
> **cosine352 said:**
> well the cost is around $8 for 24 hour. I am just killing time here (2 hour more. Have been for 90 minutes).

$8 a day?
Thats actually not too shabby for something like that, I have seen connections cost way more then that per hour.
What speeds does it get, dial up quality?

---

### Post by NormanFLinux on 2009-09-22
Connecting to a public wireless system is easy enough. As long as you sit close where the signal is strongest.

---

### Post by Bigtime_Scrub on 2009-09-22
Here at San Antonio International is is free 24/7/365. As it should be, public connections usually stink from my experience anyway.

---

### Post by haemulon on 2009-09-22
20 min. is not much internet time, but enough to check email and flight information.

So you've done some cheating here.

At our library if you use their computers it's a 1 hour limit.

If you bring your laptop and connect to the wireless there is no time limit.

I don't have much sympathy for the airport, as everything there is always overpriced anyway, but you are still cheating. Now can we see the script?

---

### Post by cosine352 on 2009-09-22
I am going India. 

For those interested here is the three line from my script
> sudo ifconfig wlan0 down
sudo macchanger -e wlan0
sudo ifconfig wlan0 up

you need to change 'wlan0' to the proper interface you are using. you also need to install 'macchanger'

---

### Post by NormanFLinux on 2009-09-22
You can also do it from your network manager GUI. It will scan for networks and tell you whether they are open or encrypted.

---

### Post by bodyharvester on 2009-09-22
> **cosine352 said:**
> I am going India. 

For those interested here is the three line from my script


you need to change 'wlan0' to the proper interface you are using. you also need to install 'macchanger'

thank you! have a good time in india!

---

### Post by darthmob on 2009-09-22
Nothing wrong with that in my opinion.

---

### Post by Mobil1 on 2009-09-22
> **cosine352 said:**
> I am going India. 

For those interested here is the three line from my script


Simple but effective - thanks and I hope you enjoy your time in India. Have a safe journey :)

---

### Post by SunnyRabbiera on 2009-09-22
> **Bigtime_Scrub said:**
> Here at San Antonio International is is free 24/7/365. As it should be, public connections usually stink from my experience anyway.

If the rate is fair though, I would do it.
Trust me $8 a day is cheap compared to some of the wireless plans out there.

---

