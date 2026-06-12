---
title: "Windows Mobile 6 Sync Bandaid Solution?"
date: 2008-04-27
forum: The Cafe
---

### Post by SoulinEther on 2008-04-27
So I was pacing downstairs, pondering the meaning of life and the practicality of getting a Windows Mobile 6 phone (namely, the Blackjack 2). As all I use is Ubuntu, this would be a bit of a hassle since there would be no way to sync with my computer...

Why not, though? Just going with what I see off of the Community docs, I know two things:

1) WM5torage is a program that will take your plugged in WM Device and mount the card within it.
2) Oggsync is a program that will sync your calendar with Google Calendar.

So, the phone/device can be more or less auto mounted... and the calendar (and I'm assuming contacts, etc) data can be manipulated by software on the phone/device.

Ok, so design some software in C# or VB.NET for Windows Mobile (or whatever Win Mobile understands) that takes your device's calendar info, contact info, etc, turning them into some standard comma-separated-values/XML file(s), storing them in a folder on your card/internal memory as a "backup" (and perhaps more structurally by date and time, just to keep the syncs all in order.)

Then, make a plugin for Evolution to look for a Windows Mobile 6 card (perhaps you can install an identifying file on it first or something) and look inside some folder for "backup" and read the data that is in the latest "backup" files (that would be the data from your calendar, your contacts, etc on your device). Merge them into your Evolution data.

And the reverse should be doable: take your Evolution data, turn it into a CSV file(s), and, comparing against the CSV file(s) on the WM device, merge the two files such that it contains both the data from Evolution and from the file(s) on the device, and save it as a new set of CSV file(s) on your device (by date / time). Then, using the program that made a "backup" of your data on your device, load the latest data from the new CSV file(s) onto the calendar/contact data of your phone...

Not only can this be useful for syncing, it can also be a good way to backup all your data. Plus you should have an advanced mode where you can pick and choose what data you want to and do not want to back up or sync...

I know i'm oversimplifying here, because I imagine somewhere along the line (probably when merging phone-side and Evolution-side) there has to be an efficient method of differentiating between the same, old data on both Evolution and the device and the new information, so that you don't duplicating information... but I think this is doable. It would be, I think, a dirty solution to a problem that probably plagues many people. (Why not just buy a Palm? For one, the only Palm on ATT that has 3G is pretty crappy, in my opinion.)

Can I get any programmers to help me out with / carry away the rest of the work on this one? :)

---

### Post by beniwtv on 2008-04-27
Last time I used my Pocket PC with Linux, there was a project called "synce".

[http://www.synce.org/moin/](http://www.synce.org/moin/)

I don't know if they support WM6 yet, but it might be worth a look.

---

### Post by SoulinEther on 2008-04-27
> **beniwtv said:**
> Last time I used my Pocket PC with Linux, there was a project called "synce".

[http://www.synce.org/moin/](http://www.synce.org/moin/)

I don't know if they support WM6 yet, but it might be worth a look.

Hum, it seems like they've got it working to somse degree. Well, that's good, because in retrospect this would be horrible to implement.

Sensei says: stop pondering life...just Google it.

---

### Post by beniwtv on 2008-04-27
> **SoulinEther said:**
> Hum, it seems like they've got it working to somse degree. Well, that's good, because in retrospect this would be horrible to implement.

Sensei says: stop pondering life...just Google it.

You could try it out, and if it doesn't work, you still can file bug reports, etc...

---

### Post by Hooya on 2008-05-08
Is that working with Windows Mobile 6 now?  The community docs seem to indicate that it doesn't yet.

---

### Post by InfinityCircuit on 2008-05-08
I have a Blackjack 2 as well.  I have never successfully synced it with Linux.

However, Internet Connection Sharing over bluetooth does work fine once you install the ICS hack.  

See: 
[http://www.howardforums.com/showpost.php?p=10356202&postcount=23](http://www.howardforums.com/showpost.php?p=10356202&postcount=23)
[http://sidux.com/index.php?module=pnWikka&tag=BTPANWM6](http://sidux.com/index.php?module=pnWikka&tag=BTPANWM6)

---

