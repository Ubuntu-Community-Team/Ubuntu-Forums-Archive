---
title: "laggy Wow"
date: 2010-05-23
forum: Wine
---

### Post by sprinda on 2010-05-23
okay How do I help with the lagg in WOW?

it is so laggy I  had to wait 30 sec to move an inch .

Is there a way to fix my wine to be less lagg? 

my guild wars works

---

### Post by dardack on 2010-05-23
> **sprinda said:**
> okay How do I help with the lagg in WOW?

it is so laggy I  had to wait 30 sec to move an inch .

Is there a way to fix my wine to be less lagg? 

my guild wars works


Didn't give much info, graphics card, specs of computer, version of wine, did you change in the Config.wtf to:


SET gxApi "OpenGL"

---

### Post by sprinda on 2010-05-23
> **dardack said:**
> Didn't give much info, graphics card, specs of computer, version of wine, did you change in the Config.wtf to:
 
 
SET gxApi "OpenGL"
 
nivida graphic card 
 
the version of wine last I checked was from 8.10 I have now upgraded to 10.04
512 ram ( it works on xp windows before changing to ubuntu)
 
I dont know how to update wine I bet I need to change it.
 
please talk to me like a moron to fix it lol 
 
I am still a noob at ubuntu          ](*,):-({|=:confused:

---

### Post by dardack on 2010-05-23
> **sprinda said:**
> nivida graphic card 
 
the version of wine last I checked was from 8.10 I have now upgraded to 10.04
512 ram ( it works on xp windows before changing to ubuntu)
 
I dont know how to update wine I bet I need to change it.
 
please talk to me like a moron to fix it lol 
 
I am still a noob at ubuntu          ](*,):-({|=:confused:



512mb is low, way low for wow, even in XP, i can't run it in XP without 2gigs myself.

in <wow directory>/WTF/ directory, look for Config.wtf file, add:

SET gxApi "OpenGL"

to the end.

As far as wine goes, winehq.org

---

### Post by sprinda on 2010-05-28
okay I had to reinstall my ubuntu after my cuz messed it up. 

I did as you said it worked and now I have this and it wont start

this application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception

program: z:\media \Shiva\World of Warcraft\wow.exe

Exception: 0xc00000005 (ACCESS_VIOLATION) at 0073:376cb490

the instruction at 0x376cb490 referenced memory at 0x376cb490
the memory could not be "read"

press OK to terminate the application[IMG]http://file:///home/sprinda/Desktop/Screenshot.png[/IMG]

---

### Post by sprinda on 2010-05-28
should I just go back to XP on this or how do I configure wine to play wow? I need to test my guild wars see if it still works

---

### Post by asdfoo on 2010-05-30
you need to install WoW in Wine or atleast try copying it from your windows partition (I see you might be trying to run it from there which is likely to cause problems)

---

### Post by cwwilson721 on 2010-06-01
Not only "likely" to give that error, but just about guaranteed.

Since you already have wine installed, just mount your WotLK DVD (Google it. you need to 'unmask' the DVD before the installer is seen), and run the install program on the DVD using wine.

I usually don't mess with my WTF file, I just add "-opengl" to the end of the launcher command. (That way, I can just copyover my Win7 WoW install, not worry about that stuff)

As to your lag...Live with it. WoW has had some BAD lag lately. I usually am at about 75-100, but lately it's been 125-400, and a few times, 4000+. Sometimes a restart/reboot will fix it, sometimes a router reboot, sometimes a modem reboot. Sometimes, nothing helps.

---

