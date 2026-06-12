---
title: "Root account"
date: 2007-03-06
forum: The Cafe
---

### Post by anaconda on 2007-03-06
I just noticed that "community docs" has been edited and now the RootSudo page hasn't got instructions about enabling root account anymore !!!!!  

instead it just says "This is not recommended!"

Shocking.. I DO agree that using sudo is a good idea, but and a big but at that I also think that root account has it's uses.

eg. in a machine that has multiple users and the administrator only maintains the machine  (doesnt use it..) think of a classfull of computers..

And if you are coming from some other distro, which has a root account.. why couldn't you still use it? propably not a newbie anymore..  and why would we want to turn away those experienced linux users..?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
at the bottom of the page under
"Going back to a traditional root account"

I have also noticed that root account hasn't been tested as well as regular ubuntu.. maybe it isn't used quite as much.. there are still some bugs..

But I think the instructions should be put back to the RootSudo page. Yes keep the "not racommended" text but also the howto..

opinions anyone?

---

### Post by TheWizzard on 2007-03-06
i disagree. 
if you should be allowed to login as root, you'll easily enable root login. 
people who do not know how to enable root, should certainly not use it. 

if you used another disrto before, the information on the ubuntu website is sufficient.

---

### Post by K.Mandla on 2007-03-06
> **anaconda said:**
> opinions anyone?
Well, it's a wiki, so if you disagree with what's there, you could conceivably correct or expand on the topic. Is that not an option for you?

---

### Post by true_friend on 2007-03-06
google can help in this regard there are other links available to enable root sudo in ubuntu.
i also use root account frequently  i have saved that old page i prefer root GUI session for upgrading my system.

---

### Post by ljpm on 2007-03-06
> **TheWizzard said:**
> i disagree. 
if you should be allowed to login as root, you'll easily enable root login. 
people who do not know how to enable root, should certainly not use it. 

if you used another disrto before, the information on the ubuntu website is sufficient.

I agree, after all, look how successful Mac and Windows have been telling us what we can and can't do.   ( Sarcasm )

I like the fact that I can totally screw up my system. It helps me learn as well as enabling me to customize my computer any way I want to.

---

### Post by anaconda on 2007-03-07
> **K.Mandla said:**
> Well, it's a wiki, so if you disagree with what's there, you could conceivably correct or expand on the topic. Is that not an option for you?

heh.. good point. Somehow I didn't realize this. Feeling quite stupid now. :confused: 

but should I do it or not? That is the question.

As I said I think sudo is a good thing, but the idea behind linux is that you can change/modify almost anything to your liking..

---

### Post by anaconda on 2007-03-07
Good points from all. 

Instructions for enabling root is quite easy to find and not really a problem to me, because I know how to do it. 

I was just suprised that the info was removed from the RootSudo page..  Now that I (finally) understand it is wiki and anyone can edit the page I also understand that it wasn't an "offical" decision.. someone just removed it..

And having seen the replies to threads asking "how to enable root?" Which are mainly: "Dont enable it use sudo instead.." and finally someone gives the link to RootSudo -page, which had instructions how to enable it.. I now also understand why someone thought best to remove it.

But should the info be there or not? Is it supposed to be hard to find and for advanced users only?

---

### Post by Mateo on 2007-03-07
I think all information should be easy to find.  I think the info should be there, provided there are warnings to the potential dangers.

---

### Post by beercz on 2007-03-07
> **TheWizzard said:**
> i disagree. 
if you should be allowed to login as root, you'll easily enable root login. 
people who do not know how to enable root, should certainly not use it. 

if you used another disrto before, the information on the ubuntu website is sufficient.
Indeed!

---

### Post by bapoumba on 2007-03-07
Hello :)
When there is an issue with the documentation pages, best thing to do is to raise it in the [ubuntu-doc mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-doc") or in #ubuntu-doc IRC channel on irc.freenode.net.
[https://wiki.ubuntu.com/DocumentationTeam]("https://wiki.ubuntu.com/DocumentationTeam")

---

### Post by CrypticBlade on 2007-03-07
Why would you want to enable the root account? So you can login directly to Gnome?

I can understand not wanting to type sudo 100+ times for system administration, but enabling root for direct login makes no sense from my perspective.

If typing sudo for several commands drives you nuts, then try the following.

Simply type at a command line:
```
sudo -i
```

It will prompt for password, and viola, you are now logged into a root shell and can issue as many commands under root as you like.

When you arre finished as root, type:
```
exit
```

and you will be returned to your normal user shell.

Cheers,
CB

---

### Post by TheWizzard on 2007-03-07
> **ljpm said:**
> I agree, after all, look how successful Mac and Windows have been telling us what we can and can't do.   ( Sarcasm )

I like the fact that I can totally screw up my system. It helps me learn as well as enabling me to customize my computer any way I want to.



you are free to screw up your system the way you want. nevertheless, the ubuntu wiki's should aim to educate the users. and by explaining the benefits of sudo and by NOT dirctly telling people how to enable root login, they do.

---

