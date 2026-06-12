---
title: "[SOLVED] &amp;quot;Cherry keyboard for linux&amp;quot; Cant wait? Your posts here!"
date: 2007-09-26
forum: The Cafe
---

### Post by Docula79 on 2007-09-26
Ive just been reviewing the new keyboard designed 4 linux systems. It looks amazing. Tux keys instead of crappy win keys and a healthy 29 hot keys for tasks such as flicking through web pages, music, cut and paste and lots more. It is not wireless which is a shame and it will set u back around  GBP30. This aside, it is definately something that i will b buying. Its available in october. If ya wanna review it yourself just google it. "linux keyboard" shud do the trick. Let me know Your thoughts. Post away. :

---

### Post by mips on 2007-09-26
[http://www.cherrycorp.com/english/cymotion-line/cymotion-line_master_linux.htm](http://www.cherrycorp.com/english/cymotion-line/cymotion-line_master_linux.htm)

Why not simply paste a link ?

---

### Post by n3tfury on 2007-09-26
> **Docula79 said:**
> If ya wanna review it yourself just google it. "linux keyboard" shud do the trick. Let me know Your thoughts. Post away. :

why bother posting if you're going to pull that crap?

---

### Post by Docula79 on 2007-09-26
Pull wot crap. I dont know how 2 add links and i dont know why Your being so blunt. I am new and thought id strike up a conversation. Wots wrong wiv wot i wrote? I thought people wud b interested. Why so harsh? If i wanted grief i wud ave joined a windows forum. Give us a break.

---

### Post by SupaSonic on 2007-09-26
Reading your posts is like deciphering a code...

---

### Post by Docula79 on 2007-09-26
Why? It looks fine 2me. Have i broken any rules?

---

### Post by Lord Illidan on 2007-09-26
I think he means, can you type in normal English? Don't use 2 instead of to, for example. Not everyone is a native English speaker, and not everyone understands sms-type language.

---

### Post by Docula79 on 2007-09-26
Sorry about that. I use my phone in the day time to go online. Having 3 kids makes it hard to use the pc. I will take notice of my sms type writing and sort it out. There was me thinking you were all picking on the newbie. Sorry again. Thanks for letting me know. Duncan. :-)

---

### Post by Lord Illidan on 2007-09-26
> **Docula79 said:**
> Sorry about that. I use my phone in the day time to go online. Having 3 kids makes it hard to use the pc. I will take notice of my sms type writing and sort it out. There was me thinking you were all picking on the newbie. Sorry again. Thanks for letting me know. Duncan. :-)
No problem..

---

### Post by Vadi on 2007-09-26
That looks awesome. If I wasn't on a laptop, I'd definitely get one :)

---

### Post by n3tfury on 2007-09-26
looks cool, but i wonder how good it feels.

---

### Post by ezphilosophy on 2007-09-26
Don't worry about it Docula79.  I don't think they were trying to be harsh.
Anyway, thanks for the info.  I'm checking it out right now!

---

### Post by Polygon on 2007-09-26
i still kinda dont like the tux key. now instead of one operating system having their logo on a keyboard, we have another. I personally think something neutral should be on ALL keyboards (a diamond or something) 

but multimedia keys look cool.

---

### Post by Paul820 on 2007-09-26
Looks good to me,  i will get one. My other keyboard needs replacing. :)

---

### Post by imagine on 2007-09-26
Hmm this keyboard is available in Germany since 2004. I didn't write on it yet, so I can't comment about it, but Cherry keyboards are usually good and reliable.

---

### Post by olejorgen on 2007-09-26
> **Docula79 said:**
> Pull wot crap. I dont know how 2 add links and i dont know why Your being so blunt. I am new and thought id strike up a conversation. Wots wrong wiv wot i wrote? I thought people wud b interested. Why so harsh? If i wanted grief i wud ave joined a windows forum. Give us a break. 
Well, you could just have posted the url. True, it does not take much time to google it up, but why should 50+ people do it when one is enough?

Great initiative (the keyvoard), but kinda ugly imho.

---

### Post by jrusso2 on 2007-09-26
> **Docula79 said:**
> Pull wot crap. I dont know how 2 add links and i dont know why Your being so blunt. I am new and thought id strike up a conversation. Wots wrong wiv wot i wrote? I thought people wud b interested. Why so harsh? If i wanted grief i wud ave joined a windows forum. Give us a break.

