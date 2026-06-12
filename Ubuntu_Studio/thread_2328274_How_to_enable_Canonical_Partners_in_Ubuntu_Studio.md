---
title: "How to enable Canonical Partners in Ubuntu Studio?"
date: 2016-06-19
forum: Ubuntu Studio
---

### Post by javierdl on 2016-06-19
I want to install Skype.
I found a tutorial to do it, but in Ubuntu 16.04, not Ubuntu Studio 16.04.

Any pointers please?

JDL

---

### Post by Bucky Ball on 2016-06-19
Software and Updates> Other Software> Canonical Partners repo?

As far as I know, UStudio uses xfce4 and so do I, so that's where it is. Don't bother enabling sources repo. Update then just install Skype with Synaptics, terminal or whatever UStudio uses.

---

### Post by javierdl on 2016-06-19
Thanks so much BB :)

I used the following Terminal command to install Skype:
"[COLOR=#333333][FONT=Monaco]sudo apt update && sudo apt install skype[/FONT][/COLOR]", as advised in [this tutorial]("http://ubuntuhandbook.org/index.php/2016/04/install-skype-4-3-in-ubuntu-16-04/#comment-3536974"). But at the end of the installation attempt it says it was **unable to locate the package Skype **:(

Any ideas?

Thanks guys,

JDL

---

### Post by Bucky Ball on 2016-06-20
Do you have Synaptic? Is it in there? Try from there if so. The 'Can't locate Skype' was a problem for someone else here, but not sure if they fixed. You'll probably be able to hunt that down and have a look.

See if its in Synaptic and we'll go from there.

PS: You could also try this and see if it makes any diff.

```
sudo apt update
sudo apt full-upgrade
sudo apt install skype
```

---

### Post by vasa1 on 2016-06-20
OP still hasn't clarified whether Canonical Partners has been enabled :(

---

### Post by Bucky Ball on 2016-06-20
> **vasa1 said:**
> OP still hasn't clarified whether Canonical Partners has been enabled :(

Yea. I added they should double check in my last post but having problems with the lag monster at this end (what's new) and wrangling disappearing and reappearing posts. :|

Somehow that bit got lost in the chaos, but yes, double check Canonical Partners is enabled.

---

### Post by javierdl on 2016-06-20
Never mind.
When at the Updates & Software I had not checkmark the right item. I was in the 1st tab instead of the 2nd one (Other software).
Got it installed already.
After I enabled Canonical P I found skype in Synaptic. 
Bucky Ball says I did not need to do it. I cannot say skype was already in Synaptic before I enabled it, I just can't recall :(

---

### Post by Bucky Ball on 2016-06-20
If all is working as expected, please mark the thread as solved to help others (Thread Tools, top right). Happy Ubuntu-ing and Skype-ing. ;)

---

