---
title: "Who's been DDOSing ubuntuforums the last few days?"
date: 2011-01-14
forum: The Cafe
---

### Post by TeoBigusGeekus on 2011-01-14
Cause I wanna know...

---

### Post by andymorton on 2011-01-14
It has been a bit slow over the last few days, although it seems pretty snappy at the moment.

---

### Post by TeoBigusGeekus on 2011-01-14
It's not only slow, but there's also the problem with the double (triple, quadruple, etc.) posts.
Something's going on...

---

### Post by Spice Weasel on 2011-01-14
Terrible ***-servers.

---

### Post by Spice Weasel on 2011-01-14
Double post... 6 minutes later?

---

### Post by Viva on 2011-01-14
Sounds like a database problem to me.

---

### Post by FuturePilot on 2011-01-14
> **Spice Weasel said:**
> Terrible ***-servers.

> **Spice Weasel said:**
> Terrible ***-servers.

i c wut u did thar.

---

### Post by sandyd on 2011-01-14
seems to be sporadic.
and doen't seem to be the network either, as im having problems even though all my network connections are routed through level3 (which is what ubuntufourms is served on).

Seems more like server overload to me...

---

### Post by sandyd on 2011-01-14
double post....
```

dolphina@dolphinaura.com [~]# traceroute ubuntuforums.org
traceroute to ubuntuforums.org (91.189.94.12), 30 hops max, 40 byte packets
 1  10gigabitethernet1-4.core1.phx1.he.net (184.105.213.17)  0.785 ms  0.787 ms  0.889 ms
 2  10gigabitethernet2-2.core1.lax1.he.net (72.52.92.249)  11.012 ms  11.082 ms  11.149 ms
 3  las-bb1-link.telia.net (213.248.67.141)  10.346 ms las-bb1-link.telia.net (213.248.70.37)  10.509 ms las-bb1-link.telia.net (213.248.67.141)  10.500 ms
 4  xe-4-2-0.edge1.LosAngeles9.Level3.net (4.68.110.221)  10.203 ms  10.279 ms  10.467 ms
 5  ae-63-60.ebr3.LosAngeles1.Level3.net (4.69.144.52)  21.282 ms  21.237 ms ae-83-80.ebr3.LosAngeles1.Level3.net (4.69.144.180)  21.245 ms
 6  ae-2-2.ebr3.SanJose1.Level3.net (4.69.132.9)  18.491 ms  18.646 ms  18.641 ms
 7  ae-83-83.csw3.SanJose1.Level3.net (4.69.134.234)  27.392 ms ae-73-73.csw2.SanJose1.Level3.net (4.69.134.230)  22.670 ms ae-93-93.csw4.SanJose1.Level3.net (4.69.134.238)  27.688 ms
 8  ae-64-64.ebr4.SanJose1.Level3.net (4.69.134.241)  32.322 ms  32.743 ms ae-94-94.ebr4.SanJose1.Level3.net (4.69.134.253)  32.571 ms
 9  ae-2-2.ebr2.NewYork1.Level3.net (4.69.135.186)  74.113 ms  74.116 ms  73.911 ms
10  ae-62-62.csw1.NewYork1.Level3.net (4.69.148.34)  74.518 ms ae-82-82.csw3.NewYork1.Level3.net (4.69.148.42)  80.729 ms ae-62-62.csw1.NewYork1.Level3.net (4.69.148.34)  80.947 ms
11  ae-61-61.ebr1.NewYork1.Level3.net (4.69.134.65)  74.310 ms ae-91-91.ebr1.NewYork1.Level3.net (4.69.134.77)  73.736 ms ae-61-61.ebr1.NewYork1.Level3.net (4.69.134.65)  74.313 ms
12  ae-42-42.ebr2.London1.Level3.net (4.69.137.69)  142.883 ms ae-43-43.ebr2.London1.Level3.net (4.69.137.73)  142.656 ms ae-41-41.ebr2.London1.Level3.net (4.69.137.65)  143.077 ms
13  4.69.143.85 (4.69.143.85)  143.090 ms 4.69.143.97 (4.69.143.97)  142.419 ms 4.69.143.89 (4.69.143.89)  144.942 ms
14  ae-3-3.ebr2.London2.Level3.net (4.69.141.190)  147.491 ms  148.143 ms  147.474 ms
15  * * *
16  gi1-0-1.oxygen.canonical.com (195.50.121.2)  148.143 ms  148.138 ms  145.610 ms
17  eth0.peumo.canonical.com (91.189.88.10)  143.238 ms  143.002 ms  143.464 ms
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *

```
the path is fine. (note, startpoint removed for security)

