---
title: "XInput 2 (multi-pointer X) has happened!"
date: 2009-10-03
forum: The Cafe
---

### Post by Mr. Picklesworth on 2009-10-03
Yes, XInput 2 **is in** XServer 1.7. Alas, Karmic isn't shipping with this unless everyone on the release team is as hopelessly excited about it as I am and a miracle occurs, but at least we'll see it in Lucid. (And Fedora 12, whose release schedule seems perfect to get all the cool new stuff before us...).

[http://who-t.blogspot.com/2009/10/xi2-and-mpx-released.html](http://who-t.blogspot.com/2009/10/xi2-and-mpx-released.html)

---

### Post by Tibuda on 2009-10-03
So now* I can plug two mouses into my computer and it will have two pointers? How it will work when I plug a mouse into my laptop: will it have two pointers for the touchpad and the mouse?

* now = when I get this X version

---

### Post by Mr. Picklesworth on 2009-10-03
For the time being, you have to tell it explicitly to create a new pointer, along with some other command line fiddling. Making that fiddling easy is up to a desktop environment.

In the distant future, I can imagine some kind of gesture like moving two input devices apart at the same time to "split" a single pointer into two, although I honestly don't know if such magic is possible. It would be pretty beautiful, though!

---

### Post by MaxIBoy on 2009-10-03
> **Mr. Picklesworth said:**
> For the time being, you have to tell it explicitly to create a new pointer, along with some other command line fiddling. Making that fiddling easy is up to a desktop environment.

In the distant future, I can imagine some kind of gesture like moving two input devices apart at the same time to "split" a single pointer into two, although I honestly don't know if such magic is possible. It would be pretty beautiful, though!
Someone has written a GNOME-panel applet to manage this. You can see it in the demonstration videos of Compiz MPX support. Don't know if it's publicly available though.

You know what "magic" I want? Drag two pointer away from each other on the title bar of a window to "split" the window in half, opening a new program, and each window is open to the same document.

(Wait, hold on a second. Was that what you were describing, and you accidentally typed pointer instead of window? Or did you mean pulling the mice apart sharply to spawn a new mouse pointer? Because that would be cool too.)

---

### Post by autumnraine on 2009-11-08
So, is it possible to utilize this at all yet (from the end user's perspective)? Because I think that after a while I would probably get used to operating with two input cursors controlled by two mice (or fingers, or whatever) and wonder how I ever managed without it! 

But seriously, can this be used yet, or will we be able to use it in the next release (10.4)?

---

### Post by Mr. Picklesworth on 2009-11-08
X11 7.5 released a bit after 9.10 could take it in, but it should be in the next release. It is present in Fedora 12, although it should be stressed that anything on top of X needs to be patched to support the features as well. (It works, but it doesn't work beautifully yet).

---

### Post by Skripka on 2009-11-08
> **Mr. Picklesworth said:**
> X11 7.5 released a bit after 9.10 could take it in, but it should be in the next release. It is present in Fedora 12, although it should be stressed that anything on top of X needs to be patched to support the features as well. (It works, but it doesn't work beautifully yet).

Speaking of X...there is a very faulty patch that Fedora submitted, and got added to X--and is causing headaches in 1.7.901 for KDE/Nvidia users.  Being early in the Dev cycle for 9.10 odds are 9.10 won't have issues.

---

### Post by Xbehave on 2009-11-08
> **Mr. Picklesworth said:**
> In the distant future, I can imagine some kind of gesture like moving two input devices apart at the same time to "split" a single pointer into two, although I honestly don't know if such magic is possible. It would be pretty beautiful, though!
I think that is possible, and would be awsome, for bonus point you could "group" the pointers by clicking on one with another. Mapping keyboards could be as simple as keycomb+number of the mouse (IMO the real strength of this is multiple independent keyboard inputs).

---

### Post by 23meg on 2009-11-08
> **Xbehave said:**
> I think that is possible, and would be awsome

I'd like to drop two links, without comment:

[list][*][1]("http://10gui.com/")
[*][2]("http://www.wacom.com/bamboo/bamboo_touch.php")[/list]

---

### Post by Favux on 2009-11-08
Link 1 is cool!  Thanks 23meg.

Right now the new Bamboo P & T's have two finger touch.  I don't know if that's due to the technology, firmware, or software.  They are not yet supported by linuxwacom.  We've got the stylus part working on this [thread]("http://ubuntuforums.org/showthread.php?t=1290251").

The first HP laptop/"tablet pc" with the new Wacom touch screen that I'm aware of just setup in Karmic using linuxwacom 0.8.5-1 [here]("http://ubuntuforums.org/showthread.php?t=1314869").

So it's getting close.

---

### Post by Xbehave on 2009-11-08
> **23meg said:**
> I'd like to drop two links, without comment:

[list][*][1]("http://10gui.com/")
[*][2]("http://www.wacom.com/bamboo/bamboo_touch.php")[/list]
1  is good but the UI ideas are terrible
2  is more to do with gestures than Multiple independent pointers (multi-finger gestures are already available for synaptic with a bit of hacking)

---

### Post by toupeiro on 2009-11-08
How is the security of this technology being addressed?  I think it is awesome, but for collaborative purposes, how does individual UID/GID security get defined on the data being used.  Obviously one person (the person logged in) controls the main X-window session, but if I am collaborating with someone who is using open office, how can I be sure that person has the profile and permissions they need to use their data in a common workspace with me?

---

### Post by Xbehave on 2009-11-08
> **toupeiro said:**
> How is the security of this technology being addressed?  I think it is awesome, but for collaborative purposes, how does individual UID/GID security get defined on the data being used.  Obviously one person (the person logged in) controls the main X-window session, but if I am collaborating with someone who is using open office, how can I be sure that person has the profile and permissions they need to use their data in a common workspace with me?
All of this is done using a single X session (so it's all done with the UID of the person that is logged in. If you want to use 2 screens for 2 people they need to be setup to run separate X sessions not this. 
If you want to wrap security into this something like xhost/xypher might be usable BUT AFAIK nobody has done that sort of this yet so you can't tie a pointer/kb to only one user.

---

### Post by toupeiro on 2009-11-08
> **Xbehave said:**
> All of this is done using a single X session (so it's all done with the UID of the person that is logged in. If you want to use 2 screens for 2 people they need to be setup to run separate X sessions not this. 
If you want to wrap security into this something like xhost/xypher might be usable BUT AFAIK nobody has done that sort of this yet so you can't tie a pointer/kb to only one user.

What would be really cool is when you activate the second keyboard/mouse you can set your credentials at that time for the entire use of that set of input devices.  Once I get my hands on it I may try to make that work.  X-windows is technically run by root so redirecting local apps to a local X server by any number of users should be 100% do-able the way ubuntu is setup by default.

---

### Post by Frak on 2009-11-08
> **Favux said:**
> Link 1 is cool!  Thanks 23meg.

Right now the new Bamboo P & T's have two finger touch.  I don't know if that's due to the technology, firmware, or software.  They are not yet supported by linuxwacom.  We've got the stylus part working on this [thread]("http://ubuntuforums.org/showthread.php?t=1290251").

The first HP laptop/"tablet pc" with the new Wacom touch screen that I'm aware of just setup in Karmic using linuxwacom 0.8.5-1 [here]("http://ubuntuforums.org/showthread.php?t=1314869").

So it's getting close.
There's no way at the current state for X to support multiple inputs without multiple cursors. Multipointer X is getting there, but a lot of people want a multitouch interface that recognizes the second input as a helper and not so much as a pointer. Sorta like an add-on to the first pointer, but not a pointer in-itself, much like a "helper" pointer.

---

### Post by Xbehave on 2009-11-08
> **toupeiro said:**
> What would be really cool is when you activate the second keyboard/mouse you can set your credentials at that time for the entire use of that set of input devices.That might be a nice option but i cant see any sensible usage cases and i can see a lot of problems (they can see anything you type, what if one of you locks the screen)

> Once I get my hands on it I may try to make that work.
You will be looking at local xforwarding (take that all you xorg nay sayers), xhost and xypher but, i think you will need to do some coding to get what you want workingit working

>  X-windows is technically run by root 
For now, the trend is towards rootless-X (depends on kms somehow), it is not here now, but any solution will need to take that into account. Perhaps the 1st user can allow the 2nd forwarding and give him control bound to the forwarded windows. Any changes would require a way for 2nd users to launch programs (even under current setups gui launchers are running under the login users UID) so would need launcher integration and possibly WM integration to grant/revoke users access to your program.

> **Frak said:**
> There's no way at the current state for X to support multiple inputs without multiple cursors. Multipointer X is getting there, but a lot of people want a multitouch interface that recognizes the second input as a helper and not so much as a pointer. Sorta like an add-on to the first pointer, but not a pointer in-itself, much like a "helper" pointer.
multitouch as in pintch/2finger scroll/etc is already possible, all it needs is the SHM and programs capable of understanding it, or programs to interpret them, which can be something as simple as a perl script will convert pinch into ctrl++/ctrl+-. MPX is a different ball game.

---

### Post by toupeiro on 2009-11-08
> **Xbehave said:**
> That might be a nice option but i cant see any sensible usage cases and i can see a lot of problems (they can see anything you type, what if one of you locks the screen) 

The one that locks the screen should be able to unlock it. or the X server should be able to detect activity on a set of input devices, authenticate that set, and if authenticated succesfully, kill the screensaver session if its owned by the other UID (which could be possible with X still running as root).  My point is that this type of collaboration will have a lot of value in business (small and large), and business cares about security.  In my opinion, the use case for the technology is the same use case to make sure its secure, especially if it's going to be adpoted into mainstream linux OS releases in the future.  Its not necessarily about everyone being able to see it, its what everyone can do as YOU if there is no role separation.

> 
You will be looking at local xforwarding (take that all you xorg nay sayers), xhost and xypher but, i think you will need to do some coding to get what you want workingit working
Ready and willing.

> 
For now, the trend is towards rootless-X (depends on kms somehow), it is not here now, but any solution will need to take that into account. Perhaps the 1st user can allow the 2nd forwarding and give him control bound to the forwarded windows. Any changes would require a way for 2nd users to launch programs (even under current setups gui launchers are running under the login users UID) so would need launcher integration and possibly WM integration to grant/revoke users access to your program.


multitouch as in pintch/2finger scroll/etc is already possible, all it needs is the SHM and programs capable of understanding it, or programs to interpret them, which can be something as simple as a perl script will convert pinch into ctrl++/ctrl+-. MPX is a different ball game.

I work with many technologies that enable multiple controls over one set of input devices (e.g. VNC,X11RDP, HP Remote Graphics etc etc.) but in all of those, as you pointed about, there is some sort of elevation and approval of a shared session.  Two sets of credentials can be accounted for, or at least two traceable sources.  Without the mechanism you pointed out, or one like I pointed out, its pretty much a giant cesspool from a security standpoint.  I'm very interested to see how that develops.  I expect it will be in pam.d modules, so it allows for multiple form factors of authentication.  I think setting the user on activation of a set of peripherals is one of the best ways to differentiate tasks, roles, and most certainly auditing who did what, and when.  I'd be willing to contribute some time to making that happen.

---

### Post by chris200x9 on 2009-11-08
I don't know if I got this right, but could someone ssh in and use a mouse and keyboard (on another machine) while I use them here? Like collaberation?

---

### Post by Xbehave on 2009-11-08
> **chris200x9 said:**
> I don't know if I got this right, but could someone ssh in and use a mouse and keyboard (on another machine) while I use them here? Like collaberation?If you use normal ssh -x, you do not connect to existing xorg session, rather anything you run runs in it's own new session.

> My point is that this type of collaboration will have a lot of value in business (small and large), and business cares about security.
If your using 2 mice+keyboards and want separation then use separate Xorg. I mean I'm not going to stop you developing this but i would be interested in where you want security, but will let somebody log in to your Xorg but don't trust, yet plan on leaving them alone on your xorg (i mean surely they aren't going to do anything bad while your there, at which point they can just steal your k/b anyway).

---

### Post by toupeiro on 2009-11-09
> **Xbehave said:**
> If you use normal ssh -x, you do not connect to existing xorg session, rather anything you run runs in it's own new session.


If your using 2 mice+keyboards and want separation then use separate Xorg. I mean I'm not going to stop you developing this but i would be interested in where you want security, but will let somebody log in to your Xorg but don't trust, yet plan on leaving them alone on your xorg (i mean surely they aren't going to do anything bad while your there, at which point they can just steal your k/b anyway).

I think you're splitting hairs. :)  Security != trusting someones computing habits while you are in the room versus out of the room.  Just because I am working on the same GUI with someone else does NOT mean I want them to have my home directory, my environment, my security.  Accidents can and will happen.  Now, would you rather an accident happen in someones own environment, or an environment which may or may not have group security reaching much farther than anyone else?  I see no reason to have a great solution like this out there with a gaping security hole.  I'm willing to help.  If I leave them alone with my xorg, thats a whole different kind of security that I am not following, now isn't it? :)  If I walk away with my input sessions still active, or windows still open as my ID, then the problem was my use of a collaborative system.  If I am logged in, trying to show someone, say, how to do some administrative tasks, and they fat finger an rm command with my UID and all my group memberships because there was no mechanism to separate roles within a shared x-session, then thats a flaw of the tool that should be addressed.  Thats just one example, I can think of many.

---

### Post by prodigy_ on 2010-02-25
> **23meg said:**
> I'd like to drop two links, without comment:

[list][*][1]("http://10gui.com/")
[*][2]("http://www.wacom.com/bamboo/bamboo_touch.php")[/list]

Only a pity such things **never** work... outside of nice presentations.

Multi-touch and clickless UIs are funny conceptual toys, I agree. But ol' good computer mice are here to stay. For a loooong time. And that's good. Because everyone who ever used at least a laptop touchpad knows from personal experience that mouse is a nearly perfect input device (if compared with the existing alternatives) for day-to-day work.

---

### Post by toupeiro on 2010-02-25
I'm still keeping my fingers crossed that one day I will be able to assign a pointer and keyboard to a user thats NOT the primary user.  Until then, this will remain a very cool, but insecure function for collaboration.

---

