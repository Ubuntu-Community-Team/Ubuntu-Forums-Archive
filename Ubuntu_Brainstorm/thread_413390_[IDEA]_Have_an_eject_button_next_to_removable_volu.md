---
title: "[IDEA] Have an eject button next to removable volumes"
date: 2007-04-19
forum: Ubuntu Brainstorm
---

### Post by lolocaust on 2007-04-19
**Summary:**
Place a tiny eject icon next to removable volumes on the desktop and in folder views (perhaps next the filename like iTunes/iPod or as an emblem on top of the volume icon) which will safely unmount it when the user clicks it.

**Rationale:**
Instead of hiding unmount in a right-click menu, which some users may not find, there could be a clearly visible way of unmounting volumes.

**Implementation Plan:**
No idea really, but I'm sure the changes would only need to be done in Nautilus.

EDIT: aysiu has a nice [example screenshot here]("http://ubuntuforums.org/showthread.php?p=2509656#post2509656"). Also, it seems that having the icon on the desktop may not be a good idea, and most people would prefer having it only in nautilus' folder view. Discuss your ideas please!

---

### Post by eentonig on 2007-04-19
I really can't see the added value in this, except for putting more clutter on my Desktop. The way it's implemented now is already easier than it is under windows, where you have to click on de icon in your taskbar. ...And hope you can identify the correct drive amongst the sometimes cryptic names available.

I really don't see the difficulty in using the right-click.

---

### Post by Bou on 2007-04-19
I once mailed desktop-devel-list about a similar idea. I think the screenshot will let you get the idea:

[IMG]http://img503.imageshack.us/img503/4111/pantallazobu2.png[/IMG]

You can follow the whole discussion [here]("http://www.mail-archive.com/desktop-devel-list@gnome.org/msg08070.html").

---

### Post by aamukahvi on 2007-04-19
The screenshot Bou posted looks way cool.

---

### Post by Bou on 2007-04-19
> **aamukahvi said:**
> The screenshot Bou posted looks way cool.

Yeah, sadly the proposal was turned down because it offered no way to use it through the keyboard. Bummer.

---

### Post by Lucifiel on 2007-04-19
> **Bou said:**
> Yeah, sadly the proposal was turned down because it offered no way to use it through the keyboard. Bummer.

Hmmm... actually, why not allow people to map the function then? That is: pressing a combo key will allow people to eject a volume? How about that?

---

### Post by rsambuca on 2007-04-19
I guess I don't really see the need for this one.  For the most part, if a person knows that they have to unmount a drive prior to unplugging it, they know to right-click the drive.  If they don't know that a drive should be unmounted prior to unplugging it, they are just gonna do it anyways.

I must be in the less-clutter-is-better camp.:)

---

### Post by junior aspirin on 2007-04-19
would be trivial to add it in nautilus' toolbar
[[IMG]http://img452.imageshack.us/img452/9381/screenshotbx2.th.png[/IMG]](http://img452.imageshack.us/my.php?image=screenshotbx2.png)

---

### Post by rbmorse on 2007-04-19
Kubuntu users can make an eject button all by yourself.

Right click on "K" menu, menu editor, right-click the desired category (I used system), select "add item." Fillout name, description, etc fields as desired.  In the command field enter 

eject

check "place in system tray" box if desired.  Click on the icon box and select an appropriate system icon.  

click on file, then save.  

Once you have created an "eject" command in the menu, you can drag it to any other window where you have write permission.

---

### Post by nicolas2b on 2007-04-20
I don't think add an icon on the desktop to unmount/eject is a good idea. But the idea of *Bou* is great, it's a good solution.
But, I don't know if in GTK, we can put two action in the same 'line' ( sorry if my question is not clear, I don't know how to explain :confused: )

Nicolas

---

### Post by ELD on 2007-04-20
I like the idea of it and the screenshout Bou sent is brilliant. I am all for it! But mabye it should be an option so it isn't too much "clutter" for picky people.

---

### Post by Bou on 2007-04-20
> **nicolas2b said:**
> But, I don't know if in GTK, we can put two action in the same 'line' ( sorry if my question is not clear, I don't know how to explain :confused: )

Well, I doubted it at first but just take a look at tomboy, it does it so you definitely can.

I'm glad you guys liked the idea, if you can come up with a good (and, more importantly, DISCOVERABLE) way to use the feature, maybe we could poke the devs about it again.

---

### Post by nicolas2b on 2007-04-20
> **Bou said:**
> Well, I doubted it at first but just take a look at tomboy, it does it so you definitely can.

