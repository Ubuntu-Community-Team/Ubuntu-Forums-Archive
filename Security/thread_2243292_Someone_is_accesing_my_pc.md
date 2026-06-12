---
title: "Someone is accesing my pc"
date: 2014-09-07
forum: Security
---

### Post by cacahuatey on 2014-09-07
I am sure that someone is having access to my personal computer, i changed my password and blocked the acces in the firewall, but this is still happening. I can't explain how i know, but i am sure that it is going on, and i know who it is. What can i do to be more protected? Or where can i check there accesing? Im noob on linux and i don't understand much, but i try to manage to learn.

Thanks in advance!
Tey

---

### Post by nerdtron on 2014-09-07
Access via what? Remote desktop or via terminal?

If he is logged into your computer, you can see who are logged in by typing "w" in the terminal. Something like this:
```
[kenneth@nerdtron ~]$ w
 16:05:57 up 10 days,  9:13, 22 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
kenneth  tty1     :0               28Aug14 10days 44:07   0.13s pam: gdm-password
kenneth  pts/1    :0.0             28Aug14  4days  0.02s  0.02s /bin/bash
kenneth  pts/8    :0.0             31Aug14  3days  0.03s  0.03s /bin/bash
kenneth  pts/7    :0.0             31Aug14  7days  0.00s  0.00s /bin/bash

```

---

### Post by Vladlenin5000 on 2014-09-07
Hi, welcome.

Can you, at least, explain what is being accessed? Nobody can give any suggestion without knowing (or inferring) the attack vector...

And needless to say you may be sure, ie, you may believe it, but that doesn't make it true... I suspect that - assuming there's actually something going on - it can come from many other avenues...
Honestly, if I were after you the LEAST of my priorities would be gaining physical or remote access to your PC. Instead I would first and foremost go after what you already offered in social networking. That's exactly what the NSA, CIA, FBI and their counterparts in other countries do in a daily basis.

Now, the hypotheses you put forth is indeed plausible nevertheless. In order to start thinking about it you should offer a lot more info. Namely:
- OS version
- What firewall and how have "blocked the access"
- ...

---

### Post by cacahuatey on 2014-09-07
i know what you mean, but they are my neighboors, they are making me war and stalking me, it is weird and sounds paranoid, i know, but they know things i write in my computer and said it in a loud voice, and they have controll to freese my computer, i suspected this before, but was affirmed by them. When i configured the firewall my computer stopped crashing for a couple days, but seems like they found another way. I know how stupid this sounds but i swear is true. 

This is what i got rununf "w" on my terminal

 22:07:01 up  2:28,  2 users,  load average: 0,04, 0,13, 0,11
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
tey      :0       :0               19:38   ?xdm?   7:49   0.15s init --user
tey      pts/0    :0               22:06    3.00s  0.06s  0.00s w

Tey it's me, looks normal to me, but i have not much idea and i don't know if they log often or when...
Is there anything else i can do to protect myself? I dont like having anyone spying me

Thanks a lot!!!!

---

### Post by cacahuatey on 2014-09-07
now i look at it better, says 2 users... both with my name, but im not sure of what that means

---

### Post by EuclideanCoffee on 2014-09-07
Sounds like a big problem. Are you accessing the Internet via Wifi or ethernet? If not the latter, I suggest doing that from now on until your neighbours stop. If the latter doesn't work, you might have something wrong with your Internet source. That is beyond my scope of knowledge. Let us know how it goes.

user tey (you)
and tey (you)

Should be what you see.

---

### Post by lisati on 2014-09-07
If it's your neighbours, then it might be a good time to up the security on your WiFi.

---

### Post by lisati on 2014-09-07
> **cacahuatey said:**
> now i look at it better, says 2 users... both with my name, but im not sure of what that means

That's perfectly normal, and nothing to worry about.

---

### Post by Vladlenin5000 on 2014-09-07
Honestly, it sounds like a bunch of BS to me but... 

