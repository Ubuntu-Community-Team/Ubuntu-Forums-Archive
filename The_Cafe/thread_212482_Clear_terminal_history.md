---
title: "Clear terminal history"
date: 2006-07-09
forum: The Cafe
---

### Post by K.Mandla on 2006-07-09
How can I clear the terminal history? I don't mean the screen; I want to clear the history of commands entered into the terminal. :confused:

---

### Post by aysiu on 2006-07-09
That history's kept somewhere...?

---

### Post by K.Mandla on 2006-07-09
Don't know. I figured it must be. Am I asking this the right way? When I press the up arrow key inside a terminal, I get the last command I entered. I want to clear that history. Does that make sense, or have I muddled things further?

---

### Post by lucia_engel on 2006-07-09
I'm not sure if there's a command to clear the history, but I know they're stored in ~/.bash_history so I guess what I'd do is open the file up and manually delete the entries.

```
sudo gedit ~/.bash_history
```

Anyone knows a better way?

---

### Post by aysiu on 2006-07-09
Whoa! Cool! I didn't know you could do that. Thanks. I'll try to look into solving your problem, though.

---

### Post by K.Mandla on 2006-07-10
Excellent. That'll work for now. Thanks.

(Sorry if it was a bewildering question. I'm selling a laptop with Xubuntu installed and I didn't want my installation commands left in the history. Cheers!)

---

### Post by aysiu on 2006-07-10
This might help:
[http://66.102.7.104/search?q=cache:Et9R5vVytI8J:beau.org/pipermail/whitebox-users/2005-January/005190.html+erase+terminal+history+bash_history&hl=en&gl=us&ct=clnk&cd=1&lr=lang_en](http://66.102.7.104/search?q=cache:Et9R5vVytI8J:beau.org/pipermail/whitebox-users/2005-January/005190.html+erase+terminal+history+bash_history&hl=en&gl=us&ct=clnk&cd=1&lr=lang_en)

---

### Post by K.Mandla on 2006-07-10
Hey, now that's slick. Kill the terminal entries on logout. I like that.

---

### Post by lucia_engel on 2006-07-10
ooo turns out it's more simple than that...
```
history -c
```

EDIT: weird...the content of .bash_history didn't get deleted though

EDIT again: nvm, I just had to refresh

---

### Post by desimo on 2006-07-22
Thanks, lucia

Works like a charm for me.  I have a habit of typing using sudo when I'm not looking at the screen and entering my password as a command...  A quick fix - much better than editing the ~/.bash_history file...

---

### Post by aysiu on 2006-07-22
[http://ubuntuguide.org/wiki/Dapper#How_to_disable_history_listing_in_Console_mode](http://ubuntuguide.org/wiki/Dapper#How_to_disable_history_listing_in_Console_mode)

---

### Post by darkziggy on 2009-10-22
go to places home folder press ctrl+H find  (.bash_history)  double click on it select all and hit backspace to clear and save it and that will clear your terminal history

---

### Post by FuturePilot on 2009-10-22
> **darkziggy said:**
> go to places home folder press ctrl+H find  (.bash_history)  double click on it select all and hit backspace to clear and save it and that will clear your terminal history

This thread is over 3 years old.....

---

### Post by Regenweald on 2009-10-22
> **FuturePilot said:**
> This thread is over 3 years old.....

Waz kind of wondering why K.Mandla would not know that :) did not check the dates. Since then bleachbit now also has a feature to clear bash history. how far we've come :P

---

### Post by Warpnow on 2009-10-22
I still think this thread is neat and every bit relevent.

Never understood why threads get closed simply because they're old.

---

### Post by cariboo on 2009-10-22
Even though a thread is closed, you can still read it. The reason for closing old threads, is that information can become out of date, or there is a newer better way of doing things.

BTW, this thread is closed.

---

### Post by schauerlich on 2009-10-22
Awww, this thread is from back when K.Mandla and aysiu were but little n00blets. Look how they've grown. :)

---