I thought only american's spoke like this?

---

### Post by ThinkBuntu on 2007-09-26
> **SupaSonic said:**
> Reading your posts is like deciphering a code...
Came across clearly to me. You guys need to live closer to international cities where you discover syntactical patterns of English you never imagined, through a coarse or slurred or just plain wrong accent :^)

Love DC!

---

### Post by mips on 2007-09-26
> **jrusso2 said:**
> I thought only american's spoke like this?

How do chavs speak ?

Anyway, I saw some of the OPs other posts and he seams to be using SMS speak etc. The code of conduct says something about this on in Section 1.9

---

### Post by sr20ve on 2007-09-26
> **Docula79 said:**
> Pull wot crap. I dont know how 2 add links and i dont know why Your being so blunt. I am new and thought id strike up a conversation. Wots wrong wiv wot i wrote? I thought people wud b interested. Why so harsh? If i wanted grief i wud ave joined a windows forum. Give us a break.

You've been watching too much Ali G.


OBTW, nice keyboard.

---

### Post by RAV TUX on 2007-09-26
> **Setting Linux up to use the Cherry CyMotion Master Linux USB keyboard**
One of the reasons I got the Cherry CyMotion Master Linux key board was to have not only a Linux styled keyboard but to have a USB keyboard, my previous keyboard was a classic AT with a PS2 adaptor !

It was getting a bit shabby, what with the dremeled off Windows keys and the neon string I wove under the keys, not mention the classic cream and grey color scheme.
  
The Cherry Cymotion is a very nice keyboard with large tops to the keys, nice feedback feel and of course it has the TUX logo and 26 extra keys!
Comes with software to control the keyboard but only for the PS2 version, thats right does not work on the original playstation ;) 

To enable the keys in the USB mode you have to patch the kernel (or wait until it becomes part of the release kernel [2.6.15 does not need patching but earlier versions may be OK as well]).
This involves taking the hid_core.c.diff(for kernel 2.6.11.7 see end of doc) from the driver CD and applying it to a copy of the kernel source code you have ready to be recompiled into a new blend of Linux kernel.

It might be possible patch and build only the module but I could find no reference to building integral kernel modules, only device driver extra type modules.

This was surprisingly easy, but depends on how your Linux system is setup, so check the documentation specific to your distribution.


Once you have got your new patch kernel running try 

** xmodmap -pk**

Look for key 112 or anything higher, most likely you will only see the normal keys.
Then run this to get the scan codes of the extra keys.

**xev | grep "state 0x0, keycode" | uniq**

