---
title: "The Pause/Play Buttons With Quod Libet"
date: 2009-06-15
forum: System76 Support
---

### Post by Cadeyrn on 2009-06-15
So, on my Pangolin Performance's tilde is a play/pause button that takes effect when I hold FN and press it. Currently in 64x Jaunty all the button does on any program is press the currently selected button of the currently selected window without the effects of that button actually happening. I would like to set it to pause and play Quod Libet's music playback regardless of what is selected.

---

### Post by thomasaaron on 2009-06-15
You would have to create a script that caused the focus to shift to Quod Libet (which shouldn't be that hard), and then trigger Quod Libet's button (and I doubt you can access its buttons via a script while its already running). Most likely you would have to dig into Quod Libet's source code and modify it so that it could be controlled while it is running.

A) That's all speculation.
B) It's beyond my area of expertise.

---

### Post by Cadeyrn on 2009-06-15
Alright. I think that's a little too much trouble for just a small perk like the pause/play button. Thanks for telling me that, and now I know. I guess if I ever really want it for some reason I'll look into that.

---

### Post by hugmenot on 2009-06-17
> **thomasaaron said:**
> You would have to create a script that caused the focus to shift to Quod Libet (which shouldn't be that hard), and then trigger Quod Libet's button (and I doubt you can access its buttons via a script while its already running). Most likely you would have to dig into Quod Libet's source code and modify it so that it could be controlled while it is running.

A) That's all speculation.
B) It's beyond my area of expertise.

Well, I don&#8217;t think all that is necessary. 

To get your button to act as the Play/Pause button for media apps you have to ascertain what signal it emits.  Just start "xev" in a terminal and then press Fn Tilde and look for the name of the button that will be displayed in the output on the terminal.

On my laptop the Fn-DownArrow combination already emits the XF86AudioPlay signal, which is automatically used as the Play/Pause media button. In xev it does not even display because it is already mapped as a global shortcut (all it displays is "NotifyGrab", i.e., the key is grabbed no matter what app is focused).

 It might be that your Fn combo sends a different signal. When you figured it out you can go to "System&#8594;Preferences&#8594;Keyboard Shortcuts" and try to set "Play (or Play/Pause) to your Fn-Combo. After that it should work for players like Totem, Rhythmbox, Banshee et al.

In Quod Libet you will need to enable the "DBus Multimedia Keys" plugin to make it work there too.

The short of it: Make sure Gnome is configured to recognize your key and enable the QL plugin.

---

### Post by thomasaaron on 2009-06-17
Like I said. It's definitely not my area of expertise. But he said...

> I would like to set it to pause and play Quod Libet's music playback regardless of what is selected. 

The way I'm understanding that, if he had, say, Totem, VLC and Quod Libet all opened, and VLC had focus, he would still want the key to control Quod Libet.

Is that the way you understand it?

---

### Post by Cadeyrn on 2009-06-17
For now I'll configure it to work with all of the media players, but what thom just said is true. What would be the point of the pause/play button working if it only affects the curren window? Quod Libet already has a button that only affects it when it's selected, CNTRL+Space, and most movie players, while selected, are paused with the space button.

---

### Post by hugmenot on 2009-06-17
No no. You got it wrong. The shortcuts defined in the "Keyboard Shortcuts" window are global to the whole desktop.

---

### Post by hugmenot on 2009-06-17
And yes, this means if you have several media programs running all of them will react to the keypress at the same time. Which is not optimal.

---

### Post by Cadeyrn on 2009-06-17
My computer doesn't do that. In fact VLC didn't even recognize FN+tilde as a button.

---

### Post by hugmenot on 2009-06-18
Ok, you don&#8217;t have to configure each app separately. The keys you configure in each app will only work when the app in question has the focus.

What I am talking about is global media shortcuts. And you have to configure those in the "Keyboard Shortcuts" window. 

Now, I&#8217;m not sure if VLC supports accepting media key events. But all other gnmoe-ish programs should.

I have the impression that you don&#8217;t believe me. Googling for this revealed this [blog post]("http://ronny.haryan.to/archives/2007/05/11/d-bus-multimedia-keys-plugin-for-quod-libet/"). Perhaps that makes it clearer.

---

### Post by Cadeyrn on 2009-06-18
Hah! After enabling that little plugin, the play/pause button only affects Quod Libet no matter what. Mission accomplished.

---

### Post by hugmenot on 2009-06-18
Well, I&#8217;m glad. ;)

---

