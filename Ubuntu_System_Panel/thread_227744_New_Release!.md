---
title: "New Release!"
date: 2006-08-02
forum: Ubuntu System Panel
---

### Post by chanders on 2006-08-02
New releases ONLY will be posted in this thread. Do not post in this thread _please_

Ver 0.31
Wed,  02 Aug 2006 05:30:10 -0400
   * 'Places' and 'Application' icon size configurable (size 1-4)
   * USP returns to 'Favourites' after close if show_allapps_on start is not set
   * 'All Application' sub-section is now highlighted
   * Applet text and icon is now configurable
   * Fixed 'Filter' bug
   * Fixed Alt-F4 bug
   * BASIC translation for 'All Applications' section (thanks vonpmg)

Other features are already in the pipeline...stay tuned

---

### Post by _simon_ on 2006-08-02
Bit dissapointed to see there is no option to change the text colour yet :(

Still loving USP though!

Can someone scrap my bug report... I did not see mention that apps_icon_size was between 1-4 until just now.

---

### Post by vonpmg on 2006-08-02
Argg. I am late by only a few minutes. :( 
I was going to send you now the translations i have been doing.
You now can have all the app translated.
I am spanish so the spanish translation is up.
I am going to download version 0.31 and send you the diff agains it.

---

### Post by _profox on 2006-08-02
> **vonpmg said:**
> Argg. I am late by only a few minutes. :( 
I was going to send you now the translations i have been doing.
You now can have all the app translated.
I am spanish so the spanish translation is up.
I am going to download version 0.31 and send you the diff agains it.

You can send them to me or chanders or post them just between [ code ] [ /code ] tags :)

Then we can review the code and include it if it's good!
Thanks for your hard work.

I will work on a Dutch translation then (I'm Dutch myself).

I will also work on a specification for 'full theming support' (we are almost there anyway, because most things are configurable) and I've got some nasty bugs to (try to) solve ;) Oh, and I'm going to write a specification to optimize the application in a few steps, because there is alot we can improve about the speed (we have some messy/redundant code in some parts of the program :))

Let's make the next release a killer release :) we are improving fast.

---

### Post by _simon_ on 2006-08-02
Do you have a list anywhere of things planned for each release?

---

### Post by _profox on 2006-08-02
Small things are in bugs as "wishlist" most of the time, and we may or may not add it... big changes will get defined on launchpad in the "specifications" part. There's not much currently, but you can already check it out if you want

---

### Post by delfick on 2006-08-02
> **chanders said:**
> New releases ONLY will be posted in this thread. Do not post in this thread _please_

hmmmm, that is the first line of this thread.......

---

### Post by _profox on 2006-08-02
Yea, we suck :P
I think we better rename this topic and start another "New release" topic :P
We're all to blame
(and make the new New release topic sticky)

---

### Post by delfick on 2006-08-02
> **_profox said:**
> Yea, we suck :P

i see it more of...ur all so excited to get updates for this menu (me included :p) that u get tunnel vision on "New Release" and don't see anything else.....

(if that doesn't make sense, then u do suk :p :D)

....:D

---

### Post by lazyd2 on 2006-08-02
> **_profox said:**
> Yea, we suck :P
I think we better rename this topic and start another "New release" topic :P
We're all to blame
(and make the new New release topic sticky)
Do that so I can put it in my sig ;)

---

### Post by _profox on 2006-08-02
Something else you can do, chanders:
make this topic sticky
just post the new releases in your first post, above the previous release :)

---

### Post by _profox on 2006-08-02
This is about the applet text/icon change/hide:

I reopened this bug/wish, because my patch isn't applied correctly in 0.31. To change the text or icon, or to hide the icon, you have to restart the applet. This shouldn't happen. It should change instantaneously (did I spell that right?)

Chanders, I think you forgot the "self.client.notify_add" for my patch ;) I think you should hurry up with the svn, because this is getting messy imo (manual patching)

Are you going to release a 0.31.1 or just wait and correct this in 0.32 ?

---

### Post by chanders on 2006-08-02
Yu guys need to read ;)

@profox - check your pm

---

### Post by chanders on 2006-08-02
Stupid %^@#$^ double post ](*,)

---

