---
title: "Keyboard without Windows-logo"
date: 2008-12-24
forum: Ubuntu Brainstorm
---

### Post by maandverband on 2008-12-24
When Ubuntu 8.10 released, Canonical started selling Ubuntu mice. How about also selling Ubuntu keyboards?

There are a lot of users who don't use Windows, but almost everyone still has a keyboard with that annoying Windows-logo on it. Why not create a Ubuntu keyboard? Mac users have their own keyboards, Windows users have their own keyboard, but we don't have a keyboard with our logo on it. I know a lot of people who are willing to buy a keyboard without that annoying Windows-logo (me included), but can't find such keyboard. Well, the Apple keyboard is an option, but not everything works as expected on those keyboards. Besides that, a keyboard with the Ubuntu logo would be perfect.

It doesn't have to be the Ubuntu logo, it'd also be Tux that's on the meta key (this way users of other distributions can also buy the keyboard).

If Canonical'd ever start selling a Ubuntu keyboard I'd like to see a keyboard that looks like the Logitech UltraX Flat (see first attachment) or the Apple Keyboard (see second attachment). So, I'm talking about a thin keyboard with thin keys (like the keys on laptops) and a full-size layout. I prefer wired keyboards, but maybe Canonical could make a wired and a wireless keyboard.

There'd also be some extra keys on this keyboard, like the Compose key (as seen on the Sun keyboards / third attachment).

Are their any plans making Ubuntu keyboards or Linux keyboards?

---

### Post by smartboyathome on 2008-12-24
ZaReason sells one. Check their site.

---

### Post by dannytatom on 2008-12-24
Oooh, I must get that keyboard. :o

---

### Post by maandverband on 2008-12-24
> **smartboyathome said:**
> ZaReason sells one. Check their site.

I wanted to post this reply:
"I know, but their Ubuntu keyboard looks very amateuristic. It looks like a Logitech keyboard covered with some stickers."

But before posting that reply, I checked their website again and I found out they made a new keyboard. This new keyboard looks way more professional and it has laptop-keys, instead of the old-fashioned keys.

