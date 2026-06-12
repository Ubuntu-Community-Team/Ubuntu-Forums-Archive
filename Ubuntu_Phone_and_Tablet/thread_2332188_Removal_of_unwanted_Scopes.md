---
title: "Removal of unwanted Scopes?"
date: 2016-07-29
forum: Ubuntu Phone and Tablet
---

### Post by sapporodan on 2016-07-29
[COLOR=#333333][FONT=&amp]Apologies if this is not the right place for this question or it&#8217;s been asked 100 times before. I did post the original question on Ask Ubuntu they told me to post the question on Launchpad, and nobody seemed to answer it there. So for a last attempt ill try here!
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Firstly whoever decided to add the Cellular Data on/off to the menu in OTA-12, You&#8217;re a genius thank you, very much appreciated.
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Right the question. As I never use thescopes I want to remove 95% of them, just to keep the phone clean and to give quickaccess to the ones I do use. There also seems to be a large amount of unwanted files attached to these and it&#8217;s all clogging up my phones tiny amountof free space.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I know there are ways to remove them manually, but really not very confident using the terminal, h[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma]ow safe is this method[/FONT][/COLOR][COLOR=#333333][FONT=Tahoma] or is there another way to remove all these? 
[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]Apart from this one annoyance, I really like the OS and so [/FONT][/COLOR][FONT=Tahoma][COLOR=#333333]I really hope this is not F-ing bloatware(oh look more Amazon and what is this 8Coupons rubbish Grrrrr!) that we can&#8217;t remove. Does anyone know if there will bean update in the future that will allow me to uninstall them like I can with other scopes? For texts and emails we have that lovely method of sliding right to get to the rubbish icon, why cant we use that for scopes?[/COLOR][/FONT]
[COLOR=#333333][FONT=&amp]
Cheers.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Dan[/FONT][/COLOR]

---

### Post by mw4jet2 on 2016-08-02
Hi sapporodan,

I am a real noob with the U-phone but I did find how to set and remove the Scopes. Say on the "Today" Scope, across the top to the right of "Today" is a star, a gear, and the search icon. Touch the star and the Scope should be removed.

If you mean to totally remove them from the device, I believe you can go to the store, search scopes and scroll through the list, the ones installed will have a check mark and you select that scope, a uninstall and a launch button will be presented.

---

### Post by sapporodan on 2016-08-03
Hi Mw4jet2, thanks for replying.

I have gone through the Ubuntu store and erased every one I can remove from the device, but there still seems to be so many that i cant find in the store.

7digital
8coupons 
Amazon
Cinema
ebay
Holidays
open Library
Reddit
Shopping
Wikipedia
Yahoo finance

and maybe a few more I may remove. 

I am sure people use and enjoy them, so no problem they were pre-installed, but the reason I bought this phone was to be rid of the typical Spyware/Bloatware you find on most mobiles these days, so its frustrating I cant get rid of them. 

All they are doing is clogging up the menu and taking up space. I think I remember reading about a way to remove them, but cant remember how, I know it was done via the Terminal.

---

### Post by mily2 on 2016-08-03
Hi,

Read my post: [https://ubuntuforums.org/showthread.php?t=2326159](https://ubuntuforums.org/showthread.php?t=2326159)

It's very frustrating. After remove scopes via UT Tweak Tool, Ubuntu Store or click unregister these continue to appear in System Settings\About\Storage

Command line: click unregister <name_of_scope_ as_ generated_by_click_list> --user=phablet
[SIZE=3]
[/SIZE][SIZE=3]
[/SIZE][SIZE=3]
[/SIZE]

---

### Post by sapporodan on 2016-08-04
This sounds like a nightmare to remove them!!! 

How do we officially contact the developers about it?

I tried putting this question on Launchpad. But it was just ignored!!!

---

### Post by howefield on 2016-08-04
> **sapporodan said:**
> ....How do we officially contact the developers about it?

A good place to be is on the [mailing list]("https://launchpad.net/~ubuntu-phone"). Also, many developers participate in the IRC channel #ubuntu-touch on Freenode.

---

### Post by sapporodan on 2016-08-04
Thanks Howefield.

---

### Post by mily2 on 2016-08-04
> **sapporodan said:**
>  I think I remember reading about a way to remove them, but cant remember how, I know it was done via the Terminal.
click unregister <name_of_scope_ as_ generated_by_click_list> --user=phablet

Howefield's advice is great.
As I say in my post there's this bug: [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824)

---