---

### Post by Queue29 on 2011-01-14
It must be this proprietary, closed source forum software. Yea. That's it.

---

### Post by handy on 2011-01-14
I have been experiencing the slowness of this forum lately also.

---

### Post by corrytonapple on 2011-01-14
> **Queue29 said:**
> It must be this proprietary, closed source forum software. Yea. That's it.
Nah, this stuff is pretty good.  Slowness drives me crazy for some reason.  IDK why.

---

### Post by kn0w-b1nary on 2011-01-14
> **Viva said:**
> Sounds like a database problem to me.
I was on these forums last night when everything stopped. After I opened a new tab and visited, The page said that there was a database error. :(

---

### Post by Quadunit404 on 2011-01-14
> **Queue29 said:**
> It must be this proprietary, closed source forum software. Yea. That's it.

Yeah, it's proprietary, commercial forum software, so therefore it MUST be the reason why! ](*,)

Proprietary or not, it's more than likely the database that's causing this loss of speed as all the evidence is stacking up to that conclusion. Maybe the site owner should try optimizing the database? Dunno if you can do that directly in vBulletin though.

---

### Post by red_Marvin on 2011-01-14
Has there been any statement from an actual forum staff member, or is the ddos rumour just--a rumour?

---

### Post by KiwiNZ on 2011-01-14
The Servers have been experiencing heavier than normal load.There is no DDOS'ing going on. We are currently investigating ways to eleviate the load.

This could mean that as a temporary measure some services or some Forums maybe turned off.

We apologise for this however it is better to have the Forum running than not at all.

---

### Post by tgalati4 on 2011-01-14
That is what happens when you break the 1% barrier.

---

### Post by sudoer541 on 2011-01-14
Call the internet police, people! :)
I am sure they will catch the criminal(s)!:D:P

---

### Post by NightwishFan on 2011-01-15
This has happened before since I have been here, they will sort it out. :)

---

### Post by foutes on 2011-01-15
Wonder if it has anything to do with the Boxxy post here in the cafe?

---

### Post by Khakilang on 2011-01-15
Time to upgrade the processor, RAM, hard disk and internet bandwidth and also software update too.

---

### Post by Ctrl-Alt-F1 on 2011-01-15
> **Quadunit404 said:**
> Yeah, it's proprietary, commercial forum software, so therefore it MUST be the reason why! ](*,)

Proprietary or not, it's more than likely the database that's causing this loss of speed as all the evidence is stacking up to that conclusion. Maybe the site owner should try optimizing the database? Dunno if you can do that directly in vBulletin though.

I hope you realize the person you quoted was joking.  :popcorn:

---

### Post by m4tic on 2011-01-15
No problems for opera mini users.

---

### Post by Elfy on 2011-01-15
> **Quadunit404 said:**
> Proprietary or not, it's more than likely the database that's causing this loss of speed as all the evidence is stacking up to that conclusion. 

At 146GB it probably has something to do with it ...

---

### Post by cpmman on 2011-01-15
> **forestpiskie said:**
> At 146GB it probably has something to do with it ...

Repair/Optimize Tables helps on my small board - not sure if it can be done with this monolith.

---

### Post by Elfy on 2011-01-15
I'd not know- I fix boats for a living :)

I leave that stuff to the server admin lot to worry about.

---

### Post by TeoBigusGeekus on 2011-01-15
```
DELETE FROM Posts_Table
WHERE YEAR(Date_of_post) <= 2007;
```

That should do it. :P

---

### Post by asifnaz on 2011-01-15
Because they are running their sever on Windows :P

---

### Post by cpmman on 2011-01-15
> **TeoBigusGeekus said:**
> ```
DELETE FROM Posts_Table
WHERE YEAR(Date_of_post) <= 2007;
```That should do it. :P

