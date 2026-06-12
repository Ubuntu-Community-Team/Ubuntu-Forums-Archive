---
title: "Which smartwatch/exercise bands work with Ubuntu?"
date: 2015-11-16
forum: The Cafe
---

### Post by Dragonbite on 2015-11-16
I don't have one, but was wondering if there are any particular exercise bands or smart watches that works with Linux, or specifically Ubuntu?  

I do see most of them work more closely with a smartphone, but I don't have one at this time.

So I am curious which, if any, works with Ubuntu Linux?

(a follow-up question could be what about programming for the smartwatches/exercise bands but that's secondary..)

---

### Post by Dragonbite on 2015-11-20
Bump!

---

### Post by blm-ubunet on 2015-11-20
The Fit-Bit (heartrate) wrist exercise band model *works* with ubuntu.
But working has a very limited meaning.
Ubuntu can only download data.

Everything goes through the cloud, their cloud.
You have to use a proprietary application **once** (Windows/Android/Mac) to create the online account.
You can not create an account without the device being discovered..
This links the device to your account/login & links the bluetooth interface to your phone (if you used your phone).
The device seems to be able to use ntp via the paired phone to sort its RTC.
You do not need to use the phone or the app again.

The bluetooth dongle works in ubuntu & you can download the data from band & upload to their server using a python script. You use webbrowser to login & see your info.

You can keep a copy of the data or just download to private file but there is no tool/program to make use of it yet.
Don't think any of the exercise device makers want the users having/using their own data except via their web servers.

---

### Post by Dragonbite on 2015-11-20
That last part about the makers not wanting users to have their data except via the associated website is an accurate assessment. I wonder if any of them are different?  Maybe some of the smaller ones?

---

### Post by Bucky Ball on 2015-11-20
By doing a little research you will discover a few that work with Ubuntu. The Fitbit HR also, but as above by the looks of it. I've heard they don't react well to sweat and this can screw with the heart rate monitor. Anyhow, have a sniff around the interwebs and you'll find more info on this and others.

---

