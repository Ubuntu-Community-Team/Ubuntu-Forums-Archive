---
title: "Migrating Neighbour to Ubuntu - iCloud?"
date: 2016-07-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2016-07-12
Neighbour currently runs win7 and uses Outlook for their mail  - currently sync's outlook Contacts list with their ipad and iphone (is this done via iCloud?).  I would like to migrate them to ubuntu (16.04) but I'm not sure (being a non Apple person) if this can be done.   Obviously I'm going to have to change their mail client - I have always used Thunderbird, but not sure if this (TBird) is the way to go re integration with iphone/ipad.  Any advise appreciated.

---

### Post by DuckHook on 2016-07-13
More info please. The key would seem to be: who is their mail provider?

Example: if provider is gmail, then the move is simplicity itself. Nothing changes on the iPhone, and TBird works (with a few tweaks) with gmail itself, the address book, calendar and task list.

---

### Post by Quarkrad on 2016-07-13
The email provider is btinternet.com - for other reasons I am having to create a gmail account  for this user and I know it is possible to link btinternet.com and gmail (*user will be using Google Cloud for backup so needs gmail account, but will continue to use btinternet as primary email*).  Having said that - not sure if it helps.

---

### Post by howefield on 2016-07-13
I'd look to import the (btinternet) contacts list into gmail, then poll the btinternet account from gmail and set it to be the default sender. Any other devices should be set with the gmail account settings.

---

### Post by Bucky Ball on 2016-07-13
Do they want to be migrated to Ubuntu??? You say you would like to migrate them to Ubuntu, but what would they like? They've asked for you to do this? 

Don't think me rude, but we have seen situations here before where a Ubuntu user has decided their friend/neighbour/cousin/grandparent should be using Ubuntu, too, as it is somehow better for them than what they already have. 

Your neighbours may be happy right where they are (many Apple users are) and not want to migrate anywhere. I am presuming, though, that as you've gone to the trouble of posting here, they are compliant with this migration. Yes? :)

---

### Post by Quarkrad on 2016-07-14
I think you are right.  This started me upgrading them from win7 to win10 and trying to out Group Emails on their Apple devices.  They are happy to move to Ubuntu but having looked into this email/Contacts sync'ing issue a little deeper I'm starting to think it is better to leave them with win10 - after all it works, as you rightly say.  It seems to me one needs iCloud Control Panel to sync Outlook and Apple devices and there is no Linux version.   Perhaps wine might be an answer but I'm guessing that would not work either - apart from this issue I think moving to Ubuntu would benefit them but this is a hurdle too high.  There must be some Ubuntu users who have an iPhone - I wonder what they do about syc'ing email?

---

### Post by Bucky Ball on 2016-07-14
> **Quarkrad said:**
> There must be some Ubuntu users who have an iPhone - I wonder what they do about syc'ing email?

May I suggest perhaps posting a support thread in [Apple Hardware Users]("http://ubuntuforums.org/forumdisplay.php?f=328") and asking just that? Sure folks there will either show you how or advise you forget it, move on, nothing to see here. :| Hopefully the former rather than the latter. :)

Also, nothing on the interwebs you can find regarding this? No doubt you've had a good sniff already. I would have thought this would be a common issue for Apple users who want to transition to Ubuntu. Maybe no. :-k

---

### Post by DuckHook on 2016-07-14
> **Quarkrad said:**
> I think you are right.  This started me upgrading them from win7 to win10 and trying to out Group Emails on their Apple devices.  They are happy to move to Ubuntu but having looked into this email/Contacts sync'ing issue a little deeper I'm starting to think it is better to leave them with win10 - after all it works, as you rightly say.  It seems to me one needs iCloud Control Panel to sync Outlook and Apple devices and there is no Linux version.  Perhaps wine might be an answer but I'm guessing that would not work either - apart from this issue I think moving to Ubuntu would benefit them but this is a hurdle too high.  There must be some Ubuntu users who have an iPhone - I wonder what they do about syc'ing email?Whether your neighbours move to Ubuntu is and ought to be their decision, as Bucky Ball has rightly stated, but on the purely technical side, I think you are making things needlessly complicated. It is very easy to sync email, contacts and calendars on different devices because *you don't sync them directly with each other*. Instead, you use some provider as a server for all of these services, and each of their devices, whether iPhones, Androids, Windows or Ubuntus becomes a client. If you are opening up a Google account for them anyway, then Google becomes the natural choice for acting in such server capacity.

The way to set it up is as follows:

[LIST=1]
[*]Create a Google account (or accounts).
[*]Map this Google account to their iPhone.
[*]Transfer their iPhone contacts, calendars and tasks to Google.
[*]Attach their current btinternet mail account to Google (as per howefield's suggestion)
[*]Their Google account now has (or can access) all of their old data and will act as the server in a classical (and simple) client-server architecture.
[*]Install any of the 'buntus and then install T-Bird (if the flavour you choose does not come with it pre-installed).
[*]Install the Lightning, Provider and gContactSync extensions (which allow calendar, contact and task synchronization) on T-Bird.
[*]Permit Google to share all its info with T-Bird.
[*]Done.
[/LIST]
Due to the fact that Google is OS-agnostic, this setup has the advantage of working for whatever device they may wish to buy or use, even Android or Windows. It also makes it very easy to add, delete and manage machines, since the data on the client is not the primary copy. It adds all sorts of additional versatility&#8213;example: Mrs DuckHook and I have our individual Google calendars but also share a common Google calendar on which we put all shared appointments. Last, but not least, our data is pretty well backed up since it resides as local copies on our desktop, is archived to the NAS, and is also stored on Google.

The issue of migrating them to Ubuntu is a separate one involving whether they really want to do so. However, the technical side is simply a non-issue and is not an the impediment to their doing so.

---

### Post by Quarkrad on 2016-07-16
Wow - thank you.  At the moment they are staying on Win10 as there are a number of other things to do like consolidating multiple address books they have - however, very much appreciate your information above re client/server - this now makes sense to me and leaves the door open for Ubuntu at a later date.

---

