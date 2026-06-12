---
title: "Desktop Zoom in Natty Sucks"
date: 2011-05-19
forum: The Cafe
---

### Post by miasmablk on 2011-05-19
I haven't seen any other threads posted about this yet so I thought I would give it a go. It's choppy and you can't pan around the page while zoomed in anymore wtf?

---

### Post by Spr0k3t on 2011-05-19
I can't even get zoom to work.  I think enhanced zoom has been disabled from Compiz to keep 11.04's unity to work.  I've been working on trying to figure out how to get it working again like it did back in 10.10 (superkey+scroll-wheel).

---

### Post by Rasa1111 on 2011-05-19
It absolutely does suck in Natty!

in my 10.10 install it works perfectly..
but in Natty.. the most I can get it to do is "zoom", but can't move around..
and everything that's zoomed is extremely pixelated and funky looking.

---

### Post by oedipuss on 2011-05-21
enhanced zoom is working here, after I enabled it with ccsm . 
It was choppy at first, but that was due to the mousepoll plugin, not the actual zoom animations. Setting mousepoll to a smaller value may make zooming more smooth.

---

### Post by Rasa1111 on 2011-05-21
yeah, it "works"... (ie, it zooms)
But it doesnt work like it has in previous releases. 
Not on the 2 PC's Ive tried on. (3, including OP's)

---

### Post by Copper Bezel on 2011-05-21
*Dammit.* Is there anything I like that they didn't break?

---

### Post by mcduck on 2011-05-21
Works fine for me. The only thing that's different from 10.10 is that it doesn't zoom the panels. Apart from that, everything works just fine.

I had to enable the shortcut myself (Enhanced Zoom Desktop plugin was enabled by default, just no shortcut), and I also set the Zoom Mode to "Pan Area" and decreased the Mouse Poll Interval.

---

### Post by Copper Bezel on 2011-05-21
Default (that most of us are used to) is "sync mouse," I think. But yeah, if that's disabled on 10,10, it acts exactly as it's being described here. Not everything is the narwhal's fault, then. = )

---

### Post by Rasa1111 on 2011-05-21
> **mcduck said:**
> Works fine for me. The only thing that's different from 10.10 is that it doesn't zoom the panels. Apart from that, everything works just fine.

I had to enable the shortcut myself (Enhanced Zoom Desktop plugin was enabled by default, just no shortcut), and I also set the Zoom Mode to "Pan Area" and decreased the Mouse Poll Interval.

S**t! 

I just screwed my 11.04 install because of this post! :???:

Booted into my 10.10 partition now..
But can;t get into my 11.04 side at all.

god dammit..

 All I did was checked out some settings in the "enhanced desktop zoom", and then I zoomed in using "super+mouse button1".. and I could not zoom out, at all! 
So I shut it down by holding power button..
and when i try to boot it now..
I get just the black screen with a white blinking **_** thing,
and after about 2 minutes it gives me a pure purple screen and I cant get anywhere.

gahhh

Gonna have to make a thread for this i think.

Just what i wanted to do today! :o

---

### Post by Spr0k3t on 2011-05-22
> **oedipuss said:**
> enhanced zoom is working here, after I enabled it with ccsm . 

It was choppy at first, but that was due to the mousepoll plugin, not the actual zoom animations. Setting mousepoll to a smaller value may make zooming more smooth.

Thanks for the tip.  I was able to get it working smoother (enough to not notice any difference between 10.10 and current).

I had to set the desktop zoom mouse to the following:
Zoom Out: <Super>Button4
Zoom In: <Super>Button5

Changed the mouse polling speed to 10 (use the search to find it).

---

### Post by Alexgucky on 2011-09-20
What about the "Pan Area/Sync Mouse" old Style?

in older version the zoom area was sync to the mousepointer, center of the zoom area.
except the zoom area was in contact to the border of the desktop.
than the cursor was able to move nearer to border.

it was a middle between Pan Area & Sync Mouse.....

And for me the biggest reason why working in linux was more
comfortable as in Windows....

sorry for my bad english i am from germany

nice greetings

bye

Alexgucky

---

### Post by blueturtl on 2011-09-20
> **Rasa1111 said:**
> S**t! 

I just screwed my 11.04 install because of this post! :???:

Booted into my 10.10 partition now..
But can;t get into my 11.04 side at all.

god dammit..

 All I did was checked out some settings in the "enhanced desktop zoom", and then I zoomed in using "super+mouse button1".. and I could not zoom out, at all! 
So I shut it down by holding power button..
and when i try to boot it now..
I get just the black screen with a white blinking **_** thing,
and after about 2 minutes it gives me a pure purple screen and I cant get anywhere.

gahhh

Gonna have to make a thread for this i think.

Just what i wanted to do today! :o

For future reference, you may want to switch to a virtual terminal and do a safe reboot from there. The zoom only affects your X-session.

That is, hit Ctrl+Alt+F1 or F2.

Log in using your account (no characters will be displayed for your password, even though each key press IS registered). Type sudo reboot and give your password again.

Practice this, it will bail you out whenever your X-session becomes unresponsive.

---

### Post by mcduck on 2011-09-20
> **blueturtl said:**
> For future reference, you may want to switch to a virtual terminal and do a safe reboot from there. The zoom only affects your X-session.

That is, hit Ctrl+Alt+F1 or F2.

Log in using your account (no characters will be displayed for your password, even though each key press IS registered). Type sudo reboot and give your password again.

Practice this, it will bail you out whenever your X-session becomes unresponsive.

That's a good hint, and also when setting a shortcut for zooming in it's a good idea to set one for zooming out as well. Preferably *before* using the zoom in. ;)

---