Losing a lot of valuable posts (including stickies) which are still valid advice to people (the purpose of UF).  Some pruning of non-bean forums with last postings beyond an appropriate date may help.

It may benefit to use vBulletin admin to delete users who are non-posters and have not visited the forums in the last n year(s).

Once they are removed the Table indexing tidy would help.

---

### Post by TeoBigusGeekus on 2011-01-15
> **cpmman said:**
> Losing a lot of valuable posts (including stickies) which are still valid advice to people (the purpose of UF).
Alright, alright...

```
DELETE FROM Posts_Table
WHERE YEAR(Date_of_post) <= 2007 AND Sticky_Flag=0;
```

---

### Post by bruno9779 on 2011-01-15
Deleting older posts is a better idea than it sounds.

I keep stumbling on ancient posts, which solution is not viable anymore

---

### Post by TeoBigusGeekus on 2011-01-15
> **bruno9779 said:**
> Deleting older posts is a better idea than it sounds.

I keep stumbling on ancient posts, which solution is not viable anymore
+1
Solutions for Feisty Fawn or Gutsy Gibbon are somehow irrelevant today...

---

### Post by Spice Weasel on 2011-01-15
Deleting all posts older than two years and all members with 0 posts older than 2 years is a great idea.

---

### Post by Joeb454 on 2011-01-15
We have been discussing some of the possible options suggested above for a while now, mainly in relation to the upgrade to vB4.

With the recent happenings, there's a possibility some action may be taken sooner, but it's hard to say, as no concrete decision ever came from the discussion, just similar ideas to what people have suggested here. Hopefully we'll be able to get this resolved soon, things appear a little better today.

---

### Post by MrGXZ on 2011-01-15
> **Spice Weasel said:**
> Deleting all posts older than two years and all members with 0 posts older than 2 years is a great idea.

Agreed. Once somebody had been registered for 2 years and has 0 posts, it's obvious they will most likely **never** come back.

---

### Post by squenson on 2011-01-15
To improve performance, please keep your messages as short as possible!

If you think about it for a few seconds, or a few minutes for some of you (not that I imply that some people are slower than others in their thinking, but simply that some people may not have several seconds of contiguous time to think about this topic and therefore will have to come back to it after a period of time of various length) we can all contribute a few bytes to speed up the entire ubuntuforum in this difficult period. I am sure that you understand the reasoning behind this approach: if each of us writes shorter messages in the future, the ubuntuforum database will grow at a lower pace and therefore we have more chances – although I cannot precisely calculate the probability nor the error margin – to get a marginal improvement of the display of the messages once the experts in database, who are certainly working hard at the moment I write this, and I want to take this opportunity to thank them and at the same time all the volunteers who are making this forum a fantastic place to be and without which I would not have become a true believer that Ubuntu, as a free operating system and I mean 'free' in his both meaning of 'free as a free beer' and 'free as opposite to proprietary' although you can also consider a third way of understanding this word, 'Free as as service provider in France for internet services, 29.99 euros per month' but it is not exactly the meaning I would consider as useful and meaningful here so please accept my apologies for this disgression, and that everyone who owns a computer should be allowed to use free software on it so the world would become a better place to leave and going back to my point about the experts who are making a fantastic job to fix the problems and who are facing exceptional difficulties or even going to unknown territories in the search of solutions (I would compare them to the pionneers who went to the Wild Wild West to only face challenges that they had to overcome in order to survive in a hostile environment – and the word hostile here is obviously not very much applicable and this is somewhat funny exactly the opposite of what Ubuntu, the Ubuntuforum and the community is, a friendly place to live in) that will make the ubuntuforum again and to be fair, as far as I know, this is the first time I am hearing of such performance issue so it would be too easy to blame the database administrators at the first small, but in a way annoying for may people who depend on this forum – I could name a few of them here but I am sure that they will recognize themselves without any problem, let me say hello to all of them and simply say 'courage, we will win this endless battle against bugs we have to keep united in this difficult moments which are certainly not the most joyful we have faced together' – and so a big, large, warm 'thank you' to all these anonymous guys who are behind their high-speed internet connections searching in gigabytes of data – have you simply thought a minute about how much a billion of characters represent, it is a fantastic number when I compare it to my old Tandy Radio Shack TRS-80 computer with 16,384 bytes of memory and which was using a plain tape recorder to store and read programs 'Ah!, the good old days' would say the nostalgic ones but I am not part of them and I am very pleased to have seen the development of those wonderful machines over the years – to fix or at least improve the performance of the Ubuntuforum and I would like to use a few smileys to show my appreciation but as they are more probably using additional bytes of colored pixels unless they are stored as text in the database and a clever process transform them 'on-the-fly' to little animated icons it would defeat the purpose of this message which is, as you have now understood, a vibrant appeal for all of us to make our messages as short and more than short, concise as possible, without, obviously, loosing the politeness that has made this forum very different from the many I am practicing over the Internet and I will conclude this by my favorite phrase from a French philosoph, Blaise Pascal “Je n'ai fait celle-ci [une lettre] plus longue que parce que je n'ai pas eu le loisir de la faire plus courte” which can be translated in English as “I would have written a shorter letter, but I did not have the time.”