[xev can be obtained through most distribution systems, rpm, emerge, deb etc or you can get the source from [http://xorg.freedesktop.org/](http://xorg.freedesktop.org/)(anyone got a direct link?)]

It will open a new window, ignore that, do not move the mouse and press each one of the extra keys on your keyboard once.
Then close the window, you will see a long list one for each key pressed plus the enter key.

Take this list (minus the enter key) and format it into *keycode ### = NAME* where ### is the keycode number and NAME is the name you want to assign the key.
Save this in your home directory as [.Xmodmap]("http://www.jumpstation.co.uk/linux/cymotion/.Xmodmap") (or just download mine, or copy the following [specific to >=Xorg 7]) [B]keycode 234 = CM_BACK
keycode 233 = CM_FORWARD
keycode 232 = CM_KILL
keycode 231 = CM_RELOAD
keycode 122 = CM_MAGNIFY
keycode 162 = CM_PLAYPAUSE
keycode 164 = CM_STOP
keycode 144 = CM_PREVIOUSTRACK
keycode 153 = CM_NEXTTRACK
keycode 204 = CM_EJECT
keycode 161 = CM_CALC
keycode 236 = CM_MAIL
keycode 130 = CM_HOME
keycode 227 = CM_POWER
keycode 188 = CM_CUT
keycode 192 = CM_COPY
keycode 248 = CM_PASTE
keycode 138 = CM_REDO
keycode 135 = CM_UNDO
keycode 115 = CM_TUX
keycode 116 = CM_MAILTO
keycode 174 = CM_MINUS
keycode 176 = CM_PLUS
keycode 160 = CM_MUTE
keycode 129 = CM_MEDIA
[/B]
Thats the first step, now as root edit the **/usr/lib/X11/XKeysymDB**(or **/usr/share/X11/XKeysymDB**) file and **append** one line per key in the format *NAME :########* where the ######## has to be unique in the file, I used the format 10090### where the final ### was the keycode and NAME is the identifer we assigned the key in the Xmodmap step above.
Again, download my [XKeysymDB.extra]("http://www.jumpstation.co.uk/linux/cymotion/XKeysymDB.extra") or copy the following.[specific to >=Xorg 7]
[B]CM_BACK :10090234
CM_FORWARD :10090233
CM_KILL :10090232
CM_RELOAD :10090231
CM_MAGNIFY :10090122
CM_PLAYPAUSE :10090162
CM_STOP :10090164
CM_PREVIOUSTRACK :10090144
CM_NEXTTRACK :10090153
CM_EJECT :10090116
CM_CALC :10090161
CM_MAIL :10090236
CM_HOME :10090130
CM_POWER :10090112
CM_R1 :10090159
CM_R2 :10090151
CM_R3 :10090171
CM_R4 :10090133
CM_R5 :10090135
CM_COPY :10090248
CM_PASTE :10090109
CM_CUT :10090188
CM_L2 :10090143
CM_L1 :10090125
CM_WEIRD :10090115
CM_TUX :10090116
CM_CONTEXT :10090117
CM_MINUS :10090174
CM_PLUS :10090176
CM_MUTE :10090160
CM_MEDIA :10090129
[/B]
 Now restart X and then in a console window type 

**xmodmap ~/.Xmodmap**

And when you run

**xmodmap -pk**

again, you can see all your new keycodes.

Note: each time you restart X you will need to tell xmodmap to load your .Xmodmap file so put the command in your ~/.xinitrc or equivalent.

Each window/desktop manager has its own way of allowing you to map keys to actions.

In KDE 3.3.1 go to "Control Center" and "Regional & Accessibility" and then either select "Keyboard Shortcuts" or "KHotKeys".
"Keyboard Shortcuts" allows you to assign keys to specific KDE actions and "KHotKeys" allows you to assign keys to applications, amongst other things.

I hope you found this useful, I had an interesting time finding out how to do the above !

any comments hate mail etc to [ [EMAIL="linux.cymotion@jumpstation.co.uk"]linux.cymotion@jumpstation.co.uk[/EMAIL] ] [<font color=&quot;#0000ff&quot;>linux.cymotion (AT) jumpstation.co.uk</font>] 

**Kernel 2.6.11.7** (and possibly higher) please try the [patch]("http://www.hexten.net/sw/cymotion/cymotion-2.6.11.7.patch") from [hexten.net]("http://www.hexten.net/")


Thanks goto Richard Grant for the Xorg 7, .xinitrc and other information.


Have not braved the >=Xorg 7 modular update ? fear not you can get the old files here :
[.Xmodmap-pre-Xorg7]("http://www.jumpstation.co.uk/linux/cymotion/.Xmodmap") 
[XKeysymDB.extra-pre-Xorg7]("http://www.jumpstation.co.uk/linux/cymotion/XKeysymDB.extra") (for **/usr/X11R6/lib/X11/XKeysymDB**(or **/usr/share/X11/XKeysymDB**))

[root]("http://www.jumpstation.co.uk/")
[http://www.jumpstation.co.uk/linux/cymotion/](http://www.jumpstation.co.uk/linux/cymotion/)

---

### Post by adamorjames on 2007-09-26
I think using an OS logo on a default keyboard key is not right.

---

### Post by nonewmsgs on 2007-09-26
it looks expensive.

---

### Post by Kingsley on 2007-09-26
Err... I'd rather buy a Microsoft or Logitech keyboard that works just as fine with Linux at a lower price.

---

### Post by RAV TUX on 2007-09-26
> **Kingsley said:**
> Err... I'd rather buy a Microsoft or Logitech keyboard that works just as fine with Linux at a lower price.

I think I would rather buy a more expensive [Razer Keyboard]("http://www.razerzone.com/index.php?main_page=product_info&products_id=40"). ;)

> **Anti-Ghosting Capability** 
With the anti-ghosting capability of the Razer Tarantula™, you can press up to an unprecedented 10 buttons at one go without the "ghosting" effect (For a conventional keyboard, signal failure occurs when three to four keys are pressed simultaneously). This means more commands can now be executed at any one time.           

    **Onboard Profile Memory**
With a 32KB onboard memory – Powered by Razer Synapse™ – up to five onboard profiles for different games can be stored. So no matter which LAN party you go to, all you need to do is bring your Razer Tarantula™ along, and you're ready to play.           

    **A Keytop That is Eight Times as Responsive**
The Razer Tarantula™ is the only gaming keyboard on the market with 1000Hz Ultrapolling™. This means a delay of only 1ms between the keystroke and the key's reaction, as compared to that of 125Hz / 8ms found in conventional keyboards.[http://www.razerzone.com/index.php?main_page=product_info&products_id=40](http://www.razerzone.com/index.php?main_page=product_info&products_id=40)

---

### Post by Kingsley on 2007-09-26
Rav, you're a gamer? :KS

---

### Post by RAV TUX on 2007-09-26
> **Kingsley said:**
> Rav, you're a gamer? :KS
just dabble a bit. ;)

---

### Post by Vadi on 2007-09-26
...!

I've never complained about my thinkpad keyboard. Responds just fine, even if not at 1000hz :|

---

### Post by PsycoGeek on 2007-09-26
> **n3tfury said:**
> looks cool, but i wonder how good it feels.

Cherry keyboards are the best out there.  Now, where to buy one...

---

### Post by Docula79 on 2007-09-27
Well, we may have got off to a bad start with my sms type text but, at least it made good conversation. Haha. I didnt even get much of a chance to look through the code of conduct. Ill have a peek later. ;-)

---

### Post by Docula79 on 2007-09-27
Taking Your advice about my grammer i have edited all my profile details. So it does not read like a child's school book anymore. Lol. Thanks for looking at this thread as bizare as it is. Concentrating more on my text slang rather than the keyboard but hey, who cares. Its a topic right? :-)

---

### Post by Spr0k3t on 2007-09-27
I wish keyboard manufacturers would throw out the OS logos and stick with a simple graphic design.  Also, I wish keyboard manufacturers would stop messing with the "chicklet-six".  The chicklet-six is a throwback to the six keys above the inverted T arrow key cluster.

[img]http://indic-computing.sourceforge.net/images/us-kbd.png[/img]

I would buy a razer keyboard in a heartbeat if they didn't screw that portion up.  At least the [DAS KEY](http://www.fahad.com/pics/das_keyboard_lrg.jpg) did it right.

---

### Post by RAV TUX on 2007-09-27
> **PsycoGeek said:**
> Cherry keyboards are the best out there.  Now, where to buy one...

[here]("http://www.bestbuybusiness.com/bbfb/en/US/adirect/bestbuy?cmd=catProductDetail&showAddButton=true&productID=BB10486138&websrc=CNBB10486138")

---

### Post by PsycoGeek on 2007-09-27
Sweet RAV!  Thanks!

That DAS KEY looks sweet too Spr0k3t!  You can always put your own rub on's on there!  I don't like the scooped F and J keys though.  Got a link to buy any of those, other than the DAS online store?

---

### Post by ~LoKe on 2007-09-27
> **Polygon said:**
> i still kinda dont like the tux key. now instead of one operating system having their logo on a keyboard, we have another. I personally think something neutral should be on ALL keyboards (a diamond or something) 

but multimedia keys look cool.

[Text](http://www.daskeyboard.com/).

---

### Post by PsycoGeek on 2007-09-27
I also found these:

[Unitron Washable Keyboards]("http://www.unotron.com/US/corded_keyboard_nokeys.htm")

Now us computer nerds don't have to be so careful with out twinkies!

---

### Post by Mr. Picklesworth on 2007-09-27
What we need is a Linux Super key sticker package. Some kind of nice acidic material to remove the Windows logo, then a white Tux shape to stick on top of the key :)

---

### Post by PsycoGeek on 2007-09-27
> **Mr. Picklesworth said:**
> What we need is a Linux Super key sticker package. Some kind of nice acidic material to remove the Windows logo, then a white Tux shape to stick on top of the key :)

