---
title: "Cooling a Wiring Closet"
date: 2005-09-11
forum: The Cafe
---

### Post by Mr. Electric Wizard on 2005-09-11
Hello,
I am trying to figure out a way to cool a wiring closet in my home.
I have installed my cable modem, an IPCop firewall, and a ClarkConnect server, as well as a gigabit switch in a coat closet in my home.
Everything is going great, but I installed a thermometer in the closet, and the temperature reaches approx. 93 deg. F (33.9 C).
This seems really hot!

I have a couple of ideas on how to fix the problem:
1) I have been throwing around the idea of putting in a Louvered door, then sucking hot air out of the closet and into the hallway.
2) Route one of my A/C ducts into the closet.

I am wondering if any of you have been in a similar situation and how have you overcome the heat issue?
I just really don't want to boil my servers...
 :)

---

### Post by adwait on 2005-09-11
33 C.........hot???? Wherever do you stay? Around here, that's the day time temeperature in summer! Anyway, I doubt that 33 C should cause any problem to any hardware.

---

### Post by Mr. Electric Wizard on 2005-09-11
Then why do you always see corporate server rooms that are sooo cold I wonder?
It might not be a problem, just a concern of mine.

---

### Post by Kvark on 2005-09-11
[QUOTE=Mr. Electric Wizard]Then why do you always see corporate server rooms that are sooo cold I wonder?
It might not be a problem, just a concern of mine.[/QUOTE]
If the room is hot then you need more fans to stay cool. (This is true for both meanings of the word "fan")

I think server rooms are cold because it makes the cooling fans' job easier. Cold air isn't neccessary but it's more effective for cooling then hot air so you need less airflow if the air is cold.

---

### Post by Mr. Electric Wizard on 2005-09-11
Ahh I see...
I just installed a fairly large fan to move the air around a little better, I'll see if it helps.
Thanks

---

### Post by Buffalo Soldier on 2005-09-11
How about trying two fans? One pushing air into the closet (lower position) and another pulling air out (higher position). Not sure if its going to make much difference, just throwing some ideas.

Hope you'll manage to solve the heat problem and share with us the solution.

---

### Post by xmastree on 2005-09-11
That's what I was thinking. moving air around isn't the answer. Moving hot air out and cool air in is.
However, I also agree with adwait. 33C isn't hot.

Do you live in a cold or hot climate? If it's cold, put a fan in the top of the door so that the warm air comes into the house. If it's a hot climate, put a fan in the ceiling of the cupboard so that the heat goes into the roof space.

---

### Post by Mr. Electric Wizard on 2005-09-11
I think I have my answer.

1)  I put a fan in and left it running for a couple of hours with the door to the closet shut - same temperature.  So the fan with the door closed didn't do anything...

2)  I simply left the closet door open a little bit, and the temperature dropped about 10 deg.  (wow).

3)  What I am going to do is get a louvered door from my local all-in-one-hardware shop.  That way it will have the effect of having the door open, but will look good too.  Then If I have to, I can hook up a fan to pull hot air out into the attic.

Thanks for all the suggestions! :)

***BTW***
What would be considered too hot for an ambient temperature for a server closet?

---

### Post by BWF89 on 2005-09-11
Could you post a picture of your server room / closet?

---

### Post by drizek on 2005-09-11
33C is pretty good. if it was in the 50s, then you should be worried. dont add fans in there cause its just going to make noise and its also going to heat up your house.

---

### Post by WildTangent on 2005-09-11
[QUOTE=BWF89]Could you post a picture of your server room / closet?[/QUOTE]
33 C is about the normal temp around here this time of year :P its really not that bad, i wouldnt worry about it

-Wild

---

### Post by bootlinux on 2005-09-11
I work on HVAC and  computer room Liebert equipment. If the room is 90+ degrees the the internal temperature of the equipment could be a lot higher. The cooler the equipment the better it will run and longer it will last. It wouldn't take long to fry your stuff if your AC breaks down. Open the door and set a fan on the floor at the door way blowing into the room. That's the best way to circulate the air through the room. Cool air blows in low and hot air goes out high. This could help heat your house in the winter but adds to the cooling load on the AC in the summer. If you're serious about keeping your stuff running 24/7 I would suggest adding a small AC unit just for the closet. That way you have a backup if one of the Ac's break down.

---

