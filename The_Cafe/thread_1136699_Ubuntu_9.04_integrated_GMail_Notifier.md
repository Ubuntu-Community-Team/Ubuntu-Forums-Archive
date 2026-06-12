---
title: "Ubuntu 9.04 integrated GMail Notifier"
date: 2009-04-25
forum: The Cafe
---

### Post by defreng on 2009-04-25
Hey guys,
I saw those nice new Ubuntu 10.04 features like those polished notifications and the indicator applet and thought that an integrated gmail-notifier would be very nice. Because I didn't found any I decided to write one:

**[SIZE="3"]21.04.2010: Lucid's release v0.10 - [Check Out!]("http://bleedingpaper.com/2010/04/21/release-gm-notify-v0-10/")[/SIZE]**

greetings
Alex

---

### Post by Tibuda on 2009-04-25
I use the mail-notification package. You need to change something in the gconf-editor for it to work with the new jaunty notifications. I don't know if it works with the indicator applet, as I don't use it.
I'll look into your new notifier today.

---

### Post by gnomeuser on 2009-04-25
Reading the source code over quickly it does seem to touch some important corners such as safely storing the password and account information in the keyring.

Could you perhaps expand this into proper GMail integration into GNOME. Such that enabling this would also set the default mail application to xdg-open + urlmagic and give some integrated UI to set account information.

Aside that this is really a life saver in terms of bringing integration with the most commonly used webmail services further. 

In the same vein, would you be open to expanding this into a framework for supporting additional webmails in such a way. I imagine my fiancée who uses Yahoo! mail might be inclined to enjoy better integration for her mail as well.

---

### Post by defreng on 2009-04-25
yes, you're right. The program itself is missing some functionality, espacially a config interface to enter the credentials. I just followed the "release early, release often" strategy and published what I already had including a simple script to set the account data, but I'm already working on a graphical configuration.

To be true my first aim is to complete this as a notification application for gmail-accounts. The GMail integration into GNOME could be a thing I could tackle when I finished the notification part to my satisfaction. Maybe you could add a blueprint into launchpad which describes in detail what you mean?

greetings
Alex

---

### Post by defreng on 2009-04-25
and hey - that's it :)

A brand new release of the gm-notify is out. Version 0.7 including a **graphical configuration tool** and the possibility to **play a sound when a new mail arrives**.

Download it at [https://launchpad.net/gm-notify/0.x/0.7](https://launchpad.net/gm-notify/0.x/0.7)

I hope you enjoy it!

UPDATE: You can find some screenshots again at [www.bleedingpaper.com](www.bleedingpaper.com)

---

### Post by Saint Angeles on 2009-04-25
im really impressed!

i'm gonna mess around with this and let you know how it goes. thanks a lot!!

---

### Post by gnomeuser on 2009-04-25
To simplify the UI for the configuration, you can use libcanberra to interact with the standard sound theme. this will also give you the consistent sounds with the rest of the desktop.

Then that becomes "Play sound when mail arrives [x]"

You should also give an indication of the measurement you use for the check interval.. 90 what. Mins, secs, hours, months? Additionally here I believe Google requests that the lowest check rate be 15 mins so maybe if the user selects something below 15 mins either reject it with that reason or allow it with a warning asking them politely not to abuse googles free service in according to the terms of use.

And for the next time, can you please provide screenshots in US English, it makes it easier to assess the dialog texts and such.

---

### Post by s_spiff on 2009-04-25
Ok, tried it. Seemed to install smooth. Only thing is Jaunty rpos could not find python-indicator.
Anyways, when I configure and run I get this:

> 
gm-notify.py
Traceback (most recent call last):
  File "/usr/local/bin/gm-notify.py", line 22, in <module>
    import pynotify, indicate, urllib2
ImportError: No module named indicate


any ideas?

---

### Post by defreng on 2009-04-26
@s_spiff:
damn, I'm sorry. This is a typo: The package is named python-indicate.

@gnomeuser:
The integration with libcanberra sounds quite good to me.
And at least 15min checkinterval is very long! Do you have a source for this (I hope it is not correct ;) )?

@Saint Angeles
thx ;)

---

### Post by gnomeuser on 2009-04-26
> **defreng said:**
> 
@gnomeuser:
The integration with libcanberra sounds quite good to me.
And at least 15min checkinterval is very long! Do you have a source for this (I hope it is not correct ;) )?


It used to be part of the terms of service you signed, as well as in their documentation for developers. Even if they now long express a set interval limit, you should consider the abuse clause and disallow checking below some reasonable limit say 10 mins. It is a free service and they will terminate accounts due to abuse.

I hope you will still address the other concerns I put up.

*edit*

also I used rosetta to translate this sucker into danish, your strings aren't as translator friendly as they could be. As 1.0 approaches I would love to work with you to enhance that situation.

---

