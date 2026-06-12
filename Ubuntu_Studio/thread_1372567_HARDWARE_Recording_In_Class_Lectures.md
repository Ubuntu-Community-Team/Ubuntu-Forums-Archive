---
title: ":HARDWARE: Recording In Class Lectures"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by Torn on 2010-01-04
Hey guys, I hope I'm in the right area.

I am looking for a solution to an In class lecture recording situation.
We have 2 systems, but only 1 in the works
The working setup consists of a moveable cart that is setup at the center of the class room and 
Via remote control with presets to point to locations around the classroom. 
(White boards)(Projector screen)(Professor) 
Our current issue is that when focusing on the Projector screen we are getting poor recordings with minimal to no text makeup. And the cart itself is also kind of a hassle
Compared to our class room cabinet system.
It’s the same type of webcam set at the back of the class.
The cabinet equipment allows easy switching between inputs. Such as  between our laptop svideo, and the webcam. Unfortunately the laptops we use cannot operate more than 2 video devices at the same time. Which leaves us with either working recordable svideo or projector and the laptop screen itself.
To my understanding, a quick fix might be finding a device that could split the laptops 2nd monitor plug *that is used for the projector* to a converter that will output to the I/O selector. If that’s even possible 
I’m not sure where to go here, I’m new to this kind of trouble shooting.
We would prefer  to use the cabinet equipment being a much larger investment. But any suggestions and ideas would be greatly appreciated

---

### Post by Tricity on 2010-01-04
Torn,  on first glance, this looks like a fixable issue, but even after repeated reading, I can't seem to get a clear picture of the actual problem. You have two systems, it seems: the cart and the cabinet system. What systems? Could you draw/scan/post a sketch?

The systems - are they running Ubuntu? I guess so, or you wouldn't post here. 

>  To my understanding, a quick fix might be finding a device that could split the laptops 2nd monitor plug *that is used for the projector* to a converter that will output to the I/O selector. If that’s even possible VGA splitters are available at very low cost - is that what you mean? So your external laptop output would go to (1) the I/O selector and (2) the LCD projector? Did I get this right? Then - why the I/O selector? This is where a sketch could come in handy.

---

### Post by Torn on 2010-01-06
My apologies for the confusion, Im just aiding the teachers right now and this is what they have me working on rofl. I spent a good couple hours drawing up a the last wiring diagram il try and get a copy of it up.
To shorten things up we want to use our cabinet system for in class recording. We have a working alternative but its not perfect.
And the problem we are facing with the cabinet system is that the camera is at the back of the class and does not focus on the projector the students are using. What i would like to do is record straight off the laptop while the teacher is giving his lesson. The I/O device allows me to switch between the presentation and the cam of the white boards.

::EDIT::
Here is the wiring diagram 
[[IMG]http://img229.imageshack.us/img229/6443/wiringdiagram.th.png[/IMG]](http://img229.imageshack.us/i/wiringdiagram.png/)

---

### Post by Tricity on 2010-01-10
To summarize, your problem is toe connection between the laptop and the data video I/O selector (bottom left of your diagram). You would prefer to use the laptop's regular monitor output and feed it into the video-only input of your video selector, did I get that right? And the reason is that you need to use the big TV for your Pinnacle recorder?

If so, would some sort of converter help? Here is a DVI to HDTV adapter:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814999205](http://www.newegg.com/Product/Product.aspx?Item=N82E16814999205)

With a DVI splitter, you may just get the signal you need.

---

