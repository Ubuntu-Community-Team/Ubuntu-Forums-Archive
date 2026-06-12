---
title: "Make Ubuntu greet you at login"
date: 2008-03-08
forum: Ubuntu Brainstorm
---

### Post by NCLI on 2008-03-08
Personally, I think it would enhance the user experience if Ubuntu greeted you, wither through voice or text, when logging in.

For example, when logging in in the morning, it would print the text: "Good morning [insert name here]." This could be combined with Hardy's new weather feature, to print "Good morning [insert name here]. It's 6 C outside today, with a wind speed of 6,7 m/s, and slightly cloudy."

I don't think it would be that difficult to pull off in time for 8.10, since all the information required is already there.

---

### Post by NightwishFan on 2008-03-08
A simple way you could do that yourself is zenity with a cron job or something.
zenity --info --text="Good morning, sir."

You could make it more advanced if you so wish. I understand your idea and I suppose they could make it an option. It seems trivial though.

EDIT: Also try espeak. (make sure no sound is in use)
espeak "Good morning, sir."

---

### Post by steveneddy on 2008-03-08
> **NightwishFan said:**
>  It seems trivial.

I agree.

I may not be alone on this, but I don't use Linux for the special features.

I would rather it be reliable, stable and robust.

Maybe he needs a girlfriend. :D

---

### Post by WearZeeP on 2008-03-08
Sounds like an extremely unnessecary idea.
The Ubuntu development team need to focus on the things that is acctually needed right now, for 8.04.
And anyway, why would you have the need to be called sir by a computer? ;)

---

### Post by Mr. Picklesworth on 2008-03-08
Ubuntu already does greet you, though!
The GDM themes are called greeters, after all :)

Having said that, I wonder how much access those themes have to outside information and printing unique text? I can't say I have looked into the system myself, but maybe it's possible to create a greeter which does that.

---

### Post by NightwishFan on 2008-03-08
Well the dam thing better be polite to me. :)
I deleted the Windows crapware.

---

### Post by -random on 2008-03-08
lol ye... but don't make it 'too friendly' like that windoze paper-clip!!! omw that fails [-(

---

### Post by NightwishFan on 2008-03-08
[IMG]http://members.ozemail.com.au/~lbrash/msjokes/blue-screen-of-death.gif[/IMG]

---

### Post by hyperair on 2008-03-08
NightwishFan, I'd like to request compensation for permanent head damage induced by excessive head-desking.

Back on topic, you could add it to the startup programs in the Sessions configurator.
```

padsp espeak "Greetings, boss"

```

---

### Post by Redenbacher on 2008-03-08
That's the amazing thing about Ubuntu, and Linux in general... if you want it to do something, you can generally make it do whatever it is you want it to do yourself! 

Whereas windows just says, " This is how it's going to be $&#@%, take it or leave it. However, if you give me some more cash for my deep pockets, I'm sure we can figure out something *similar*."

---

### Post by tretle on 2008-03-08
I don't think this idea is that bad... in fact I think its a quite good one... Maybe not have ubuntu use the speakers to greet and tell you the weather unless accessibility requires it. 
I was always a bit apprehensive about seeing the widgets being drawn to the screen when gnome loads, especially with desktop effects enabled because the gnome panel would look broken while it loads, awn doesn't look the best while loading either. 
These things can give the user the impression of an unfinished piece of software when in reality its as finished as it could be its just that the open source community doesn't really think about the small details when it comes to appearance. 
What I think should be done is have everything from the moment you hit grub to the moment you hit gnome aesthetically match. No Brown blank screen in between the gdm and gnome... no broken looking widgets being drawn on the screen before your eyes... This guys idea could be a nice thing to greet the user while gnome loads the widgets in the background and would use the same amount of time as waiting for the widgets to be drawn to the screen. after the greet everything would be loaded in the gnome desktop instantly and not one by one in front of your eyes. 
So all in all I think its a good idea.

---

### Post by -random on 2008-03-08
> **-random said:**
> lol ye... but don't make it 'too friendly' like that windoze paper-clip!!! omw that fails [-(

rofl :) umm... seems iv'e quoted myself!! :/ meant to quote your pic!

---

### Post by NCLI on 2008-03-08
Well, it's just something I think would add to the interaction with the OS, but hell, it's not important. Also, I never said I wanted my computer to call me sir, haha! Anyway, I never said it had to be through speak, just some text on the screen while loading the settings and such would be fine.

