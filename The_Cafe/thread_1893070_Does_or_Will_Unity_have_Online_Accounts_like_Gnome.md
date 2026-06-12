---
title: "Does or Will Unity have Online Accounts like Gnome?"
date: 2011-12-09
forum: The Cafe
---

### Post by Dragonbite on 2011-12-09
One of the exciting features of Gnome 3.2 is [_Online Accounts_]("http://library.gnome.org/misc/release-notes/3.2/#goa") (even though I haven't managed to get it to work yet, but the idea is cool!)

[CENTER][IMG]http://ubuntuforums.org/picture.php?albumid=2258&pictureid=8297[/IMG][/CENTER]

I haven't seen anything relative to this included in Unity. It is different than Ubuntu One.

Am I missing it in Unity or is this something that will be coming into Unity in the future?

---

### Post by haqking on 2011-12-09
Unity is a shell, 11.10 is already running Gnome 3.2.

As for online accounts it is in top right menu

see attached from my virtual machine

---

### Post by Dragonbite on 2011-12-09
Now, all of my attempts with Gnome-shell have failed to connect (Fedora 16 and openSUSE 12.1).  Has Unity's version been more successful?

---

### Post by Mr. Picklesworth on 2011-12-09
> **Dragonbite said:**
> Now, all of my attempts with Gnome-shell have failed to connect (Fedora 16 and openSUSE 12.1).  Has Unity's version been more successful?

The point is that Unity doesn't have its own "version" of this. We ship Gnome 3.2, but with Compiz / Unity instead of Mutter / Gnome Shell. Just think of these two shells as launchers and window managers. They help you organize applications,  but they don't affect the applications in a significant way.

So, if Online Accounts isn't working for you in Fedora, there's a good chance it isn't working over here, and a bug report might be in order. It might be the software that's pulling from GOA, though, because it's quite a new feature and it isn't supported everywhere it should be yet.

---

### Post by Dragonbite on 2011-12-09
I'm hopeful.

So Unity is just a shell sitting on top of Gnome (3.2 in this case)?

---

### Post by haqking on 2011-12-09
> **Dragonbite said:**
> Now, all of my attempts with Gnome-shell have failed to connect (Fedora 16 and openSUSE 12.1).  Has Unity's version been more successful?

I am pretty sure there is no difference.

Online accounts is a feature of Gnome 3.2.

Gnome-shell or Unity are just shells which sit on top of Gnome 3.2 so i dont think Unity has its own version of Online accounts.

Though i may be wrong.

Anyways i just quickly added a gmail account in my 11.10 VM and it works fine

see attached

---

### Post by Dragonbite on 2011-12-09
Well, I'm going to be hopeful and give it a try.

One thing that Fedora and openSUSE both given trouble with, which may be related to not getting Online Accounts working, was that they both have ipv6 enabled on the LiveCD which needs to be turned off.

I don't remember Ubuntu having that issue, so if that is what is causing me problems then Ubuntu may work better.

Thanks for clarifying things up!  So much is being said it's hard to tell what is really going on and what really is "Unity".

*cross fingers*

---

### Post by mcduck on 2011-12-10
I've tried the Gnome-Shell's online accounts in Ubuntu, and it doesn't seem to do much at this point. It *did* fill Gnome Contacts with the contact information from my Google account, but that's pretty much the only thing it did.

I would assume that the feature isn't fully implemented by Gnome yet. Adding an account works fine, it just doesn't seem to be used for anything.

---

### Post by Dragonbite on 2011-12-10
> **mcduck said:**
> I've tried the Gnome-Shell's online accounts in Ubuntu, and it doesn't seem to do much at this point. It *did* fill Gnome Contacts with the contact information from my Google account, but that's pretty much the only thing it did.

I would assume that the feature isn't fully implemented by Gnome yet. Adding an account works fine, it just doesn't seem to be used for anything.

According to the Gnome site, it should enable searching through Google Docs, though I thought I read somewhere that you cannot open them locally yet, and to have it so when you click on the clock and it shows the calendar, your appointments in Google calendar are listed.

Oh, and doing a search with somebody's name if they are in contacts is supposed to pull up their contact information and current online status.

---

### Post by Frogs Hair on 2011-12-10
In  Gnome the only account selection on the drop-down  menu is Google . How would I add other account types with Google as the  only  option ?

---

### Post by Dragonbite on 2011-12-10
> **Frogs Hair said:**
> In  Gnome the only account selection on the drop-down  menu is Google . How would I add other account types with Google as the  only  option ?

I've seen Google and Twitter so far.  I'm sure if there are others people are interested they may find their way into it.

Google, Twitter, maybe Facebook, Zoho or even Microsoft Live.

---

### Post by Dragonbite on 2011-12-29
Quick updates!
[LIST]
[*]While Google and Twitter are there first, there is a PPA available for connecting Empathy to Microsoft's MSN XMPP chat I found in OMG! Ubuntu [_[How to]Install Empathy with MSN XMPP Support in Ubuntu _]("http://www.omgubuntu.co.uk/2011/12/how-to-install-empathy-with-msn-xmpp-support-in-ubuntu-11-10/")
[*]With my (Google) online account set, when I installed and opened Evolution my email and contacts were automatically set up for my Online account without anything from me.  Calendar didn't but I hope that will change in the future.[/LIST]

---

