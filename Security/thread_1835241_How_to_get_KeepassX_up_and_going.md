---
title: "How to get KeepassX up and going"
date: 2011-08-29
forum: Security
---

### Post by Danno2468 on 2011-08-29
My little brother brought to my attention that my current password security system is bad.... a txt file with a list of user names and passwords.  I have decided to switch over to keepass.

So with this program I should be able to save my info from that text file, into keepass, and then when I open something that requires my password keepass will fill that stuff out automatically.  My problem is I can't figure out how to get the program to do that.

I think i am missing plugins or something in both firefox, and chrome.  I have tried to install them unsuccessfully.

Is there a good step by step how too out there?  Or can someone talk me through it.  

I am running 11.04 64 bit.

Please ask if I am un clear about anything, or you need any further info.  Thanks in advance.

---

### Post by Danno2468 on 2011-08-30
I think I have it all but solved.  Keepass is up and running.

Here are the 2 links i used.

[https://addons.mozilla.org/en-US/firefox/addon/passifox/reviews/](https://addons.mozilla.org/en-US/firefox/addon/passifox/reviews/)

[http://maketecheasier.com/install-keepass2-on-ubuntu-natty/2011/05/14](http://maketecheasier.com/install-keepass2-on-ubuntu-natty/2011/05/14)

Somethings I learned:
keepass 1, keepass 2 and keepassx are all very different beasts.
keepass 1 and 2 are the windows versions, they require pluggins to work with firefox

keepassx doesn't have any pluggins,  I guess you just copy paste usernames and passwords over to the web browser.

I went with keepass2 cause that was what the how too above gave me.  I still don't have full auto type, but the auto keys opens keypass, and then you can right click and the option comes up, to fill username and password. It also automatically gives me the choice to fill in a new entry if I create a new username and password I think that is pretty good. You might need xdotool to get full auto typing what ever that is.

If you would like to elaborate on what I have written, or you also have a good how too, please add a post.

---

### Post by cariboo on 2011-08-31
Why didn't you just install keepassx, it's in the repositories, no need to enable any ppas.

---

### Post by Danno2468 on 2011-08-31
That is what I initially did.  But it refuses, to communicate with firefox or chrome.

---

### Post by Larkspur on 2011-09-02
> **Danno2468 said:**
> That is what I initially did.  But it refuses, to communicate with firefox or chrome.

Have you set up the Auto-type script for your password entries?  The quickstart pages in KeepassX Handbook will give you the run-down on how they work.  Once they are set up, go to the login page for whatever you're using, click on the KeepassX window, press ctrl+v and it'll do the rest.

---

### Post by user2037 on 2012-05-13
Keepass2 is also in the Ubuntu repos now. It works quite well with Firefox and the hostname-in-titlebar add-on. There is also Pass-i-fox; though, I've yet to get that one going on Ubuntu.

---