It would be a nice feature for 8.10 though.

Lastly, are there any other voices for espeak? :p

tretle: My thoughts exactly. The gnome panles are damn ugly too while loading, especially if you have a transparent background image for them.

---

### Post by smartboyathome on 2008-03-08
You can do it now, see above. It probably won't be implimented in GNOME since it arguably offers less options to the default user in order to keep it simple.

---

### Post by NCLI on 2008-03-09
> **smartboyathome said:**
> You can do it now, see above. It probably won't be implimented in GNOME since it arguably offers less options to the default user in order to keep it simple.

I haven't seen any post detailing how to do exactly what I described i  the OP - could you please point me to it?

---

### Post by smartboyathome on 2008-03-09
> **hyperair said:**
> NightwishFan, I'd like to request compensation for permanent head damage induced by excessive head-desking.

Back on topic, you could add it to the startup programs in the Sessions configurator.
```

padsp espeak "Greetings, boss"

```

Here is how to do it, you can change the text (Greetings, boss) to whatever you would like.

---

### Post by Mr. Picklesworth on 2008-03-10
I find this idea kind of amusing, so I'm toying with a script to run when I log in to my session.

So far:
```

#!/bin/bash

espeak "Greetings, `who | awk -F' ' '{ print $1 }' | sort | uniq > list2; while read record; do cat /etc/passwd | grep $record | cut -d: -f5; done < list2; rm list2`" #No idea how that humumgous line of commands does it, I just pulled it from a Unix forum
espeak "Today is `date +'%A, %B %d, %Y'`. The time is `date +'%I:%M %p'`"
espeak "The system is now running at a load average of `cat /proc/loadavg`" #Any way to get /just/ the first number?
espeak "You have mail" #Will a command tell us via Evolution Data Server?

```

---

### Post by NightwishFan on 2008-03-10
:) cool

Espeak is just fun to mess with. I apologize for any umm "head desking".

---

### Post by Omnios on 2008-03-10
Hi k I like the it just works approach but think a vocal greeting would be great. Not just because it is kewl but rather because it is something different. A text greeting would be interesting but would not have a shock value. 
 
 As for a focal greeting it might be interestng as a shock value as in holy .... this is awsome . This is more or a marketing aspect but this has a few possibilities for certain things. Voice recognision is way off . Only system that works good is a actual hardware card system that totallt blows everything else away, as it works. 
 
 There is another aspect to this is vocal feedback. Such as say a hall voice saying hello tom or good morning tom. This is a simple approach but complicated as in there are many many usernames and languages. This might be addressed with vocal language packs where you can say if your username it tom you can download the t-en files. 
 
 Now the big part here is other options for other stuff. Which actually makes the greeting more desirable as it will be part of a lot of other features with vocal feedback. 
 
 For example if you have dial up and are trying to connect you can do a: the line is bussy b: The modem is dialing, the modem is authenticating, you are now connected at 6kbs. Your connection has been droped or timed out. This can actually be usefull if running in the background while playing full screen games for example. 
 
 There are also other usefull stuff such as say a lm-sensors plug in wich can do stuff like say your cpu is running very hot at 60* etc for example. This can also tie into other things such as say a clock or a day organizer. So you can say set a time reminder and it could say it is now this is your 1:30 reminder etc. 
 
 Even more importantly you can have stuff like your root account is being accessed or there is another user trying to log on to this computer. 
 
 Though voice recognition controll is way off, voice based feedback is a possibility now. 
 
 As for shock value I think this would give vista users a shock and a reason to try the wonderfull world of Ubuntu.

---

### Post by lime4x4 on 2008-03-10
My screen saver comes on then i have to type in my password to unlock my desktop. Would it be possible to have a script like the login one posted above run?

---

### Post by smartboyathome on 2008-03-10
> **lime4x4 said:**
> My screen saver comes on then i have to type in my password to unlock my desktop. Would it be possible to have a script like the login one posted above run?

I don't think so, since it doesn't really "start" but just restores your session back to the state it was in before your screensaver came on.

---

### Post by rhenrick on 2008-03-15
> **Mr. Picklesworth said:**
> I find this idea kind of amusing, so I'm toying with a script to run when I log in to my session.

