---
title: "Ubuntu one - Contacts sync to evolution"
date: 2010-07-20
forum: Ubuntu One (CLOSED)
---

### Post by Red62 on 2010-07-20
Hi... I was happily using ubuntu one on 9.10... as soon as I upgraded to 10.04 the contact sync stopped... I know the contact syn was switched off initially... but has it not been turned back on yet?
 
My contacts from ubuntu one are still not syncing over.... any ideas?
 
Cheers

---

### Post by Excedio on 2010-07-20
Do you have a paid U1 account or a free account? The free account only gets contact sync free for 30 days.

---

### Post by Red62 on 2010-07-20
I have the free acount.  I thought the 30 day trial sync was to mobile devices.  I believe the sync to evolution contacts on the desktop is unlimited.
 
I'm sure somebody will correct me if I'm wrong!

---

### Post by hartl_vienna on 2010-07-20
It's still disabled for the most users!

See here:
[https://wiki.ubuntu.com/UbuntuOne/Status]("https://wiki.ubuntu.com/UbuntuOne/Status")

---

### Post by Excedio on 2010-07-21
```
 
sudo apt-get update && sudo apt-get upgrade

```
 
Three new Ubuntu One packages today. Upgrade and then test again.

---

### Post by hartl_vienna on 2010-07-21
There are no new Ubuntu One packages to upgrade so far.

---

### Post by Excedio on 2010-07-21
That's odd. I upgraded:
 
python-ubuntuone-client
ubuntuone-client
ubuntuone-client-gnome

---

### Post by hartl_vienna on 2010-07-21
This is strange. Which package version do you have after the update?


Ubuntuone-client       1.2.2-0ubuntu2
ubuntuone-client-gnome 1.2.2-0ubuntu2

---

### Post by Excedio on 2010-07-21
> **hartl_vienna said:**
> This is strange. Which package version do you have after the update?
 
 
Ubuntuone-client 1.2.2-0ubuntu2
ubuntuone-client-gnome 1.2.2-0ubuntu2
 
python-ubuntuone-client [B]1.2.2-0ubuntu2
[/B]ubuntuone-client **1.2.2-0ubuntu2**
ubuntuone-client-gnome **1.2.2-0ubuntu2**

---

### Post by Red62 on 2010-07-21
Yeah I did get some updates today.. but still no joy.. in fact when I now select my "ubuntu one" address book, I get a "Error loading address book" - permission denied.

Any ideas anybody?  April to almost August for this feature to be down in not great.

---

### Post by hartl_vienna on 2010-07-22
@Red62: 

> It's still disabled for the most users!

See here:
[https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

The file and the notes sync work quite good since a few days and it's very fast. It's almost as fast as Dropbox. 
Now I try to switch from Dropbox to U1 and if it's working as good as i suppose then I take the 50GB account.

\\:D/
[I]
PS: I try to improve my English skills. If my sentences are wrong, please send me a PM! (Yes, I'm serios. It's very important for me.) :-)[/I]

---

### Post by scottiw2000 on 2010-08-10
Is there any progress on the contacts sync service? I still have no luck with it and the status page still says there is a "service outage." This is terrible if an advertised service has been out this long!!! And there's nothing about an outage on the Ubuntu One pages.

---

### Post by LaptopU on 2010-08-11
Ubuntu One contacts and bookmarks problem reminds me of the old British Rail service in the UK before it was privatised.  Admittedly it is not much better or worse these days than it is, but BR used to be great for apologising.

Sorry it's the wrong type of snow on the tracks, sorry there are too many leaves on the line, sorry the heat has warped the tracks, sorry there are delays.

Very good at saying sorry, not much good at taking action.  I propose the phrase 'we have the wrong type of servers' to now be synonymous with Ubuntu One.  Months on, this is not good at all and the service is becoming a joke.

---