---

### Post by squenson on 2011-01-15
To improve performance, please keep your messages as short as possible!

If you think about it for a few seconds, or a few minutes for some of you (not that I imply that some people are slower than others in their thinking, but simply that some people may not have several seconds of contiguous time to think about this topic and therefore will have to come back to it after a period of time of various length) we can all contribute a few bytes to speed up the entire ubuntuforum in this difficult period. I am sure that you understand the reasoning behind this approach: if each of us writes shorter messages in the future, the ubuntuforum database will grow at a lower pace and therefore we have more chances – although I cannot precisely calculate the probability nor the error margin – to get a marginal improvement of the display of the messages once the experts in database, who are certainly working hard at the moment I write this, and I want to take this opportunity to thank them and at the same time all the volunteers who are making this forum a fantastic place to be and without which I would not have become a true believer that Ubuntu, as a free operating system and I mean 'free' in his both meaning of 'free as a free beer' and 'free as opposite to proprietary' although you can also consider a third way of understanding this word, 'Free as as service provider in France for internet services, 29.99 euros per month' but it is not exactly the meaning I would consider as useful and meaningful here so please accept my apologies for this disgression, and that everyone who owns a computer should be allowed to use free software on it so the world would become a better place to leave and going back to my point about the experts who are making a fantastic job to fix the problems and who are facing exceptional difficulties or even going to unknown territories in the search of solutions (I would compare them to the pionneers who went to the Wild Wild West to only face challenges that they had to overcome in order to survive in a hostile environment – and the word hostile here is obviously not very much applicable and this is somewhat funny exactly the opposite of what Ubuntu, the Ubuntuforum and the community is, a friendly place to live in) that will make the ubuntuforum again and to be fair, as far as I know, this is the first time I am hearing of such performance issue so it would be too easy to blame the database administrators at the first small, but in a way annoying for may people who depend on this forum – I could name a few of them here but I am sure that they will recognize themselves without any problem, let me say hello to all of them and simply say 'courage, we will win this endless battle against bugs we have to keep united in this difficult moments which are certainly not the most joyful we have faced together' – and so a big, large, warm 'thank you' to all these anonymous guys who are behind their high-speed internet connections searching in gigabytes of data – have you simply thought a minute about how much a billion of characters represent, it is a fantastic number when I compare it to my old Tandy Radio Shack TRS-80 computer with 16,384 bytes of memory and which was using a plain tape recorder to store and read programs 'Ah!, the good old days' would say the nostalgic ones but I am not part of them and I am very pleased to have seen the development of those wonderful machines over the years – to fix or at least improve the performance of the Ubuntuforum and I would like to use a few smileys to show my appreciation but as they are more probably using additional bytes of colored pixels unless they are stored as text in the database and a clever process transform them 'on-the-fly' to little animated icons it would defeat the purpose of this message which is, as you have now understood, a vibrant appeal for all of us to make our messages as short and more than short, concise as possible, without, obviously, loosing the politeness that has made this forum very different from the many I am practicing over the Internet and I will conclude this by my favorite phrase from a French philosopher, Blaise Pascal “Je n'ai fait celle-ci [une lettre] plus longue que parce que je n'ai pas eu le loisir de la faire plus courte” which can be translated in English as “I would have written a shorter letter, but I did not have the time.”