It's called an air powered sander... :twisted:

---

### Post by Docula79 on 2007-09-27
> **PsycoGeek said:**
> I also found these:

[Unitron Washable Keyboards]("http://www.unotron.com/US/corded_keyboard_nokeys.htm")

Now us computer nerds don't have to be so careful with out twinkies!

That looks awesome. Who would have thought that a keyboard can withstand that. Still, shame about the windows keys. :-)

---

### Post by Mr. Picklesworth on 2007-09-27
> **Docula79 said:**
> Taking Your advice about my grammer i have edited all my profile details. So it does not read like a child's school book anymore. Lol. Thanks for looking at this thread as bizare as it is. Concentrating more on my text slang rather than the keyboard but hey, who cares. Its a topic right? :-)

Sir, your ability to stop doing the evil text slang is commendable. Odd coincidence that it cropped up in a thread about a keyboard... that's what we need, is a force feedback keyboard that gets angry if people are not writing full English words.

---

### Post by Docula79 on 2007-09-27
> **Mr. Picklesworth said:**
> Sir, your ability to stop doing the evil text slang is commendable. Odd coincidence that it cropped up in a thread about a keyboard... that's what we need, is a force feedback keyboard that gets angry if people are not writing full English words.

For instance... If you try typing in bad english then the keyboard picks up on it and gives you a few volts of juice. That would make the user (namely me, lol) think about the grammer. Good idea dude.

