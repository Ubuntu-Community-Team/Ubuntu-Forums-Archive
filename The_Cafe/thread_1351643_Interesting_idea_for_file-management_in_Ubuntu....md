---
title: "Interesting idea for file-management in Ubuntu..."
date: 2009-12-10
forum: The Cafe
---

### Post by AICollector on 2009-12-10
Hey all; I've just had a rather interesting idea :D

Currently, I'm in a bit of a pickle; as a student in IT, I more or less need to work on documents at home, on the move, at the College computers...transferring them between USB sticks all the while.

Now, wouldnt it be lovely to have a system that could update every file so they are all up to date? (IE: If I had a document called "Example.odt", I worked on this at my home computer, put it on a USB stick, transferred it to my netbook, worked on it a bit more (where whatever magic automatically saves the new file, plus the old one, to the USB stick) and then the same magic happens when I plug it back into the home computer again)


That would make my life SO MUCH EASIER!

What do you think?

---

### Post by Tibuda on 2009-12-11
[http://dropbox.com](http://dropbox.com)
[http://ubuntuone.com](http://ubuntuone.com)

---

### Post by Psumi on 2009-12-11
> **danielrmt said:**
> [http://dropbox.com](http://dropbox.com)
[http://ubuntuone.com](http://ubuntuone.com)

And if 2 GB is not enough, but cannot pay for it?

---

### Post by Berk on 2009-12-11
Or if you don't always have access to the internet when you need to work on these files?
I have similar issues at the moment, my new plan is to simply save everything directly to my USB stick then transfer it from the USB stick to whichever computer I'm working on, for backup more than anything else.

---

### Post by Tibuda on 2009-12-11
> **Berk said:**
> Or if you don't always have access to the internet when you need to work on these files?
I have similar issues at the moment, my new plan is to simply save everything directly to my USB stick then transfer it from the USB stick to whichever computer I'm working on, for backup more than anything else.

Both Ubuntu One and Dropbox store your files in your harddisk. It only syncs them with the Internet.

---

### Post by Berk on 2009-12-11
So i work on my laptop, save the file there on Ubuntu One.
I need that file at college on my netbook, no internet available.. I can't sync. 
Saving to the USB as the master copy is much easier for me.

---

### Post by Psumi on 2009-12-11
> **danielrmt said:**
> Both Ubuntu One and Dropbox store your files in your harddisk. It only syncs them with the Internet.

And if you have three different versions of the file?

1. On one computer
2. on USB Drive
3. on another computer

all with different changes, similar time of modification, and all of them having edits you want to keep?

---

### Post by Tibuda on 2009-12-11
> **Psumi said:**
> And if you have three different versions of the file?

1. On one computer
2. on USB Drive
3. on another computer

all with different changes, similar time of modification, and all of them having edits you want to keep?

The latest version keeps with the filename, but Dropbox saves the other file versions with a suffix. It is not smart enough to merge the files. I don't know about Ubuntu One.

> **Berk said:**
> So i work on my laptop, save the file there on Ubuntu One.
I need that file at college on my netbook, no internet available.. I can't sync. 
Saving to the USB as the master copy is much easier for me.

Even in your case Dropbox/UbuntuOne are good, because you can work while offline, and when you got a connection it will sync for you.

You don't have to stop using USB drives to use Dropbox or Ubuntu One. I use  [grsync]("apt:grsync") to sync my files with my drive. It is a friendly frontend for the powerful commandline rsync.

---

### Post by sdowney717 on 2009-12-11
google docs also does this

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAsQFjAA&url=http%3A%2F%2Fdocs.google.com%2F&ei=GzEiS_jMJpCwlAf51v2ECg&usg=AFQjCNHj75Au5kt8svXmuNkhBD_DjnPhNQ&sig2=BUeuTgcIGv8KlaSDhowh7A](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAsQFjAA&url=http%3A%2F%2Fdocs.google.com%2F&ei=GzEiS_jMJpCwlAf51v2ECg&usg=AFQjCNHj75Au5kt8svXmuNkhBD_DjnPhNQ&sig2=BUeuTgcIGv8KlaSDhowh7A)

---

### Post by forrestcupp on 2009-12-11
In your case, I actually do think that using one shared internet storage is your best option.  If your project is important enough that you need to work on it "on the move" where there is no internet access, then you need to get some kind of wireless internet service.

Although it does seem like there should be some kind of USB key syncing software out there.  It would have to be a manual thing, though.  If it were completely automatic every time you plug your device in, that could cause a lot of trouble if you were wanting to revert back to one of the older versions.

---

### Post by Tibuda on 2009-12-11
> **forrestcupp said:**
> In your case, I actually do think that using one shared internet storage is your best option.  If your project is important enough that you need to work on it "on the move" where there is no internet access, then you need to get some kind of wireless internet service.

Although it does seem like there should be some kind of USB key syncing software out there.  It would have to be a manual thing, though.  If it were completely automatic every time you plug your device in, that could cause a lot of trouble if you were wanting to revert back to one of the older versions.

As I said, you can still work on Dropbox/UbuntuOne files when you are offline. No need of "wireless internet service". You only have to remember that the changes you make will only be synced when you connect again.

---

### Post by forrestcupp on 2009-12-11
> **danielrmt said:**
> As I said, you can still work on Dropbox/UbuntuOne files when you are offline. No need of "wireless internet service". You only have to remember that the changes you make will only be synced when you connect again.

Hmm.  Nice.  But there's still the 2GB free limit to deal with.

I was talking about some of the other free online storage options that offer way more than 2GB.  You don't have all the features, but you can have a lot more space if you need it.  In that case, you would need wireless service for when you're on the go.

But a lot of people probably don't need more than 2GB, in which case Ubuntu One would be a good option.

---

### Post by cosine352 on 2009-12-11
why not just keep the files in the external drive and work on them directly from the that external drive. just do a backup every now and then to be safe. these days you can buy up to 8 GB of pen drives for around $20. Even there is pen drive of 32 GB.

---

### Post by AICollector on 2009-12-11
Well, not really;

Let me explain a bit more, now that I've got time to work on the idea;

It came about because very soon I'll be looking at a very slow Internet connection (I'm moving into a new place) and rather then use those systems, I'd rather have a system that not only worked offline, but also saved previous versions (and make them searchable) I don't know if something like GNOME 3.0 would provide that functionality.

With Dropbox, Ubuntu One, etc; I'd need to still have some vauge idea of which file is where, is the old one on Ubuntu One, or is it on my computer?

I'd rather just have the one file which was updated (which could THEN be put on those services)


Think of it as sort of akin to what the KOffice developers were doing with NEPOMUK; making it so the user never really needed to memorise the file directory, the program could just save it anywhere and be as easily acessible to the user (if not more) then the current methods.

---

### Post by Tibuda on 2009-12-11
> **AICollector said:**
> Well, not really;

Let me explain a bit more, now that I've got time to work on the idea;

It came about because very soon I'll be looking at a very slow Internet connection (I'm moving into a new place) and rather then use those systems, I'd rather have a system that not only worked offline, but also saved previous versions (and make them searchable) I don't know if something like GNOME 3.0 would provide that functionality.

With Dropbox, Ubuntu One, etc; I'd need to still have some vauge idea of which file is where, is the old one on Ubuntu One, or is it on my computer?

I'd rather just have the one file which was updated (which could THEN be put on those services)


Think of it as sort of akin to what the KOffice developers were doing with NEPOMUK; making it so the user never really needed to memorise the file directory, the program could just save it anywhere and be as easily acessible to the user (if not more) then the current methods.

Hmm... I think the Zeitgeist project plans to implement stuff like that, not only for files, but for everthing the user does like websites, emails. See the use case:
> John turns on his computer to work on his seminar paper. **Instead of digging through his hierarchal file system**, he simply opens up Gnome Zeitgeist and clicks on the top item in the "Recently Used Files" list. When he realizes that he can't remember the name of the website that he was reading for research yesterday, he simply looks at the list of files related to his paper and clicks on the website.

[http://live.gnome.org/GnomeZeitgeist](http://live.gnome.org/GnomeZeitgeist)
[https://blueprints.launchpad.net/zeitgeist](https://blueprints.launchpad.net/zeitgeist)

---