- Are you in a shared internet access of some kind with your neighbors? If so, many things can happen depending on your network configuration. If not then your neighbors need to be as good as NSA and, unless their filthy rich, they simply DON'T have the resources to pull such stunt.

Now... This other part intrigued me: > [COLOR=#000000]they know things i write in my computer[/COLOR]

Ok, for starts, you don't just "write things in your computer". Such statement is so vague it says absolutely nothing. Let's see... Do they know what you wrote in a text file/spreadsheet/presentation/whatever that never left your PC? That would be weird indeed... OTOH, things you write in the web - including your own posts here - are easily accessible and **it doesn't require too much social engineering to have access to "things you wrote in the web which weren't for public display"**, ie, "things" requiring a password...

Speaking of which... **Have you changed ALL your passwords already?**&#8203;

---

### Post by chopra on 2014-09-07
The only evidence you've given that this individual has access to your computer is that they "know things", but you didn't say what.  First, they may not be causing your computer problems, but they might be trying to trick you into thinking that they are.  Did they bring up the subject, or did you?

Never mind.  It doesn't matter.  It's already been suggested that you use an ethernet cable.  However, if they have access to your modem's password (unlikely), then they could concievably still log in and perform something with their computer that requires an absurd amount of bandwidth.  I don't know of any way to block that, short of covering your modem in tinfoil, which seems like overkill.

I don't think anyone can really advise you better without knowing more details.

---

### Post by uRock on 2014-09-07
Maybe they sneaked a wireless camera into your office room. If your phone has a camera, wait until night time when it is nice and dark, turn off the lights, turn on your phone's camera and sweep the room looking for an unexpected light. If you find a dim light, then look to see if it is a camera with night vision. The IR lights on night vision cameras are visible to digital cameras. I have cameras on my house and this is tried and true.

On your PC run **sudo ufw enable** in a terminal to turn on the firewall.

On your router, set a strong WPA2 password.

If you really and truly think they are cracking into your PC, then it may also be time to install and run Snort. [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696) Yes, there is a lot of learning, trial, and error, but it may be worth the sense of security once it is in place.

Change the password on your machine and don't use password12345. Use something like SM@c|{-F4<3

If your neighbor is a Black Hat style cracker and you do thing Snort thing and get proof it is the neighbor hacking your system, then you can get law enforcement involved.

---

### Post by QIII on 2014-09-07
Have you asked about this issue before?

---

### Post by cacahuatey on 2014-09-08
Thanks for all your answers. 
Is it really possible to have acces to a computer via wifi? :S I think im gonna change to cable asap. 
Im really noob on all this, but what i am saying is not BS as someone said. They have read private notes i sent on deviant art (Ok, maybe this is accesible to public), but when my computer crashes, They laugh and say thing like "oh, crashing again". It is not a coincidence, happened many times. 
I'm having a lot of connection issues and i know they know internet providers so maybe someone gave them the password, idk... im gonna try changing it.
And for last, i never asked about this before or posted in this forum.

Thanks again

---

### Post by cacahuatey on 2014-09-08
i'm gonna try to use snort, thanks!!!

---

### Post by cacahuatey on 2014-09-08
i have another question now, i can't access to my root user, is there a way to do it?

---

### Post by ofnuts on 2014-09-08
In Ubuntu you don't use the root user. Everything you would do with root is done with "sudo" using from your own id, and providing your own password.

About the rest:


[LIST]
[*]To do things with your computer someone has to either log on it from the keyboard (which requires entering your house) or connect through a network to which you computer is connected.
[*]You computer is normally connected to a single network, that includes as a minimum the computer itself and the modem/router/Wifi hotspot (*).
[*]There are only four ways to connect to that:
[LIST]
[*]An ethernet cable plugged in the router. This requires entering your house.
[*]An ethernet cable from the router to a PLC adapter, and in some power outlet, outside of your home, another PLC adapter. This requires entering your house for the first adapter, and PLC frequencies usually don't survive across your main breaker. If they spy on your own PLC, then PLCs can be encrypted.
[*]Entering your network through the router: the standard configuration of such routers normally doesn't allow inbound connections.
[*]Connecting to your network via Wifi. If your network is open it's easy. If it uses WEP protection is not very difficult. It is uses WPA/PSK it is a lot harder if you use long keys, and even harder if you change them regularly. You can of course disable the Wifi and use only Ethernet/PCL.
[/LIST]

[*]Once they can connect to the network they can spy your non-encrypted traffic, in particular, what you do with "http" sites (but not with the "https" ones).
[*]But if they want to access your computer they il have to log in to it (**):
[LIST]
[*]this can be impossible if you have set up a firewall
[*]even without a firewall this will be very hard if you have a decent password.
[/LIST]

[*]About the "w" output:
[LIST]
[*]If the "From" column says :0 or 127.0.0.1 then that's someone physically on your computer
[*]You have to worry only if that column has another address (likely 192.168.x.y, which woul dbe another address on your home network)
[/LIST]
[/LIST]

(*) There is also the possibility that your computer is configured with a "ad-hoc" Wifi connection (instead of talking to a hotspot, it is itself a hotspot). Not too likely, though, but your network manager should tell you if so.

(**) assuming of course that your are not running some FTP/HTTP or Samba  server that allows anyone to retrieve files from your disk (but these  are not setup by default)

---

### Post by cacahuatey on 2014-09-08
Thanks for taking the time on that long answer Ofnuts! Cleared many thing. I have changed all passwords of my computer and modem. Is there any chance that i have installed a key copier (I don't know the name, i know that something exists that makes a copy of all what you write)

---

### Post by ofnuts on 2014-09-08
The word is "key logger". Not too likely to be installed remotely on Linux. This would require access to your computer first.

---

### Post by lisati on 2014-09-08
A couple of thoughts about router security here.

[LIST]
[*]Make sure you have set an admin password for your router. Avoid using the default settings as many routers come with easily guessed "standard" user/password combinations.
[*]Use a password for your WiFi. Avoid using WEP it is easily bypassed by someone who knows what they're doing. WPA is better. 
[*]Restrict WiFi access to allow only your devices. Although MAC filtering isn't infallible (and shouldn't be used on its own) it adds a layer of security that will slow down potential intruders.
[/LIST]

---

### Post by nerdtron on 2014-09-08
And also:

What did you install on your computer? Did someone asked you to install something or click a link on your browser? Or someone gave you commands to run on the terminal?
Maybe someone already have a program installed on your computer that sends your activity on the internet.
You should always be aware on what you do on your computer.

---

### Post by Habitual on 2014-09-08
Secure your router, if you have one.

---

### Post by cacahuatey on 2014-09-08
i have a wifi modem, i changed the password and it is configured on wpa-aes with password.
I didnt installed anything weird, only few programs from the software center. 
I have been told to try with tripwire to see if i have any intrusion but i dont get a clue of how it works

---

### Post by cacahuatey on 2014-09-08
im reading a lot about tripwire, can any of you give me a good guide for that? every page i look to says something different.
Thanks!!!

---

### Post by JKyleOKC on 2014-09-09
I see you have another thread asking about that, also. Having used tripwire for several years, I can tell you that it is NOT a program I would recommend to anyone without several years' experience using Linux at the command line. As a longtime geek myself, I consider it to be a program written **by** geeks **for** geeks, and there be dragons hiding all through it.

That said, it does what it's intended to do quite well -- which is to detect any changes in critical files. What makes it difficult for a newcomer to set up is that **you** have to define which files are critical, and that takes quite a bit of knowledge about what goes on behind the scenes. While the versions currently available do have sample lists of files to be checked, these lists are of a "one size fits all" nature and may include files that don't exist on your system while omitting some that are really critical for your uses.

And it won't prevent malware from adding a key logger or spyware to your system. **All** that it will do is alert you to changes made in files that it already has in its database.

Apparmor comes with Ubuntu by default, and is much more like what you might need given the history you've posted here. It, too, is quite tedious to set up, but it does prevent some bad things from happening. The "security" forum here has a sticky thread, listed at the top of the forum's first page, that tells you how to set it up.

---

### Post by cacahuatey on 2014-10-21
Hi, i have posted this before, but i could not fix it yet. And it's making me feel angry taht someone can acess my pc.
I have the latest ubuntu and windows 7 on a partition cos i need to use acrobat products.
I have wifi internet and no chance on changing it to ethernet, cos i share it with my family.

Thing is that i'm on a big fight with my sister and neighboors, and they are accesing my pc when i'm working and they freeze it. And they laugh and tell me things like "happened again?" I have firewall on both OS and all protected with passwords, but my guess is they are accesing trough my wifi. Is there something i can do about it? 
I know this sounds like bs and paranoia, but it is real, and i' tired of it. I even formated my computer and they found the way to access again.
Ah, one more thing, every time i open windows (I don't use it much, only for work on some designs i can't do with gimp) i find my firewall disabled, i change it back, and then i find it off again, this has happened like 3 times lately.

One last thing, is there an easy way to see if i have a keylogger???

---

### Post by pfeiffep on 2014-10-21
> [COLOR=#000000]I have wifi internet and no chance on changing it to ethernet, cos i share it with my family.[/COLOR] I hope that you have this wifi connection secured with a password - or is this a public wifi?

> [COLOR=#000000]and they are accesing my pc when i'm working and they freeze it[/COLOR] How do you know that this isn't a bandwidth issue with shared wifi?

> [COLOR=#000000]One last thing, is there an easy way to see if i have a keylogger???[/COLOR]
[http://www.securitygeeks.net/2013/06/how-to-find-out-if-you-have-keylogger.html](http://www.securitygeeks.net/2013/06/how-to-find-out-if-you-have-keylogger.html)
[http://security.stackexchange.com/questions/11117/can-i-determine-if-my-computer-has-a-ke](http://security.stackexchange.com/questions/11117/can-i-determine-if-my-computer-has-a-ke) y-logger-installed

---

### Post by jdeca57 on 2014-10-21
Do they have physical access to that hardware? I mean, shut down your pc and put it in a locked closet when you're away, that should eliminate one problem at least...

---

### Post by Bucky Ball on 2014-10-21
I have merged your threads. Please do not duplicate post. Thanks.

---

### Post by GrouchyGaijin on 2014-10-21
Or I guess you could put up a spy camera and see if anyone is messing with it...

---

### Post by MartyBuntu on 2014-10-21
> **cacahuatey said:**
> 
Thing is that i'm on a big fight with my sister and neighboors, and they are accesing my pc when i'm working and they freeze it. And they laugh and tell me things like "happened again?"

I suspect the answer to the "problems" you're encountering lies outside of the realm of software, or computers for that matter.

---

### Post by QIII on 2014-10-21
Then let's keep our discussion limited to computers, please.

---

### Post by Vladlenin5000 on 2014-10-21
> **QIII said:**
> Then let's keep our discussion limited to computers, please.

Sure... But if it walks like a duck and quacks like a duck and now has feathers, beak and feet too like a duck?... In most situations furthering the discussion about the wildest hypotheses validates and consequently worsens the... Duckness.

Before further elaboration, @cachuatey, [B]avoid voicing your opinion about this subject to family members, friends, neighbors or other acquaintances. Avoid above all accusing potentially - and most likely - innocent people. You WILL regret it later!
[/B]This situations should be dealt with the utmost caution even with proof and so far you have nothing.


At first, we were presented with a "neighbors vs Ubuntu" scenario that now escalated to a "neighbors+sister vs Ubuntu and Windows". The focus also shifted from "reading/knowing what I write" - (in my own Ubuntu computer), implicitly - to freezing - (while away at work) with the computer running Ubuntu -or- Windows 7.
This brings a plethora of new questions.
1. Above all is the **physical **access to your computer. While it's far fetched your neighbors breaking into your house without your consent (and leaving no trace apparently), _your sister who lives with you certainly has physical access to your computer_. It doesn't take a leap of imagination to suggest a simple prank of shutting down your PC while you're away and simply unplugging it from the mains will do it... Or simply shutting it down from the menu as even if it is in the look screen you don't need a password to reboot or shutdown; your password is needed to open the current session only.
2. Now we have also a Windows 7 in the equation, something you "forgot" to mention in the first interaction. Everybody else posting in your thread, including me, were focused on **evaluating the plausibility **of such attack in a networked Linux system, nothing else. Simply put, it isn't plausible. Knowing it's a dual-boot with Windows then there are some things you should be aware of like
3. Windows 7 by default allows login without password and, unlike what is any Linux default, allows any change to be made without asking for the (admin) user's password. That includes, of course, **disabling the firewall** and **accessing all the user's and system's files** unless the files themselves have some password protection, whether they are in the Windows main partition or in a typical 'shared' secondary NTFS partition. 
4. Freezes particularly have quite materialistic and mundane explanations, hardware and/or software.   



There are lots of other possibilities open in the second iteration scenario and ALL of them should be ruled out before escalating to a 'conspiracy-theorist' mode. And most likely it's just a duck.

---

### Post by cacahuatey on 2014-10-21
Sorry for opening another thread and thanks for merging them.

> **Vladlenin5000 said:**
> 

1. Above all is the **physical **access to your computer. While it's far fetched your neighbors breaking into your house without your consent (and leaving no trace apparently), _your sister who lives with you certainly has physical access to your computer_. It doesn't take a leap of imagination to suggest a simple prank of shutting down your PC while you're away and simply unplugging it from the mains will do it... Or simply shutting it down from the menu as even if it is in the look screen you don't need a password to reboot or shutdown; your password is needed to open the current session only.

It is not while i am away, i work at home, with my computer, and when  i'm really focused on something, the shut it off and i have to restart  it. 
When i am using it, and i have to restart it. I didn't  understoon much the duck methaphore, but they allways laugh when this  happen, and they even said they read all what i write, that is why i was  asking about keyloggers. I'm gonna check that later, im mind burnt  right know

> **Vladlenin5000 said:**
> 2. Now we have also a Windows 7 in the equation, something you "forgot" to mention in the first interaction. Everybody else posting in your thread, including me, were focused on **evaluating the plausibility **of such attack in a networked Linux system, nothing else. Simply put, it isn't plausible. Knowing it's a dual-boot with Windows then there are some things you should be aware of like

I think i mentioned that i have windows, but not on the first post, i'm sorry, i didn't thought the possiblility of being managed via windows while using ubuntu.

> **Vladlenin5000 said:**
> 4. Freezes particularly have quite materialistic and mundane explanations, hardware and/or software.   
There are lots of other possibilities open in the second iteration scenario and ALL of them should be ruled out before escalating to a 'conspiracy-theorist' mode. And most likely it's just a duck.

I know, but this allways happens when they are around, only at that  moments, and they allways make a comment about it. I know how "Ducky"  this sounds, but it is the sad truth.

I have to add that my wifi is protected by pasword, but my sister can give it to them for sure. 
I don't know what else can i add to let you see the whole thing. But i am 100% sure they are making my computer crash, with the only intention of bother me. That's what they do the whole day.

---

### Post by Mark Phelps on 2014-10-21
I'm retired from the InfoSec field now, but when I was working, one of our favourite sayings was "Once they have physical access to your PC, all bets are off!" -- meaning, if someone can get physical access to your PC, presuming they know how (or can figure out how), they can do pretty much whatever they want to compromise it, including installing spyware and keyloggers.

If you can't physically secure your PC from unwanted access while you are at work, all discussions here are basically a waste of time.  

This is what we used to call a "Social Engineering" problem, meaning, it's NOT a PC hardware or software problem, and something only YOU can fix.

If you drive to work, then lock the PC in the trunk of your car.  IF you walk or otherwise get to work in a manner that does not allow you to remove the PC from home, then basically, you're at the mercy of anyone at home that gets access to the PC -- and there's nothing here we can do to guarantee that they can not continue to get access.

---

### Post by cacahuatey on 2014-10-21
> **Mark Phelps said:**
> I'm retired from the InfoSec field now, but when I was working, one of our favourite sayings was "Once they have physical access to your PC, all bets are off!" -- meaning, if someone can get physical access to your PC, presuming they know how (or can figure out how), they can do pretty much whatever they want to compromise it, including installing spyware and keyloggers.

If you can't physically secure your PC from unwanted access while you are at work, all discussions here are basically a waste of time.  

This is what we used to call a "Social Engineering" problem, meaning, it's NOT a PC hardware or software problem, and something only YOU can fix.

If you drive to work, then lock the PC in the trunk of your car.  IF you walk or otherwise get to work in a manner that does not allow you to remove the PC from home, then basically, you're at the mercy of anyone at home that gets access to the PC -- and there's nothing here we can do to guarantee that they can not continue to get access.

That is so sad, but i guess the truth...

---

### Post by pfeiffep on 2014-10-21
> **Mark Phelps said:**
> I'm retired from the InfoSec field now, but when I was working, one of our favourite sayings was "Once they have physical access to your PC, all bets are off!" -- meaning, if someone can get physical access to your PC, presuming they know how (or can figure out how), they can do pretty much whatever they want to compromise it, including installing spyware and keyloggers.

**If you can't physically secure your PC from unwanted access while you are at work, all discussions here are basically a waste of time. ** 

This is what we used to call a "Social Engineering" problem, meaning, it's NOT a PC hardware or software problem, and something only YOU can fix.

If you drive to work, then lock the PC in the trunk of your car.  IF you walk or otherwise get to work in a manner that does not allow you to remove the PC from home, then basically, you're at the mercy of anyone at home that gets access to the PC -- and there's nothing here we can do to guarantee that they can not continue to get access.Possibly putting a bios level password would help! While that can be overcome by resetting the bios usually by a jumper on the mother board it will slow down and frustrate folks who are pranking you.

[SIZE=4]**[COLOR=#000000]@cacahuatey  [/COLOR]**[COLOR=#000000]Y[/COLOR][/SIZE]ou mentioned family and neighbors and wifi ... perhaps I missed the answer, but is this wifi connection secured by a password? Is it public?

---

### Post by ofnuts on 2014-10-21
> **Mark Phelps said:**
> if someone can get physical access to your PC, presuming they know how (or can figure out how), they can do pretty much whatever they want to compromise it, including installing spyware and keyloggers.

Isn't this what complete disk encryption (such as LUKS) is supposed to make very difficult? (*)


(*) Yes they can play with the boot partition, but it is also possible to boot first from a USB key to check that the boot partition hasn't been tampered with.

---

### Post by bashiergui on 2014-10-21
Are they messing with ypur computer while you're working on it? Or do they mess with it when you are away from it?

If it's the latter, then as someone else mentioned, full disk encryption + lock the computer inside of a cabinet or something when you leave.

---

### Post by whitesmith on 2014-10-21
> **cacahuatey said:**
> I am sure that someone is having access to my personal computer, i changed my password and blocked the acces in the firewall, but this is still happening. I can't explain how i know, but i am sure that it is going on, and i know who it is...Since you are unwilling to provide what may well be critical information, how do you expect us to help solve your problem?

---

### Post by bashiergui on 2014-10-21
> **Mark Phelps said:**
> I'm retired from the InfoSec field now, but when I was working, one of our favourite sayings was "Once they have physical access to your PC, all bets are off!" -- meaning, if someone can get physical access to your PC, presuming they know how (or can figure out how), they can do pretty much whatever they want to compromise it, including installing spyware and keyloggers.

If you can't physically secure your PC from unwanted access while you are at work, all **discussions here are basically** **a waste of time**.  

This is what we used to call a "Social Engineering" problem, meaning, it's NOT a PC hardware or software problem, and something only YOU can fix.

If you drive to work, then lock the PC in the trunk of your car.  IF you walk or otherwise get to work in a manner that does not allow you to remove the PC from home, then basically, you're at the mercy of anyone at home that gets access to the PC -- and **there's nothing here we can do to guarantee that they can not continue to get access.**
+1

---

### Post by mastablasta on 2014-10-23
> **ofnuts said:**
> Isn't this what complete disk encryption (such as LUKS) is supposed to make very difficult? (*)


(*) Yes they can play with the boot partition, but it is also possible to boot first from a USB key to check that the boot partition hasn't been tampered with.

or have the boot partition on USB key and boot from USB key. when away just take the USB key out and computer is useless then unless they know how to crack the encryption :)

---

### Post by cacahuatey on 2014-10-24
> **pfeiffep said:**
> Possibly putting a bios level password would help! While that can be overcome by resetting the bios usually by a jumper on the mother board it will slow down and frustrate folks who are pranking you.

[SIZE=4]**[COLOR=#000000]@cacahuatey  [/COLOR]**[COLOR=#000000]Y[/COLOR][/SIZE]ou mentioned family and neighbors and wifi ... perhaps I missed the answer, but is this wifi connection secured by a password? Is it public?

Sorry for the late reply, i have been too busy last days and forgot this.
Wifi is not public, and it has a password, but i think that my sister could have gave it to my neighboors.
How is that, putting a bios level pass?

---

### Post by cacahuatey on 2014-10-24
> **bashiergui said:**
> Are they messing with ypur computer while you're working on it? Or do they mess with it when you are away from it?

If it's the latter, then as someone else mentioned, full disk encryption + lock the computer inside of a cabinet or something when you leave.

It ONLY happens when i'm working on it. I have it on almost all day and night and never happens when i'm away, and i'm sure they are making it, cos they laugh every time. (my neighboors)

---

### Post by cacahuatey on 2014-10-24
> **mastablasta said:**
> or have the boot partition on USB key and boot from USB key. when away just take the USB key out and computer is useless then unless they know how to crack the encryption :)

It is a good idea, but problem is the mess with it while im using it. I'm gonna try to lock my door when i go out to see if they can cahnge my firewall configuration anyway

---

### Post by pfeiffep on 2014-10-24
> [COLOR=#000000]It is a good idea, but problem is the mess with it while im using it.[/COLOR]I understand, but what occurred prior to your using it? If folks have physical access to an unprotected computer they can reload / reactivate anything they choose.  > [COLOR=#000000]How is that, putting a bios level pass?[/COLOR] Usually on power up depressing a certain key (F2 on my machines) will present the bios setup; you need to look for security (do NOT use the same password as wifi). Setting a bios level password should prevent most folks from booting your device.>  [COLOR=#000000]Wifi is not public, and it has a password, but i think that my sister could have gave it to my neighboors.[/COLOR] [COLOR=#000000]I strongly suggest changing the password; give it to your sister AFTER she requests and counsel her not to share it.[/COLOR]

---

### Post by Elfy on 2014-10-24
This has gone beyond what people can do with software. We can do nothing about any issues you have outside of software.

You've been given good advice, that that and do it. 

Thread closed.

---

