---
title: "Children, don't try this at home!"
date: 2008-04-19
forum: The Cafe
---

### Post by ibuclaw on 2008-04-19
Okay,
Today, I wanted to create a Shortcut to my Home Directory on my Desktop, so what is the most obvious way to do that?

I know, lets open up "Places" in the menu bar and "Click and Drag" the shortcut to Home to your desktop...

**WARNING, DO NOT TRY THIS!!!**

Hmmm....
Why is it taking so long?

Next minute,  poof!
The system freezes. I loose all control of Ubuntu!
And eventually have to do a hard reboot.

But why did this happen?
Well, apparently "Home" in the Places menu is no shortcut, it's a folder!

And by clicking an dragging the folder to your Desktop, you copy all the folders (and files) from within that folder.

Now, my name is "administrator" and the first folder in my Home Directory is "Desktop" and the first folder name in my desktop is name "administrator", since I copied my home folder to my Desktop, It then copies that folder, which copies the Desktop folder, which copies the Home, which, as you can see is a recursive decompression bomb!

I tried entering the directory, this is how far I got before Nautilus started to loose control and I was forced to hard quit (I copied the address bar beforehand)

```
/home/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop/administrator/Desktop
```

And I can guarantee, that *that* is surely going to be the tip of the iceberg for that!

I think a warning should be made about this, as it is seriously dangerous!

Regards
Iain

---

### Post by LaRoza on 2008-04-19
What did you expect?

---

### Post by ibuclaw on 2008-04-19
Well, for it to automatically create a shortcut for starters...

But I've removed it now, and gone back to the trusty CLI

```
 ln -s ~/ Home 
```

Thank goodness for BASH!

---

### Post by Happy_Man on 2008-04-19
That gave me a chuckle. No offense, but I must agree with LaRoza. What did you expect? I was surprised the Places menu even let you drag. If you are still searching for the "right" way to do this, open up gconf-editor (Applications --> System Tools --> Configuration Editor) go to Apps/Nautilus/Desktop and check the home_icon_visible option. 

Other than that, though, I congratulate you on your novel and innovative way of crashing Linux, something the experts say should be impossible! Mad props to you, my good man.

---

### Post by conehead77 on 2008-04-19
> **LaRoza said:**
> What did you expect?

I guess he expected a shortcut ;)

---

### Post by Kingsley on 2008-04-19
LOL

Hold down ctrl and shift while dragging the file or folder. It did take me a long time to realize GNOME can have shortcuts.

---

### Post by kragen on 2008-04-19
Yeah, I'd agree with tinivole on this one - you would have expected a shortcut.

I mean, if you know and understand all the workings thats going on behind this, yeah - its not that silly, but as far as intuitive behavior thats pretty stupid. I'd probably raise it as a bug if i were you.

At the very least nautlius should detect when its entering a recursive-copy situation like that.

---

### Post by FuturePilot on 2008-04-19
This is indeed a bug. I tried this on Gutsy and Nautilus will give you a warning that you can't do this. In Hardy there is no warning and it will actually proceed with the operation. I tried to copy my Desktop to my Desktop and I got a folder called Desktop on my Desktop that went something like this
```
Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop
```
etc. :shock:

---

### Post by TBOL3 on 2008-04-19
While I can see that logically, I think that's crap.  If I wanted my folder copied I would copy it.  Why would I want TWO folders, thus TWICE the size?  It really should make a link.

---

### Post by Polygon on 2008-04-19
I would report this to launchpad

---

### Post by LaRoza on 2008-04-19
> **TBOL3 said:**
> While I can see that logically, I think that's crap.  If I wanted my folder copied I would copy it.  Why would I want TWO folders, thus TWICE the size?  It really should make a link.

No, you are just used to other file managers. They all do things differently, and it is easy to get used to them.

Dragging and dropping a file to another directory on the same disk using moves it, but not in Thunar, it copies it. Both are logical if you think about it.

---

### Post by Google Spider on 2008-04-20
Now I'm itching to try this myself :|

---

### Post by swoll1980 on 2008-04-20
I would have expected it to make a link there would be no intelligent reason to believe it would copy. When you drag app shortcuts of the menu it creates a shortcut it doesn't copy the entire application I wouldn't expect the places menu to behave any differently than the app menu