---

### Post by asifnaz on 2011-01-15
> **squenson said:**
> To improve performance, please keep your messages as short as possible!

If you think about it for a few seconds, or a few minutes for some of you (not that I imply that some people are slower than others in their thinking, but simply that some people may not have several seconds of contiguous time to think about this topic and therefore will have to come back to it after a period of time of various length) we can all contribute a few bytes to speed up the entire ubuntuforum in this difficult period. I am sure that you understand the reasoning behind this approach: if each of us writes shorter messages in the future, the ubuntuforum database will grow at a lower pace and therefore we have more chances – although I cannot precisely calculate the probability nor the error margin – to get a marginal improvement of the display of the messages once the experts in database, who are certainly working hard at the moment I write this, and I want to take this opportunity to thank them and at the same time all the volunteers who are making this forum a fantastic place to be and without which I would not have become a true believer that Ubuntu, as a free operating system and I mean 'free' in his both meaning of 'free as a free beer' and 'free as opposite to proprietary' although you can also consider a third way of understanding this word, 'Free as as service provider in France for internet services, 29.99 euros per month' but it is not exactly the meaning I would consider as useful and meaningful here so please accept my apologies for this disgression, and that everyone who owns a computer should be allowed to use free software on it so the world would become a better place to leave and going back to my point about the experts who are making a fantastic job to fix the problems and who are facing exceptional difficulties or even going to unknown territories in the search of solutions (I would compare them to the pionneers who went to the Wild Wild West to only face challenges that they had to overcome in order to survive in a hostile environment – and the word hostile here is obviously not very much applicable and this is somewhat funny exactly the opposite of what Ubuntu, the Ubuntuforum and the community is, a friendly place to live in) that will make the ubuntuforum again and to be fair, as far as I know, this is the first time I am hearing of such performance issue so it would be too easy to blame the database administrators at the first small, but in a way annoying for may people who depend on this forum – I could name a few of them here but I am sure that they will recognize themselves without any problem, let me say hello to all of them and simply say 'courage, we will win this endless battle against bugs we have to keep united in this difficult moments which are certainly not the most joyful we have faced together' – and so a big, large, warm 'thank you' to all these anonymous guys who are behind their high-speed internet connections searching in gigabytes of data – have you simply thought a minute about how much a billion of characters represent, it is a fantastic number when I compare it to my old Tandy Radio Shack TRS-80 computer with 16,384 bytes of memory and which was using a plain tape recorder to store and read programs 'Ah!, the good old days' would say the nostalgic ones but I am not part of them and I am very pleased to have seen the development of those wonderful machines over the years – to fix or at least improve the performance of the Ubuntuforum and I would like to use a few smileys to show my appreciation but as they are more probably using additional bytes of colored pixels unless they are stored as text in the database and a clever process transform them 'on-the-fly' to little animated icons it would defeat the purpose of this message which is, as you have now understood, a vibrant appeal for all of us to make our messages as short and more than short, concise as possible, without, obviously, loosing the politeness that has made this forum very different from the many I am practicing over the Internet and I will conclude this by my favorite phrase from a French philosopher, Blaise Pascal “Je n'ai fait celle-ci [une lettre] plus longue que parce que je n'ai pas eu le loisir de la faire plus courte” which can be translated in English as “I would have written a shorter letter, but I did not have the time.”

You are right

---

### Post by Zero2Nine on 2011-01-15
> **MrGXZ said:**
> Agreed. Once somebody had been registered for 2 years and has 0 posts, it's obvious they will most likely **never** come back.

I came back after 3 years without any post :P But I agree that's an exception and if my account was deleted I would've understood.

---

### Post by TeoBigusGeekus on 2011-01-15
> **squenson said:**
> To improve performance, please keep your messages as short as possible!

