---
title: "Mouse free computing."
date: 2008-09-28
forum: The Cafe
---

### Post by hessiess on 2008-09-28
Recently I have been trying to find a way to totally remove the mouse as a nesseserry part of computer control, there are a number of reasons behind this.

Im dyslexic and carry a laptop prity much everywhere I go, primevally to help with writing. it runs a fairly minimal Arch install, and boots in around 30 seconds from cold, 10 from standby. however this is nullified if I have to waste time untangling a mouse, as the tuchpad is so twitchy its next to useless(not a driver isule, its the same in XP). the second issue is if I use a mouse for any length of time my wrist and fingers ache, which for some reason isn't a problem when using a keyboard.

one solution is using CLI applications as much as possible, this is fine, except some things just aren't passable in the CLI, for example open office(I need it for my collage coerce).

web browsing presents a significant problem, as it evolved around the GUI. in firefox(my preferd browser, due to some extensions) pages can be navigated by searching through links "'", but that only works with text, not images. in the case of image-links, you eather have to get as close as possible with "'" and "/", or use "F7" mode, then tab to the link. while this works it is highly inefficient. the other option, disabling images and using the text search is totally dependent on the existence of "alt" attributes on the images. if threes a missing attribute on a image link, the link may as well not exist. another problem is with the spell checker, for some reason the "open right mouse click menu keybord button" dousent work with the spell checker, it just opens the menu as if the cursor wasent over a spelling error.

the other problem, Open Office. while this can be used with keyboard short cuts, its not exactly intuitive, and was obviously designed to be mouse oriented. although thankfully the 'right click button' actualy works proppaly. Currently i just tent to wright out the text using Vim, and copy it into OO. fine, but still very slow, and dousent work for spreadsheets etc. a partial solution would be Vi emulation in OO, but I have been unable to find a plug-in to do this. I would expect there to be one, as there is a pligin for MS office offering Vi emulation. spreadsheets etc with just the keyboard is just plain annoying.

all suggestions welcome.

---

### Post by schauerlich on 2008-09-28
If you're looking for a better WM, I would suggest wmii. It's a good balance of powerful keyboard controls and ease of use.

---

### Post by hessiess on 2008-09-28
> **EDavidBurg said:**
> If you're looking for a better WM, I would suggest wmii. It's a good balance of powerful keyboard controls and ease of use.
Im using Awesome, I have tryed wmii, but couldn't work out how to configure it.

---

### Post by init1 on 2008-09-28
From what I understand, this will make Firefox easier to operate without a mouse
[https://addons.mozilla.org/en-US/firefox/addon/4891](https://addons.mozilla.org/en-US/firefox/addon/4891)

---

### Post by hessiess on 2008-09-28
thanks, verry usefal :)

---