### Post by defreng on 2009-04-26
well I read all the documents about GMail I could find ([http://www.google.com/mail/help/terms.html](http://www.google.com/mail/help/terms.html)) and I couldn't find any restriction of checking. Even the official Google Notifier itself checks every 2mins for new mails. But in the next version I will raise the smallest Limit to 60 seconds.

EDIT: Why aren't they translator friendly or what can I improve to make them better?

---

### Post by Pasdar on 2009-04-26
I always set check interval to 1 min, have done this for years. Anyway, awesome app, keep developing it please, and before you decide to make it work with other email providers, please make it work perfectly and be user friendly as possible for gmail.

---

### Post by gnomeuser on 2009-04-26
> **defreng said:**
> 
EDIT: Why aren't they translator friendly or what can I improve to make them better?

You introduce new wording instead of using platform consistent terminology such as Credentials when Account information is more commonly used. Using the same terms across applications make the job easier for translators and decreases the chance of errors sneaking in as well as increases the consistency between applications.

You also also invent your own words like checkinterval, not only does this word not exist it is unclear. The string might be better if it was "Mail checking interval". 

Using inconsistent use of Caps, e.g. "Play Sound on new Mail", typically "Play sound on new mail" is better as it doesn't force a translator into deciding which words to start with capital letters. Even better would be "Play sound when mail arrives" as it is clearer.

The clearer your intend is the easier it is for translators to avoid mistranslations. The more consistent the terminology is the easier it is to translate correctly and the better your application will fit into the platform.

I would be happy to go string by string for you in private.

---

### Post by Mazza558 on 2009-04-26
Error upon launching in your latest version:

> gm-notify.py
Traceback (most recent call last):
  File "/usr/local/bin/gm-notify.py", line 22, in <module>
    import pynotify, indicate, urllib2
ImportError: No module named indicate


---

### Post by gnomeuser on 2009-04-26
> **Mazza558 said:**
> Error upon launching in your latest version:

install the required dependencies, in your case you are missing python-indicate

---

### Post by smbm on 2009-04-26
> **defreng said:**
> well I read all the documents about GMail I could find ([http://www.google.com/mail/help/terms.html](http://www.google.com/mail/help/terms.html)) and I couldn't find any restriction of checking. Even the official Google Notifier itself checks every 2mins for new mails. But in the next version I will raise the smallest Limit to 60 seconds.

EDIT: Why aren't they translator friendly or what can I improve to make them better?

I've been using other clients to check every 30 seconds for years with no ill effects. I think Gmail in your browser refreshes your inbox every 30 seconds.

Edit: Been using this since yesterday afternoon, and just upgraded to the latest trunk, very good, working a treat.

---

### Post by defreng on 2009-04-26
@Mazza:
yes, there is a typo in the README. Please install python-indicate

@gnomeuser:
Thank you a lot for this suggestions -they indeed sound much better. For further suggestions (I would really appreciate that) contact me at defreng@jabber.org.

---

### Post by gnomeuser on 2009-04-26
oh I have found a bug.

You do not get notifications for mails that are filtered and labeled, just for things that go in the inbox, or so it appears.

---

### Post by ELD on 2009-04-26
Looks like a good application, nice work.

---

### Post by albinootje on 2009-04-26
> **gnomeuser said:**
> It used to be part of the terms of service you signed, as well as in their documentation for developers. Even if they now long express a set interval limit, you should consider the abuse clause and disallow checking below some reasonable limit say 10 mins. It is a free service and they will terminate accounts due to abuse.

I cannot find something about that here :
[http://www.google.com/accounts/TOS](http://www.google.com/accounts/TOS)
And for the record, I've been using a gmail account via pop3 for more than a year, automatically checking it every 5 minutes.

---

### Post by ELD on 2009-04-26
> **albinootje said:**
> I cannot find something about that here :
[http://www.google.com/accounts/TOS](http://www.google.com/accounts/TOS)
And for the record, I've been using a gmail account via pop3 for more than a year, automatically checking it every 5 minutes.

Indeed my G1 checks google mail constantly as it updates me pretty much straight away when i get an email.

---

### Post by Kareeser on 2009-04-26
Hm. If your script only checks the inbox, you could configure it similar to Checkgmail and check the "All Mail" folder instead..

---

### Post by Polygon on 2009-04-26
well...why would it check your all mail? all of your new mail by default goes into the inbox, unless you set it to archive it (which means you don't want to read it)

and hot diggity, an actual use for indicator applet! I'm so there.

---

### Post by defreng on 2009-04-26
Ladies and gentlemen,
**release v0.8**! Actually not so many new visible things, but it now integrates with the GNOME Sound Framework!

[https://launchpad.net/gm-notify/0.x/0.8](https://launchpad.net/gm-notify/0.x/0.8)

One of the next versions will get a new backend and thus fix many problems regarding Labels and POP3 fetching.

By the way it doesn't crash anymore when there are more than 20 unread mails ;)

enjoy!

---

### Post by Polygon on 2009-04-26
hi,

i really like this program, but i have found some issues =P

it seems really hard to change your credentials or how many times it checks for  mail, after the program said 'you are possibly using a too frequent checking timelimit" i tried to change it to something like 10 minutes and i can't figure out how to change it =/



otherwise, good work =)

---

### Post by defreng on 2009-04-26
to change credentials and check interval go to system->settings->GMail Notifier Configuration. You have to restart the notifier, so it's best to log out and login again ;)

---

### Post by Polygon on 2009-04-26
ok, thanks for that. Although you should really have the time to check specified in minutes, to prevent people from setting too frequent of refresh times

---

### Post by Jay_Bee on 2009-04-26
Hi, this is a great application I am using it and I love it! :)
I have a suggestion, would it be possible to make it check multiple Gmail accounts?

---

### Post by mc4100 on 2009-04-26
Once you configure it and hit apply (why isn't it instantly applied?) notify-osd gives a warning (if you go under 180 seconds between sever checks) saying that you're downloading too often, but the dialog is far too long to be both noticed and read.

"You're new mails are being fetched more often than every three minutes. This is possible but not recommended as it produces high load on the GMail servers"

Firstly, it should say "your" and not "you're", the latter being a contraction of "you are".
Secondly, do we need it at all?
If we do, it needs to be made shorter and clearer (you don't even need "This is possible" -- they've already done it).
How about:

"The set time for checking new mail is under three minutes, a smaller demand from the server is suggested."

---

### Post by defreng on 2009-04-26
well, this grammatical mistake is quite embarassing :oops:

but you address some quite important issues: The instant apply is one thing that comes with the next version.

You're also right that this hint is quite long. Next version will have the string "Small Check Interval" - "Increasing ( > 180sec ) would be appreciated"

@Jay_Bee:
multiple accounts maybe come with the new backend for 1.0

---

### Post by smbm on 2009-04-26
Just realised I double posted. Sorry

---

### Post by smbm on 2009-04-26
> **defreng said:**
> 
You're also right that this hint is quite long. Next version will have the string "Small Check Interval" - "Increasing ( > 180sec ) would be appreciated"

Is this message only going to come up the first time the prefs are applied or will it be persistent?

---

### Post by defreng on 2009-04-26
good point. I think it will be persistend because storing what messages already have been displayed is a bit senseless - or how often do you normally configure an email notifier?

---

### Post by smbm on 2009-04-26
> **defreng said:**
> good point. I think it will be persistend because storing what messages already have been displayed is a bit senseless - or how often do you normally configure an email notifier?

I think you should only put it up each time you change the prefs myself.

---

### Post by mc4100 on 2009-04-26
> **defreng said:**
> Next version will have the string "Small Check Interval" - "Increasing ( > 180sec ) would be appreciated"
It's small enough. I've never been fond of using numbers where words would do fine, but that's up to you. One thing I do think is that "*Short* check interval" would preferable to "small" since it's a time.

---

### Post by mc4100 on 2009-04-26
By the way, if you do plan on supporting multiple accounts, or multiple inboxes, etc., is there anyway it could look something like this (from the Messaging Menu wiki page)?
[https://wiki.ubuntu.com/MessagingMenu?action=AttachFile&do=get&target=structure.jpg]("https://wiki.ubuntu.com/MessagingMenu?action=AttachFile&do=get&target=structure.jpg")
It's really nice. A click on a specific inbox or account could take you right there in your browser.

---

### Post by Kosimo on 2009-04-26
Hey, I've just installed it but seems like not working....

sudo ./setup.py install

this is what I did.

How can I uninstall it?

---

### Post by defreng on 2009-04-26
unfortunately there is no real way to uninstall with python distutils.
But you can delete the files manually. That are:

in /usr/share/applications delete:
gm-notify.desktop
gm-notify-config.desktop

in /usr/local/lib/python2.6/dist-packages:
gmailatom.*
gm_notify*
gmxdgsoundlib.*
keyring.*

in /usr/local/bin:
gm-notify-config.py
gm-notify.py
(set-gmail-password.py)

and those files:
/usr/share/locale/da/LC_MESSAGES/gm-notify.mo
/usr/share/locale/de/LC_MESSAGES/gm-notify.mo
/usr/share/locale/ca/LC_MESSAGES/gm-notify.mo

delete Folder: /usr/share/gm-notify

But what's the problem - why doesn't it work. Please tell me so I can fix it ;)

---

### Post by gnomeuser on 2009-04-26
I just had a brainwave. Perhaps one shouldn't focus specifically on the checking interval but on the workflow a user is trying to achieve.

I e.g. try to practice Inbox Zero with minimal interuption so I have it set at once an hour to avoid distractions every few minutes.

Maybe the workflow should be a top level setting for the desktop and it could permiate the required settings to things like the mail notification applets and other reasonable places - or gather optimal times to check from the calendar to not interrupt important tasks.

---

### Post by Kosimo on 2009-04-26
> **defreng said:**
> unfortunately there is no real way to uninstall with python distutils.
But you can delete the files manually. That are:

in /usr/share/applications delete:
gm-notify.desktop
gm-notify-config.desktop

in /usr/local/lib/python2.6/dist-packages:
gmailatom.*
gm_notify*
gmxdgsoundlib.*
keyring.*

in /usr/local/bin:
gm-notify-config.py
gm-notify.py
(set-gmail-password.py)

and those files:
/usr/share/locale/da/LC_MESSAGES/gm-notify.mo
/usr/share/locale/de/LC_MESSAGES/gm-notify.mo
/usr/share/locale/ca/LC_MESSAGES/gm-notify.mo

delete Folder: /usr/share/gm-notify

But what's the problem - why doesn't it work. Please tell me so I can fix it ;)



Hey, thanks for the answer! Gonna try right now!

---

### Post by phaed on 2009-04-26
This is a nice idea, but why don't you get involved with an existing project, like [Specto]("http://specto.sourceforge.net/"), rather than reinventing the wheel?  They need help improving their Gmail notifier, as witnessed by [my feature request]("http://groups.google.com/group/specto/browse_thread/thread/96133a42d8ffcd70") on their forum, and they are looking for contributors.

---

### Post by Polygon on 2009-04-26
specto and any email checker, including this one are completely different programs.

---

### Post by jespdj on 2009-04-26
Your program is not the only e-mail checker for Gmail, before I installed Jaunty I was using [cGmail](http://cgmail.tuxfamily.org/). Unfortunately, cGmail does not use the new notification system, so you get a big, ugly window that you have to click away when you use it on Jaunty. There are already some patches available to make it use the new notification system, however.

And did you know there's also a program called [GmNotify](http://gmnotify.sourceforge.net/)?

But, gm-notify looks like a nice program, I'll try it out.

---

### Post by smbm on 2009-04-26
> **jespdj said:**
> Your program is not the only e-mail checker for Gmail, before I installed Jaunty I was using [cGmail](http://cgmail.tuxfamily.org/). Unfortunately, cGmail does not use the new notification system, so you get a big, ugly window that you have to click away when you use it on Jaunty. There are already some patches available to make it use the new notification system, however.

And did you know there's also a program called [GmNotify](http://gmnotify.sourceforge.net/)?

But, gm-notify looks like a nice program, I'll try it out.

I have a patched version of cGmail in my [_PPA_]("https://launchpad.net/~t.vetterlein/+archive/ppa") but I recommend gm-notify, it seems to be more stable and lighter on resources.

I'm also working on a gm-notify package which I'm talking to the author about which will probably be released tomorrow.

---

### Post by Garrulousbrevity on 2009-04-27
I just installed it, and so far it works fine. 

The only suggestion I can think of right now would be some kind of "Check Now" function.  

And overtime you probably would want to add some of the features from other programs such as checkgmail.  Things like being able to mark a message as read or delete a message without opening up the full inbox.  

Good work though! A good use for the notification system.

---

### Post by smbm on 2009-04-27
There's now a gm-notify package for Jaunty available from this PPA:

[https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)

---

### Post by Polygon on 2009-04-27
ppa works fine here. =)

---

### Post by TheAxeR on 2009-04-28
This is just what I was looking for.  Thank you.  

I am curious if there are going to be plans to extend this to a general imap account beyond gmail?  

I have a imap account which gets imported into gmail, but, it seems like I always get the emails approx. 1hr late.  Which is usually not an issue.  But it would be nice for more instant notification.   If there are no plans for a general imap account then no big deal.  Just curious.

---

### Post by Tibuda on 2009-04-28
> **TheAxeR said:**
> This is just what I was looking for.  Thank you.  

I am curious if there are going to be plans to extend this to a general imap account beyond gmail?  

I have a imap account which gets imported into gmail, but, it seems like I always get the emails approx. 1hr late.  Which is usually not an issue.  But it would be nice for more instant notification.   If there are no plans for a general imap account then no big deal.  Just curious.

Try the mail-notification package from Synaptic. Works with POP3, IMAP, GMail, Yahoo, Hotmail... But it needs some tweaking in gconf-editor to work with the new jaunty notifications.

---

### Post by defreng on 2009-04-28
it's very nice to hear all those positive comments :) 

Here is my current feature list for release 0.9, which will be released this weekend, probably:

- Switch to IMAP Backend
- Possibility to choose labels and folders that should be checked
- Possibility to mark mails you have been notified about as read (Useful for users who use POP3 for mail fetching)

if you had further feature requests, please add them as a bug to launchpad ( [https://bugs.launchpad.net/gm-notify](https://bugs.launchpad.net/gm-notify) ), so I don't forget them :)

@gnomeuser
interesting approach, altough I don't fully understand it yet. Maybe you want to add a blueprint explaining it more detailed?

greetings

---

### Post by gnomeuser on 2009-04-28
> **defreng said:**
> 
@gnomeuser
interesting approach, altough I don't fully understand it yet. Maybe you want to add a blueprint explaining it more detailed?


gm-notify is a small part of that plan, from my point of view if you could consider offering the following:

A dropbox box for check method containing:

1) Fewest interruptions
2) Instant notification
3) Custom interval (in minutes)

3 should reveal a input field

Then let 1 and 2 be defined as 60 mins and 2 mins for now. Later these should be folded into one item called "Work flow default" which will be set by a separate project I currently call WorkKit which will set this as a session wide preference.

The idea is to have a larger project to let little applications like your own gm-notify fit into a work flow for the user. Some users like being interrupted when there is new information for everything, others for just instant messages from people in certain groups and so on. WorkKit will be an abstraction layer to set this policy which other applications can query on dbus to provide the user with the most desirable work flow per session (and eventually per location, based on calendar and device).

And example of the latter might be:

David goes to college and during lectures takes notes in the awesome Tomboy, every pop up is a distraction and he wants to be as focused as possible. Since we have his calendar which says he is having "Introdution to Data security from 8am till 10am" and it is from the college class calendar we know that the context and work flow should be set to least interrupts. 

Furthermore geolocation data (from his IP, the network he is connected to and the built in GPS in his netbook) tells us he is actually on campus so he must be in class. We can now be really sure this is a good default for the hours between 8am and 10am.

Now during lectures David might still want to be interrupted by instant messages but only from people in his study group. In separate contexts certain groups can be elevated to be allowed to breach work flow defaults.

WorkKit is a larger idea, all you need to worry about for now is to help prototype it's idea in the small scale but allowing the user to pick between few and a lot of interrupts as well as custom.

---

### Post by outdooricon on 2009-04-28
Great job on this plugin, looks beautiful and it's working well! I was wondering, would you be able to somehow state that the new mail shown in the notification pop-up was for gmail? I use Evolution for my work account at the same time and so I can't tell if the new mail is for my gmail account or for work from the bubble, so then I have to click on the indicator-applet to find out, which takes away from dev flow...

---

### Post by TheAxeR on 2009-04-28
mail-notification does work, but I prefer the style that gm-notify has.  It is out of the way, in particular it does not have a tray icon and integrates very well with the notify-osd.  gm-notify seems to be going with spirit of notify-osd as opposed to just adjusting to it, which I think is a good thing.

If gm-notify eventually does work with a general imap then I will be happy.  If it doesn't, well I am still pretty happy so I can leave it at that. Its not a deal breaker for me.

---

### Post by Tibuda on 2009-04-28
> **TheAxeR said:**
> mail-notification does work, but I prefer the style that gm-notify has.  It is out of the way, in particular it does not have a tray icon and integrates very well with the notify-osd.  gm-notify seems to be going with spirit of notify-osd as opposed to just adjusting to it, which I think is a good thing.
mail-notification uses the notification area as it is supposed to be used: when there's a unread message, or when it can't connect to your server. That's same the behaviour they want with the "indicator applet".

---

### Post by abhiroopb on 2009-04-28
Is it possible for you to start a PPA? So that we can update gm-notify much quicker? And without having to compile it each time?

---

### Post by Polygon on 2009-04-28
> **abhiroopb said:**
> Is it possible for you to start a PPA? So that we can update gm-notify much quicker? And without having to compile it each time?

there is one

[https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

---

### Post by EnSeNiX on 2009-04-29
is this 64bit compatible?

---

### Post by defreng on 2009-04-29
sure, python is architecture independent ;)

---

### Post by Paqman on 2009-04-29
> **defreng said:**
> Because I didn't found any I decided to write one

There's a few actually. I've been using [checkgmail](http://packages.ubuntu.com/jaunty/checkgmail) for a while and it's excellent. I'll give your one a go too, though.

---

### Post by Polygon on 2009-04-29
> **Paqman said:**
> There's a few actually. I've been using [checkgmail](http://packages.ubuntu.com/jaunty/checkgmail) for a while and it's excellent. I'll give your one a go too, though.

the whole point is that he didn't find any that actually used the new notification system and indicator applet.  All of those take up a space in the tray area and use their own notifications, which is kinda annoying.

---

### Post by abhiroopb on 2009-04-29
The new indicator applet is good, but for some reason I don't find it very "clear". Perhaps it is the arrangement of the text or the fact that it is all the same font/size/colour.

I installed Kgmailnotifier, and the notification is much clearer, and more customisable. While the new jaunty notifications are good on principle, I think the lack of any customisation makes it difficult for it to be effective for all tasks.

---

### Post by mihai.ile on 2009-04-30
Just translated your project into portuguese and romanian. Have fun and keep the good work!

---

### Post by par129 on 2009-04-30
Can anyone explain how to get this installed? I have tried many times following the read me file but I don't know how to execute the setup.py in root and without that the sudo command doesnt work in terminal.

---

### Post by Polygon on 2009-04-30
just add the ppa and install gm-notify from the terminal or synaptic or wherever: [https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

---

### Post by pat23_2007 on 2009-04-30
I am having a problem, It does not show a system tray icon. 

[https://bugs.launchpad.net/gm-notify/+bug/370128](https://bugs.launchpad.net/gm-notify/+bug/370128)

how do I fix this so that it shows a icon on the panel??

---

### Post by Tibuda on 2009-04-30
> **pat23_2007 said:**
> I am having a problem, It does not show a system tray icon. 

[https://bugs.launchpad.net/gm-notify/+bug/370128](https://bugs.launchpad.net/gm-notify/+bug/370128)

how do I fix this so that it shows a icon on the panel??
I don't it is supposed to show a icon there.

---

### Post by pat23_2007 on 2009-04-30
> **danielrmt said:**
> I don't it is supposed to show a icon there.

On the guy who made its website it show this:

[IMG]http://bleedingpaper.files.wordpress.com/2009/04/screeni2.png[/IMG]

---

### Post by abhiroopb on 2009-04-30
Thats only when you get an e-mail. It doesn't always stay there.

---

### Post by Dougie187 on 2009-04-30
The Message applet is not part of the notification area.

It is part of notify-osd which is new in jaunty. If you are not running jaunty, you shouldn't see this notification applet. Once you run gm-notify.py it should put that in the message applet.

---

### Post by Dougie187 on 2009-04-30
> **abhiroopb said:**
> Thats only when you get an e-mail. It doesn't always stay there.

Yes it does. It stays there even when you don't get emails. It just doesn't have (x) in it where x is the number of new messages.

---

### Post by pat23_2007 on 2009-04-30
> **abhiroopb said:**
> Thats only when you get an e-mail. It doesn't always stay there.

I sent myself several test emails from one of my other email address and it never once appeared or even poped up a message.

---

### Post by Tibuda on 2009-04-30
> **pat23_2007 said:**
> On the guy who made its website it show this:
That's not the notifications area, that's the indicator applet (only available in jaunty).

---

### Post by pat23_2007 on 2009-04-30
> **danielrmt said:**
> That's not the notifications area, that's the indicator applet (only available in jaunty).

Yeah I know, I figured it out a few minutes ago. I had removed the indicator applet, but I put it back on the panel and all is good now.

---

### Post by delfick on 2009-04-30
I use this one : [http://gmail-notify.sourceforge.net/](http://gmail-notify.sourceforge.net/)

I prefer to have a dedicated icon to it in the system tray :)

---

### Post by defreng on 2009-05-01
hey guys,
I just commited the almost complete Translation Template for 0.9 including the new config-interface and some backend libs. In general the whole thing isn't yet really usable, so don't try it unless you know what you're doing ;)

But for the translators: It would be nice if you could start translating, so your work can be integrated into the final release! :)

greetings
Alex

---

### Post by michele.b on 2009-05-04
> **defreng said:**
> 
But for the translators: It would be nice if you could start translating, so your work can be integrated into the final release! :)


I'd like to help, but I keep getting launchpad errors when clicking on Italian links... :(

---

### Post by defreng on 2009-05-04
Dear michele,
unfortunately I had the same problem. But if you click only on the "untranslated"-number it works. At this page you can choose just to display translated strings, too.

---

### Post by michele.b on 2009-05-04
thanks for the quick response, but I keep getting the oops.. I noticed that clicking on the numbers works for some (but not all) languages, and unfortunately Italian isn't among them.. I'll try later

---

### Post by NCLI on 2009-05-04
I just completed the Danish translation :)

---

### Post by abhiroopb on 2009-05-04
I'm wondering if it would be possible tos how who the message is from. Usually I like to see who the message is from, the subject and the first few lines. however, that last bit may be too bloated for the notification applet.

---

### Post by defreng on 2009-05-04
@michele
very annoying. It seems to be a launchpad bug... Don't know what to do now

@abhiroopb
well, this could be a good point. It would be the best if you just file a bug report so I don't forget it.

@all
whoo... Again a big Thanks to all your great feedback and translations :) It seems like there are already some blog recommendations for this small piece of code. Just awesome :)

[http://lifehacker.com/5239203/gmail-notifier-is-a-light-convenient-email-checker-for-ubuntu]("http://lifehacker.com/5239203/gmail-notifier-is-a-light-convenient-email-checker-for-ubuntu")
[http://www.kabatology.com/05/01/gmail-notifier-highly-integrates-with-ubuntu-904/]("http://www.kabatology.com/05/01/gmail-notifier-highly-integrates-with-ubuntu-904/")

---

### Post by abhiroopb on 2009-05-04
Neither of the blogs actually suggest adding the PPA which I would think would be easier than installing it manually. Perhaps you may want to suggest that to the blog authors.

Also where can I file the bug report?

---

### Post by defreng on 2009-05-04
mmh, that is a quite good point...

Anyway you can file your bug reports here: [https://bugs.launchpad.net/gm-notify](https://bugs.launchpad.net/gm-notify)

---

### Post by abhiroopb on 2009-05-05
I have added this to my startup applications, however, it keeps asking me for my keyring password everytime I log in. Is there anyway to automate this?

BTW I posted the "bug"

---

### Post by mihai.ile on 2009-05-06
select always allow when asked for keyring?

---

### Post by michele.b on 2009-05-06
Bug fixed, translation done! :o

---

### Post by abhiroopb on 2009-05-06
The always allow checkbox does not show up in this case :(

---

### Post by abhiroopb on 2009-05-06
I added it to the startup but it still does not appear to run. I added gm-notify.py to the startup. Is there another way to add it to the startup?

---

### Post by defreng on 2009-05-06
@abhiroopb
I think there's a way to unlock the keyring during login. For startup try to use the complete path...

---

### Post by abhiroopb on 2009-05-07
I tried the complete path, that works fine. As for the unlocking. How do I do that?

---

### Post by defreng on 2009-05-07
don't know - maybe you should ask one of the gnome-keyring guys ;)

---

### Post by gnomeuser on 2009-05-07
> **NCLI said:**
> I just completed the Danish translation :)

I don't mean to demean your effort but I am trying to help Alex clean up the strings to aim for higher quality and I do that by reviewing the translations for Danish. So till we reach 1.0 can I politely ask you and others to not touch the danish strings?

Looking at the ones that change and the ones that are new is the quickest way I have of spotting where I need to turn my attention, if you complete the translation it means I might miss a new string.

---

### Post by ELD on 2009-05-08
Where exactly do i put in my username and password?

---

### Post by defreng on 2009-05-08
just use the configuration utility at System-Settings-GMail Notifier Configuration

---

### Post by Wokm4n on 2009-05-08
After entering my username and password it is 'checking...' forever :s

---

### Post by defreng on 2009-05-08
uh, unfortunately I have no idea beside trying it again...

---

### Post by Wokm4n on 2009-05-08
I got some experimental features like Gmail Offline enabled. Could that be a problem?

---

### Post by defreng on 2009-05-09
no, I don't think so - should work as expected ;)

---

### Post by Wokm4n on 2009-05-09
I added the PPA, installed gm-notify, launched gm-notify-config.py.
Username: [email]myname@gmail.com[/email]
Password: mypass

After clicking on something the status changes to 'checking...' with the throbbler animation. Only console output:
['__doc__', '__implemented__', '__init__', '__module__', '__providedBy__', '__provides__', 'buildProtocol', 'clientConnectionFailed', 'clientConnectionLost', 'doStart', 'doStop', 'noisy', 'numPorts', 'password', 'protocol', 'startFactory', 'startedConnecting', 'stopFactory', 'username']


purged and reïnstalled.. does not seem to make a difference. I also fetch mail from other accounts (1 gmail, 2 pop3) with the gmail mail fetcher. Checking the 'Mark messages as read' box does not seem to make a difference.

:(

---

### Post by defreng on 2009-05-09
ooh, damn - I see. The package in the given PPA didn't packaged the 0.8 stable revision - so it isn't currently working...

I changed the gm-notify launchpad homepage linking to another PPA which features the 0.8 stable version.

Thanks for your hint!

---

### Post by defreng on 2009-05-10
[SIZE="4"]Release 0.9 almost ready[/SIZE]

whee... Release 0.9 is almost finished and waiting for the last 5 strings to be translated :) . I think I'll give the translators time till tomorrow evening, 0:00h - so the whole thing can be packaged and released maybe on tuesday evening!

If you want to try the "Beta", just check out revision 30 from Bazaar.
0.9 features many new things, like an IMAP Backend (checking different labels), a completely new configuration dialog and much more!

---

### Post by abhiroopb on 2009-05-11
will the ppa be updated? or will we have to manually download?

---

### Post by defreng on 2009-05-11
of course the PPA will be updated - just in time with the release...

---

### Post by abhiroopb on 2009-05-11
Thanks, just realised you had a new ppa!

---

### Post by phaed on 2009-05-11
This app is coming along nicely.  

Is there a way to have the Notification Icon reset after you click it to read your Gmail?

---

### Post by abhiroopb on 2009-05-11
> **phaed said:**
> This app is coming along nicely.  

Is there a way to have the Notification Icon reset after you click it to read your Gmail?

What notification icon? In the 0.8 version I just have the black notification box show up. When I scroll over the box it fades away and when I move the pointer away it reappears and then it disappears completely. How are you able to "click it"? (I'm using Jaunty, with the new growl style notification system).

---

### Post by phaed on 2009-05-11
Sorry, I mean the Indicator Applet in the panel.  When I click it to load Gmail in Firefox, it stays lit up like there's new mail.

---

### Post by abhiroopb on 2009-05-11
How do you have an indicator applet? I don't have one :*(

---

### Post by abhiroopb on 2009-05-11
ah found it!

---

### Post by Wokm4n on 2009-05-12
It will stop displaying the 'new message' icon once CGmail has checked again and there are no unread mails. Maybe it should indeed switch icons once you clicked CGmail in the indicator applet.

---

### Post by mihai.ile on 2009-05-12
> **Wokm4n said:**
> It will stop displaying the 'new message' icon once CGmail has checked again and there are no unread mails. Maybe it should indeed switch icons once you clicked CGmail in the indicator applet.

This is a different application, it's not cGmail...

---

### Post by nvinhphu on 2009-05-12
Hi all,

I've just installed gm-notify 0.8, the configuration went fine but when I launched the gm-notify by using Alt-F2, nothing happened, no icon on the panel. 

I then ran it in the terminal and here is the output:

phu@phu:~$ gm-notify.py
Traceback (most recent call last):
  File "/usr/local/bin/gm-notify.py", line 198, in <module>
    cm = CheckMail()
  File "/usr/local/bin/gm-notify.py", line 68, in __init__
    soundfile = soundlib.findsoundfile(self.client.get_string("/desktop/gnome/sound/theme_name"))
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 84, in findsoundfile
    directories = findsearchdirectories(soundtheme)
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 64, in findsearchdirectories
    sounddir = findthemedir(soundtheme)
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 31, in findthemedir
    dirs = os.environ["XDG_DATA_DIRS"].split(":")
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'XDG_DATA_DIRS'
phu@phu:~$ 

Could you please give me solution to this.
Thanks in advance.

Phu

---

### Post by z0mbie on 2009-05-13
> **smbm said:**
> There's now a gm-notify package for Jaunty available from this PPA:

[https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

Thanks for this smbm!

---

### Post by z0mbie on 2009-05-13
> **nvinhphu said:**
> Hi all,

I've just installed gm-notify 0.8, the configuration went fine but when I launched the gm-notify by using Alt-F2, nothing happened, no icon on the panel. 

I then ran it in the terminal and here is the output:

phu@phu:~$ gm-notify.py
Traceback (most recent call last):
  File "/usr/local/bin/gm-notify.py", line 198, in <module>
    cm = CheckMail()
  File "/usr/local/bin/gm-notify.py", line 68, in __init__
    soundfile = soundlib.findsoundfile(self.client.get_string("/desktop/gnome/sound/theme_name"))
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 84, in findsoundfile
    directories = findsearchdirectories(soundtheme)
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 64, in findsearchdirectories
    sounddir = findthemedir(soundtheme)
  File "/usr/local/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 31, in findthemedir
    dirs = os.environ["XDG_DATA_DIRS"].split(":")
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'XDG_DATA_DIRS'
phu@phu:~$ 

Could you please give me solution to this.
Thanks in advance.

Phu

Hit ALT+F2 and run **gm-notify-config.py**

---

### Post by mihai.ile on 2009-05-13
Well this is quite stupid but the application should be smart enough to detect that it is not configured with any account and start the config automatically. I spent quite some time to find out how in the world I could configure this application (found solution from terminal, and several days after noticed the icon in system menu). And it's not that I didn't know about how the application works because I translated it even before using it.

I think that there ar quite many applications that does the same thing (check email and notify) but make yours a little smarter than the others, this is the real challenge, not some features you find quite the same in other applications.

And again take this as constructive criticism, as I do use the application, translated it and I like it.

---

### Post by nvinhphu on 2009-05-13
Hi,

I did Alt+F2, gm-notify-config.py, everything went fine. Then I did Alt+F2, gm-notify.py, nothing appeared. 

Does any of you here experience the same problem and any solution suggested please.

Thanks a lot.
Phu

---

### Post by smbm on 2009-05-13
There is a brand new version in this (official) PPA:

[https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)

---

### Post by phaed on 2009-05-13
So is that the one we should be using?

---

### Post by smbm on 2009-05-13
It is now, yes.

Version 0.9 has many improvements.

---

### Post by smbm on 2009-05-13
> **mihai007 said:**
> Well this is quite stupid but the application should be smart enough to detect that it is not configured with any account and start the config automatically. I spent quite some time to find out how in the world I could configure this application (found solution from terminal, and several days after noticed the icon in system menu). And it's not that I didn't know about how the application works because I translated it even before using it.

I think that there ar quite many applications that does the same thing (check email and notify) but make yours a little smarter than the others, this is the real challenge, not some features you find quite the same in other applications.

And again take this as constructive criticism, as I do use the application, translated it and I like it.

The config issue is fixed in 0.9

---

### Post by phaed on 2009-05-13
I just installed it and it notified me that I have 1100 unread messages.  I had no unread messages.  Basically it just notified me of all messages being unread.

It also crashed Notification Icon.

---

### Post by phaed on 2009-05-13
Sorry repost

---

### Post by smbm on 2009-05-13
> **phaed said:**
> I just installed it and it notified me that I have 1100 unread messages.  I had no unread messages.  Basically it just notified me of all messages being unread.

It also crashed Notification Icon.

Could you file bugs for these issues please?

---

### Post by phaed on 2009-05-13
Just did.

---

### Post by defreng on 2009-05-13
okay, I see it's already posted, but here is the official announcement:

[COLOR="DarkGreen"][SIZE="6"]gm-notify v0.9 is out[/SIZE][/COLOR] :popcorn:

as smbm already said there are many, many improvements! Just check out the release announcement (in English) on
[SIZE="4"][http://bleedingpaper.com]("http://bleedingpaper.com")[/SIZE] ;)

have a lot of fun

---

### Post by defreng on 2009-05-14
... and Thank God, I finally found and **fixed this major bug #376157** preventing one from applying correct credentials.

The new version is available in the Download section on
[https://launchpad.net/gm-notify/0.x/0.9](https://launchpad.net/gm-notify/0.x/0.9)

PPA at
[https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa) (Please wait for ppa3 to come)

announcement on
[http://bleedingpaper.com](http://bleedingpaper.com)

---

### Post by anonymous_user on 2009-05-15
When I run gm-notify-config.py I get this:
```
Traceback (most recent call last):
  File "/usr/bin/gm-notify-config.py", line 36, in <module>
    import gmimap, keyring
  File "/usr/lib/python2.6/dist-packages/keyring.py", line 4, in <module>
    import gnomekeyring as gkey
ImportError: No module named gnomekeyring
```
I have gnome-keyring installed so I don't know whats the problem.

---

### Post by abhiroopb on 2009-05-15
Why are you running the scirpt? just download the deb or add the PPA and install it that way.

---

### Post by anonymous_user on 2009-05-15
I did add the PPA and did install it. The launcher in the menu is the same as running the script anyways.

---

### Post by defreng on 2009-05-15
for some reason you don't seem to have the package **python-gnome2-desktop** installed, which contains the required module. Just install this and please file a bug report at [https://bugs.launchpad.net/gm-notify](https://bugs.launchpad.net/gm-notify) , so we don't forget to add this to the package dependencies...

---

### Post by smbm on 2009-05-15
> **defreng said:**
> for some reason you don't seem to have the package **python-gnome2-desktop** installed, which contains the required module. Just install this and please file a bug report at [https://bugs.launchpad.net/gm-notify](https://bugs.launchpad.net/gm-notify) , so we don't forget to add this to the package dependencies...

I've just fixed this, the updated package should be filtering through RSN.

---

### Post by 1jackjack on 2009-05-20
I prefer mail-notification as it displays the number of unread emails in the system tray icon.

---

### Post by defreng on 2009-05-20
that's perfectly fine ;)
but for example on a netbook a new notification icon would waste valuable space

---

### Post by 1jackjack on 2009-05-20
true dat. i will certainly recommend this to all my netbook using friends!

---

### Post by elgoog on 2009-05-28
@gnomeuser 

After installation and first run, how do I edit the Account settings and Sound file settings of gm-notify



SOLVED. 
Ok i figured it out. /usr/bin/gm-notify-conifg.py

---

### Post by abhiroopb on 2009-05-28
Its also in System>Preferences

---

### Post by timcredible on 2009-05-28
> **elgoog said:**
> @gnomeuser 

After installation and first run, how do I edit the Account settings and Sound file settings of gm-notify



SOLVED. 
Ok i figured it out. /usr/bin/gm-notify-conifg.py

it's not at the normal right-click on the icon, it's at system->preferences->gmail notifier configuration

also, nice app, author!  i really like how it uses the standard 9.04 notification bubble.

---

### Post by hackel on 2009-07-03
I just tried this as I was looking for an alternative to the memory-grabbing checkgmail, and mail-notification doesn't play well with notify-osd.  It seems to do the job just fine, but I really miss not having an icon to display the number of unread mails in my account.  I realize many people do not want this, and I might not want it on my netbook either, but you should at least have it as an option!  My only other complaint is that it seems to use a lot of memory, no doubt because it's using python.  Right now I'm showing 46m res/432m virt, whereas mail-notification only uses 16/371.  The good news is that, so far at least, I'm not seeing any memory leaks, it's staying consistent!  Look forward to future versions.

Cheers,
Ryan

---

### Post by Tibuda on 2009-07-03
> **hackel said:**
> ... and mail-notification doesn't play well with notify-osd.
It does play well. You just have to [tweak it in gconf-editor]("http://vinodkhare.blogspot.com/2009/06/mail-notifications-and-notify-osd.html").

---

### Post by zorkerz on 2009-07-05
would it be possible to get an amd64 package in the ppa?

---

### Post by l-x-l on 2009-07-06
Is there a way to check what version you're using?

---

### Post by abhiroopb on 2009-07-07
Go to synaptic package manager, search for the package gm-notify. The installed version number will be shown. :D

---

### Post by abhiroopb on 2009-07-21
Any updates of this program?

---

### Post by zorkerz on 2009-07-25
I would love to try this program out, however, there is no AMD64 package in the PPA. Would anybody be willing to walk me through how to run it on my 64 bit ubuntu?

---

### Post by smbm on 2009-07-25
The package should work on all versions as it is written in Python. I am running it on AMD64 here.

---

### Post by zorkerz on 2009-07-25
How did you install it then? I have added the ppa but it will not install a package marked as i386. Do I download the deb anyway and run the .py file inside somehow? I guess I'm just stuck on the basics.

---

### Post by Ecomonist on 2009-07-30
I have just installed Gmail Notifier and I like it. However, how secure is this? As in: does it encrypt my username and password when it checks for new mail?

Over the web Gmail uses HTTPS. Can I enable Gmail Notifier safely when I'm on my university WIFI?

---

### Post by mazz0 on 2009-08-18
Ooh, lovin' it, thanks.  Actually, my emails go straight to my iPhone, so I suppose this is a bit pointless for me, but I'm keeping it anyway, cos it's ace!

---

### Post by Merkaba_ZA on 2009-08-31
For the past week GMail Notifier seems to be giving me issues.  It asks for my password on startup but the indicator applet doesn't load it as per usual and the process dies immediately if I check it in System Monitor.  anyone else having issues?

---

### Post by toobuntu on 2009-09-09
When will packages be available for karmic?

---

### Post by Merkaba_ZA on 2009-09-13
*Bump*

> **Merkaba_ZA said:**
> For the past week GMail Notifier seems to be giving me issues.  It asks for my password on startup but the indicator applet doesn't load it as per usual and the process dies immediately if I check it in System Monitor.  anyone else having issues?

Running it in the terminal gives me the following output:
> Traceback (most recent call last):
  File "/usr/bin/gm-notify.py", line 261, in <module>
    cm = CheckMail()
  File "/usr/bin/gm-notify.py", line 86, in __init__
    soundfile = soundlib.findsoundfile(self.client.get_string("/desktop/gnome/sound/theme_name"))
  File "/usr/lib/python2.6/dist-packages/gmxdgsoundlib.py", line 87, in findsoundfile
    for onefile in os.listdir(onedir):
OSError: [Errno 2] No such file or directory: 'stereo'

Any help guys? GMail Notifier is by far the best mail notification I've used and I'd hate to ditch it for something else.:(

---

### Post by ELD on 2009-09-15
Is this actually still under development? I checked out the original posters profile and he hasn't been active since may apparently? :(

---

### Post by toobuntu on 2009-09-16
From the developer's blog: [http://bleedingpaper.com/2009/05/13/gmail-notifier-release-v0-9/#comment-61]("http://bleedingpaper.com/2009/05/13/gmail-notifier-release-v0-9/#comment-61")

> 
2009 September 16
unfortunately I have not much time at the moment – but I’ll try to make a rework for karmic maybe including the proposal of using jabber for notification…

---

### Post by ELD on 2009-09-16
Well i am looking elsewhere for now.

---

### Post by Merkaba_ZA on 2009-10-03
I've opened a bug report for my GMail Notifier problem in case anyone else is experiencing the same problem with the notifier exiting straight after starting up:

[https://bugs.launchpad.net/gm-notify/+bug/441136](https://bugs.launchpad.net/gm-notify/+bug/441136)

---

### Post by the.lost.one on 2009-10-06
what exactly do i have to add to software sources in jaunty?

i added this: deb _[https://launchpad.net/~gm-notify-maintainers/+archive/ppa/ubuntu/jaunty](https://launchpad.net/~gm-notify-maintainers/+archive/ppa/ubuntu/jaunty)_[]("https://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/jaunty") main

and it couldn't find anything to download.

(its a beginner's question but hey, i'm not a techie)

---

### Post by the.lost.one on 2009-10-06
i found the deb link from the launchpad site.

but i get this error

W: Failed to fetch [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  mai/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by defreng on 2009-10-23
okay - here I am :)

I would really like to make this finally working with karmic, but I have some problems:

[http://bleedingpaper.com/2009/10/23/call-for-help-getting-gm-notify-ready-for-karmic/](http://bleedingpaper.com/2009/10/23/call-for-help-getting-gm-notify-ready-for-karmic/)

I would be glad if someone has an idea :)

greetings

Alex

---

### Post by abhiroopb on 2009-11-09
Getting an error when I try and launch this program:

```

$ gm-notify.py
Traceback (most recent call last):
  File "/usr/bin/gm-notify.py", line 261, in <module>
    cm = CheckMail()
  File "/usr/bin/gm-notify.py", line 109, in __init__
    self.addIndicator("dummy")
  File "/usr/bin/gm-notify.py", line 212, in addIndicator
    new_indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'

```

Worked fine in Interpid. No longer works in Karmic.

---

### Post by coolbrook on 2009-11-09
> **delfick said:**
> I use this one : [http://gmail-notify.sourceforge.net/](http://gmail-notify.sourceforge.net/)I use the same.

---

### Post by zorkerz on 2009-11-11
hey all it was just brought to my attention that there is another gmail notifyer that is integrated with the indicator-applet and notify-osd.

The website can be found at [http://ahadiel.org/projects/gmail-notifier](http://ahadiel.org/projects/gmail-notifier)

Has anybody used this one who could provide a comparison of the two?

---

### Post by Keyper7 on 2009-11-11
> **zorkerz said:**
> hey all it was just brought to my attention that there is another gmail notifyer that is integrated with the indicator-applet and notify-osd.

The website can be found at [http://ahadiel.org/projects/gmail-notifier](http://ahadiel.org/projects/gmail-notifier)

Has anybody used this one who could provide a comparison of the two?

Didn't use it, but peeked at the code and it seems very basic, requiring you to type your username and password each time it starts, for example. But there are people who like things simple, so this might appeal to some.

Plus, it seems like a nice example for those wanting to learn about libnotify and libindicate APIs.

---

### Post by abhiroopb on 2009-11-11
I just installed "gmail-notify" from the repo (not sure if it is the same as "gmail-notifier).

I tried both gnome-gmail-notify and gmail-notify. Both don't perform the basic function that this app (gmail notifier) performs.

Therefore, I'm having a look at the link posted by zorkers.

---

### Post by abhiroopb on 2009-11-11
The good thing about gm-notify (which NONE of the others seem to support well) is that it shows who the new message is from and the subject in the notify-osd. Other apps either use their own notification engine or don't show all the information (e.g. gnome-gmail-notify only says: "you have 1 new message").

---

### Post by abhiroopb on 2009-11-11
Ok fixed my problem on gm-notify.

changed "IndicatorMessage" and put in "Indicator"

edit the file: /usr/bin/gm-notify.py

---

### Post by defreng on 2009-11-12
hey guys :)

just wanted to let you know that I'm currently rewriting gm-notify to perfectly fit into karmic - since many things changed a lot! Hope to release it this weekend - so stay tuned and thank you for your patience! ;)

greetings

---

### Post by Ahadiel on 2009-11-20
> **Keyper7 said:**
> Didn't use it, but peeked at the code and it seems very basic, requiring you to type your username and password each time it starts, for example. But there are people who like things simple, so this might appeal to some.

Plus, it seems like a nice example for those wanting to learn about libnotify and libindicate APIs.

I've just updated it to include subject/sender instead of just "You have mail" and support for saving your email/pass in to the Gnome Keyring.

[img]http://ahadiel.org/wp-content/uploads/2009/11/gmail-notifier-ss2.png[/img]

---

### Post by NCLI on 2009-11-20
> **defreng said:**
> hey guys :)

just wanted to let you know that I'm currently rewriting gm-notify to perfectly fit into karmic - since many things changed a lot! Hope to release it this weekend - so stay tuned and thank you for your patience! ;)

greetings

:biggrin::biggrin::biggrin::biggrin::biggrin:

---

### Post by abhiroopb on 2009-11-20
Works perfectly for me in Karmic, can't really see what needs changing/fixing.

---

### Post by defreng on 2010-02-22
[COLOR="DarkRed"][SIZE="6"]yay - new alpha out[/SIZE][/COLOR] :popcorn:

believe me or not - to be true I promised it too often, but NOW it's reality :D

if you would like to do some alpha-testing (and I mean ALPHA - there are bugs and you can be lucky if it works for you) check out [http://bleedingpaper.com/]("http://bleedingpaper.com/2010/02/22/the-unbelievable-new-gm-notify-version-out-in-the-near-future/")

---

### Post by defreng on 2010-02-28
and again a new revision - the notification itself should now work fine... Please report bugs via the blog if you find some :-)

[http://bleedingpaper.com/2010/02/22/the-unbelievable-new-gm-notify-version-out-in-the-near-future/](http://bleedingpaper.com/2010/02/22/the-unbelievable-new-gm-notify-version-out-in-the-near-future/)

---

### Post by Elcid247 on 2010-03-18
```
/bin/sh: gnome-sound-properties: not found

```

can't set sound, i'm using karmic.

and i get this
```
gm-notify.py: no process found
Traceback (most recent call last):
  File "/usr/bin/gm-notify.py", line 261, in <module>
    cm = CheckMail()
  File "/usr/bin/gm-notify.py", line 109, in __init__
    self.addIndicator("dummy")
  File "/usr/bin/gm-notify.py", line 212, in addIndicator
    new_indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'

```

when i press apply

---

### Post by defreng on 2010-04-21
ok - not too many words... It's finally done and I'm quite glad because it works very well for me.

Release notes, and installation instructions at **[http://bleedingpaper.com/2010/04/21/release-gm-notify-v0-10/](http://bleedingpaper.com/2010/04/21/release-gm-notify-v0-10/)** have a lot of fun and any feedback would be great! Thank you for your patience

Edit: Can someone of the mods please remove the Ubuntu version number from the thread title? Thank you :)

---

### Post by zorkerz on 2010-04-21
When I click Google Mail in the indicator applet no configuration dialogue appears. Without this I have no way of setting it up for my gmail account. How can I tell what is happening?

---

### Post by areteichi on 2010-04-21
> **Elcid247 said:**
> ```
/bin/sh: gnome-sound-properties: not found

```

can't set sound, i'm using karmic.

and i get this
```
gm-notify.py: no process found
Traceback (most recent call last):
  File "/usr/bin/gm-notify.py", line 261, in <module>
    cm = CheckMail()
  File "/usr/bin/gm-notify.py", line 109, in __init__
    self.addIndicator("dummy")
  File "/usr/bin/gm-notify.py", line 212, in addIndicator
    new_indicator = indicate.IndicatorMessage()
AttributeError: 'module' object has no attribute 'IndicatorMessage'

```

when i press apply

Sound configuration also didn't work for me on Karmic using v0.9, but I pulled the newer version by changing the repos to Lucid and v0.10 solves this issue (at least for me)!

---

### Post by defreng on 2010-04-22
> **zorkerz said:**
> When I click Google Mail in the indicator applet no configuration dialogue appears. Without this I have no way of setting it up for my gmail account. How can I tell what is happening?

Oh... maybe you've used it before? In this case everything should work fine. If you still want to configure it go to System-Settings-GMail Notifier Configuration - I'll add this case to the help page, too. Thank you!

---

### Post by zorkerz on 2010-04-22
I have used it before but I thought it was completely removed. There is no GMail Notifier Configuration in system->preferences or in system->administration

Nothing happens when I click Google Mail in the indicator applet and when I click inbox I get a server error from google. > **Google Apps - Server error** Sorry, you've reached a login page for a domain that isn't using  Google Apps. Please check the web address and try again. [Learn  more]("http://www.google.com/support/a/bin/answer.py?hl=en&answer=33419")  This seems to indicate that my gmail account is not correctly setup.

---

### Post by defreng on 2010-04-22
did you install the PPA? In this case there really should be an icon in the Preferences menu.

But you can also open the config utility by calling gm-notify-config.py from the run dialog or the terminal...

---

### Post by zorkerz on 2010-04-23
I have version 0.10 installed from the PPA (ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu). Calling gm-notify-config.py in a terminal opened the config utility and all appears to be working now. I still can only get to the config utility via a terminal though.

---

### Post by jermza on 2011-01-10
Great application.

If my Gmail inbox is already open, and I click on the indicator, then it opens a 2nd instance of my Gmail inbox rather than simply taking me to my already opened one.

Is there a way to fix this?

---

