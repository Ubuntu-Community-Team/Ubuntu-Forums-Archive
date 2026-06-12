---
title: "Quote key quark?"
date: 2008-04-27
forum: System76 Support
---

### Post by Sean-Michael on 2008-04-27
I seem to have a quark or something I do not understand about my key board.  There are about four characters that come from my "quotations key".

Single quotes,

1 =** ´**

2 = **'**

Double quotes,

3 = **¨**

4 = **"**

these are all coming from the key mentioned and I dont really understand it, I use this key a lot for my web work and would like to get it to function like normal!

Thanks,
Sean-Michael.

---

### Post by thomasaaron on 2008-04-29
Please give more info on what the problem is. When that key is pressed without the shift key, it gives single-quotes. With the sift key, it gives double-quotes.

It appears to be providing two different variations of each, but I don't understand when/where that happens. Does it give variations within the same program or in different programs.

---

### Post by Sean-Michael on 2008-04-29
This is happening system wide, let me better explane the behavior of the key.

Single quote when I push the key twice = ´ and once and then the space bar = '


Double quotes when holding the shift key, twice = ¨ once and then the space bar = "

Once again I would like it to behave like a normal key.

My laptop is a new Serval Performance running hardy 64 bit.

Thanks,
Sean-Michael.

---

### Post by thomasaaron on 2008-04-29
I've tried to duplicate it, but I'm not having any luck.
It might be a font setting or something.

Give me a call and walk me through it. I'm still not convinced I'm doing it right.

---

### Post by octathlon on 2008-04-30
If you go to System|Preferences|Keyboard, on the layout tab, are you using U.S. English, or is some other layout listed?  

Sounds like you might be using U.S. International or some other layout where the apostrophe/quote key is a dead key used for making international characters, since you are having to hit an additonal key before a character appears.  If you have more than one layout installed, they are usually toggled by pressing Ctrl+Space.

---

### Post by Sean-Michael on 2008-05-01
I think you got it octathlon,

Late last night I fixed this problem but wasnt quite clear what I had done, I was trying so many things...  as you mentioned my Layout is U.S. International (with dead keys).

I think I fixed it by changing the keyboard model but I would like to ask, what is the proper way to fix it?  Do I need to use USA layout?

Also, can anyone tell me what the keyboard model should be, mine currently is set at Classmate PC lol

Also sorry about the later reply Thomas, I've been so busy!

Thanks,
Sean-Michael.

---

### Post by thomasaaron on 2008-05-01
USA Layout
Generic 105-Key (Intl) PC

---

### Post by Sean-Michael on 2008-05-01
I tried the settings you suggested thomasaaron and it brings me back to the same problem...

---

### Post by thomasaaron on 2008-05-01
What Octhalon said was interesting.

The setup I gave you is what I have on our shop serval, and I can't seem to duplicate the problem.

Do you have a second keyboard layout installed. If you do, then perhaps you are inadvertently toggling between the two. Let us know if this is not the case, and we'll continue to tinker with it.

It's definitely a configuration issue of some kind. I feel pretty certain about that.

---

### Post by octathlon on 2008-05-01
I just got Hardy installed on my desktop today and it looks like it uses slightly different layout names than Feisty.  First make sure your selected keyboard model is Generic 105 key, not Classmate. :)  Then if you don't have the correct USA layout in the list, you need to Add it: Layouts-USA and Variants-Default.  Then you should Remove whatever other layouts were there, assuming you don't actually want additional layouts that is.

---

### Post by Sean-Michael on 2008-05-03
It's working now, using the settings you described, but I did have to remove the original layout like you suggested or the problem persisted.

Thank you so much for the help, this one was driving me buggy!
Sean-Michael.

---

### Post by todb on 2008-05-06
Changing the keyboard layout to USA (and not the USA international) will certainly fix this problem. Quotes, backticks, and doublequotes are all affected. Again, to fix:

System > Preferences > Keyboard
Layouts (tab)
Add (button)
Add "USA" and "Default," and hit Add.
Remove the USA Alternative layout.

Unfortunately, "USA Alternative international (former us_intl)" is the default with the stock Ubuntu804desktop VMware pre-built image, so I imagine a bunch of new users are going to run into this behavior out of the box, which is a shame. I did and was irritated for many minutes. :)

---

### Post by jammindice on 2008-05-14
i used the alternate cd to use lvm with encryption and i had this same problem since the keyboard selector is very odd during that installation

---