### Post by brunovecchi on 2008-09-28
> **init1 said:**
> From what I understand, this will make Firefox easier to operate without a mouse
[https://addons.mozilla.org/en-US/firefox/addon/4891](https://addons.mozilla.org/en-US/firefox/addon/4891)

+1
Vimperator is great, specially if you are already used to Vim's keybindings.

---

### Post by Dr Small on 2008-09-28
> **hessiess said:**
> the second issue is if I use a mouse for any length of time my wrist and fingers ache, which for some reason isn't a problem when using a keyboard.
My fingers are the same way.


> **hessiess said:**
> 
web browsing presents a significant problem, as it evolved around the GUI. in firefox(my preferd browser, due to some extensions) pages can be navigated by searching through links "'", but that only works with text, not images. in the case of image-links, you eather have to get as close as possible with "'" and "/", or use "F7" mode, then tab to the link. while this works it is highly inefficient. the other option, disabling images and using the text search is totally dependent on the existence of "alt" attributes on the images. if threes a missing attribute on a image link, the link may as well not exist. another problem is with the spell checker, for some reason the "open right mouse click menu keybord button" dousent work with the spell checker, it just opens the menu as if the cursor wasent over a spelling error.

Look up Vimperator. I think you would love it. It uses Vim's keyboard commands, and makes web-browsing 10 times easier :)

---

### Post by niccholaspage on 2008-09-28
> **init1 said:**
> From what I understand, this will make Firefox easier to operate without a mouse
[https://addons.mozilla.org/en-US/firefox/addon/4891](https://addons.mozilla.org/en-US/firefox/addon/4891)
It is a awesome addon. I just can't find a way to click into a text box like the post reply one.

---

### Post by hessiess on 2008-09-29
> It is a awesome addon. I just can't find a way to click into a text box like the post reply one.

you can press the 'f' key, which puts a number over the HTML form that, when followed like a link, allows you to insert into the form.

> 
My fingers are the same way.

would you have any idea why my and your fingers ache when using a mouse?

> 
Look up Vimperator. I think you would love it. It uses Vim's keyboard commands, and makes web-browsing 10 times easier

Vimperator is just what I was looking for, sweet :)
except for some obscure reason the 'quick reply activate' links on this website vanish when I press 'f' and the simely links don't have numbers assigned to them.

next problem, OpenOffice.

---

### Post by brunovecchi on 2008-09-29
> **hessiess said:**
> 

next problem, OpenOffice.

My suggestion would be to write all your text in a text editor (not a word proccessor) such as vim or emacs. They are designed to be used with the keyboard only. If you **really** need some formatting, then you can 1) paste it into OOffice and make some finishing touches, or better yet 2) learn LaTeX or Html and add the appropiate formatting tags right there with the text editor.

With option 2, you'll never need a mouse. It doesn't play well with collaborative projects though, since it's not a popular choice.

---

### Post by Stefanie on 2008-09-29
Latex isn't very popular but it's extremely efficient. you can use vim, vim-latexsuite and the built-in spellchecker without needing to worry about the mouse ;-)

---

### Post by regomodo on 2008-09-29
#

---

### Post by hessiess on 2008-10-03
Is there any way to convert HTML into a doc or PDF?.
I am yet to find a way of accuratly printing HTML, short of tacking multiple screenshots and stiching them together.

---

### Post by cardinals_fan on 2008-10-03
> **hessiess said:**
> Is there any way to convert HTML into a doc or PDF?.
I am yet to find a way of accuratly printing HTML, short of tacking multiple screenshots and stiching them together.
[http://linux.die.net/man/1/htmldoc](http://linux.die.net/man/1/htmldoc)

---

### Post by brunovecchi on 2008-10-03
> **hessiess said:**
> Is there any way to convert HTML into a doc or PDF?.
I am yet to find a way of accuratly printing HTML, short of tacking multiple screenshots and stiching them together.

Alternatively, you can open your html file in OOffice or your web browser and save as pdf file or print to pdf, respectively.

---

### Post by hessiess on 2008-11-02
Im now using LaTeX for typesetting all my documents, not only does it work perfectly without the mouse, The output looks much beatter aswell.

> Alternatively, you can open your html file in OOffice or your web browser and save as pdf file or print to pdf, respectively.

This works with sumple documents, but with anything remotily complecated the output is always inconsistent from what is displayed in a web browser. Also, OO dosent seam to support CSS.

Anybody here know how to make firefoxes spell ckecker work porpaly with the ``open right click menu'' key?

---

### Post by chucky chuckaluck on 2008-11-02
another solution for web browsing could be **elinks**. (i've found it to be better than both lynx and links2 for dealing with sites like yahoo.) pressing "." will put a number in front of each link which you can simply select by typing that number and pressing "enter" twice. images are handled as links and can be opened with an external image viewer (i use **feh**). if you're using a laptop, using a text browser might save you a little battery power, as well.

---

### Post by hessiess on 2008-11-02
> **chucky chuckaluck said:**
> another solution for web browsing could be **elinks**. (i've found it to be better than both lynx and links2 for dealing with sites like yahoo.) pressing "." will put a number in front of each link which you can simply select by typing that number and pressing "enter" twice. images are handled as links and can be opened with an external image viewer (i use **feh**). if you're using a laptop, using a text browser might save you a little battery power, as well.

Thanks for the suggestion.

---

