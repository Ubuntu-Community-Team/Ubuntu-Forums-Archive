---
title: "No audio out of output"
date: 2012-02-10
forum: Ubuntu Studio
---

### Post by grimmson on 2012-02-10
Hello all. It's been a nightmare trying to set studio up. I'm no a nood to linux but but I don't know JACK (ha ha). I'm a noob to midi or other advanced audio configs. I'm running studio 11.10 with all updates. I don't think Jack liked my onboard intel audio chip so I picked up a Diamond Xtreme sound 5.1 (C-media CMI8738-LX chipset.) I dualboot Ubuntu / ubuntu studio and in ubuntu I had to select analog 5.1 to get full audio out. I have JACK setup to run without xruns (I think) and everything appears correct in patchage.

I think I need to select 5.1 audio in studio (like regular ubuntu) but when I go to applications/settings/ Linux Audio settings it won't start. If JACK is running it will tell me to stop JACK and if Qjackctl is open but jack is stopped Linux audio says "You have to have a saved / stopped studio running to change something or other." 

I know the problem is me but I'm screwd without guidance. Please throw me a bone.

---

### Post by sgx on 2012-02-10
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

read the tutorials/screenshots at the 4th and 8th links.
If pulseaudio is running, or certain web applications,
your access to jackd can get blocked. Command:

killall pulseaudio 

Cheers

---

### Post by Noobuntu79 on 2012-02-10
That link helped me massively in several areas!!  It directed me to this one anyway - perhaps the best explanation of QJack functionality and setup I've found....

[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

---

### Post by grimmson on 2012-02-11
Thanks for the help guys. It looks like either updates or adding a second user borked my system. Did a clean install last night and had sound three minutes after that. Wish it didn't take 16 hours to figure that out. To anyone reading this do yourself a favour. Install, don't update, tinker until it works. Then you can break your system with updates if you want. 

P.s. If anyone wants to explain how adding users and downloading updates will break studio let me know. I'm sure the next guy would love to find a post on it to avoid pitfalls. Thanks again.

---

### Post by sgx on 2012-02-11
We get total freedom, including total destruction. :):guitar:

Creating a  separate /home partition will help if you reinstall similar linux versions, you can choose not to format it, and your internet and gui settings will usually work.

I love fiddling around, and learned the hard way to use extra systems
on usbsticks and external drives, or live media sessions for learning new things.

You can install apps in live sessions for testing purposes, and spare
your real setup the bloat of things you find you don't like or need.
Cheers

---