I'm glad you guys liked the idea, if you can come up with a good (and, more importantly, DISCOVERABLE) way to use the feature, maybe we could poke the devs about it again.

I just look it, and there are  two "actions" in the same line. But Tomboy run with mono. Is this GTK too?

---

### Post by PriceChild on 2007-04-20
I may be confused... but what's wrong with "right click + eject" or "right click + unmount" on the desktop?

---

### Post by r3m0t on 2007-04-20
If I were trying to navigate that through the keyboard, I would press "right arrow" - just like I would to open a submenu.

(If I were using a RTL (right-to-left) language like Hebrew, I would press "left arrow", of course.)

---

### Post by Boring Bloke on 2007-04-20
> **rsambuca said:**
> I guess I don't really see the need for this one.  For the most part, if a person knows that they have to unmount a drive prior to unplugging it, they know to right-click the drive.  If they don't know that a drive should be unmounted prior to unplugging it, they are just gonna do it anyways.

I must be in the less-clutter-is-better camp.:)

For those who don't know, it might be worth having a waning pop up first time (and only the first time otherwise it will become annoying) they mount a usb drive saying something like "please eject the drive before removing it to avoid data corruption". 

Making the eject option more obvious in the places menu, nautilus, disk mounter panel applet etc. seems like a good idea. Just not on the Desktop.

---

### Post by dtsdude on 2007-04-20
dont you just have to drag the desktop icon of the drive to the trash, if not implement it. (i know, i might be confusing with osx, but i just cant be bothered to reboot now to check)

---

### Post by aysiu on 2007-04-20
I'd love to see it in the sidebar of a file browser, but on the desktop it may just look awkward.

---

### Post by spanella47 on 2007-04-22
for the desktop:
the button wouldn't have to be anything large.  a small eject button that showed up in the corner of the icon would be very convenient (much like emblems appear).  all other methods of ejecting could still exist taking care of any concerns about accessability. 

another idea would be to move eject to the top of the right click menu for removable media. (understand there could be issues with this for consistency sake since every menu starts with OPEN)

for nautilus browser:
like the iTunes like eject buttons next to the drive names

---

### Post by tgoose on 2007-04-22
> **dtsdude said:**
> dont you just have to drag the desktop icon of the drive to the trash, if not implement it. (i know, i might be confusing with osx, but i just cant be bothered to reboot now to check)

This is only in OS X. Personally I don't think that's a particularly user-friendly way of doing it, since one action does completely different things in different contexts. OK, so the icon does change, but you'd have to select the drive to drag it somewhere before this even appears.

There are a number of ways of making ejection easier than it currently is in Ubuntu.


