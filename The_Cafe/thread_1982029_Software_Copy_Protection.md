---
title: "Software Copy Protection"
date: 2012-05-17
forum: The Cafe
---

### Post by TheCaculator1980 on 2012-05-17
We are looking to implement ESD for our software application.  Can anyone recommend an affordable and reliable software DRM solutions?

---

### Post by Artemis3 on 2012-05-20
Anything you do will probably get cracked by someone in Russia or anyplace your lawyers can't reach. Do your users a favor: Don't.

Maybe what you need to do is reconsider your business model, perhaps going open source and sell your services instead.

"Copy Protection" has been tried since the dawn of personal computers in the 80ies, and every single one of them have been defeated, one way or the other. DRM tends to punish your legitimate users, causing them annoyances (and increasing your support overhead); whereas the crack users have a much better (just works) experience.

One of the reasons people move to Free Software is to put and end to that endless cycle, to have software that "just works" without having to hunt obscure cracks or dealing with abusive "protection" schemes.

If your software is server oriented (ie. online multiplayer game) you could simply use a subscription model, no need to charge for the client.

---

### Post by Erik1984 on 2012-05-20
Just don't do DRM.

---

### Post by del_diablo on 2012-05-20
Just rename the archive files extensions to something else. Its roughly the best format of security. Secondly: They don't have the source code, so they can't actually sell good support.

---

### Post by eriktheblu on 2012-05-20
In my estimation, the only worthwhile copy protection would be to have the application subscription based. Keys can be cracked, processor and MAC IDs can be faked, call homes can be rerouted.

For course, private servers for MMOs are common enough... it might be hopeless.

---

### Post by Dr. C on 2012-05-21
Here is a suggestion. Before going with any DRM "solution" take a good look at the performance of Microsoft stock. Compare the period 1985 - 2000, when the company sold software without DRM with the period 2000 - today when the company sells its software with DRM and spends billions of dollars to implement and support DRM. 

Now ask the following question: Which return would you rather give your owners and shareholders?

---

### Post by KiwiNZ on 2012-05-21
Direct share price comparisons tell you nothing without taking into account prices ex dividend andshare splits. You also make comparisons with  revenue etc.

---

### Post by Dr. C on 2012-05-21
Of course you do. Take the total return on investment including reinvested dividends for both periods. It like two completely different companies one a stellar performer the other pathetic.

---

### Post by rai4shu2 on 2012-05-21
> **TheCaculator1980 said:**
> We are looking to implement ESD for our software application.  Can anyone recommend an affordable and reliable software DRM solutions?

The best copy protection is a nice high price. No one ever uploads a $5000 application to the scene.

---

### Post by 3rdalbum on 2012-05-21
> **rai4shu2 said:**
> The best copy protection is a nice high price. No one ever uploads a $5000 application to the scene.

Not true. Krackers work in every industry in the world. They can simply borrow their workplace's copy of that $5000 program to krack. I've seen very expensive software on warez sites.

To the OP: Reconsider. You can spend thousands of dollars inconveniencing your legitimate customers with DRM, and still have your work put on warez sites; or you can save that money and use a subscription-based model or have no DRM and give your users a good experience with your product.

If this is Linux software, you should know that Linux users are very ANTI-DRM and may simply avoid a DRM-infested product rather than buy a license. In short, your sales will be higher without copy prevention on Linux. They'll be close to nil if you implement copy prevention.

---

### Post by rasmus91 on 2012-05-23
> **rai4shu2 said:**
> The best copy protection is a nice high price. No one ever uploads a $5000 application to the scene.

Im definitely not openly admitting that one of my friends who programs a lot, used a cracked version of the most expensive version of M$ visual studio. no, thats now a 5000$ program. its more like 20000$

no DRM will go uncracked. im not a hacker, and i do not know how to crack a program, but im just sayin, if history has shown us anything, it is that the hackers are always one step ahead.

---

### Post by rg4w on 2012-05-23
True, all forms of security are ultimately crackable.  But most of those with the skillz to crack warez would probably never be paying customers anyway, so you needn't worry about them.  The key is to find a solution which merely provides enough security to not be worth the trouble for the average person to crack, or the risks involved with downloading cracked files and keygens, many of which are just Trojan horses.

