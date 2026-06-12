---
title: "My computer is being hacked"
date: 2011-02-27
forum: Security
---

### Post by nec207 on 2011-02-27
I have windows computer and it is being hacked.About month ago or more some one hacked my router and install new firmware from Firmware Version: Talisman/Basic V1.2.9a
 
 
My router is linksys and SSID got changed to sveasoft.I had WPA set up and MAC filtering .
 
Some one hacked my router and change Firmware Version.And user name and password also got change to just admin.
 
Well now I got a pop up from my Kaspersky saying network attack scan.generic.TCP 74.63.245.168
 
 
only thing I can find on it [http://whatismyipaddress.com/ip/74.63.245.168](http://whatismyipaddress.com/ip/74.63.245.168)
 
It is Limestone Networks in Dallas.
 
 
Some strang things have been happing to my computer in past 4 months and is getting worse.
 
I have no firewall or router now.And have not gone to the store and get new router yet and I'm thinking of formatting my computer and putting linux and get good firewall like zone-alarm.
 
I think some one on my street is hacking me.

---

### Post by uRock on 2011-02-27
This has nothing to do with Ubuntu.

Why not reset your router, then configure it with a strong password. Reinstall Windows, then create a non-admin account to use for surfing and day to day activities. Install Microsoft Security Essentials to protect the system. It isn't a firewall, but once your router is reset it will do all of the firewall work.

---

### Post by CandidMan on 2011-02-27
Sorry to hear that you're having trouble.
If your PC has been hacked as badly as you say then right now it's kind of futile to clean it up whilst connected to the internet.
How are you getting online now?
LiveCD?

---

### Post by nec207 on 2011-02-27
I'm thinking of formating it and putting Ubuntu on it.And get a good firewall like zone-alarm.
 
 
I use Kaspersky .

---

### Post by jeremyjjbrown on 2011-02-27
You should manully reset your router to it's default settings. There is probably a hardware reset switch somewhere on the case.

---

### Post by geoffmcc on 2011-02-27
> Some one hacked my router and change Firmware Version.And user name and password also got change to just admin.

This would have probably been done locally as updating router firmware via remote connection would most likely have resulted in the drop of the connection while pushing threw the firmware and possibly brick router

---

### Post by uRock on 2011-02-27
> **geoffmcc said:**
> This would have probably been done locally as updating router firmware via remote connection would most likely have resulted in the drop of the connection while pushing threw the firmware and possibly brick router
+1 Most routers do not allow this to be done wirelessly.

If it is a Cisco router, then there is a reset button on the back where the ports are, use a non-metallic instrument to press and hold it fr about 10 seconds.

---

### Post by geoffmcc on 2011-02-27
> **uRock said:**
> +1 Most routers do not allow this to be done wirelessly.

If it is a Cisco router, then there is a reset button on the back where the ports are, use a non-metallic instrument to press and hold it fr about 10 seconds.

Yes this would disable any ports opened by whomever and reset the password to default but he/she would still be using the firmware that other person put on. Would just be reseting that firmware.

If its a linksys like i think you said - just get the correct firmware from them for your model. Or if model supports dd-wrt throw that on there and make it better than it ever was (if your confident in doing so)

---

### Post by CandidMan on 2011-02-27
> **geoffmcc said:**
> Yes this would disable any ports opened by whomever and reset the password to default but he/she would still be using the firmware that other person put on. Would just be reseting that firmware.
This is what I was considering, if they haven't got a Ubuntu CD already. Am I being paranoid in thinking that anything this person downloads could be substituted by the attacker? (inc .iso file and checksum)

---

### Post by nec207 on 2011-02-27
> **geoffmcc said:**
> This would have probably been done locally as updating router firmware via remote connection would most likely have resulted in the drop of the connection while pushing threw the firmware and possibly brick router
 
Well 3 things came to my mind.
 
1.The router updated the firmware my it self.
2.I gone to bad web site
3.Some one hacked my router 
 
But what do you mean this would have been done locally .
 
All this hacking started when I moved into a apartment building in down town area.
 
>  
Yes this would disable any ports opened by whomever and reset the password to default but he/she would still be using the firmware that other person put on.

 
What do you meam?

---

### Post by geoffmcc on 2011-02-27
> **CandidMan said:**
> This is what I was considering, if they haven't got a Ubuntu CD already. Am I being paranoid in thinking that anything this person downloads could be substituted by the attacker? (inc .iso file and checksum)

I cant speak to that but I too would be paranoid and would def not want to download the cd from home. It all depends on the firmware put on - is it orignal Sveasoft's firmware or did the "hacker" modify it in some way.

If i had to guess- this firmware was probably only put on the router for persistence - probably supports many different DDNS or using ipv6 so the machine can always be found.

---

### Post by geoffmcc on 2011-02-27
> **nec207 said:**
> Well 3 things came to my mind.
 
1.The router updated the firmware my it self.
2.I gone to bad web site
3.Some one hacked my router 
 
But what do you mean this would have been done locally .
 
All this hacking started when I moved into a apartment building in down town area.
 


I put dd-wrt firmware on my router and part of the process is making sure it is a wired connection with a static ip address of 192.168.1.100 (i believe)

The reason for this is when the firmware gets pushed threw the router is going to reboot. 

So if this was done remotely the person would have lost connection to your computer. That break in connection also runs the risk of firmware not being properly loaded into the router and breaking it all together


## Edit

Not saying it isn't possible. If you haven't allowed anyone into your home (family/friends included) then i guess it was done remotely, but chances are it was done from a computer with a wired connection into your router.

---

### Post by CandidMan on 2011-02-27
I've generated a sha512 checksum for the latest Ubuntu 10.10 iso if that's any help. Assuming communication between nec207 and the forums aren't being tampered with
```
83cd8b32378f7745112f019e5b641fe8a625548cc7193f57217afe065252a1f9f7d03003bdd2335791adb7c3e58cf76b0dd9c4fc127800bf960e72b3ba3fb005  Documents/Technical/ubuntu-10.10-desktop-i386.iso
```

---

### Post by doas777 on 2011-02-27
are you absolutely certain that you are connected to the right wireless network?

---

### Post by geoffmcc on 2011-02-27
after reading about the firmware they claim

> Increased RF power output by 900 percent to 251 mw

sounds to me whoever was piggybacking off your connection wasn't getting a strong enough signal so they put this on.

That being said, like someone else suggested most routers don't let you update firmware threw wifi. either yours did or you let someone into your home and they did it without your knowledge.

Got any friends in the building or near it?

---

### Post by nec207 on 2011-02-27
None of the tech guys at kaspersky know what is going on.
 
 
Here was the information.
 
Talisman
Firmware Version: Talisman/Basic V1.2.9a
Routers name SVEASOFT
password admin
user name admin
Linksys WRT54G/GS/GL, BCM5352E Ethernet
13:02:25 up 2:56, load average: 0.13, 0.06, 0.01
Automatic Configuration - DHCP

 
Mode: AP 
Network: Mixed 
SSID: sveasoft 
DHCP Server: Enabled 
Channel: 6 
Wide Channel: None 
Channel Width: 20 MHz Standard 
TX Power: 50 mW (17.0 dBm) 
Rate: 54 mbps 
Encryption: Disabled 
 
[]("http://sveasoft.com/") 

> This would have probably been done locally 
 
Are you saying it cannot be done over the internet has they would loss conection? So would have to be close by?
 
My router is Linksys model number WRT54GL v1.1

---

### Post by doas777 on 2011-02-28
> **nec207 said:**
> None of the tech guys at kaspersky know what is going on.
 
 
Here was the information.
 
Talisman
Firmware Version: Talisman/Basic V1.2.9a
Routers name SVEASOFT
password admin
user name admin
Linksys WRT54G/GS/GL, BCM5352E Ethernet
13:02:25 up 2:56, load average: 0.13, 0.06, 0.01
Automatic Configuration - DHCP

 
Mode: AP 
Network: Mixed 
SSID: sveasoft 
DHCP Server: Enabled 
Channel: 6 
Wide Channel: None 
Channel Width: 20 MHz Standard 
TX Power: 50 mW (17.0 dBm) 
Rate: 54 mbps 
Encryption: Disabled 
 
 


 
Are you saying it cannot be done over the internet has they would loss conection? So would have to be close by?
 
My router is Linksys model number WRT54GL v1.1

it would mean that they would have to be directly connected to your router with a physical cable. so yes, close enough to touch you.

---

### Post by nec207 on 2011-02-28
My router is Linksys model number WRT54GL v1.1.
 
What does it say about doing firmware uptades ?

---

### Post by KegHead on 2011-02-28
Hi!

Are you in an office or your house/apt/condo?

My wife's old compaq logs on to suerman... from three blocks away!

Double check your wifi connection.



KegHead

---

### Post by uRock on 2011-02-28
> **nec207 said:**
> None of the tech guys at kaspersky know what is going on.
 
 
Here was the information.
 
Talisman
Firmware Version: Talisman/Basic V1.2.9a
Routers name SVEASOFT
password admin
user name admin
Linksys WRT54G/GS/GL, BCM5352E Ethernet
13:02:25 up 2:56, load average: 0.13, 0.06, 0.01
Automatic Configuration - DHCP

 
Mode: AP 
Network: Mixed 
SSID: sveasoft 
DHCP Server: Enabled 
Channel: 6 
Wide Channel: None 
Channel Width: 20 MHz Standard 
TX Power: 50 mW (17.0 dBm) 
Rate: 54 mbps 
Encryption: Disabled 
 
 


 
Are you saying it cannot be done over the internet has they would loss conection? So would have to be close by?
 
My router is Linksys model number WRT54GL v1.1

Did you get this info via wired or wireless connection? 

Why is encryption disabled. 

Why is the maintenance user name and password set to admin?

---

### Post by nec207 on 2011-02-28
> Did you get this info via wired or wireless connection? 

Why is encryption disabled. 

Why is the maintenance user name and password set to admin?  
My guess so the person can get free internet access or the person tried to install firmware but some thing gone wrong so did not lock me out if.
 
I also got 
 
incoming log
Source IP ------------------------ Destination Port Number 

10.241.124.1 ----------------------- bootpc 

Outgoing log
nothing here yet..
 
 
I got all this info in the routers setting by opening the browser and typing address of the router.
 
The user name and password got set to just admin.Most firmware updates you lose all your settings and admin or password is default for most routers .That why it is important to change this ASAP.
 
Proper security and strong passphrase would not allow this to happen.

---

### Post by emiller12345 on 2011-02-28
It is possible that the firmware could have been loaded
remotely through cross-site scripting.  If you visited a
website from you compter that had malicious content,
it's possible that your browser loaded the firmware
without you knowing it.

```
[Internet] ---->[linksys-router] ---->[pc]
                       ^               ||
                       |               ||
                       |            [firefox]
                       |               ||
                       |               ||
                       |-----------[webpage]

```

---

### Post by SeijiSensei on 2011-02-28
Have you actually reset the router by pressing the switch to restore factory defaults?  It sounds like you've ignored this advice throughout.

After that, make sure the administrative password is a strong one, and only use WPA2 encryption for client connections.  Disable any external access to the router's admin pages.  You might also consider restricting access by MAC address as well just for good measure.

This isn't an Ubuntu problem.  It's a problem because you put an insecure router in a place where someone could connect to it and futz with your settings.

---

### Post by nec207 on 2011-02-28
> Have you actually reset the router by pressing the switch to restore factory defaults? It sounds like you've ignored this advice throughout. 
That will do nothing do to the bad firmware is on it.
 
What is this 
incoming log
Source IP ------------------------ Destination Port Number
 
10.241.124.1 ----------------------- bootpc

---

### Post by rookcifer on 2011-02-28
> **nec207 said:**
> My router is Linksys model number WRT54GL v1.1.
 
What does it say about doing firmware uptades ?

Install the Tomato firmware, enable WPA2 encryption with a strong random password and be happy.

---

### Post by geoffmcc on 2011-02-28
To be clear on what i said yesterday. The website of the firmware claims to boost the signal of wifi. That is most likely the reason this firmware got put on. Chances are if you enable security and your mac filtering again and change password for accessing router as well as making sure the config page is only available to local network you are probably safe.

Best bet though, or at least the securest would be to get firmware you know is legit on there. Could even put the same custom firmware on there, but from a trusted source.

All that being said. Especially with WPA being on before coupled with MAC Filtering and if the router would even allow it to be done threw wifi all points to someone using your pc or using a Ethernet cable to physically plug theirs into your router to open it up for them to use.

P.S 

> My guess so the person can get free internet access or the person tried to install firmware but some thing gone wrong so did not lock me out if.

The goal of this was not to lock you out. It was for you and them to have access without you ever knowing. The only thing that went wrong was that you found out.

---

### Post by nec207 on 2011-02-28
So do you think it is most likely I gone to bad web site or some one hacked my router?

---

### Post by uRock on 2011-02-28
> **nec207 said:**
> So do you think it is most likely I gone to bad web site or some one hacked my router?
No.

---

### Post by geoffmcc on 2011-02-28
> 
All that being said. Especially with WPA being on before coupled with MAC Filtering and if the router would even allow it to be done threw wifi all points to someone using your pc or using a Ethernet cable to physically plug theirs into your router to open it up for them to use..             


So have you allowed anyone access to your router or pc?

---

### Post by bean@ on 2011-02-28
**RE.HACKED COMPUTERS**
Am very much a beginner [1 wk] but am sure someone else had complete control of this computer 30 mins ago,i had 2 unplug it to stop random playing of music  that woz nothing 2 do with me.Rythm box just displayed gibberish and totally locked up.I think i may to be blame as am not sure have got firestarter set rite or wot. however Ubuntu is supposed to be for all and i get the feeling that maybe someone woz giving me a relatively harmless example of how vulnerable my computer is! Maybe a message would be less stressful next time! My first post, tragically incompetent i know

---

### Post by cariboo on 2011-02-28
There could be plenty of reasons for your system to be playing music, including moving your mouse pointer over any file in your music directory. I'd suggest you make sure you stop remote desktop from starting in System->Administration->Startup Applications.

---

### Post by Jive Turkey on 2011-02-28
Out of curiosity are you associated with Koch Industries, Georgia-Pacific, the Koch brothers or Gov. Scott Walker in any way?

---

### Post by nec207 on 2011-03-01
> **cariboo907 said:**
> There could be plenty of reasons for your system to be playing music, including moving your mouse pointer over any file in your music directory. I'd suggest you make sure you stop remote desktop from starting in System->Administration->Startup Applications.
 
What are you talking about? None of those things are happing to me and if it did , I will click on format ASAP or take my computer to 10 floor and through it out as you cannot trust any anti-virus program and firewall to clean up that infection 100%
 
> So have you allowed anyone access to your router or pc? 
 
Wrong if you look at log it points clearing that this is hacking .
 
>  no 
 
Please translate this to proper english.

---

### Post by uRock on 2011-03-01
> **nec207 said:**
> Please translate this to proper english.
You asked a yes or no question and I answered as such. Apply the answer to the question.

---

### Post by nec207 on 2011-03-01
elaborate I don't read minds. I'm having trouble understanding what you are saying.

---

### Post by uRock on 2011-03-01
> **nec207 said:**
> So do you think it is most likely I gone to bad web site or some one hacked my router?

> **uRock said:**
> No.

> **nec207 said:**
> elaborate I don't read minds. I'm having trouble understanding what you are saying.
No, I do not think your router was hacked because of a site you visited. (Mind reading not needed to apply answer to question.)

Download the proper firmware for your router, then disconnect the router from the internet, then connect your PC to the router with wire, then go through the router's GUI and install the proper firmware.

Once the firmware is installed, set up your router with new passwords to include setting up WPA encryption with a really strong passphrase, enable logging(this way you can see if someone has been trying to connect), being that you have a hacker near by that I am guessing was able to configure the router wirelessly(usually hard to do) you may want to make your settings match those in screenshot-3 so that one will have to physically connect to the router in order to get into the management utility.

Once you have a working configuration, back it up, so that if you have to reset the router in the future you can do so easily.

Connect the router to the modem/DCE and be confident that your neighbor will have to hack someone else's network.

---

### Post by geoffmcc on 2011-03-01
> **bean@ said:**
> **RE.HACKED COMPUTERS**
Am very much a beginner [1 wk] but am sure someone else had complete control of this computer 30 mins ago,i had 2 unplug it to stop random playing of music  that woz nothing 2 do with me.Rythm box just displayed gibberish and totally locked up.I think i may to be blame as am not sure have got firestarter set rite or wot. however Ubuntu is supposed to be for all and i get the feeling that maybe someone woz giving me a relatively harmless example of how vulnerable my computer is! Maybe a message would be less stressful next time! My first post, tragically incompetent i know

One day ubuntu will click for you if u keep at it. There is a lot i dont know but i learn something new everyday threw forums and irc and i like that i am able to help some newer users (sure some of them are way past me now)

If i remember correctly (as i mainly use ubuntu server) that the desktop version comes with a built in remote desktop and i kinda remember someone saying the default settings arent secure --- this may be what happened to you.

If your not sure about firestarted setup try using UFW (super easy) until your more confident

P.S - not trying to be a jerk but at what point are you going to accept the answers that have been given to you. 
I will say it, or ask it again --- Who had access to your router (probably someone in same building or near by) as the firmware states it boosts the signal. Whoever was piggybacking off your connection was probably getting a weak signal so this was put on in effert to boost it.

Because you had WPA (not that it cant be cracked) enabled along with Mac Filtering (Further securing your WPA security) and that most routers wont let firmware be pushed threw a wireless connection all points to someone being in hour home doing this.

---

### Post by nec207 on 2011-03-01
>  
you may want to make your settings match those in screenshot-3 so that one will have to physically connect to the router in order to get into the management utility.
 

 
Can you explain this batter.
>  
 
P.S - not trying to be a jerk but at what point are you going to accept the answers that have been given to you. I will say it, or ask it again --- Who had access to your router (probably someone in same building or near by) as the firmware states it boosts the signal. Whoever was piggybacking off your connection was probably getting a weak signal so this was put on in effert to boost it.

 
No idea why a peron did it and is irrelevant to guess why.
 
We can only guess a hacker did it ,bad web site or router was set to update firmware. Most likey a hacker.Most likey it would not have happen if the router was set up right in the first place.
 
 
> Because you had WPA (not that it cant be cracked) enabled along with Mac Filtering (Further securing your WPA security) and that most routers wont let firmware be pushed threw a wireless connection all points to someone being in hour home doing this.
 
 
Some thing was not set up right because proper security would make it next to impossible for even NSA to crack.
 
And yes on other message board it saying you can update some routers firmware by wfi.We can only guess why the hacker did it and not block my computer from going on the internet and not change admin and password to some thing other admin to get into the routers setting so I cannot get into the routers setting.
 
I know enough about networking that Kaspersky saying network attack scan.generic.TCP 74.63.245.168 
 
And
 
incoming log
Source IP ------------------------ Destination Port Number
 
10.241.124.1 ----------------------- bootpc
 
 
Is very very very very very very MUCH not normal behavior and points to hacking.It not to be taken likely AT ALL.That alone the routers firmware getting change.
 
For all I know my computer may be compromised.I definitely have to format my computer and set up proper security this time.It is irrelevant to guess why the hacker did this other than lack of security on my part.
 
 
All this spit splashing message here on why and how or her did it is giving me sick stomach.I'm done when this thread.

---

### Post by uRock on 2011-03-01
> **nec207 said:**
> Can you explain this batter.
I think the screenshot explain this very well. You may need to visit the Linksys site to get in depth directions for your router model.

---

### Post by jeremyjjbrown on 2011-03-02
Wow!

---

### Post by dionysius on 2011-03-02
> **jeremyjjbrown said:**
> Wow!

I was thinking exactly the same thing.

---

### Post by jeremyjjbrown on 2011-03-02
> **dionysius said:**
> I was thinking exactly the same thing.

I'd have to say uRock went above and beyond the call to try and help this person.

---

### Post by geoffmcc on 2011-03-02
Still not reading what I am writing, but that's ok. Im not asking you to guess why it was done, you just have yet to answer the question. 


> We can only guess why the hacker did it and not block my computer from going on the internet and not change admin and password to some thing other admin to get into the routers setting so I cannot get into the routers setting.

The goal of this would not to be to block you out. A hack is like a con, the perfect one goes un-noticed. Cause if you notice (like you have, you will do something about it)

---

### Post by |{urse on 2011-03-02
There's free help and then there's pointless arguing with free help. Just do what uRock said and mark this sucker solved.

---