So far:
```

#!/bin/bash

espeak "Greetings, `who | awk -F' ' '{ print $1 }' | sort | uniq > list2; while read record; do cat /etc/passwd | grep $record | cut -d: -f5; done < list2; rm list2`" #No idea how that humumgous line of commands does it, I just pulled it from a Unix forum
espeak "Today is `date +'%A, %B %d, %Y'`. The time is `date +'%I:%M %p'`"
espeak "The system is now running at a load average of `cat /proc/loadavg`" #Any way to get /just/ the first number?
espeak "You have mail" #Will a command tell us via Evolution Data Server?

```

That is pretty rad! NOOB question ... how could i auto-activate this script each time i log in / boot up? Do i type anything specific into the sessions menu?

thank you for your help in advance.

---

### Post by hyperair on 2008-03-15
Save it into a file, give it execution permissions. Then, put the path of the file into Sessions as a command.

---

### Post by Danijel Snajder on 2008-04-04
Wau, excellent idea, SCI-FI...

Well I remember my first time with knopix, they have some sexy female voice with each start-up saying something like "initializing, and something other, dont remember exactly, and i fall in love with linux :)

---

### Post by Danijel Snajder on 2008-04-04
It doesnt need to be flexible, can be pre-rendered...
Like some system sound scheme, for every event...
To speak some sexy female voice, it can be ...
For login to say somethig (like: system up and running, have a nice day), for logout to say something, for error someting, for...
You know what i mean, to hear computer speaking to you, like in sci-fi movies...

If this cant be in ubuntu, let someone try to make something like this and post it... I will download first :)

---

### Post by bfakefree on 2008-04-05
> **Omnios said:**
> Hi k I like the it just works approach but think a vocal greeting would be great. Not just because it is kewl but rather because it is something different. A text greeting would be interesting but would not have a shock value. 
 
 As for a focal greeting it might be interestng as a shock value as in holy .... this is awsome . This is more or a marketing aspect but this has a few possibilities for certain things. Voice recognision is way off . Only system that works good is a actual hardware card system that totallt blows everything else away, as it works. 
 
 There is another aspect to this is vocal feedback. Such as say a hall voice saying hello tom or good morning tom. This is a simple approach but complicated as in there are many many usernames and languages. This might be addressed with vocal language packs where you can say if your username it tom you can download the t-en files. 
 
 Now the big part here is other options for other stuff. Which actually makes the greeting more desirable as it will be part of a lot of other features with vocal feedback. 
 
 For example if you have dial up and are trying to connect you can do a: the line is bussy b: The modem is dialing, the modem is authenticating, you are now connected at 6kbs. Your connection has been droped or timed out. This can actually be usefull if running in the background while playing full screen games for example. 
 
 There are also other usefull stuff such as say a lm-sensors plug in wich can do stuff like say your cpu is running very hot at 60* etc for example. This can also tie into other things such as say a clock or a day organizer. So you can say set a time reminder and it could say it is now this is your 1:30 reminder etc. 
 
 Even more importantly you can have stuff like your root account is being accessed or there is another user trying to log on to this computer. 
 
 Though voice recognition controll is way off, voice based feedback is a possibility now. 
 
 As for shock value I think this would give vista users a shock and a reason to try the wonderfull world of Ubuntu.

This idea is kicks ***, voice feed-back, this will inturn put pressure on voice re-gonition to take off,   yeah Ubuntu developes put this in, time to pull ahead and have M$ copy linux

---

### Post by Zyphrexi on 2008-04-06
I'm more interested in fast boots, low resource usage, and high compatability/performance with my hardware.

although I suppose that could be helpful for assistive technologies, which can always use fresh ideas.

---

### Post by bfakefree on 2008-04-07
> **Zyphrexi said:**
> I'm more interested in fast boots, low resource usage, and high compatability/performance with my hardware.

although I suppose that could be helpful for assistive technologies, which can always use fresh ideas.

boring lol... only joking, but still why all this drab talk, sure u will want Ubuntu to work on some old computer in a 3rd world country, but it wont be long before those old computers will be running Intel duo core processors, its like why are the ISPs providing 20Mbs links and we only getting 4Mbs throughput or High Def TV technology from over 20 years ago only taking off now, Ubuntu can either copy and play catch up to M$ or move ahead, Talking to your computer will happen, will it be Apple, M$ or Linux to win the battle.

---