To completely discourage all forms of software protection will only continue to dissuade software publishers from porting to Ubuntu.  No one wins with that.

If you prefer only free software by all means exercise that right, but I like to think of The Fifth Freedom as the freedom to choose proprietary software if it does what you need for a price you find acceptable.

---

### Post by Bandit on 2012-05-23
> **TheCaculator1980 said:**
> We are looking to implement ESD for our software application.  Can anyone recommend an affordable and reliable software DRM solutions?

I seriously doubt you will get any DRM recommendations from anyone here.
Your best bet is to not be greedy with the software prices and charge more for tech support where you can setup accounts for users paying for tech help.

---

### Post by donkyhotay on 2012-05-23
This is a bad forum to be asking questions about DRM, especially about implementing DRM. As mentioned previously many linux users are very anti-DRM (including me, it's one of the main reasons I made the switch) and while you *might* get the kind of response you're looking for, 99% of what you're going to get here is "don't use it". My advice of course is to not use it (for the reasons posted previously) but if you *really* want to know the best DRM implementation scheme you're better off posting on a MS or apple based developers forum and know that I'll never buy your software (whatever it does).

---

### Post by roelforg on 2012-05-23
Shoving aside my fierce opposition to drm for a second here...

How were you going to do it anyway on linux?
As you can edit every file and you need the source to make it work on any distro.
There are 14 major version of ubuntu (counting from 5.04 as that where ubuntu started to pick up steam) in widespread use today (ever noticed how old the versions are some around here use?) alone. Even more when also counting the 32bit 64bit differences and the other major distros.
It's not practical to compile for each and every one yourself, that way you'd have to spend more money on compilation/building and hosting the packages then on development.

So for those reasons it's a requirement to release the source unless you have the resources to do the compilations or are prepared to only address a eeny teeny fraction of the linux community and miss out on a lot of income?
And with source code available, drm is moot.

Another strategy i've seen somewhere and worked for them was to release the source as gpl and accept patches and donations like most opensource software...
But they sold the binary packages, that way they saved a lot of money on the development by allowing others to contribute, a lot on compilation because they only compiled for the most popular five distros/versions (and both 32- and 64-bit builds) and the others could build from source.
The binary packages sold because humans are by nature "lazy" (no personal attack intended), they don't want to spend the time compiling themselves and are willing to spend a low amount of money for the binary packages as long as the purchase/install process is easy to follow and quick (e.g. direct downloads are a must).
And the others that either don't have money or have the time/knowledge to compile had the free source code.

That last one is something i'd like to see happen instead of drm.

---

### Post by MisterGaribaldi on 2012-05-23
Why in God's name would someone with any brains at all ask

[FONT="Book Antiqua"][SIZE="3"]"How can I implement DRM?"[/SIZE][/FONT]

on a message board which services

[FONT="Arial Black"][SIZE="6"][COLOR="Red"]the LINUX community?!?!?!?!?[/COLOR][/SIZE][/FONT]

---

### Post by chris200x9 on 2012-05-23
> **MisterGaribaldi said:**
> Why in God's name would someone with any brains at all ask

[FONT="Book Antiqua"][SIZE="3"]"How can I implement DRM?"[/SIZE][/FONT]

on a message board which services

[FONT="Arial Black"][SIZE="6"][COLOR="Red"]the LINUX community?!?!?!?!?[/COLOR][/SIZE][/FONT]

trolling?

---

### Post by thatguruguy on 2012-05-23
> **MisterGaribaldi said:**
> Why in God's name would someone with any brains at all ask

[FONT=Book Antiqua][SIZE=3]"How can I implement DRM?"[/SIZE][/FONT]

on a message board which services

[FONT=Arial Black][SIZE=6][COLOR=Red]the LINUX community?!?!?!?!?[/COLOR][/SIZE][/FONT]

Well, he hasn't come back. There's at least some chance that he was trolling the board.

---

### Post by KiwiNZ on 2012-05-23
Thread has been busted

---