### Post by TravisNewman on 2005-09-12
The problem is that, since you put it in the closet, you probably don't want to look at it :) I'd suggest getting a door vent with a fan attached to the inside of the door, blowing air in, and a fan somewhere at the top (I'd have to see your house to know where) blowing out. That way the door stays closed, air circulates and stays cool, and you're good.

---

### Post by Mr. Electric Wizard on 2005-09-12
[QUOTE=panickedthumb]The problem is that, since you put it in the closet, you probably don't want to look at it :) I'd suggest getting a door vent with a fan attached to the inside of the door, blowing air in, and a fan somewhere at the top (I'd have to see your house to know where) blowing out. That way the door stays closed, air circulates and stays cool, and you're good.[/QUOTE]

Yup, exactly...
I already found one with louvers that I am going to install...

---

### Post by Mr. Electric Wizard on 2005-09-12
[QUOTE=BWF89]Could you post a picture of your server room / closet?[/QUOTE]

Yeah, will do.  I'll get some after work today and post.

Been working on this project for a while now, and just now got done (proud parent, heehee).
 :)

---

### Post by Mr. Electric Wizard on 2005-09-15
Here you go guys:

---

### Post by Mr. Electric Wizard on 2005-09-15
**Above, you can see the cable modem on the far left.
**Just to right of that you can see my SMC 8 Port Gigabit switch.
**Behind those you can see the power outlet I installed, along with the modular rj45 block.
**On the far right you can see my IPCop box. (amd k6 333)
**Just to the left of that you can see my ClarkConnect server. (amd k6 333)

Finally done!
I am still going to install a louvered door so that I can close the door without worrying too much about heat.

---

### Post by xmastree on 2005-09-15
Hmm... not much space behind the computers, where the exhaust fans are. I would rotate them, so that the back panel is facing the center of the space to improve the airflow.

Are there any additional case fans? If not, consider fitting some. If you don't want to turn the units round, then fit the extra fans in the left side of the cases.

Or, why not just open the cases? Looking at the wiring, you're not too bothered about how it looks...  :wink:  So removing the covers would allow more airflow.

Do you ever use the CDs? Disconnect them if not, less load on the PSUs means less heat.

---

### Post by BWF89 on 2005-09-15
Thanks for the photos.

---

### Post by wmcbrine on 2005-09-16
[QUOTE=xmastree]Or, why not just open the cases? Looking at the wiring, you're not too bothered about how it looks...  :wink:  So removing the covers would allow more airflow.[/QUOTE]I disagree. Most cases are designed for proper airflow when closed. If you open the case, the fans cease to work at full efficiency -- they draw air in from everywhere, instead of from the front vents, passing over the circuitry, cooling it.

My suggestion would be to take out the coats. Probably not what you want to hear, though. :)

---

### Post by xmastree on 2005-09-16
[QUOTE=wmcbrine]I disagree. Most cases are designed for proper airflow when closed. [/QUOTE]Good point, although I was taking into account the desk fan in there, which would blow air directly at the motherboard.

On a similar topic, why don't case manufacturers make the rear panel fan grille removable? I mean, a 3" x 3" plate full of holes is rather restrictive. They ought to make it snap out, like the slot covers, for those of us who want to improve airflow by fitting a proper grille. 

I realise it has to be there to stop your fingers entering the fan, but it should be easy to remove.

I usually cut mine out and keep my fingers well away. Look at the pic, imagine how much more air comes out from the hole, compared to if the fan was strangled by the 'grille' in the location just above it.

If the fan blades don't get you, the sharp edges will!  :eek:

---

### Post by Mr. Electric Wizard on 2005-09-16
I think I am going to fit a couple of 80 mm case fans to the inside of the louvered door (once I install it).  The case fans will be at the very top of the door (top louvers), and suck hot air out of the closet.

---

### Post by graabein on 2005-09-16
[QUOTE=Mr. Electric Wizard]**Above, you can see the cable modem on the far left.
**Just to right of that you can see my SMC 8 Port Gigabit switch.
**Behind those you can see the power outlet I installed, along with the modular rj45 block.
**On the far right you can see my IPCop box. (amd k6 333)
**Just to the left of that you can see my ClarkConnect server. (amd k6 333)[/QUOTE]

I love a good rack... What I want to know is where you got your penguin stickers? I am going full GNU/Linux now. No more [COLOR=SlateGray]Designed for Microsoft Windows[/COLOR] in my house!

---

### Post by Mr. Electric Wizard on 2005-09-16
I got them from Directron.com.
I just did a search on their site for "Tux" i think.
They were pretty cheap, like $5.00 (US) for 5.

I wondered if anyone would notice! :) 

All my friends think I'm crazy to spend the amount of time I spent on retrofitting rj45 into my house...  So much more secure, and so much faster...

Now if I could just get my Gigabit Ethernet card to work in my Ubuntu box. :neutral: 
Anybody heard any updates on gigabit support with kernel 2.6.13?

---

### Post by Mr. Electric Wizard on 2005-09-16
[QUOTE=graabein]No more [COLOR=SlateGray]Designed for Microsoft Windows[/COLOR] in my house![/QUOTE]

What's funny is that the HP box on the left actually has that sticker on the front. :grin:

---

### Post by gw90se on 2005-09-16
Another suggestion. Why not add the small bathroom style fan in the ceiling to exhaust the heat into the attic?

---

### Post by Mr. Electric Wizard on 2005-09-16
I thought about that, but it would have to run all the time, and I don't really want my A/C from the house being redirected out to the attic 24/7... :)

---

### Post by godzero on 2005-09-16
Your door idea is great, the thermometer is great, but I would at least pull the cpus out a bit for air (around the back). 

