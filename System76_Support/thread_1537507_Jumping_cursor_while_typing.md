---
title: "Jumping cursor while typing"
date: 2010-07-23
forum: System76 Support
---

### Post by volkerbradley on 2010-07-23
I am one of a long list of Ubuntu users who have complained of the cursor jumping to elsewhere on the screen or to another screen while typing.
I'm using the keyboard on the Serval Pro.
I have tried the included touchfreeze utility.  Unfortunately, I could find no documentation for the choices in this utility.  After having tried various choices, I finally gave up using this utility because no setting seemed to stop the jumping cursor problem.
I then read various suggestions on how to fix this problem in lucid. Nothing that I tried fixed the problem.
Just typing this note was agony.
Do you have a suggestion that works?

---

### Post by Anxious Nut on 2010-07-23
There is actually an applet for the gnome panel called "pointer capture" that when you click on it, it captures the pointer and wont let go until you click again! You can try it by right clicking on the gnome panel --> Add to panel, then go to "Pointer Capture" and click the add button!

I know this is not an acceptable solution, but think of it as a temporary one until you find the perfect answer!

---

### Post by volkerbradley on 2010-07-23
OK, I installed this utility.  I still see some peculiar behavior.  While I was typing this message, a new screen popped up asking me to type in the URL?  Have no idea what that was about. Also, the cursor still jumps at times.  The cursor moved back into a portion of this message that I had already typed and highlighted a portion of a sentence.  Weird.
Not quite fixed yet.
Thanks for replying.

---

### Post by nealaustin on 2010-07-25
I have the same problem with my Starling. I attribute it to my thumb brushing against the touch pad while typing. If I am careful to keep my thumbs elevated it never happens.

> **volkerbradley said:**
> OK, I installed this utility.  I still see some peculiar behavior.  While I was typing this message, a new screen popped up asking me to type in the URL?  Have no idea what that was about. Also, the cursor still jumps at times.  The cursor moved back into a portion of this message that I had already typed and highlighted a portion of a sentence.  Weird.
Not quite fixed yet.
Thanks for replying.

---

### Post by volkerbradley on 2010-07-25
That's the problem.  If a sleeve or anything else touches the touchpad, all sorts of things start to happen.  That is just not acceptable. There must be a reliable solution to this problem.
As you know, HAL is no longer included in Lucid and therefore most of the previous solutions don't work.
Perhaps the answer is here: [http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html)

---

### Post by jdb on 2010-07-25
> **volkerbradley said:**
> That's the problem.  If a sleeve or anything else touches the touchpad, all sorts of things start to happen.  That is just not acceptable. There must be a reliable solution to this problem.
As you know, HAL is no longer included in Lucid and therefore most of the previous solutions don't work.
Perhaps the answer is here: [http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html)

On my Daru2 I just turn the trackpad off & use a mouse.

See the 3rd message in this thread:

[http://ubuntuforums.org/showthread.php?t=846863&highlight=Re:+Trackpad/mouse]("http://ubuntuforums.org/showthread.php?t=846863&highlight=Re:+Trackpad/mouse") 

jdb

---

### Post by volkerbradley on 2010-07-25
Hi jdb,
That did it for me.  Works very well.
Thank you very much.

---

### Post by Flyers2391 on 2010-07-26
> **jdb said:**
> On my Daru2 I just turn the trackpad off & use a mouse.

See the 3rd message in this thread:

[http://ubuntuforums.org/showthread.php?t=846863&highlight=Re:+Trackpad/mouse]("http://ubuntuforums.org/showthread.php?t=846863&highlight=Re:+Trackpad/mouse") 

jdb

Does: 

System > Preferences > Mouse > Touchpad Tab
[] Disable Touchpad while typing

not work?

---

### Post by isantop on 2010-07-26
No, it doesn't. We're aware of this issue. It's complicated by the fact that this trackpad actually works in a way similar to a theramin than a Synaptics touchpad. Currently, the best solution I can provide is to turn the trackpad off (Fn+F1) while typing, then turn it back on when you're finished.

---

### Post by volkerbradley on 2010-07-26
It does not work for me either.  I clicked on System > Preferences > Mouse.  There is a General and a Accessibility Tab.  There is no Touchpad Tab.  There is no reference to the touchpad in this application at all.

---

### Post by Tart on 2010-07-27
> **isantop said:**
> ... Currently, the best solution I can provide is to turn the trackpad off (Fn+F1) while typing, then turn it back on when you're finished.

How to do it on Starling? Fn+F1 puts it to sleep? what command can I use to put it in keyboard shortcuts?

---

### Post by rubyji on 2011-01-18
I have this same problem and these solutions are all pretty lame. :-| I am now contorting my wrists to keep my hands away from the touchpad while typing, and the cursor still jumps around sometimes.

Why aren't there proper touchpad controls/drivers on these machines? (I'm on a brand new Starling.)

---

### Post by volkerbradley on 2011-01-19
> **rubyji said:**
> I have this same problem and these solutions are all pretty lame. :-| I am now contorting my wrists to keep my hands away from the touchpad while typing, and the cursor still jumps around sometimes.

Why aren't there proper touchpad controls/drivers on these machines? (I'm on a brand new Starling.)
Hopefully, this issue will be corrected in the next release of Ubuntu.  That's what we have been promised.  
For now, you may consider using a Bluetooth mouse and to click on Fn-F1.  Solves this problem quite nicely.  No more worrying about the position of the wrists.