If you think about it for a few seconds, or a few minutes for some of you (not that I imply that some people are slower than others in their thinking, but simply that ..................................................
```
DELETE FROM Posts_Table
WHERE (YEAR(Date_of_post) <= 2007 AND Sticky_Flag=0) OR Paragraph_Usage=0;

```

---

### Post by chriswyatt on 2011-01-15
```
DELETE FROM Posts_Table
WHERE (YEAR(Date_of_post) <= 2007 AND Sticky_Flag=0) OR Character_Count > 1000 && Paragraph_Usage=0;
```

That should do it.

---

### Post by ki4jgt on 2011-01-15
> **teobigusgeekus said:**
> +1
solutions for feisty fawn or gutsy gibbon are somehow irrelevant today...

+ 1

---

### Post by ki4jgt on 2011-01-15
> **chriswyatt said:**
> ```
DELETE FROM Posts_Table
WHERE (YEAR(Date_of_post) <= 2007 AND Sticky_Flag=0) OR Character_Count > 1000 && Paragraph_Usage=0;
```

That should do it.

Be sure to allow users who have tech problems the ability to post more :-)

---

### Post by KiwiNZ on 2011-01-15
We deactivate accounts in some circumstances. Deleting accounts causes Database corruptions and other stability issues so we do not do it.

---

### Post by TeoBigusGeekus on 2011-01-15
> **KiwiNZ said:**
> We deactivate accounts in some circumstances. Deleting accounts causes Database corruptions and other stability issues so we do not do it.

What about ancient posts?

---

### Post by KiwiNZ on 2011-01-15
We archive them away so they do not affect the day to day performance

---

### Post by KiwiNZ on 2011-01-15
We archive them away so they do not affect the day to day performance

---

### Post by themarker0 on 2011-01-15
Double post.

---

### Post by themarker0 on 2011-01-15
KiwiNZ, I have a question. Why not just Split the DB to say, 2008, and merge it unto a free forum software? I know the merge system of MyBB would do that. It'd just take time, it wouldn't timeout. I'm sure getting rid of that many posts from the DB would optimize it quite a bit.

---

### Post by matthekc on 2011-01-15
If throwing money at the problem would work I'll donate.

---

### Post by cpmman on 2011-01-15
> **KiwiNZ said:**
> We deactivate accounts in some circumstances. Deleting accounts causes Database corruptions and other stability issues so we do not do it.

Whilst my board is nowhere near this size I do not understand why deleting accounts with no posts and no visits in the preceding n periods would cause corruption if using vBulletin admin.  It did not in mine and gave a useful leeway following indexes rebuild.

Deleting threads and/or posts may lead to indexing problems but if approached sensibly in stages can provide similar benefits.

---

### Post by CharlesA on 2011-01-15
> **cpmman said:**
> Whilst my board is nowhere near this size I do not understand why deleting accounts with no posts and no visits in the preceding n periods would cause corruption if using vBulletin admin.  It did not in mine and gave a useful leeway following indexes rebuild.

Deleting threads and/or posts may lead to indexing problems but if approached sensibly in stages can provide similar benefits.
The problem with deleting accounts is that the posts that are linked to them do not go with the account, and it can cause things to break.

---

### Post by cpmman on 2011-01-15
> **CharlesA said:**
> The problem with deleting accounts is that the posts that are linked to them do not go with the account, and it can cause things to break.

Which is why I specified accounts with no posts (and no recent visits to the forum).

(edit: this is easily quantified in admin.)

---

### Post by Quadunit404 on 2011-01-15
> **Ctrl-Alt-F1 said:**
> I hope you realize the person you quoted was joking.  :popcorn:

Sarcasm be difficult to detect on the 'net.

---

### Post by Joeb454 on 2011-01-15
> **cpmman said:**
> Which is why I specified accounts with no posts (and no recent visits to the forum).

There's still the possibility of that user deciding to come back to the forum though. And as it's not in our Code of Conduct, or any official policy of any kind, that we delete accounts after X months/years I would be rather against doing so.

The option has been discussed, but we have no plans to do anything like this in the foreseeable future.

---

### Post by cpmman on 2011-01-15
> **Joeb454 said:**
> There's still the possibility of that user deciding to come back to the forum though. And as it's not in our Code of Conduct, or any official policy of any kind, that we delete accounts after X months/years I would be rather against doing so.

The option has been discussed, but we have no plans to do anything like this in the foreseeable future.

My experience of doing this showed that those persons who had been removed were quite happy to re-register and did not hold a grudge.

---

### Post by disabledaccount on 2011-01-15
Removing "inactive" users with 0 posts wont help much - guests are reading existing threads, active users will write posts as usual - so server/db engine load won't change at all.
True solution is to get faster (dedicated) server with more bandwidth together with archiving old threads.

