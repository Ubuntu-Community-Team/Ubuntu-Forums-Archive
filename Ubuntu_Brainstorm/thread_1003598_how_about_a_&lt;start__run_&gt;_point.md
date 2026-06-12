---
title: "how about a &lt;start | run &gt; point?"
date: 2008-12-06
forum: Ubuntu Brainstorm
---

### Post by theDaveTheRave on 2008-12-06
Hi all,

here on the ubuntu forums we are dedicated linux users, learner, or simple wannabes

However, there now exists a large group of new linux users who don't realise that they are using linux. I'm thinking of users of the newest ultra portable netbooks, that run a stripped down Linux OS (I'm thinking of the EeePC and acer1 type machines).

I've been contemplating getting one of these, and have been reading a few forums and wiki's etc that are out there for ubuntu on these types of device.

Well the advice out there is obviously targeted at newbie users, and tries not to use too much in the way of <open a terminal and type in this command> type advice, which I think is great.

But this lead me to think about a potential solution.

On windows (yes sorry I know :rolleyes:) there is a little thing in the <start> bar that says <run> where you can type in a command.

Could it be an idea to have such a thing on the next release of ubuntu, so as advice can be given to a new user along the lines of...
> 
copy this line of code
```

lsusb

```
and paste it into the <run> bar that is in the <applications|system tools> of the menu bar, and then copy and paste the contents of the output window here and we can tell you where you need to look for help.


so our new user can get the full power of the command line, and still not have to worry too much about the scaryness of...
> 
open a terminal and type in the following......

which seems to scare a lot of people?

In fact maybe even put a "print" function on the window so as us techies can tell friends to do the same thing and have it in printed format?

Just a thought? what do you think??

David.

---

### Post by smartboyathome on 2008-12-06
There already is. Alt+F2. :)

---

### Post by theDaveTheRave on 2008-12-07
> **smartboyathome said:**
> There already is. Alt+F2. :)


Hmm interesting, first I've heard of it?

I just tried it... and it doesn't work for me?

I tried running the <alt F3> whilst a terminal had TOP going, and nothing ran through it!?

am I doing something wrong?

Dave

---

### Post by Chris Watts on 2008-12-07
Alt F2   not  Alt F3

---

### Post by smartboyathome on 2008-12-07
You also must be in GNOME/XFCE (I don't think KDE has the same key combo last I tried it) for it to work.

---

### Post by theDaveTheRave on 2008-12-09
Alt-F3 or alt-F2

neither worked for me?

If however it is an available shorcut then it should be even easier to add it to the menu somewhere.

[quote]
smartboyathome  	
Re: how about a <start | run > point?
You also must be in GNOME/XFCE (I don't think KDE has the same key combo last I tried it) for it to work.
[\quote]

Not really very helpfull for a newbie, but if it was in the menu I assume it could allways be set to be in the same place under system tools

But if one

David

---

### Post by smartboyathome on 2008-12-09
It can't be added to the menu. Its part of the panel itself. The key binding is built into the panel. Only way is to use the run program applet.

---

### Post by theDaveTheRave on 2008-12-10
Hm OK,

So now I'm getting a little further.

Why not add this applet to the menu bar by default.
then it is just a matter of changing the name, making the terminal the default, and leaving the terminal open until it is closed manually by the user.

---

### Post by smartboyathome on 2008-12-10
> **theDaveTheRave said:**
> Hm OK,

So now I'm getting a little further.

Why not add this applet to the menu bar by default.
then it is just a matter of changing the name, making the terminal the default, and leaving the terminal open until it is closed manually by the user.

I actually don't know why Run Command isn't in the menu by default. That you would have to talk to the GNOME devs on.

---

### Post by k_aneda on 2008-12-14
> **smartboyathome said:**
> I actually don't know why Run Command isn't in the menu by default. That you would have to talk to the GNOME devs on.

I understand the OT's comment on how daunting it may be seeing the UNIX terminal for the first time, just as many Windows users are sometimes daunted by the Command Prompt...

However, I was a bit surprised when I saw this in the Brainstorm pages, see the top comments @  [Idea #10748: Bring back the "Run application" menu item in Gnome...]("http://brainstorm.ubuntu.com/idea/10748/")

---

### Post by theDaveTheRave on 2008-12-15
Hello again all...

Well I must say thanks to K_aneda for that link, I hadn't done an extensive search on this issue, but the quick search I did do didn't throw up that page.

I does seem that the dev at Gnome shot themselves in the foot a bit with this one... but then maybe they are more concerned on system security that other devs on other teams? That could be a justification for the removal to a "secret shortcut".

David

---

