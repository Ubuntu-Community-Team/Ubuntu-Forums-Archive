---
title: "Xubuntu&amp;Xfce keyboard window management. How do you do it?"
date: 2015-07-09
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2015-07-09
It annoys me to no end, that I am always fussing with the mouse to minimize, maximize and place windows on the desktop.

So, how do you Xfce keyboard-centric people manage placement of windows. Like minimize, maximize, place in one quarter of the desktop or change to another quarter. Change to 1/2 screen or full screen. Open four windows and have them placed in all four quarters of the desktop, maximize one, or minimize one and place another open page in it's place, On and on.

I do have the compositor enabled that comes with Xubuntu DE, but won't use Compiz or Kwin and the like.

I bet I get some ideas. Do you have an available screeny of the key combos you use?

Thanks.

---

### Post by ajgreeny on 2015-07-09
Here you go.  This is my window of the Settings-manager ->Window manager tab, which may be what you want, though I think you may want to be able to open a new window in a specific place; I'm not sure that is possible but it could be that I have just never needed or looked for a way to do that.

I don't use them a lot but it is good occasionally to have them available.

PS:  The Super + number shortcut are using a numberpad on my keyboard, not the numbers along the top of the keyboard so if that is all you have available you may need a different set of shortcuts.

---

### Post by vasa1 on 2015-07-09
Devilspie is a favorite of Toz. I think I remembering him saying it plays well with Xubuntu/XFCE.

Here's an example:```
 To force my pluma text editor to always open on the second virtual desktop, 
in the top-left corner of the screen and 700 pixels wide by 500 pixels high, I have to create a file
containing a rule to apply to pluma windows with the following text:

(if
      (is (application_name) "Pluma")
      (begin
          (set_workspace 2)
          (geometry "700x500+0+0")
      )
)

The filename is unimportant, but must end in .ds, and must be saved to a directory in your home directory named .devilspie. 
```From: [http://pclosmag.com/html/Issues/201506/page01.html](http://pclosmag.com/html/Issues/201506/page01.html)

---

### Post by mikodo on 2015-07-09
Thanks, folks!

Those look great, ajgreeny.

I'll have to read about DevilSpie, vasa1 and thanks, for looking up and sharing Toz's, file with your explanation and link.

---

### Post by vasa1 on 2015-07-10
And I'm sure **Dennis N** will add some helpful stuff as well.

---

### Post by flocculant on 2015-07-10
> **mikodo said:**
> Thanks, folks!

Those look great, ajgreeny.

I'll have to read about DevilSpie, vasa1 and thanks, for looking up and sharing Toz's, file with your explanation and link.

If you do go the way of devilspie (I've been using it for a long time) check out gdevilspie (in repos) - gui to set up the rules.

---

### Post by mikodo on 2015-07-11
> **flocculant said:**
> If you do go the way of devilspie (I've been using it for a long time) check out gdevilspie (in repos) - gui to set up the rules.
Hey, thanks for that. That would be best for me.

---

