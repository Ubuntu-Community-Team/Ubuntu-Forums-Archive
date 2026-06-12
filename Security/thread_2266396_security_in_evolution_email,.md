---
title: "security in evolution email,"
date: 2015-02-22
forum: Security
---

### Post by de Bacon on 2015-02-22
I have been using evolution since 2008, using the backup function when switching to new versions of Ubuntu.  Currently the flavor Ubuntu version in use is Ubuntu Studio 14.04.1   Currently the Evolution version in use is 3.10.4. The source for my email is POP3, originating from my own web domain rather than google, yahoo, or other commonly used companies.  I am ignorant as to the technical side of most things in the computer realm.  I use it, a lot and react when I see a need.

Well I don't know about encryption and at this point don't use it in my email setup.  This may be a mistake, I just don't know the what, why, when, where, how or why with encryption.  Regardless, having made no changes in either the server side or the email accounts side in my box in recent days, last night there was an evolution sourced (supposedly) pop-up that appeared, asking for a password for a specific email account (I have many).  I didn't respond to it, because it didn't seem logical that it would suddenly loose its password without any deliberate alterations deliberate input.  

As stated, I didn't respond to the pop-up, I closed the box and at the end of my night I shut down my computer as per normal for me.  Upon opening it again this day, again the pop-up appeared, but at start up of Evolution.  Again I didn't respond, closing the pop-up.  It did cause me to do some minor investigation, where as in the preferences for Evolution I started looking around.  I eventually found myself looking at the Certificates page, with its tabs, startling!  At least to me it seems startling, but I don't know what that should look like.

In the tab "Your Certificates" there is nothing.
in the tab "Contact Certificates" there are a few.  Two I guess are group named, specifically: Global Trustee (having one item), and the other Google Ltd. (having eight items).  As to the eight items under Google Ltd I don't now, nor have I ever had any connection to email through Evolution to any of the named locations either past or present.  These eight are: addons.mozilla.org, login.live.com, login.skype.com, login.yahoo.com (three of these with unique Serial Numbers), mail.google.com, [www.google.com](www.google.com).

In the tab "Authorities" there are far too many to list, probably upwards of one hundred of them.  

Again, in total, this seems alarming to me. 

I am wondering if I have dug myself a big hole by using the backup and restore functions of Evolution when upgrading to new versions of Ubuntu over the years?  The accumulated certificates seem both numerous and possibly intrusive, from my ignorant point of view.  I have spent a few hours this morning attempting to learn something about this stuff, finding nothing at all useful to my ignorant mind.  I accumulate a long list of meaningless acronyms that can make sense to me as long as I am reading their actual words then go off into space when I get to the next acronym and the cycle repeats, culminating in a true lack of communication.  

I am wondering about these certificates, if they truly have a continuous use for my particular data set in Evolution or if most of it is now archaic?  

The way I use the backup system in Evolution is this: at the end of a year, I do a backup, archiving that, then I remove all the messages from the year prior, meaning that at the start of any given year, evolution contains one year of data. 

I know this doesn't address the pop-up box that showed up, it is merely the side effect of my looking into what might be an issue causing that pop-up.  Furthermore, found nothing seemingly of conflict in that process.

Oh, I use unique overkill strong passwords on each of my email accounts as well as the server side domain account itself.  That is just a fact, not a statement that this stuff is all secure.  I know that even strong passwords have the potential of being cracked.

Then there is the question of email encryption.  Do you have any pointers that can help me figure out, one if I should use it? If so what type to use, or is SSL adequate?  Followed by, if so, this question, if I begin using encryption now what will happen to the data that is now stored as backup if I choose to re-introduce it for some now unknown reason?  I guess also, if I use encryption in my own email system will I have to send everyone I communicate with an encryption key?

Thanks in advance.  Humbley yours,

---

### Post by PhilGil on 2015-02-22
I am far from an expert on how security certificates work, but I don't see anything alarming here.

The  Contact Certificates you are referring to are there so Gnome online  accounts can connect securely to your Gmail, Skype and/or Yahoo  Messenger contacts. These are typically curated by the OS and are not an  indication that anyone has actually established a connection to the  service. The Authorities are a list of certificate-issuing  organizations trusted by your OS.

You didn't say where the password prompt was coming from, but I get regular, annoying prompts from Gnome to re-enter my Google password. I believe that's because Google made a change to their authentication code that created a bug in Gnome Contacts. I just dismiss the prompt and haven't noticed any ill effects.

And just to add my own rant here... I hope whoever came up with the brilliant idea to make Gnome Shell password prompts global-modal spends eternity typing random character passwords on a keyboard of molten lava. Not being able to copy/paste long passwords from my password safe is both user and security hostile.

---

### Post by bashiergui on 2015-02-22
> I am wondering about these certificates, if they truly have a continuous use for my particular data set in Evolution or if most of it is now archaic?Evolution is an email client that allows you to manage email accounts hosted locally, in your LAN, and elsewhere on the internet. Email services on the internet (like gmail and yahoo) require certificates to deliver your email over ssl. Evolution comes bundled with all the necessary certificates to use popular internet email services. I imagine that the certs are updated routinely through evolution apt updates. 

In short, the certs are standard in every installation.

I haven't used email encryption with gpg so I can't offer advice beyond what you'll find in the Ubuntu help documentation. 100% of my friends that have used gpg email have found it cumbersome and not user friendly, maybe even one of their favorite subjects to complain about ;) YMMV

---

### Post by de Bacon on 2015-02-22
> **PhilGil said:**
> 
And just to add my own rant here... I hope whoever came up with the brilliant idea to make Gnome Shell password prompts global-modal spends eternity typing random character passwords on a keyboard of molten lava. Not being able to copy/paste long passwords from my password safe is both user and security hostile.

That is very funny.  I am in agreement about that function.  I have found that I can't even type accurately in these prompts when they pop up.  They seem to block all other desktop function if left open too!  I have to close the popup then evolution, get the password into the clip board, then reopen evolution.  It is pretty unfreindly, but...  I don't know how to change that!

Thanks for the info, my alarm is now pretty much relieved, thanks for the replies.

---