---

### Post by rubyji on 2011-01-19
[Duplicate, please ignore/delete]

---

### Post by rubyji on 2011-01-19
[Duplicate, please ignore/delete]

---

### Post by rubyji on 2011-01-19
> **volkerbradley said:**
> For now, you may consider using a Bluetooth mouse and to click on Fn-F1.  Solves this problem quite nicely.  No more worrying about the position of the wrists.

Well unfortunately the Starling doesn't have Bluetooth as far as I can tell - this in spite of the fact that there is a BT icon on the keyboard (grumble).

---

### Post by volkerbradley on 2011-01-19
In the days before I had Bluetooth, I preferred a small wireless USB antenna and a small mouse from Logitech. Example: [http://www.techfresh.net/wp-content/uploads/2008/05/logitech-v450-nano.jpg](http://www.techfresh.net/wp-content/uploads/2008/05/logitech-v450-nano.jpg)
I suspect you have considered all of this.  Don't mean to be bothersome.

---

### Post by volkerbradley on 2011-01-19
In the days before I had Bluetooth, I preferred a small wireless USB antenna and a small mouse from Logitech. Example: [http://www.techfresh.net/wp-content/uploads/2008/05/logitech-v450-nano.jpg](http://www.techfresh.net/wp-content/uploads/2008/05/logitech-v450-nano.jpg)
I suspect you have considered all of this.  Don't mean to be bothersome.

---

### Post by volkerbradley on 2011-05-11
> **isantop said:**
> No, it doesn't. We're aware of this issue. It's complicated by the fact that this trackpad actually works in a way similar to a theramin than a Synaptics touchpad. Currently, the best solution I can provide is to turn the trackpad off (Fn+F1) while typing, then turn it back on when you're finished.

I now have Natty installed.  My touchpad is still nearly unusable because it is overly sensitive.  Has this problem been resolved with some new drivers or a new program in Natty?

---

### Post by volkerbradley on 2011-05-17
Ian from system76.com> wrote today:
We do have a configuration utility available though. It's separate from the general Ubuntu Touchpad configuration, and the instructions for getting it set up are available on the Serval knowledge base article, here:

[http://www.knowledge76.com/index.php/SerP6](http://www.knowledge76.com/index.php/SerP6)

I installed this application and it solved the jumping cursor for me.

---

### Post by spegru on 2011-08-02
I also have this problem with a recent Packard Bell netbook (made by Acer). I saw the idea post #10 to disable the touchpad using Fn F1, but it doesn't work for me- all I get is Help. However it looks like this feature is hardware based, so it depends on your laptop. On mine I just noticed that the touchpad disable feature is in fact on the Fn-F7 key. Just tried it and while posting this is the first time I ever didn't have the jumping cursor problem!
It would be nice for the feature to be automatic but this is nearly as good.
If you are having trouble, have a careful look at the Fn keys or manual to see which is the correct one. I also know that some laptops have a specific button for this.

---

### Post by alfalfa55 on 2011-08-09
> **volkerbradley said:**
> I am one of a long list of Ubuntu users who have complained of the cursor jumping to elsewhere on the screen or to another screen while typing.
I'm using the keyboard on the Serval Pro.
I have tried the included touchfreeze utility.  Unfortunately, I could find no documentation for the choices in this utility.  After having tried various choices, I finally gave up using this utility because no setting seemed to stop the jumping cursor problem.
I then read various suggestions on how to fix this problem in lucid. Nothing that I tried fixed the problem.
Just typing this note was agony.
Do you have a suggestion that works?

Yes, my right hand touches the mouse pad as it is not centered under the space bar but is off to the right by at 3/4 inch.  That and that it does not have a "center" button for "pasting" (I have been using Unix since 1976 and do not use the keystrokes just the mouse as it is so much faster) are my only complaints about my Serval7 (now running Gentoo as that is my favorite distro.)

---

### Post by pjman on 2011-09-28
> **volkerbradley said:**
> Ian from system76.com> wrote today:
We do have a configuration utility available though. It's separate from the general Ubuntu Touchpad configuration, and the instructions for getting it set up are available on the Serval knowledge base article, here:

[http://www.knowledge76.com/index.php/SerP6](http://www.knowledge76.com/index.php/SerP6)

I installed this application and it solved the jumping cursor for me.

Will this work the with GazP6? 

It's not listed here:
[http://knowledge76.com/index.php/GazP6](http://knowledge76.com/index.php/GazP6)

---

