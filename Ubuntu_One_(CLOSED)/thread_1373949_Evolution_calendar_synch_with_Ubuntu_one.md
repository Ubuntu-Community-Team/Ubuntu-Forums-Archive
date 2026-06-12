---
title: "Evolution calendar synch with Ubuntu one"
date: 2010-01-06
forum: Ubuntu One (CLOSED)
---

### Post by serfcx on 2010-01-06
Does anyone know if it is possible to publish Evolution calendars to ubuntu one as this would be an easy way to share my calendar with my wife who also uses ubuntu.

---

### Post by joshuahoover on 2010-01-15
> **serfcx said:**
> Does anyone know if it is possible to publish Evolution calendars to ubuntu one as this would be an easy way to share my calendar with my wife who also uses ubuntu.

We currently don't provide any services for syncing calendars. One way to achieve what you want is to use Evolution's iCal support to share calendars between you and your wife.

---

### Post by serfcx on 2010-01-18
> **joshuahoover said:**
> We currently don't provide any services for syncing calendars. One way to achieve what you want is to use Evolution's iCal support to share calendars between you and your wife.

The Ical support is frankly poor and cumbersome.
If you are going to have the ability in Ubuntu one to sync address books from Evolution then it would seem to me to be the next logical step to enable calendar syncing.

How about adding it to the list of "nice to haves" ?

---

### Post by e-Gee on 2010-01-18
You can sync Evolution with google calendar

---

### Post by serfcx on 2010-01-18
> **e-Gee said:**
> You can sync Evolution with google calendar

I know but looking at all the posts on that you can only sync a default calendar - If there are more than one calendar it becomes complex or impossible.
I prefer easy logical solutions and Ubuntu one sync calendars would do that.

---

### Post by Kobalt on 2010-01-18
I disagree, I can sync multiple Google calendars using Evolution... I do it all day long and sync my 3 Google calendars with Evolution, an iPhone and an Outlook.

---

### Post by Grenage on 2010-01-18
I think he is referring to a secondary calendar on the google account, not two separate google accounts.

I sync my Gcal on evolution.  It's good but it doesn't store them locally (despite me telling it to), and that's a pain.

---

### Post by Kobalt on 2010-01-18
I'm also talking about different calendars of a single Google account.

---

### Post by serfcx on 2010-01-19
What I am talking about is several calendars in Evolution and syncing them to another computer also running Evolution. This should be simple, if it can be done then please enlighten me, or at least point me in the correct direction, I have googled this and have not been able to find a solution.

---

### Post by Kobalt on 2010-01-20
From this point, Ubuntu One won't let you do this. 
What you're asking can be done, as I'm doing it through Google Calendar. 
Create your different calendars from the Google Calendar website. Then, in Evolution, add a new calendar and select "Google" as a type of calendar. You'll get a window where you'll fill in your calendar details and credentials, and a button where you can retreive the list of calendars for your Google account. Pick you first calendar and add it. And repeat the operation for your other calendars... 
It works like a charm for me on multiple computers, with multiple calendars, storing them locally for offline editing...

---

### Post by hhlp on 2010-01-25
you only can sync the follows :

Files - your pc (files photos, doc, etc )

Contacts - evolution

Notes - tomboy

Bookmarks - firefox

follow this guide for that :

[https://wiki.ubuntu.com/UbuntuOne/Tutorials](https://wiki.ubuntu.com/UbuntuOne/Tutorials)

---

### Post by a_c_h_i_m on 2010-02-08
Syncing calendars is possible by 

1. creating ubuntu one accounts on both  (or more) machines
2. creating a new calendar in evolution
3. creating a new folder in ubuntu one
4. saving the calendar into this new folder
5. changing the properties / options of this calendar: Filename must be the file in the ubuntu one folder  
6. syncing ubuntu one
7. repeating steps 2 and 5 on the second machine

Evolution should now read calendar data from the ubuntu one file and should store it there.  
If you don't use folders and subfolders, deleting a calendar in evolution may delete every calendar file in your ubuntu one folder (a bug?). 
I had some problems with conflicts between older and newer files. So at the moment I'm trying dropbox instead of ubuntu one. 
I'm using evolution 2.28.1 on ubuntu 9.10 and it works quite well.

---

### Post by NotonyourNelly on 2010-09-14
Second that, using ubuntu one it is possible to sync calendar using the method in the post immediately above this.

The step by step guide is good but you need to know to use the customise options when setting up the new calendar  so that you point Evolution to the file in the ubuntu one folder (this needs to be done on each computer you want to sync calendars of course), I set the Refresh option to 'On open', haven't tried the others yet.

A few more tips:

I found that I had to mark all the ubuntu one entries in Synaptic for reinstall and then it was straightforward. 

As I hadn't set up the ubuntu one sync since I upgraded I set it up like this:

System>Preferences>Ubuntu One>Accounts>Manage account

clicking on this opens your default browser, taking you to the ubuntu one login page, enter your account details and you should then be able to set up a sync, manage files, settings and computers connecting to this cloud account.

Opera browser (10.62) didn't work with ubuntu one login - something to do with the caching of the web page I think, I set chromium as default and this worked fine, Firefox should be fine too.

---

### Post by joho68 on 2010-09-15
All we need now is for **Ubuntu One** to actually work ;)

---

### Post by djpemberton on 2010-10-12
I'm interested in being able to do this as well. Can you not just right click on certain existing folders (perhaps ~/.evolution and ~/.gconf/apps/evolution) and tell Ubuntu One to sync these folders? I'm very new to all of this, so I'm sure there are factors I am not considering. Is it necessary to move files around though?

---

### Post by camzrama on 2010-10-21
I find this puzzling.  I can read multiple Google calendars but I can only edit one of them from Evolution.  The one is the first calendar I created in Google.  I have one additional calendar in Google under the same account and I have another that is shared from my wife's account.  I can read the calendars from Evolution, but not edit them.

If someone knows how to enable editing on multiple Google calendars from Evolution, I would like to know how.

---

