---
title: "Easycert"
date: 2009-06-29
forum: Wine
---

### Post by sparky77 on 2009-06-29
having a problem with easycert with wine
menu's don't open correctly.
anyone resolved this problem

i have installed the latest wine & winetricks
mdac 25 + vcrun6 installed

[http://www.tysoft.co.uk/easycert_download2.htm](http://www.tysoft.co.uk/easycert_download2.htm)

---

### Post by albert s on 2011-04-13
has anyone ever sorted this?
its one of the last reasons I still boot windows

---

### Post by cogadh on 2011-04-13
Given that this thread is almost two years old and got no responses at all, I seriously doubt it. It might help if you provided some details on what you in particular have experienced with this. Both Ubuntu and Wine have changed a lot since this thread was originally posted, it might not even be valid anymore.

---

### Post by albert s on 2011-04-13
.dll files keep getting deleted .
I have been trying to get it to work for a few weeks now,
but unfortunately have to dual boot.
it is a fairly limited/specialised software in all honesty so Im not really expecting a solution if truth be told,
just hoping.

---

### Post by cogadh on 2011-04-13
What do you mean by ".dll files keep getting deleted"? Wine doesn't (and as far as I know can't) do that.

---

### Post by albert s on 2011-04-13
I dont think it is wine,
Im not totally sure as I dont understand enough,
but I think ubuntu is deleting them as it doesnt know where to put them, or is trying to put them somewhere that isnt suitable.
I can sometimes see the file, but there is nothing inside it, it is corrupt/empty.
it may well be just one of these things I have to live with.

---

### Post by cogadh on 2011-04-14
Again, Ubuntu can't do that either, at least without you telling it to. 

If you really want some help getting this app to run, we can try to help you, but it kind of sounds like you've already given up. If you haven't given up, try to run the app using the terminal to get Wine's error output and post that here, it could explain what exactly is going on and may lead us to a solution.

---

### Post by albert s on 2011-04-14
ok, Im not at that computer just now, but I will give it a go as soon as I can,
what do I need to type in the terminal to get it to run?
sorry if that is a stupid question, I really dont know much about Ubuntu/computers,
and everything else I do is almost perfect in Ubuntu, its only this one small issue.
thanks.

---

### Post by cogadh on 2011-04-14
Assuming you already have the app installed, open the terminal, change directories to where the app is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<app installation directory>
wine <executable name>.exe
```
Obviously replace that <app installation directory> and <executable name> with the correct information.

If you don't have the app installed, then change directories to wherever you downloaded the installer and "wine" the installer executable (usage is basically the same as above).

---