Firstly, the eject button in Nautilus which is also implemented in OS X's Finder is definitely the way I'd support. See
[http://www.edb.utexas.edu/help/tutorials/security/images/ed_step5b.jpg](http://www.edb.utexas.edu/help/tutorials/security/images/ed_step5b.jpg) . The disadvantage this has is that Nautilus needs to have its sidebar active and set to Places or Tree for this to even be visible.

Secondly, this button could be added to the desktop icons too (which is what I guess the topic suggests.)
That way it's one click, rather than the present Ubuntu menu which after right-clicking presents eleven other options; most of which are greyed out because they're irrelevant to a disk drive (in fact, maybe these should be removed from disk drive context menus: cut, copy, make link, rename, move to trash, and delete, unless some of them like "rename" can be made functional.)

Thirdly, a keboard shortcut like CTRL + E would be handy. That may or may not be implemented in OS X; I don't remember.

Fourthly, the menu as in [http://img503.imageshack.us/img503/4111/pantallazobu2.png](http://img503.imageshack.us/img503/4111/pantallazobu2.png) isn't a bad plan at all.

Fifthly [http://img452.imageshack.us/my.php?image=screenshotbx2.png](http://img452.imageshack.us/my.php?image=screenshotbx2.png), but I don't know I don't know how obvious that is to see unless you already know where to look.

Sixthly, dragging to the wastebasket could work, but as I said that's not very intuitive.

---

### Post by aysiu on 2007-04-22
**Summary**
An eject button in the file browser side bar next to each removable drive, mounted partition, or CD/DVD.

**Rationale:**
Fewer clicks than the current right-click to unmount volumes and the proposed [drag volume to trash to eject it proposal](http://ubuntuforums.org/showthread.php?p=2509441#post2509441). It's also immediately visually obvious. A context menu and a magically appearing eject icon in place of the trash are discoverable but involve searching and experimenting. A little eject icon in the sidebar cannot be missed.

**Scope and Use Cases:**
Leslie has very little computer experience and has plugged in a USB drive full of photos his niece gave him. It shows up in the file browser. He has absolutely no inclination to right-click the drive icon or drag it to the trash (why would he?), but since he sees an eject icon next to the volume icon, he thinks that might be a good thing to do (otherwise, he would have just yanked the stick right out without ejecting/unmounting it).

**Implementation Plan:**
Make the icon appear next to anything that's mounted.

---

### Post by zeeR on 2007-04-22
I think this is a great idea...Reminds me of the eject button on iTunes.

It's simple, smart and useful! Hope it gets implemented on Gutsy!

---

### Post by chamberlain2006 on 2007-04-22
+1, seems like an easy way  to do it.

---

### Post by lolocaust on 2007-04-22
I'm a favour of this idea, in fact I've made a thread with this suggestion but I also suggested that there should be another eject button on the desktop.

EDIT: thinking about it, it's not probably needed on the desktop, since the user will have a file browser open on the drive and will eject from there. But then again from the desktop they'll either have to double click to open a new window then eject, or use the current right-click eject method.

---

### Post by The Joe on 2007-04-22
That's actually a wonderful idea. I vote for it.

---

### Post by aysiu on 2007-04-22
Whoops! You're right. You proposed it first. I'm merging the two threads.

---

### Post by lolocaust on 2007-04-22
Thanks, though I'm starting to think that the button on the desktop is a bit too much clutter-wise, so I'm in favour of just in nautilus' folder views. Also, I edited my original post.

---

### Post by Feba on 2007-04-23
Almost any of the above ideas would be a huge improvement for such little effort to me. This makes it much easier, and should be added if for nothing else but to stop data corruption.

I mean hell, add two popups. "Device (DeviceName) mounted. Press the Eject button or Right-Click and select Eject to safely remove", for the first time a device is mounted after ubuntu install, and "Device safely removed! Remember to always eject devices before unmounting them in the future." after a "Eject" is clicked (and of course, the device safely unmounted) the first time. Keep the warning about always ejecting popping up whenever someone just rips it out, as it is now.

So three warning windows/popups: "You should do this." "Dammit, do this." and "Good boy!". I promise you, this would help most users a lot simply because your average user will have their mind go from wondering what "Mount" means to thinking about animal husbandry in thirty seconds flat.

---

### Post by tonyr1988 on 2007-04-27
+1

Love it - very clean design, very simple and straight-forward.

---

### Post by PhilipGanchev on 2007-05-21
Bou: nice mockup! I have been thinking this functionality is needed for a while.  The issue is not only knowing that you can and should eject it, but the convenience of being able to do that from the Places menu which is easily accessible from anywhere.  By contrast, now you have to open the drive in a Nautilus window, open a menu and choose unmount.  This is two more operations, and extra waiting.

I don't understand the objection of not being able to access it via the keyboard.  How is that done now?  Plus it can be made so that the eject button is selected when the whole item is selected and you press the Tab key, then activated when you press Space.

---

### Post by rsambuca on 2007-05-21
> **PhilipGanchev said:**
> By contrast, now you have to open the drive in a Nautilus window, open a menu and choose unmount.  This is two more operations, and extra waiting.
Uh, no.  If the drive is on your desktop, all you have to do is right click the drive and the unmount option is already there.

---

### Post by RAOF on 2007-05-21
> **aysiu said:**
> **Summary**
An eject button in the file browser side bar next to each removable drive, mounted partition, or CD/DVD.
...

Cool idea, I've been wanting something like this.  Is there a spec up (or bug on Launchpad/Gnome bugzilla) that I can subscribe to?  I'd like to help with this (time to learn GTK coding & resurrect the C knowledge :)), but I'd like to make sure I'm not duplicating someone else's work!

---

### Post by Quibly on 2007-05-21
Its a cool idea but its trivial... The devs should focus on greater features and not on the small things.

---

### Post by tgoose on 2007-05-21
> **Quibly said:**
> Its a cool idea but its trivial... The devs should focus on greater features and not on the small things.

If it's trivial **to implement** and improves usability, then surely it's a good thing to code?

---

### Post by Feba on 2007-05-22
agreed, it's the little things that make things wonderful or a pain in the ***. Think about how much of a pain it would be to have to search for every application in a file manager, instead of a start/application menu. It might seem trivial, but I can promise you that if I had to search for an executable every time I wanted to run a program, I'd switch OSs very quickly.

---

