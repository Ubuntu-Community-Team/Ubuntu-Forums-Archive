---
title: "Lemur Ultra spontaneous actions"
date: 2012-04-30
forum: System76 Support
---

### Post by shochatd on 2012-04-30
I recently received a new Lemur Ultra. One thing I haven't figured out is that while I'm typing at the keyboard, things will happen spontaneously, such as the cursor jumping to a different part of the text or the application I'm using behaving as if I had asked for a context menu (right mouse). What is going on here? Am I inadvertently performing some gesture with the track pad that is causing these seemingly out-of-nowhere responses?
Thanks.
-- David

---

### Post by pete04 on 2012-04-30
Gotta watch the track pad. I do the same thing when I'm not careful.

There is a setting in System Settings to disable the track pad while typing. Hasn't worked for me in the past but it might be worth a shot.

---

### Post by shochatd on 2012-04-30
> **pete04 said:**
> Gotta watch the track pad. I do the same thing when I'm not careful.


That would imply that there was a way to use the track pad to make these things happen explicitly. How, for example, can you use the track pad to cause the cursor to jump suddenly to a new location, or to put up a context menu (as if I had used the right mouse button)?
-- David

---

### Post by pete04 on 2012-04-30
Here's a way to test it.

If you press Fn + F1, that will turn your track pad off. Try typing and see if the same thing happens. 

Remember, the trackpad is multi-touch, taps are left clicks and two fingers right clicks. 

You could turn multi-touch off in the settings which will make the trackpad only able to move your cursor.

---

### Post by isantop on 2012-04-30
> **shochatd said:**
> That would imply that there was a way to use the track pad to make these things happen explicitly. How, for example, can you use the track pad to cause the cursor to jump suddenly to a new location, or to put up a context menu (as if I had used the right mouse button)?
-- David

Yes, in fact. The system is configured for multi-touch by default, and so if you brush a finger or hand across the trackpad, it will move the cursor. A quick tap or brush will trigger a left-click, and if there are two points (i.e. thumbs) touching simultaneously, it can trigger a right-click.

---

### Post by shochatd on 2012-04-30
> **isantop said:**
> The system is configured for multi-touch by default, and so if you brush a finger or hand across the trackpad, it will move the cursor. A quick tap or brush will trigger a left-click, and if there are two points (i.e. thumbs) touching simultaneously, it can trigger a right-click.

Very interesting. Two questions: (1) Is this documented somewhere? (2) You say "by default". Is there a place where you can configure it differently? I feel like I didn't do the required reading. The machine came with no printed documentation. 
-- David

---

### Post by isantop on 2012-04-30
> **shochatd said:**
> Very interesting. Two questions: (1) Is this documented somewhere? (2) You say "by default". Is there a place where you can configure it differently? I feel like I didn't do the required reading. The machine came with no printed documentation. 
-- David

Yes, within the Mouse and Trackpad section of system settings, you can set the system to recognize either edge scrolling or two-finger scrolling.

---

### Post by ccrs8 on 2012-05-02
This was happening to me all the time.  Definitely the trackpad registering my hovering thumbs as taps (and worse, clicks) while typing.  As I hate tap-to-click anyway, I just disabled tap-to-click on the touchpad and all my problems went away.  My cursor still moves around at times when I type if my thumbs get too close, but since there is no click, the cursor is not repositioned so my typing location does not change.

I use Xubuntu and have a startup script run to disable tap-to-click, but I think in Ubuntu there is a mouse/trackpad GUI option for it.

---

### Post by shochatd on 2012-05-05
Thanks for all the responses. Now that I understand what is going on, I´m enjoying the interesting touchpad functionality. Haven´t decided whether to turn it off. I noticed in System Settings, it has an option to ¨disable the touchpad while typing¨ which is checked. Has that been there all along (I just upgraded to 12.04)? Anyway, I just managed to type this response without any jumping of the insertion point. I´m being careful with my thumbs.
-- David

---

