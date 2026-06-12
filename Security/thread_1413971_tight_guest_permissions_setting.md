---
title: "tight guest permissions setting"
date: 2010-02-23
forum: Security
---

### Post by tpo_tudor on 2010-02-23
hi
one thing i can't seem to be able to do is give the guest account just these permissions: using firefox (or other browser) and using one file directory and using a text editor. means the guest can browse the net and sefe some infos form that - nothing more.
the previous version had something like that, it was really easy for me, a noob, to do it with two or three clicks.
if this possibiility exists, please tell me what to do. if it's not implemented... maybe it should be. 'cause many people let others use the computer but don't want any complications... :D

---

### Post by bodhi.zazen on 2010-02-23
I use apparmor to confine the guest account. If you want to take it for a spin Download Zenix:

[http://zenix-os.net/](http://zenix-os.net/)

The apparmor profile is here (jailbash) :

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

You can of course restrict the guest account further if you wish (by further modifying the jailbash profile).

---

### Post by tpo_tudor on 2010-02-24
:) thank you :KS

---

### Post by bodhi.zazen on 2010-02-24
you are most welcome, glad it worked out for you.

---

### Post by tpo_tudor on 2010-02-26
:P actually, being a noob, it worked for me information wise.
from what i read (including your detailed apparmmor presentation [here]("http://ubuntuforums.org/showthread.php?t=1008906") , i understand this application limits the usage of applications, regardless the user, right? :shock:
what i'm looking for (again: as a noob) is some security app allowing me to take a specific user's rights straight down to using two or three apps and one location. this, without affecting the other user's rights. :idea:

i must confess this is what scares new users the most: the need to learn console commands, to understand how the OS works and the language used there. i'd need to learn those commands (like sudo) and the concepts behind installing things over the internet and all. ](*,)

this probably sounds absurd to the savvy linux users, but what we, the newcomers need, is something like a clear graphic interface (not fancy, just easy to use) saying "if you click here, the user X will be able to run Y aplication. if not - well, he won't". i guess my example is quite clear: "*guest one* can browse the internet with firefox, can use some text editor and can print. also, the only volume he can use (mount) is the *guest folder*". end of story.\\:D/

don't laugh: i didn't know where to find the apparmor icon, to start the app, so installing/editing a profile prety much went blank to me, like those ancient maps: "hic sunt dragones" :lolflag:

---

### Post by tpo_tudor on 2010-02-26
i opened a guest session, i saw i couldn't mount the preset computer browser volumes, but i created a new folder with a test text document, then i took the browser window back all the way to the system files and all - so the initial limitation of volume mounting doesn't help me a lot...
note: the guest account has all the priviledge options unchecked, so the guest shouldn't be able to do anything. stil... :D

---

### Post by bodhi.zazen on 2010-02-26
Linux does not really use per user / per application restrictions in this way, and certainly not with a graphical interface.

apparmor is probably as close as it gets, but you would almost need to go through the system binary - by - binary .

IMO this kind of restriction is not really necessary, and honestly it does not really work all that well in Windows either in that it is easy to circumvent.

If something such as jailbash is not restrictive enough do not offer your box to friends and family (keep in mind Physical Access is essentially root access).

---

