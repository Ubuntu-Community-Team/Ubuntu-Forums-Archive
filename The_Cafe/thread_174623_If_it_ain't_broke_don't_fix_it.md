---
title: "If it ain't broke don't fix it?"
date: 2006-05-12
forum: The Cafe
---

### Post by sophtpaw on 2006-05-12
Greetings,

Thought this question might fit more in the cafe environment, as it isn't a technical question.

I just wondered whether it was worth upgrading to Dapper?
They say if it ain't broke don't fix it. It seems such a hassle to have to start all over again. 
Is Dapper really better, and what is actually the difference. I imagine one just gets the latest of everything, but besides that? functionally speaking it is still the same os, no?!
It annoys me that just as i get snug to have to pick up and start again as i already said. 
Apparently one can just update from breezy which isn't any hassleof course but in reality what i hear is that the done thing is to make a fresh install, and that is when it gets troublesome. Seeing what i want to save and back up to carry across with me in terms of valuable documentation email etcetc...aside from having to re-configure and thematise a fresh install to look the way it did in the previous install aswell.

arrghh...

People might say, hey, don't worry you can stay in breezy, it'll remain supported for x amount of time, but knowing most people will have moved on to Dapper aswell... one doesn't want to be left behind...but then i'm still on my donkey and it gets me to where i am going even if it isn't as fast as everyone else

just my thoughts...

sophtpaw

---

### Post by mostwanted on 2006-05-12
If there's no new feature in Dapper that you need, yeah, why upgrade? Just remember that once Dapper is out, this whole community will quickly transition to the new version and you'll be left alone in a corner with your outdated software :p

j/k

---

### Post by Virogenesis on 2006-05-12
Dapper is faster upon boot up, more polished off, has newer apps and generally better than breezy.

that good enough? ;)

---

### Post by Titus A Duxass on 2006-05-12
I agree with you "if it ain't broke don't fix it" policy.
I do not think I will upgrade on my wife's pc, but I may for my test bench pc.

By the way, you can make fresh installations a lot easier if you have a separate /home partition.  With a separate /home partition you do not need to move your documents, etc. (apart from address books and bookmarks).  Just be careful during the partition phase of the install and ubuntu will not touch the existing data.

---

### Post by matthew on 2006-05-12
I would say don't upgrade now unless you enjoy tinkering. If Breezy is working for you, keep it at least until Dapper is officially released--maybe a month or so after that. Dapper will have a 3 year support cycle, so it should be a good choice to keep for a long time without upgrading if everything works as you want/need it to.

---

### Post by sophtpaw on 2006-05-12
[QUOTE=Titus A Duxass]I agree with you "if it ain't broke don't fix it" policy.
I do not think I will upgrade on my wife's pc, but I may for my test bench pc.

By the way, you can make fresh installations a lot easier if you have a separate /home partition.  With a separate /home partition you do not need to move your documents, etc. (apart from address books and bookmarks).  Just be careful during the partition phase of the install and ubuntu will not touch the existing data.[/QUOTE]
Titus, 
What do you mean by a separate /home partition? :confused:  please bear in mind that you're talking to a noob here. 

sophtpaw

---

### Post by sophtpaw on 2006-05-12
[QUOTE=mostwanted] Just remember that once Dapper is out, this whole community will quickly transition to the new version and you'll be left alone in a corner with your outdated software :p

j/k[/QUOTE]

[COLOR="DarkOrange"]That is my Fear exactly! Alone in a corner with old software :( [/COLOR]

:D

---

### Post by sophtpaw on 2006-05-12
[QUOTE=matthew]I would say don't upgrade now unless you enjoy tinkering. If Breezy is working for you, keep it at least until Dapper is officially released--maybe a month or so after that. Dapper will have a 3 year support cycle, so it should be a good choice to keep for a long time without upgrading if everything works as you want/need it to.[/QUOTE]

thx, matthew,

No, i hate tinkering. And, so i wasn't going to upgrade now anyways. But i realise that the date for the new release is looming and it is then i don't want to be left behind in a corner :)  
Hence, i am wondering if i can just do an upgrade then, eventually, as you say a month in or so, or is it really better to do a fresh install. I'd rather avoid as much  tinkering as possible. It's heartening to hear about this /home directory solution aswell, but i need to hear more exactly how that works,

regards,

sophtpaw

---

### Post by Virogenesis on 2006-05-12
he basically means don't do a standard ubuntu install....partion off the drive properly so basically /home is on its own partion that way when you come to reinstall you don't lose your /home settings.

Think of partions like how they would be on windows..... c:\, e:\.... do you get me?

---

### Post by sophtpaw on 2006-05-12
[QUOTE=Virogenesis]he basically means don't do a standard ubuntu install....partion off the drive properly so basically /home is on its own partion that way when you come to reinstall you don't lose your /home settings.

Think of partions like how they would be on windows..... c:\, e:\.... do you get me?[/QUOTE]

If i understand you right, when inserting the Dapper install cd when i get to partitions manually delete all except /home?

I get you about not loosing /home settings but not clear how i would make a fresh install while saving those. Is /home something i would back up? and install within Dapper?

sophtpaw

---

### Post by eentonig on 2006-05-12
If all you need is in Breezy. and it's the way you want it. Why bother being left alone in a corner? You already got everything you need.

And it 'll stay supported for a while. So security and bugs will remain up to date.

Hey, I still know a few companies who are still working on DOS boxes. and they're happy.

---

### Post by Titus A Duxass on 2006-05-12
As Virogenesis confirmed you make a separate /home partition during the install process.

I usually end up with something like this (going from memory):

hda1 / 5gb bootable
hda2 /home 74gb or whatever is spare in your disc
swap of 1 gb.

I cannot show my table now but can give further guidance when I get home if necessary.

Basically when you come to the partition phase for the first time with a new disc let it do the default partiton, this will establish a single partition plus the correct swap space.

Then click on the back buttons until you get to the main menu where you can start the partition phase again.
Now select manual partitioning, delete the existing partition but keep the swap space.

Now create a / partition of between 5-10gb, make it bootable.
Now create a /home partition using the remaining space.

When you come to do a fresh install during the partition phase you can select the / to be formatted ready for new distro and you can select on the /home so that it will not be touched.

That is a very rough guide from memory.

No doubt there is someone who can correct any blunders that I have written.

---

