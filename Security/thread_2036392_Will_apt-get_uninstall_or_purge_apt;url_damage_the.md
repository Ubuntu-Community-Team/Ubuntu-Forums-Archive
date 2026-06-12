---
title: "Will apt-get uninstall or purge apt;url damage the system?"
date: 2012-08-01
forum: Security
---

### Post by houseworkshy on 2012-08-01
I've never been a fan of apt;urls, many people have had many of conversations about the security side of them;  social engineering, sudo default timer, hidden apt;urls etc etc.   So seeing that it is a command can I just remove it without damageing the rest of the system?   If so what is the best method of doing so?

---

### Post by Ms. Daisy on 2012-08-01
apturl uses the apt protocol, but it is a separate program.

[https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)

You can also open a terminal and type in 
```
man apturl
```and that will tell you more about it.

But you should be able to remove it using 
```
sudo apt-get remove apturl*
```That won't affect the apt package itself.

---

### Post by houseworkshy on 2012-08-02
Thanks for that.  It was findng it in the man paages which gave me the idea it was a command though in the version I'm using, 10.04, the man page says it hads't been completed yet.  Thanks for the link too.  I was afraid that purge might take too much out.  I'll remove it when I'm back on the other drive, on this one (mepris) the apt;url man page hasn't even been started,  it says :)

---

### Post by Ms. Daisy on 2012-08-02
> **houseworkshy said:**
> Thanks for that. It was findng it in the man paages which gave me the idea it was a command though in the version I'm using, 10.04, the man page says it hads't been completed yet. Thanks for the link too. I was afraid that purge might take too much out. I'll remove it when I'm back on the other drive, on this one (mepris) the apt;url man page hasn't even been started, it says :)That's correct- apturl is a mini-program that runs through command line in any version of Ubuntu it's installed on.
 
The man page hasn't been completed. The man page is the documentation to explain how to use apturl. But an incomplete man page doesn't mean the _apturl program_ is incomplete.  It just means no one has gotten around to documenting the progam yet.

---

### Post by houseworkshy on 2012-08-02
That's what I guessed.  The mepris man page is a bit older as it is based on the stable branch of debian. The idea of a page which tells one that it hasn't been started yet appealed to the sillyness in me. 

All I really want to do is disble apt;urls as the risk of hitting a second hidden one during the sudo time period bothers me, slight though that risk currently is.  I like to see details everytime too.  

I'm actually tempted to take the sudo timer down to 0 as my use of sudo is usually restricted to one off commands, the problem with that, I imagine, is that whilst fine for quickies, for example apt-gets of the known, it would also apply to things where thinking time searching for the unknown would be handy, for example graphic installers.  

Will probably go with the remove apt;urls option as should I need to use one putting it back is only a line away.  Perhaps some sort of switch might be handy, like apt;url -disable and apt;url -enable.  Unnessesary frill now perhaps but maybe a useful security feature in future years. 

Still reading up.  

Thanks again.

---

### Post by cariboo on 2012-08-02
You can still set the sudo time out to 0, and when you need the command for a longer time, use:

```
sudo -i
```

---

### Post by houseworkshy on 2012-08-03
Ah thankyou.  I've been a bit woolly minded recently I think; juggling too much. Working through bodhi zazens guide to apparmor ( should have done it years ago but couldn't find the time ) on the Ubuntu side and Firefox is temporarily out of commission atm so posting from the other side.  That's not a problem by the way, put a copy of the guide some profiles and other bits there to work through.  Not the guides fault incidentially, just me ferriting around seeing what does what.  Will probably do a clean install of the browser anyway so I can see what differance add-ons make installed one at a time.  Trying to understand rather than just copy.  Will ask if I get stuck and can't find the answer elsewhere or already posted.  Sorry total aside but may explain why I'm so slow posting back "solved" or new problems, very grateful for the advice.  I'm trying to do as much as I can with ubuntu staying offline while I fiddle.

So if I were to open a gui tool which required root powers and thinking time I'd just do if from the terminal, sudo -i, whatever the program is, use the program, close it, sudo -k in the terminal and exit.
I've been doing that sort of thing when it seems I need to, sometimes using gksu instead, with the timer as it is for system monitor, freshclam, gedit, beachbit, several of them anyway.   So if I don't mind using the terminal, and I don't, then timer to 0 looks like a very good option.  Thankyou.

---