---

### Post by bapoumba on 2011-01-15
> **cpmman said:**
> My experience of doing this showed that those persons who had been removed were quite happy to re-register and did not hold a grudge.

Another reason not to remove accounts is that a lot of spammers could come back and use the spam usernames and emails over again. We spend enough time cleaning once, I'm not sure we would like to go over the same account multiple times..

---

### Post by bapoumba on 2011-01-15
> **tomazzi said:**
> Removing "inactive" users with 0 posts wont help much - guests are reading existing threads, active users will write posts as usual - so server/db engine load won't change at all.
True solution is to get faster (dedicated) server with more bandwidth together with archiving old threads.

We've already been archiving in the past. We can do it again. We've been pruning too. iirc, it took several days for 2 people to clean things out, something like 500,000 posts, maybe more. A few months later, we were back at the same level.

---

### Post by chriswyatt on 2011-01-15
> **CharlesA said:**
> The problem with deleting accounts is that the posts that are linked to them do not go with the account, and it can cause things to break.

That seems like rather a rubbish design fault to me.

---

### Post by Elfy on 2011-01-15
> **bapoumba said:**
> Another reason not to remove accounts is that a lot of spammers could come back and use the spam usernames and emails over again. We spend enough time cleaning once, I'm not sure we would like to go over the same account multiple times..

> **chriswyatt said:**
> That seems like rather a rubbish design fault to me.

This is the reason we don't want to delete accounts.

---

### Post by CharlesA on 2011-01-15
> **chriswyatt said:**
> That seems like rather a rubbish design fault to me.

Happens on other forum software as well. It's not a design fault.

---

### Post by chriswyatt on 2011-01-15
> **CharlesA said:**
> Happens on other forum software as well. It's not a design fault.

I would've thought after deleting an account there would be a certain period where no one would be able to use that username, that way spammers would be able to come back, but not for say 2 years (or a set amount of time).  Though their posts wouldn't be linked to an account and I guess would just show their username at the time, the username would be greyed out so would suggest it's nothing to do with anyone else who may be using that username.

Ideally deleting a user would disassociate that user with all his posts but the posts would still remain (or their username would be linked with a unique number incase their account is re-activated).  The reason why I said it's a design fault is that I think this should be the sort of situation that is accounted for when the forum software is written.

---

### Post by Johnsie on 2011-01-15
Hahah, now I know why so many threads get locked... They are too cheap to invest in bigger hard drives and are fighting to conserve disk space :-)

I knew it wasn't really excessive censorhip for the good of the community.

IMO opinion the first thing to go will be recurring discussions... That's where they bury the topics they don't like anyway. Not too many people visit that forum, so it's a good place to hide something that doesn't contravene the code of conduct but could be embarrasing ;-)

Delete it!! Get rid of those evil Windows vs. Linux threads

Lol, jk... I hope they get the issues sorted out quicky.

---

### Post by CharlesA on 2011-01-15
> **chriswyatt said:**
> I would've thought after deleting an account there would be a certain period where no one would be able to use that username, that way spammers would be able to come back, but not for say 2 years (or a set amount of time).  Though their posts wouldn't be linked to an account and I guess would just show their username at the time, the username would be greyed out so would suggest it's nothing to do with anyone else who may be using that username.

That's not how it works. Once a username is gone it's "free."

> Ideally deleting a user would disassociate that user with all his posts but the posts would still remain (or their username would be linked with a unique number incase their account is re-activated).  The reason why I said it's a design fault is that I think this should be the sort of situation that is accounted for when the forum software is written.

That is what happens now. The posts remain, but once a username is deleted, it is free to be used again.

---

### Post by themarker0 on 2011-01-16
What about my solution? Splitting threads from 200X and setting it as an archieve only forum that is completely seperate.

---

### Post by castrojo on 2011-01-16
Is there a way to do some google robot indexer magic to make archived posts not rank so highly on Google? 

I think having an archive makes sense and is useful, but it can be infuriating when the correct (and usually easier!) solution is on page 2 of google and page 1 is filled with related threads from intrepid or something that recommend hard/workaround things that would be easy today.

---

