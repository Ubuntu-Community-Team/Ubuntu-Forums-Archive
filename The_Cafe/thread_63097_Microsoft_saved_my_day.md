---
title: "Microsoft saved my day"
date: 2005-09-06
forum: The Cafe
---

### Post by Brunellus on 2005-09-06
...not the way that you're thinking.

My PS2 mouse went on the fritz...so I needed a backup. Luckily, we have one here at home..

it's an old...like, mid-90s MS mouse with no scrollwheel. 

Life without a third button is awful.  

Sorry, just had to rant.  Any suggestions on a new mouse?  Don't mind spending a bit of cash if I can get something that works well with ubuntu and will last a bit.

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=Brunellus] Any suggestions on a new mouse?  Don't mind spending a bit of cash if I can get something that works well with ubuntu and will last a bit.[/QUOTE]

Logitech. Simply the best. You can pry my Mouseman out of my cold dead hands.

---

### Post by John.Michael.Kane on 2005-09-06
this might be something to look into MX1000
[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=3,CONTENTID=9043,ad=g03,srch=1](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=3,CONTENTID=9043,ad=g03,srch=1)

Or this [http://www.razerzone.com/](http://www.razerzone.com/) 

Hope this helps

---

### Post by Brunellus on 2005-09-06
[QUOTE=poofyhairguy]Logitech. Simply the best. You can pry my Mouseman out of my cold dead hands.[/QUOTE]
 wasn't there some sort of jiggery-pokery requred to get the MX500 to work fully with ubuntu?  and is it USB-only?

---

### Post by Wolki on 2005-09-06
[QUOTE=Brunellus]Life without a third button is awful.  [/QUOTE]

You can emulate the third button by clicking right and left at the same time. It's annoying, but better thaan having none at all ^^;;

On the topic of mouses... i had to buy a new one recently, and was very disappointed with what I found. I love scroll wheels, but why does everyone have have to use it as a third button too? It's such a frequent button under linux, and clicking on something that moves, has too much resistance and requires clicking at a weird angle feels tiring. My old mouse had the third button seperately on the side, and that was so great... the first few days with the new mouseI got the feeling my middle finger would fall off :-/

---

### Post by endy on 2005-09-06
[QUOTE=Brunellus]wasn't there some sort of jiggery-pokery requred to get the MX500 to work fully with ubuntu?  and is it USB-only?[/QUOTE]

I have a mx510 which is the same model as the 500 except it has a greater resolution (there is a newer mx518 too, again with higher resolution). Anyway, it came with a USB to PS/2 adapter so that base is covered, then to get the use of the side buttons you need to correctly edit your xorg.conf file for the extra buttons then set up a ~/.Xmodmap file to make sure the scroll wheel is mapped to do the scrolling. 

That's it for basic operation however, if you want to use it's high resolution 800dpi I use the [logitech_applet](http://freshmeat.net/projects/logitech_applet/), although there is another tool (I forget the name as I couldn't get it to work).

If you connect it via USB and you customise a new-ish kernel you can have the ability to increase the mouse polling from the standard 100ms (I think it is) to up to 2ms.

If you don't play games much then the higher resolution and polling times wont mean much I guess but if they do then the mx518 or the newer (and superior) G5 would be the best wired mouse you can get :)

xorg.conf example:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
EndSection
``` 

Contents of my ~/.Xmodmap:
```
pointer = 1 2 3 6 7 4 5
``` 

Nowadays I use the evdev protocol with my mouse attached via USB, but as you want a PS/2 connection I'll save that for another story :)

Edit: I got the ~/.Xmodmap example wrong but I think it's right now :)

---

### Post by benplaut on 2005-09-07
bah... M$ Mice are really the way to go!

my 3YO Intellimouse beats the logitec i got a few months ago- i ended up returning the POS because it was way too jittery  :roll: 

/flame away  :)

---

### Post by BAshworth on 2005-09-07
As long as it doesn't have one of those damned "nubbins" instead of a wheel, I'm happy.  I tend to poo poo the mice with lots of buttons on them.  They gave me an Intellimouse Explorer here at work, and the first thing I did was to go into the IT room and dig out the standard wheel mouse that had come boxed with the system.  Just too touchy for my taste.  Plus the wheel was too "slick" for me.  I use AutoCAD, so mouse and keyboard "feel" are very important to me.

Ultimately, it's whatever feels comfortable for you.  Software wise, I'm not sure which works best with Ubuntu.  The smart shopper would find a mouse that fit right in their hand, then check out how compatible it was with linux by either checking here, or on the company's website.

---

### Post by GreyFox503 on 2005-09-07
I use a very plain 3 button corded optical mouse from Logitech that works great.  I tend not to like many buttons on mine, though I do like the shape of some of the new logitech mice.

For me, its all about how it feels using it, regardless of buttons or features or cpi.

---

### Post by N'Jal on 2005-09-07
I own a Mac and just bought the mightmouse and it's fantastic it CAN be configured to use two button's under OSX and is set to two button's on every other system.It's usb and has a vertical and horizontal scroll ball. Hefty price tag but it's a good piece of kit.

---

### Post by wmcbrine on 2005-09-08
I see a lot of divided reaction to the Mighty Mouse -- some love it, some hate it.

Me, I'm currently using a Microsoft (gasp!) optical trackball. It's got five buttons (counting the scroll wheel). I haven't even tried to set up the extra two.

---

### Post by xequence on 2005-09-08
Longitech. We have a good laser mouse with a scrollwheel. It is a couple years old, yet great working.

It says M/N: M-BD58 on the bottom =O

People seem to aggree that microsoft mouses and keyboards are good products...

My couple year old microsoft internet keyboard works good :)

---

### Post by Brunellus on 2005-09-11
UPDATE!

I am the proud owner of a new Logitech MX510.  

Most of the buttons now work.  the 'cruise control' buttons are remarkably cool.  And, thanks to panickedthumb's excellent howto, I have functional thumb buttons.

Unfortunately, those thumb buttons only seem to work in Firefox, and not in epiphany.  the buttons are mapped, just as directed in the howto, to alt+left and alt+right.  

In firefox, this lets me go 'forward' and 'back'.  Epiphany has the same keybinding, and yet I don't have the thumb-button functionality.

any ideas as to why epiphany won't recognize the thumb buttons?

---

### Post by YourSurrogateGod on 2005-09-11
[QUOTE=poofyhairguy]Logitech. Simply the best. You can pry my Mouseman out of my cold dead hands.[/QUOTE]
I got a logitech mousey, I've bought it, ohh... like 3-4 years ago and it's still going strong. Gotta love optical mice, you never have to buy new ones and you don't need to clean 'em.

---

### Post by Brunellus on 2005-09-11
[QUOTE=Brunellus]UPDATE!

I am the proud owner of a new Logitech MX510.  

Most of the buttons now work.  the 'cruise control' buttons are remarkably cool.  And, thanks to panickedthumb's excellent howto, I have functional thumb buttons.

Unfortunately, those thumb buttons only seem to work in Firefox, and not in epiphany.  the buttons are mapped, just as directed in the howto, to alt+left and alt+right.  

In firefox, this lets me go 'forward' and 'back'.  Epiphany has the same keybinding, and yet I don't have the thumb-button functionality.

any ideas as to why epiphany won't recognize the thumb buttons?[/QUOTE]
 One more weird behavior:  the "cruise control"-UP button goes BACK in firefox, while it behaves nicely (scrolling up) in epiphany.  Meanwhile, I can't owrk out what, for the life of me, the little windowsomethingorother button does below the "cruise down" button--it's nonfunctional as far as I can tell.

buggy browsers, or (more likely) stupid setup on my part?

EDIT:  
If I count the scrollwheel as a button, there are 8 buttons on the mouse.  the xorg.conf snippet someone posted on this thread for the MX510 counts 7.  why is this so?  would telling xorg.conf that I had 8 buttons change the behavior of my mouse?

---

### Post by Brunellus on 2005-09-11
bump?

---

### Post by majikstreet on 2005-09-11
Brunellus,
I know that you already bought your mouse, but I would like to add something:
I have a Dell cordless mouse and keyboard combo. It works wonderful w/ ubuntu. The keyboard has extra buttons that don't work, but I don't care.

It's basic, but it does the job.

---

