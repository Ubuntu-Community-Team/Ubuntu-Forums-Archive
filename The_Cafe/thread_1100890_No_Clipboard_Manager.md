---
title: "No Clipboard Manager?"
date: 2009-03-19
forum: The Cafe
---

### Post by kevin11951 on 2009-03-19
Any reason why there is no clipboard manager in gnome?  I just tried out parcellite, and love it! I can copy from one program **CLOSE IT** and then paste in in another.

---

### Post by smartboyathome on 2009-03-19
> **kevin11951 said:**
> Any reason why there is no clipboard manager in gnome?  I just tried out parcellite, and love it! I can copy from one program **CLOSE IT** and then paste in in another.

Not all people need one. For example, I never use it even though I've had it installed for a while.

---

### Post by swoll1980 on 2009-03-19
I would use it. I hate when I copy from firefox, close it then go to paste, and it's lost. You would think I would remember this after doing it 20, or more times.

---

### Post by cdwillis on 2009-03-19
This is something that really confused me when I first installed Ubuntu. This is really something that should be going by default.

---

### Post by ajgreeny on 2009-03-19
Glipper is still here, surely?  I use it all the time in 8.04 and 8.10 (Mint6).

---

### Post by binbash on 2009-03-19
Not may ppl need it.Parcellite is one of the best for sure.

---

### Post by Yashiro on 2009-03-19
If you select text within the Gnome environment but do not 'Cut' it via a command it is placed into the 'primary selection' buffer.

You can usually retrieve this stored text by pressing your middle mouse button. (or pressing shft+insert)

If you 'Cut' information using Ctrl+C or a gui command it is placed into the Gnome clipboard. You can paste this information with Ctrl+V or 'Paste' like in Windows.

You are confusing yourself by trying to use the two methods in the same way. You *can* make all selections get copied to the clipboard, but this is actually very annoying in practice. 
(This involves running two instances of a program called 'autocutsel')

If you still have issues and are losing data install Parcellite or Glipper.

---

### Post by Tibuda on 2009-03-19
> **kevin11951 said:**
> Any reason why there is no clipboard manager in gnome?  I just tried out parcellite, and love it! I can copy from one program **CLOSE IT** and then paste in in another.

Not only close it, but you can also restart your computer. Parcellite is really great.

---

### Post by ajgreeny on 2009-03-20
You can also do that with glipper, though after a reboot you have to choose what to paste;  it's all still there in the buffer.

---

### Post by twowheeler on 2009-03-20
> **Yashiro said:**
> 
You are confusing yourself by trying to use the two methods in the same way. You *can* make all selections get copied to the clipboard, but this is actually very annoying in practice. 
(This involves running two instances of a program called 'autocutsel')


Wow.  It is incredibly dumb for two methods to do the same thing exist in gnome, so that an ordinary user, not knowing these geeky details, would very reasonably conclude that it is just broken.

---

### Post by Yashiro on 2009-03-20
It's useful but the crossover between 'gui' and older apps can be confusing in the beginning. 
You get used to it and it's quite helpful in the end. 
Just stick to using Cut and Paste like you would in Windows and you should be fine.

---

### Post by cthulhu_54 on 2009-03-24
Hi!
You will have to excuse me but how do I use glipper or parcellite? I installed both but can't seem to find how to start glipper, "man glipper" does not give anything. So I installed parcellite and started it "parcellite &" and I can see it running in the background but I tried copying (ctrl+c) and closing the editor to paste somewhere else but is just like before, i.e. nothing happens when pressing ctrl+v. What am I doing wrong?

---

### Post by ubuntu27 on 2009-03-24
> **cthulhu_54 said:**
> Hi!
You will have to excuse me but how do I use glipper or parcellite? I installed both but can't seem to find how to start glipper

I haven;t used Glipper for one year..
But, Glipper should be avaiable at 
**Application menu/Accessories/Glipper**

It should be there, unless it changed in the new versions..

---

### Post by Yashiro on 2009-03-24
Close Parcellite if you have it running.
Go to getdeb.net
Download and install their Parcellite package. (0.9.1)
If it doesn't appear in your tray automatically, open your Applications>Accessories menu and run it.
Right click the icon in the tray.
Select Preferences.

Put a tick in synchronize clipboards. (if you require this function)

Now if you ever cut some text and it vanishes. Left click the tray icon and select the text you 'lost'.

---

### Post by chris4585 on 2009-03-24
> [chris@Dax ~]$ pacman -Ss glipper
community/glipper 1.0-8
    Clipboard for gnome desktop
community/glipper-old 0.95.1-2
    Gnome clipboard for nongnome desktop
[chris@Dax ~]$ 


;)

---

### Post by Kingsley on 2009-03-24
> **cthulhu_54 said:**
> Hi!
You will have to excuse me but how do I use glipper or parcellite? I installed both but can't seem to find how to start glipper, "man glipper" does not give anything. So I installed parcellite and started it "parcellite &" and I can see it running in the background but I tried copying (ctrl+c) and closing the editor to paste somewhere else but is just like before, i.e. nothing happens when pressing ctrl+v. What am I doing wrong?
Glipper is a panel applet. It'll be labeled "clipboard manager."

---

### Post by cthulhu_54 on 2009-03-24
OK I see parcellite in my tray now. Better than before, but is there any whay to paste with ctrl+v?

its annoying to use the mouse just to paste the latest ctrl+c-text.

---

### Post by sgosnell on 2009-03-24
Parcellite remembers everything you copied, up to the limit of the number in the settings, then it starts recycling the selections in order of age.

To paste something from the past, click on the iconl in the panel, and you'll get a list of the clipboard contents.  Select the one you want, and when you use Ctrl-V or Paste, that selection will be pasted.  Otherwise, the clipboard action is the same as always.

Glipper is not provided by default in Jaunty, and IIRC, not in Intrepid either.

---

### Post by cthulhu_54 on 2009-03-24
OK, so I have to use the mouse, even if it is the latest copied text?
So to: ctrl+c, *close-editor*, ctrl+v in another editor, I have to go to the tray in between, jest prior to pasing it?

I was hoping I could get it working like it does in windows... 

Having a copy-history is good, but it would be most excellent if ctrl+v automaticly pasted the latest in the clipboard history.

---

### Post by sgosnell on 2009-03-24
As I said, if you don't do anything special, everything works the same as it would without it being installed, and the last thing you copied will be pasted via Ctrl-V.  You only need to access the history if you want to paste something from it instead of the current selection.  Copy and paste, by default, works the same in Linux and Windows.

---