---

### Post by fedex1993 on 2008-04-20
trust tried it in my virtual machine didnt really freeze just took a good 10 mins to finally finish but dont expect linux to do things automactially create a shorcut

---

### Post by heathenos on 2008-04-20
i used the  Ubuntu Tweak app for that.

---

### Post by SomeGuyDude on 2008-04-20
File managers should ALWAYS default to creating a shortcut when dragging something from one location to another. ALWAYS. If you want to copy or move, use control/shift/combination.

Why? Because it's a safeguard. It's better to have people accidentally making shortcuts and being annoyed for 10 seconds than to have someone accidentally doing something like this. I would have 100% expected a shortcut as well.

---

### Post by Energise on 2008-04-20
> **Kingsley said:**
> LOL

Hold down ctrl and shift while dragging the file or folder. It did take me a long time to realize GNOME can have shortcuts.

Could you tell me if this works with Ubuntu please?
Many thanks

---

### Post by swoll1980 on 2008-04-20
> **Energise said:**
> Could you tell me if this works with Ubuntu please?
Many thanks

Yes this is the easiest way to make a link in Ubuntu

---

### Post by pbpersson on 2008-04-20
The bottom line here is this:

1.  If I am Joe Newbie User and I do something simple to make my life easier and the OS self-destructs......that is a bad thing

2. Ideally, if I try to do something and I do it the wrong way, the OS should tell me what I NEED to do

Here is a perfect example - tonight I was in Mint, went to the command line and typed "lame" to see what would happen.  It told me in plain English that lame was not installed.....and then to my total shock told me what to type at the CL to get it installed.

In my opinion that level of hand-holding is what we need more of.

Ah....Kubuntu Gutsy does the same thing!  Excellent!

I was in Fedora and typed lame and it just said command not found - no help, nothing......that IS lame!!  Then I went to add/remove programs and told it to find lame, it was not in the list.  That is a perfect example of an OS I don't need to use.

---

### Post by swoll1980 on 2008-04-20
> **SomeGuyDude said:**
> File managers should ALWAYS default to creating a shortcut when dragging something from one location to another. ALWAYS. If you want to copy or move, use control/shift/combination.

Why? Because it's a safeguard. It's better to have people accidentally making shortcuts and being annoyed for 10 seconds than to have someone accidentally doing something like this. I would have 100% expected a shortcut as well.

I would double this when your not even dealing with an actual folder, but a menu that has what appears to be a shortcut to a folder. Never in a million years would I have thought that dragging an Icon of a menu would move an actual folder, and when I was a newb if it were not for tweak Ubuntu I would have tried it that way my self perhaps

---

### Post by Energise on 2008-04-20
Thanks very much
I'll give it a try when I get to work
Cheers

---

### Post by koenn on 2008-04-20
The MS Windows terminology used in these posts (shortcut, in stead of link/symlink or launcher) indicates that you've learned to expect certain behaviour in a MS Windows environment and you just assume other environments to behave the same (no, that is not 'intuition', it's learned). 
> 
Ideally, if I try to do something and I do it the wrong way, the OS should tell me what I NEED to do
And how is the OS supposed to know what you want to do ? read your mind ? One of the good things about Linux is that it allows you to do anything you want. That includes shooting yourself in the foot
You yourself should know what you need to do. At best; the OS (actually the user interface) could give you hints about how to do it.. 

In this case, the OP told the OS to copy a folder recursively, and that's what happened. Good. The OS seems capable of recursive copying, so there's nothing there to trigger a warning or an error.

What's going on here illustrates one of the drawbacks of GUI interfaces. The GUI developer needs to make an arbitrary choice about what a given action  (drag&drop) will do : move ? copy ? create a link ?   display a list of possible actions ?  let it vary depending on what's being dragged and where it's dragged to ?  Whatever the dev chooses, there'll always be people who expected something else. 

Given that Gnome cares about consistency and usability, they'd probably accept it as a bug, unless they have a good rationale for this behaviour. Other than that, consider it a learning experience and move on.

---