---

### Post by ~LoKe on 2007-09-27
> **Docula79 said:**
> For instance... If you try typing in bad english then the keyboard picks up on it and gives you a few volts of juice. That would make the user (namely me, lol) think about the grammer. Good idea dude.

The one thing that bothers me most is when someone misspells "grammar".

---

### Post by olejorgen on 2007-09-27
Well, it's worse if the person in question picks on someone elses grammar

---

### Post by ~LoKe on 2007-09-27
> **olejorgen said:**
> Well, it's worse if the person in question picks on someone elses grammar

I could take it a step further and mention that he didn't capitalize the "e" in "English".

---

### Post by Lord Illidan on 2007-09-27
Take it easy! Personally I love the razer series of products. Even though I am not a heavy duty gamer, I use a Razer Copperhead mouse with a Razer mouse, and it's the smoothest experience I've had in a long time. My hand used to ache with other mice. Aesthetically, it's gorgeous, too, and it works fine with Ubuntu.

---

### Post by sr20ve on 2007-09-27
> **PsycoGeek said:**
> I also found these:

[Unitron Washable Keyboards]("http://www.unotron.com/US/corded_keyboard_nokeys.htm")

Now us computer nerds don't have to be so careful with out twinkies!


I've put my regular microsoft ergo keyboard through the dishwasher, it doesn't hurt anything, and it looks brand new.:)

---

### Post by easyease on 2007-09-27
This thread has been hijacked by pedants..........

---

### Post by RAV TUX on 2007-09-27
> **Lord Illidan said:**
> Take it easy! Personally I love the razer series of products. Even though I am not a heavy duty gamer, I use a Razer Copperhead mouse with a Razer mouse, and it's the smoothest experience I've had in a long time. My hand used to ache with other mice. Aesthetically, it's gorgeous, too, and it works fine with Ubuntu.

I love my Razer Copperhead mouse and my Razer eXactMat mousepad with the Razer armrest.

Once you get used to the high quality of Razer mice you can never go back to cheap mice.

---

### Post by Ebuntor on 2007-09-27
> **PsycoGeek said:**
> I also found these:

[Unitron Washable Keyboards]("http://www.unotron.com/US/corded_keyboard_nokeys.htm")

Now us computer nerds don't have to be so careful with out twinkies!

Woah, that looks awesome! :D If I had known about a keyboard like that it would have saved me a lot of trouble and money. :)

---

### Post by %hMa@?b&lt;C on 2007-09-27
I will keep my IBM model M.  It does look nice though.

---

### Post by Docula79 on 2007-09-28
> **~LoKe said:**
> The one thing that bothers me most is when someone misspells "grammar".

............... Ive just checked my other halfs dictionary and i think you will find that you can spell it both ways. Grammer and grammar. Think you should check that your right before correcting people. No offense of course. :-)

---

### Post by tsnell on 2007-09-28
Sweet, but, alas, I am running linux on a laptop.

---

### Post by olejorgen on 2007-09-29
> **Docula79 said:**
> ............... Ive just checked my other halfs dictionary and i think you will find that you can spell it both ways. Grammer and grammar. Think you should check that your right before correcting people. No offense of course. :-)
That must be a quite huge/liberal dictionary..

---

