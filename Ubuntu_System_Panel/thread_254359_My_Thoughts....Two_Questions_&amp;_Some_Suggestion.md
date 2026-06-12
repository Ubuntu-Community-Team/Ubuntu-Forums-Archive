---
title: "My Thoughts....Two Questions &amp; Some Suggestions"
date: 2006-09-09
forum: Ubuntu System Panel
---

### Post by Coolit on 2006-09-09
Hi,

I've been spending the last few days setting up USP, I like it a lot, its far better than the alternative menu in my opinion, more configuration options and distro specific.

I have two questions though that I have been unable to find an answer too,

1. I've been looking for "plugins_list" but have been able to find it on my system, do I need to create this file somewhere? I'd like to try some of the cool plugins availible :)

2. I have the hex code for my theme colour but again I cant find any configuration file to edit this, where about is the darn thing!

I also have a few feature suggestions for future versions, in order of importance,

1. menu automatically closes after an app has been launched.
2. Return key to activates a search would be handy
3. Cosmetically like the SLAB menu a colour border round the full window would be nice.

Thanks for the work thats went into it so far, I'll be using it from now on and of course thanks for any help I'll get for the two questions :)

---

### Post by delfick on 2006-09-09
> **Coolit said:**
> 1. I've been looking for "plugins_list" but have been able to find it on my system, do I need to create this file somewhere? I'd like to try some of the cool plugins availible :)
go into the terminal and type "gconf-editor", then go to apps -> usp

then more towards the bottom of the list is the "plugins_list" entry thingo....

> 2. I have the hex code for my theme colour but again I cant find any configuration file to edit this, where about is the darn thing!

same as above, into gconf-editor then to apps -> usp
put ur colour in the "custom_colour" entry
then check the "use_custom_colour" entry at the bottom

> 1. menu automatically closes after an app has been launched.

already implemented....
once again in gconf-editor, uncheck the "pin_menu" entry

> 2. Return key to activates a search would be handy
i think Chanders is doing that for the next release

> 3. Cosmetically like the SLAB menu a colour border round the full window would be nice.
there is a "border_width" entry, change it and you should get a border :D

---

### Post by Coolit on 2006-09-10
Fantastic, got it all setup now, thanks for the help:KS 

Heres a little pic of it all setup :D 

[http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png]("http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png")

---

### Post by delfick on 2006-09-10
> **Coolit said:**
> Fantastic, got it all setup now, thanks for the help:KS 

Heres a little pic of it all setup :D 

[http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png]("http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png")

no probs :D

looks good :D

---

### Post by Coolit on 2006-09-10
Hi again,

I have another question, is there any way to set the font size for system managment? 

I'm able to see a setting for most of the other fonts but not system management:(

Any ideas?

---

### Post by bulldog on 2006-09-10
As far as I know,you can't.

---

### Post by Coolit on 2006-09-11
Ahh ok, thanks :-|

---

### Post by nomorewindozeforme on 2006-09-11
> **Coolit said:**
> Fantastic, got it all setup now, thanks for the help:KS 

Heres a little pic of it all setup :D 

[http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png]("http://www.coolit.pwp.blueyonder.co.uk/Linux/USP.png")

nice theme!

you mind helping out a poor n00b and telling me the hexcode of your border and the background?

thanks in advance,

---

### Post by Coolit on 2006-09-11
Border = #5f5f5e
Background = #e7e7e7

:)

I've changed themes but what I've found is the the System Management menu doesnt display correctly, is there anyway to fix this?

Here's a pic....

[http://www.coolit.pwp.blueyonder.co.uk/Linux/menuissue.png]("http://www.coolit.pwp.blueyonder.co.uk/Linux/menuissue.png")

Thanks :)

---

### Post by chanders on 2006-09-11
System Management buttons are fixed height (programming oversight). It is fixed in USP2 and should be out in a few days..

BTW, what theme is that you're using? ;-)

---

### Post by Coolit on 2006-09-11
Great thanks, looking forward to V2:)


The first pic is  Water Vapor using the black Orbulecent compiz border,

Theme
[http://www.gnome-look.org/content/show.php?content=26980]("http://www.gnome-look.org/content/show.php?content=26980")

Border
[http://www.gnome-look.org/content/show.php?content=45214]("http://www.gnome-look.org/content/show.php?content=45214")

The 2nd pic and my current theme is Carbonit, it was just released yesterday and updated this morning along with the matching Compiz window border. The quality of this theme is really high, it looks fantastic,

[http://www.gnome-look.org/content/show.php?content=45590]("http://www.gnome-look.org/content/show.php?content=45590")

Enjoy :)

---

### Post by delfick on 2006-09-12
> **chanders said:**
> should be out in a few days.

YAY!!!! 
can you give us a small taste of what to expect from the long anticipated USP2 ? please :D

---

### Post by chanders on 2006-09-12
> **delfick said:**
> YAY!!!! 
can you give us a small taste of what to expect from the long anticipated USP2 ? please :D

I really dont want to disappoint you guys, so the main addition is the USLAB plugin for the slab users.. and tonns of bugfixes and requests (sorry no theming yet delfick :P) I was going to wait and Release when USPKickoff was ready but I figured, what the hell..

I will post up a changelog soon...

---

### Post by delfick on 2006-09-12
> **chanders said:**
> I really dont want to disappoint you guys, > the main addition is the USLAB plugin for the slab users.. and tonns of bugfixes and requests

bugfixes, rquests, uslab....of curse you won't dissapoint :D

 > (sorry no theming yet delfick :P)
there will be one day :D and I'm very patient (i also believe good jobs take time....)

>  I was going to wait and Release when USPKickoff was ready but I figured, what the hell..

what is USPkickoff? that sounds fun :D

> I will post up a changelog soon...

yay!
changelogs are good :p

---

### Post by _simon_ on 2006-09-15
Please, please, please can we have the option to change text colour this time? please!!!

---

### Post by delfick on 2006-09-15
> **_simon_ said:**
> Please, please, please can we have the option to change text colour this time? please!!!

i second that :D

---

### Post by chanders on 2006-09-15
> **_simon_ said:**
> Please, please, please can we have the option to change text colour this time? please!!!

Already coded in ;-)

---

### Post by _simon_ on 2006-09-15
I love you xxxx

---

### Post by delfick on 2006-09-15
> **chanders said:**
> Already coded in ;-)

yay!

i have a question (think i've asked it before, sry if i have and you've answered :p)

is it possible to add real transparency like with the gnome-terminal?

(doesn't have to be done for this release if time consuming)

that would be cool :D

---

