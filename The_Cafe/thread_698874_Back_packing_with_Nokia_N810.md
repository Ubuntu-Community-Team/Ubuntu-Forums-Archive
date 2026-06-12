---
title: "Back packing with Nokia N810"
date: 2008-02-16
forum: The Cafe
---

### Post by kiplingw on 2008-02-16
So I would like to do some traveling and reasoned the Nokia N810 is the way to go after doing some extensive research. I would now like some more advice from the gracious forum community.

Throughout my travels, I will most likely want to record dates and times, new contacts, and communicate via email. But there is always the potential risk that my N810 might get lost / broken / stolen / etc.. If that were to happen, it would be tragic to lose any of the various forms of data I may have gathered throughout my travels.

Email has a simple solution, IMAP. Everything is automatically synchronized and get on my mail server.

Contacts and calendar are the next issue. I've been using Evolution for a long time on my laptop and desktops. I don't mind moving to another PIM that is available and well maintained in one of the many Maemo apt repositories available, but I would like to use something that also has a server based backend like IMAP, but still accessible locally when offline. Any recommendations?

Kip

---

### Post by kiplingw on 2008-02-16
So the word on the street that I've heard a couple times now is Evolution Data Server is the way to go contacts and calendar. Finding documentaiton on EDS, other than developer APIs, is almost impossible. 

Is it even possible to separate the client / server to actually separate machines?

Kip

---

### Post by tgalati4 on 2008-02-17
Buy a bunch of cheap memory sticks and write a script to back up your device each night.  This way if you lose the device, you will have several backups on memory sticks that you can use to transfer when you get back home.

---

### Post by kiplingw on 2008-02-17
I kind of like the idea of synchronization a bit better, since it handles sync'ing specifically and I might end up using the data from more than one place. Thanks though.

Kip

---

### Post by Spitphire on 2008-02-17
Can you create an ssh session with the nokia n810?

---

### Post by kiplingw on 2008-02-17
Yes.

Kip

---

### Post by Spitphire on 2008-02-18
Well, if you can create an ssh session i would suggest using something like rsync with your home system...

```

rsync -a /nokia/path homecomputername:/path/to/syncto

```

The above would just sync nokia files that have change with your remote home computer.

It would be very easy to backup your entire nokia in this manner, and then when you ran the above command it would only send (securely of course) the files that have changed... 

I know it's not an ideal solution for what you actually want, but it may suffice...

---

### Post by kiplingw on 2008-02-18
That is definitely a good idea and I will try that as well. I just hope dreamhost lets me run an rsync daemon that I can backup TO and not just from.

Kip

---

### Post by Spitphire on 2008-02-18
Glad to help

maybe look into rsync.net

I've never used their services, so i couldnt give you any advice. But I've heard of people using it with no complaints.

---

### Post by jpeddicord on 2008-02-18
DreamHost does provide an rsync daemon, but their official policy is that any data you store on their servers must in some way be related to a website. So be careful with that. ;)

---

### Post by kiplingw on 2008-02-18
Really? That's terrible news for me, really terrible. If I understand that correctly, it means that I can't even backup my hard drive to the server. I can't understand why they'd even care really.

Kip

---

### Post by savantelite on 2008-05-30
I was excited for this thread when I read the title. I imagined all the cool things you were able to do with the GPS mapping and photo tagging. 

Then all I read was crying about syncing your contacts?

Come on, does google earth work on this thing? is there an easy way to update to flickr when you do get to an internet conection? 

I guess that is a syncing issue.

---

### Post by kiplingw on 2008-05-30
If you can't sync, then you might as well be ready to kiss everything that you've accumulated throughout your journey good bye (e.g. photos, movies, contacts, etc.) in case you ever lose it.

Kip

---