After that, let it go for a day or two, the re-read the temp. It should be fine.

Oh, another thing... ya, disconnect the cdroms, and anything else you don't need every day like videocards. If you put new/more fans in the cases, go for the big-but-slow ones; more efficient and quieter. Probably cheaper too.

The table fan isn't helping. If anything it's hurting (with normal door). I assume  the light's only on when you're digging around in there.

---

### Post by BENSTER on 2005-09-16
Unless you have really tight carpet to the bottom of your closet door, just exahusting the air out the top should get the closet to room tempature.  Although Routing your A/C duct in there seems like a really good idea, Computer Decks in business constantly run the cooler 24/7 365 days a year - except for the two times every year we shut down the cooling towers, to disinfect the system.  I'd give up on this idea immediatly.  Besides, when you turn the heat on, You'd have to disconnect the system.

If you constantly vent the closet in to a small bedroom, your going to heat up your room eventually, then you'll want the air out of there too.  Regardless think about fans.

Small "in wall" fans are not very common, but you should be able to find one in  Heating/cooling shop, or somewhere that sells wood burning stoves.  I've seen a small one  approx 6" x 6" before, and it had a plastic gril to attach on both sides of walls.  You simply cut out a proper hole, and insert the fan housing - which will block the hollow wall - and attach yoru wall plates.  The hardest part regarding this would be runnign electrical wires through the wall. A rheostat should be included to adust the fan speed.  By exhausting the hot air out the top, and keeping your closet doors shut, you'll be drawing cooler air in the bottom of the door, and through the crack of a bi-fold door.  This would be yoru cheapest permanent solution.

If you want colder air than the room, I'd recommend making a vent to your basement and drawing the cool air from there...but still exhausting hot air from the top.  If yoru not worried about looks, you could run a piece duct form the basement to the top of the closet to suck the hot air down the the baesment.  This would allow you to put a fan in the baement, instead of the room, and keep it quiet.

Letting your hard drives get 33 celcius can be bad for them.  when you turn off the computer, they will cool rapidally, and possibly warp.  Heat is bad.  :)  I monitor my case/HD/CPU,  24/25/35~48 (depending on 3d games or not.

---

### Post by Mr. Electric Wizard on 2005-09-16
[QUOTE=godzero]Your door idea is great, the thermometer is great, but I would at least pull the cpus out a bit for air (around the back). 
[/QUOTE]

I did pull them out a bit further, but I guess the picture is an optical illusion because both cases were approx 6 cm away from the wall already.

[QUOTE=godzero]
The table fan isn't helping. If anything it's hurting (with normal door). I assume  the light's only on when you're digging around in there.[/QUOTE]

Yeah, the light is only on when I'm messing around in there.
The table fan was there for an experiment, and you are correct, it did not help at all... :)

---

### Post by Mr. Electric Wizard on 2005-09-16
[QUOTE=BENSTER]Unless you have really tight carpet to the bottom of your closet door, just exahusting the air out the top should get the closet to room tempature.  Although Routing your A/C duct in there seems like a really good idea, Computer Decks in business constantly run the cooler 24/7 365 days a year - except for the two times every year we shut down the cooling towers, to disinfect the system.  I'd give up on this idea immediatly.  Besides, when you turn the heat on, You'd have to disconnect the system.

If you constantly vent the closet in to a small bedroom, your going to heat up your room eventually, then you'll want the air out of there too.  Regardless think about fans.

Small "in wall" fans are not very common, but you should be able to find one in  Heating/cooling shop, or somewhere that sells wood burning stoves.  I've seen a small one  approx 6" x 6" before, and it had a plastic gril to attach on both sides of walls.  You simply cut out a proper hole, and insert the fan housing - which will block the hollow wall - and attach yoru wall plates.  The hardest part regarding this would be runnign electrical wires through the wall. A rheostat should be included to adust the fan speed.  By exhausting the hot air out the top, and keeping your closet doors shut, you'll be drawing cooler air in the bottom of the door, and through the crack of a bi-fold door.  This would be yoru cheapest permanent solution.

If you want colder air than the room, I'd recommend making a vent to your basement and drawing the cool air from there...but still exhausting hot air from the top.  If yoru not worried about looks, you could run a piece duct form the basement to the top of the closet to suck the hot air down the the baesment.  This would allow you to put a fan in the baement, instead of the room, and keep it quiet.

Letting your hard drives get 33 celcius can be bad for them.  when you turn off the computer, they will cool rapidally, and possibly warp.  Heat is bad.  :)  I monitor my case/HD/CPU,  24/25/35~48 (depending on 3d games or not.[/QUOTE]

Man, I wish we had basements here! :)

---

### Post by occy8 on 2005-09-16
Looking at the pictures that big fan only contributes to the heat because it doesn't get rid of the excess temperature it just moves it around and its motor heats up too

best thing to do would be to suck air in with a fan at the bottom and cover the fan with a dust matt.
Then have some kind of exhaust near the top of the cabinet above your equipment.
And leave some space around the computer

---