Old design:
[http://www.zareason.com/shop/product.php?productid=16162](http://www.zareason.com/shop/product.php?productid=16162)
In my opinion a case badge on a keyboard looks silly and unprofessional. That's why I never ordered that keyboard.

New design:
[http://www.zareason.com/shop/product.php?productid=16189&cat=0&page=1](http://www.zareason.com/shop/product.php?productid=16189&cat=0&page=1)
Looks way better, in my opinion. Finally someone's selling a great Linux keyboard.

I see Zareason's located in America. I'm going to find out if they ship to The Netherlands. If so, than I'm going to order five of those keyboards for me and my friends.

Thank you. Because of your reply I checked their website for updates and found this new keyboard.

---

### Post by Flimm on 2008-12-27
[[IMG]http://brainstorm.ubuntu.com/idea/3599/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3599/)

---

### Post by k_aneda on 2009-01-01
> **maandverband said:**
> I wanted to post this reply:
New design:
[http://www.zareason.com/shop/product.php?productid=16189&cat=0&page=1](http://www.zareason.com/shop/product.php?productid=16189&cat=0&page=1)
Looks way better, in my opinion. Finally someone's selling a great Linux keyboard.

I see Zareason's located in America. I'm going to find out if they ship to The Netherlands. If so, than I'm going to order five of those keyboards for me and my friends.

Thank you. Because of your reply I checked their website for updates and found this new keyboard.

New keyboard is nice.. however be warned, I think there's a problem with some of the function keys.   I'm just @ work so haven't had time to check the keymappings and make a change, but I can't use *any* of the function keys in Ubuntu 8.10 unless I use the laptop's keyboard..   (yes, it's probably a quick fix..)

EDIT: Apart from that, it's an awesome keyboard in both Windows and Linux!

---

### Post by Martje_001 on 2009-01-02
Just make a logo-less keyboard.

---

### Post by k_aneda on 2009-01-02
> **Martje_001 said:**
> Just make a logo-less keyboard.

Don't get the point of your post, but here's something to humour you with - they already exist as the "Happy Hackers" keyboard range:

[http://en.wikipedia.org/wiki/Happy_Hacking_Keyboard]("http://en.wikipedia.org/wiki/Happy_Hacking_Keyboard")

---

### Post by maandverband on 2009-01-02
> **k_aneda said:**
> New keyboard is nice.. however be warned, I think there's a problem with some of the function keys.   I'm just @ work so haven't had time to check the keymappings and make a change, but I can't use *any* of the function keys in Ubuntu 8.10 unless I use the laptop's keyboard..   (yes, it's probably a quick fix..)

EDIT: Apart from that, it's an awesome keyboard in both Windows and Linux!

I already made an account at Zareason, but haven't ordered the keyboard yet. Could you keep me up-to-date about those function keys?

---

### Post by k_aneda on 2009-01-02
Had some time this weekend to do some searching and have managed to put together the following info for the issue with Apple keyboards:

**WORKAROUND**:
Apparently is to hold down the Fn key while using the Function keys.   For those who haven't used OSX, apple keyboards by default map the function keys to their special commands (i.e. adjust brightness, run Expose, etc.) and apparently this is what's happening in Ubuntu.

**POSSIBLE SOLUTIONS**:
this seems to be what you have to do...

> [LIST]
[*]/sys/module/hid/parameters/pb_fnmode - set that to 2
[*]must add "option hid pb_fnmode=2" in /etc/modprobe.d/options
[*]THEN you must regenerate initrd (update-initramfs -u)
[/LIST]

I'll get a chance to try this out on Monday when I'm back in @ work with the Apple keyboard and will reply and let you know.

Helpful URLs where I gleaned this info from:

> [LIST]
[*][Bug #201711: Apple fn key behavior isn't consistent with what's expected (https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201711)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201711")
[*][Bug #201887: Slim USB Apple Keyboard not working correctly when pressing the "numlock" key (https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887")
[/LIST]

EDIT: Apologies for slightly OT, however searching for Apple keyboard bugs brought me to this thread, hoping the above will help someone else as well.. I should probably make this out to be it's own post..

---

### Post by maandverband on 2009-01-03
@k_aneda:
You're talking about the Apple keyboard? I thought you were talking about Zareasons new Tux Keyboard.

---

### Post by innovati on 2009-01-04
please don't hurt me for saying I don't desire an ubuntu-specific keyboard, but I don't think of the windows button as 'Microsoft Windows!' button.

Most keybord manufacturers use an abstract 4 squared shape that refers to the panes of a window, but it can't be the windows logo because that's trademarked.

It has never bothered me, and to me an abstract shape is preferable over a penguin.

I really enjoy the mac solution in calling it the command key, and having the clover icon there.  My solution for Ubuntu and beyond is maybe to produce or encourage other manufacturers to produce a key that features a typographic symbol that suggest a function, or state that could logically be combined with other keystrokes.

What we need to settle on is the naming convention for it: is it a windows key, a win key, a super key, a meta key, a tux key?

On mac keyboards it's called command, but sometimes referred to as 'apple' even though there is no apple on current models.  Oh, and BTW, I love my slim apple keyboard and because of the low keys I can type for hours without finger fatigue.  Wonderful!

---

### Post by k_aneda on 2009-01-05
> **innovati said:**
> What we need to settle on is the naming convention for it: is it a windows key, a win key, a super key, a meta key, a tux key?

Quick Google search says it's the Super key:

[http://en.wikipedia.org/wiki/Super_key_(keyboard_button)]("http://en.wikipedia.org/wiki/Super_key_(keyboard_button)")

> Super key (keyboard button)
From Wikipedia, the free encyclopedia

The Super key was a special key on the Space-cadet keyboard; today, it is typically identified with the Windows key or Apple logo, although these may also be identified with the Meta key.

---

### Post by theacerguy on 2009-01-05
cherry cymotion hhas tux on it i know that but they are extremely hard to get if you can code pygame well enter lxf competition to get one

---

### Post by maandverband on 2009-01-10
> **theacerguy said:**
> cherry cymotion hhas tux on it i know that but they are extremely hard to get if you can code pygame well enter lxf competition to get one

Yes, I know about that Cherry keyboard. It's very old and there's no way get one of those keyboards nowadays. Besides that, the keyboard from Zareason looks way better in my opinion.

---

### Post by vamped on 2009-01-15
> **Martje_001 said:**
> Just make a logo-less keyboard.

Just scrape the paint off the logo ?

---

