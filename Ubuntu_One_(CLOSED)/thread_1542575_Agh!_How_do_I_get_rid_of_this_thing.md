---
title: "Agh! How do I get rid of this thing?"
date: 2010-07-30
forum: Ubuntu One (CLOSED)
---

### Post by louis_mallow on 2010-07-30
I want to remove U1. All of it. From context menus in nautilus, the syncdaemon, the client. Every trace. How do I do it? It's either that or remove Ubuntu and go up/downstream. Can I just use Synaptic to remove the packages without harm?

It's killing me. People here have been kind with workarounds but I cannot make it stop. It's killing my machine every few hours until I kill the syncdaemon. What follows is for context only - I don't want to fix it, I want it gone, gone, gone!

I've tried the client - nothing is checked, no machine is linked, no services are supposed to be active. I've tried going to the couple of folders still syncing in Nautilus and 'stop syncing on U1...'. It doesn't work then and next startup I still have

> ~$ u1sdtool --list-folders
Folder list:
  id=af46ad5f-889c-484f-a622-e41256361366 subscribed=True path=/home/michael/Pictures
  id=cbc7f7d1-6ef7-49d8-96b2-384d31251ef0 subscribed=True path=/home/michael/.ubuntuone/Purchased from Ubuntu One
  id=03179148-e225-4b04-8a49-064a857dd609 subscribed=True path=/home/michael/Documentsand also
> ~$ u1sdtool --status
State: LOCAL_RESCAN
    connection: Not User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTHand my upward bandwidth crushed (why?! where's it managing to send anything?!)

---

### Post by Sub101 on 2010-07-30
If you go to synaptic and remove ubuntuone-client then your problem should be sorted?

or try;

```
sudo apt-get remove ubuntuone-client
```

---

### Post by louis_mallow on 2010-07-30
> **Sub101 said:**
> If you go to synaptic and remove ubuntuone-client then your problem should be sorted?


Sounds good - I just don't know enough to know if it would break anything. Also, I fear that would leave syncdaemon. Can that be pulled too?

Right - I'm going into Synaptic and removing everything that starts with 'ubuntuone'. I'm considering another OS, so it can't hurt all that much if I break anything... Wish me luck.

---

### Post by louis_mallow on 2010-07-30
It worked. My system restarted. My disc is not grinding, my bandwidth is my own.
I love my OS again.

---

