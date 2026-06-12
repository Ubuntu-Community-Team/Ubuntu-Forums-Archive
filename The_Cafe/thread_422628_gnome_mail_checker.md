---
title: "gnome mail checker"
date: 2007-04-25
forum: The Cafe
---

### Post by redgun on 2007-04-25
Hi all :) 

Do you have a gmail account? Do you have used gmail-notify? 
Ok you must give a try to my app :) 

I've coded a new gmail notifier for the gnome desktop that support gnome keyring to store credentials and notifications daemon via dbus to alert when new mails are in your gmail account.

Future versions will support multiple accounts (including pop3)

If you are interested please go here: [http://cgmail.tuxfamily.org/]("http://cgmail.tuxfamily.org/")

you will find an ubuntu package also :D

---

### Post by vicks on 2007-04-25
Great work!

Should go into ubuntu main.

---

### Post by karellen on 2007-04-25
nice job :)
(even if I use evolution for my gmail account)

---

### Post by prizrak on 2007-04-25
Cool, does it support issueing a command on new mail and no mail like checkgmail does?

---

### Post by reclusivemonkey on 2007-04-25
Installed it on Feisty, works great. Using libnotify was a very nice touch. Excellent work! =]

---

### Post by reclusivemonkey on 2007-04-26
Ah, I think I have discovered a small problem. In the libnotify window, when I click on the button to go to gmail, in the browser it opens the URL;

file:///usr/share/cgmail/%22https://mail.google.com%22

which of course doesn't work. I'm sure this is easily fixed. Thanks in advance.

---

### Post by redgun on 2007-04-26
> **reclusivemonkey said:**
> Ah, I think I have discovered a small problem. In the libnotify window, when I click on the button to go to gmail, in the browser it opens the URL;

file:///usr/share/cgmail/%22https://mail.google.com%22

which of course doesn't work. I'm sure this is easily fixed. Thanks in advance.

Uh 8-[ 
For me it works well

Anyway I will try to find the problem.

Stay tuned for next version

---

### Post by redgun on 2007-04-26
> **prizrak said:**
> Cool, does it support issueing a command on new mail and no mail like checkgmail does?

Currently cGmail don't support this feature

maybe in a future version.

But why should you need this?
Try to convince me that its not useless :D

:lolflag:

---

### Post by prizrak on 2007-04-26
> **redgun said:**
> Currently cGmail don't support this feature

maybe in a future version.

But why should you need this?
Try to convince me that its not useless :D

:lolflag:

My laptop has a new mail light that can be activated/deactivated via CLI so it's useful. Could also be useful if you want mail notifications sent to your phone, make a little SMS script and have it run :)

---

### Post by redgun on 2007-04-26
> **prizrak said:**
> My laptop has a new mail light that can be activated/deactivated via CLI so it's useful. Could also be useful if you want mail notifications sent to your phone, make a little SMS script and have it run :)

Ok you won :D

This feature is now into TODO list

---

### Post by orb9220 on 2007-04-26
Just tried it and get error loading page on clicking for new mail

file:///usr/share/cgmail/%22https://mail.google.com%22

Also would like to see sound notification. In checkgmail I could set aplay notify.wav notify.wav so when I am watching the tube or reading I am alerted.

checkgmail also uses > mail.google.com/mail/feed/atom is yours?

---

### Post by redgun on 2007-04-26
> **orb9220 said:**
> Just tried it and get error loading page on clicking for new mail

file:///usr/share/cgmail/%22https://mail.google.com%22

Also would like to see sound notification. In checkgmail I could set aplay notify.wav notify.wav so when I am watching the tube or reading I am alerted.

checkgmail also uses  is yours?

I really don't know why you receive that error. I've retried on my pc and it works well :confused: 

I simply use a python module that open the default browser in a way like this:

```

webbrowser.open_new(GMAIL_URL)

```

where 

```

GMAIL_URL="https://mail.google.com"

```

Maybe a python problem? Which python version do you have?

Sound notification is already implemented into the development version, so stay tuned.

cgmail use atom also

---

### Post by orb9220 on 2007-04-26
What ever is the latest for Feisty. Up to date as of 4-26-07

Python 2.5.1`rc1
Python 2.4
Python 2.5
etc...

---

### Post by redgun on 2007-04-26
so I

I don't find the problem for now. 

I will try to use a different approach to open the default browser for next version

---

### Post by prizrak on 2007-04-26
> **redgun said:**
> Ok you won :D

This feature is now into TODO list

LOL that was easy :) Thanks ;)

---

### Post by reacocard on 2007-04-26
Wonderful little application! I've been using Specto for this, but this works WAY better for GMail than Specto right now. Keep up the good work!

---

### Post by macogw on 2007-04-27
i also have the file:///usr/... problem

---

### Post by redgun on 2007-04-27
I've used a different approach for the upcoming cGmail 0.3 to open browser, hoping that will work for all :)

---

### Post by mustang on 2007-04-28
Very neat app my friend. Thank you for contributing to the open source community. One request I would like to make is to include the "mark as read", "mark as spam", etc options on the dbus notification bubble. Much like the other check gmail application.

---

### Post by redgun on 2007-04-29
version 0.3 is almost completed and I cannot add more features to that version. I will consider your suggestion for 0.4.

Thanks

---

### Post by redgun on 2007-05-02
cGmail 0.3 is out. Check [http://cgmail.tuxfamily.org/]("http://cgmail.tuxfamily.org/") for news and for download :)

---

### Post by Kobalt on 2007-05-02
Thanks for the release redgun ;)

I get this error message when I try to launch it : > Traceback (most recent call last):
  File "/usr/bin/cgmail", line 11, in <module>
    StatusIcon()
  File "/usr/share/cgmail/statusicon.py", line 51, in __init__
    self.checker.init_checkers(self.no_config)
  File "/usr/share/cgmail/checker.py", line 204, in init_checkers
    if len(accounts) == 0:
TypeError: object of type 'NoneType' has no len()

Any idea ?

---

### Post by graabein on 2007-05-02
Is there an option not to show the *no new mail* icon in the notification panel? Kind of like the **update manager** works?

You'd have to use a different way to reach the settings on first run and change of settings when there's no new mail though... Hmmm... Maybe as an icon in the Appliactions menu under Internet or Accessories.

---

### Post by zerwas on 2007-05-02
When i enter my information for my GMail-Account and click on OK, it is still not added. (I cannot add anything). :-(

---

### Post by macogw on 2007-05-02
The new version's "go to gmail" button works properly now.  thanks!

---

### Post by moinster on 2007-05-07
cGMail is the best notifier I've found yet.  Keep up the great work!

---

### Post by redgun on 2007-05-07
@ kobalt: it should be fixed in 0.3.1 Please download this version

@ graabein: this is fixed into development version that you can find at [https://launchpad.net/cgmail]("https://launchpad.net/cgmail"). Please note that is a very instable version

@zerwas: mmm this is really strange. Can you execute cgmail from console and post its output? Try to delete cgmail accounts settings on gnome keyring (or in ~/.config/cgmail if you use plain file) You can file a bug on cgmail launchpad page if it still not work

@macogw: thanks for the information ;)

@moinster: I'm happy about this :)

---

### Post by Nonno Bassotto on 2007-05-07
A very stupid question. How do I tell cGmail that I read the mail? It shows 88 new mails. Fine, I already know those. I want it to show the next ones, but I couldn't find how.

---

### Post by macogw on 2007-05-07
If you click on the envelope in your notification area, it'll re-check your account and revert to "blank" if it's empty.

---

### Post by Nonno Bassotto on 2007-05-07
> **macogw said:**
> If you click on the envelope in your notification area, it'll re-check your account and revert to "blank" if it's empty.

Do you mean I have to empty my account? What if I use to leave the mail on the server? I guess a mail checker should remember what messages were already signaled to me. If it does... well, it doesn't work for me. I click and click and always get 88 new messages.

---

### Post by macogw on 2007-05-07
no sorry. if everything's read, it'll be blank.

---

### Post by redgun on 2007-05-10
> **Nonno Bassotto said:**
> A very stupid question. How do I tell cGmail that I read the mail? It shows 88 new mails. Fine, I already know those. I want it to show the next ones, but I couldn't find how.

To do this you must wait version 0.4 and your email service must support imap protocol. If you want you can try the development version that already support imap accounts ;) You can find it at [https://launchpad.net/cgmail](https://launchpad.net/cgmail)

---

### Post by Nonno Bassotto on 2007-05-10
So on POP accounts I cannot see the last messages, but only the whole content of the mailbox? If this is the case, I cannot use it, since I have to leave some messages on the server, in order to be able to work on my mail when I'm not home. :(

Gnubiff gets this right, maybe you can have a look there if you want to implement this function?

---

### Post by redgun on 2007-05-10
If your mailbox support imap protocol I suggest to give a try to the development version of cgmail. Follow this steps:
* Install bzr (sudo apt-get install bzr)
* Do a checkout (bzr checkout [http://bazaar.launchpad.net/~redgun/cgmail/dev-branch](http://bazaar.launchpad.net/~redgun/cgmail/dev-branch) cgmail)
* Install debhelper and fakeroot
* build the cgmail deb package using buildeb from cgmail dir
* Install the package

Before you launch the development version please remember to delete old configuration, either the gnome keryring key (from gnome menu->System->Administration->Keyring Manager) and the directory .config/cgmail under your home.

Hoping this can be usefull.

---

### Post by _obelix_ on 2007-05-15
Hi,

having planed similar Features to [kshowmail]("http://kshowmail.sourceforge.net/") ?

> e.g.:
    * delete selected mails on servers


Best regards,

Obelix

---

### Post by redgun on 2007-05-15
It must be a mail notifier and not a mail reader ;)

---

### Post by felicity on 2007-06-21
Redgun: Thanks for sharing this wonderful application! I really like it, especially the ability to execute a command on new mails. I have it set to open my gmail inbox in a new tab of firefox when I receive new emails. :-D :-D

But is there any way to hide the icon for cGmail in the "notification area" on the taskbar? Probably not, but here's a vote for its usefulness if you ever ponder adding that feature!

---

### Post by redgun on 2007-06-21
This feature is already implemented in development version. I have had no time to do a new release but it is almost there. If you want you can find it here [https://launchpad.net/cgmail](https://launchpad.net/cgmail)

---

### Post by felicity on 2007-06-22
Awesome, so cool!! Thanks!

---

### Post by impulse1618 on 2007-10-01
I'd like to second the request for options to Open/Mark as read/Mark as spam/Delete etc. when notified of new messages.

Also, I like that clicking the icon can check for new mail. Can you add the feature that double clicking the icon will open your inbox? This would be a great added convenience. When taking you there, the checkgmail program will automatically log you into your account if you aren't already. This is nice and I've never seen another program do that for gmail.

Another great feature would be adding a preview of the message to the notification to see the first 20 words or so of new messages.

Thanks and great work!

---

### Post by pt123 on 2007-10-01
wow neat application just what I was looking for.

---

### Post by cwhitehouse on 2007-10-03
I just found this application.  So far it looks just like the kind of simple gmail application I was looking for.

Thanks!

---

### Post by ImpressMe on 2007-11-14
A pleasant surprise. If you need more inspiration take a look at PopTray for Windows. A shame the program was never ported to Linux.

Thanks

---

### Post by ImpressMe on 2007-11-17
One thing I really miss:

From the tray menu: a CHECK FOR MAIL option (you call it 'refresh' in preferences, but that is a misleading or confusinglabel). I don't need the program to check for mail every 100 secs (I use every 5 mins), but I need it to check when I want it to.

Can you add this? Please, please, with sugar on top? ;)

If you could also add this as a double click action, it would be great.

---

### Post by reacocard on 2007-11-17
> **ImpressMe said:**
> One thing I really miss:

From the tray menu: a CHECK FOR MAIL option (you call it 'refresh' in preferences, but that is a misleading or confusinglabel). I don't need the program to check for mail every 100 secs (I use every 5 mins), but I need it to check when I want it to.

Can you add this? Please, please, with sugar on top? ;)

If you could also add this as a double click action, it would be great.

it does a 'refresh' if you click the tray icon

---

### Post by ImpressMe on 2007-11-17
> **reacocard said:**
> it does a 'refresh' if you click the tray icon

Negative. Not true. At least not here. I have two accounts, one POP3, one GMail. I send a test message to both. I verify that they are available as unread mails on GMail and POP3 server.

Before and after verifying I click on the icon. I get a big yellow balloon telling me NO NEW MAILS.

I then go to preferences and click refresh. It checks showing blue arrow symbol.. and then detects the mails.

(BUT if it already DID detect a new mail cGmail will re-show the balloon window every time you click the tray icon with your left mouse button)

---

### Post by redgun on 2007-11-18
cGmail 0.4 no more support refresh when clicking on status icon. Clicking on it now reshow last notification. Now if you want to force a refresh you must open cgmail (account manager) and click on the reload button. I will try to restore the refresh feature on the status icon also, but I have had problems with it so I disabled it in 0.4

---

### Post by reacocard on 2007-11-18
> **redgun said:**
> cGmail 0.4 no more support refresh when clicking on status icon. Clicking on it now reshow last notification. Now if you want to force a refresh you must open cgmail (account manager) and click on the reload button. I will try to restore the refresh feature on the status icon also, but I have had problems with it so I disabled it in 0.4

Ah, I wasn't aware 0.4 was out. You could at least bring it back to the right-click menu, so that it would still be readily accessible.

---

### Post by ImpressMe on 2007-11-18
> **redgun said:**
> cGmail 0.4 no more support refresh when clicking on status icon. Clicking on it now reshow last notification. Now if you want to force a refresh you must open cgmail (account manager) and click on the reload button. I will try to restore the refresh feature on the status icon also, but I have had problems with it so I disabled it in 0.4

It doesn't have to happen via clicking the icon; an extra option in the menu (when right clicking the status icon) it would be sufficient, if the other problem cannot be resolved.

EDIT: "use your open eye, Frank" ; reacocard already said that. Well, I support him. ;)

---

### Post by pt123 on 2007-11-18
Also when there are 0 new mail can it show a 0 like it does with 1,2,3 etc.

---

### Post by ImpressMe on 2007-11-20
I wasn't able to enable "Start cGmail automatically with the Gnome Desktop".

Output from terminal was:
```
Warning: cannot write to path /home/impressme/.config/autostart/cgmailservice.desktop

```[B] Problem:
The directory 'autostart' did not exist. I created it myself, then cGmail was able to create the file.

[/B] Permissions in the directory '.config' were as they should be, read-write-execute for the current user. So, cGmail must be able to create the missing directory/directories itself.

Kind of problem #2:
This error should be shown in a dialog box rather than in the terminal, should it not?

I think this is enough for a quick release of a 0.4.1. My Gutsy setup is very normal so I assume that the problem can be widespread.

---

### Post by mech7 on 2008-02-19
How can i change it that on a left click it will open up my gmail in browser ?

---

### Post by reacocard on 2008-02-19
> **mech7 said:**
> How can i change it that on a left click it will open up my gmail in browser ?

you would have to change the code itself to do that. If you don't know how to do that already, you probably shouldn't be messing with it.

---

### Post by G|N| on 2008-02-20
I have a little question:
If you have more than 20 unread mails, are you able to retrieve information (sender, subject) from email #21, #22,...?

I am searching for a good library that supports this, but so far i didn't find one yet...it seems gmail is only able to show information from the first 20 messages.

---

### Post by _Stevie_ on 2008-03-26
is it possible to define my own sound for notifying?
i couldnt find an option for that...

---

### Post by macogw on 2008-03-26
> **G|N| said:**
> I have a little question:
If you have more than 20 unread mails, are you able to retrieve information (sender, subject) from email #21, #22,...?

I am searching for a good library that supports this, but so far i didn't find one yet...it seems gmail is only able to show information from the first 20 messages.

Idk, but as it is, it just claims there are only 20 new mails total, when there are 97.

---

### Post by reacocard on 2008-03-26
> **_Stevie_ said:**
> is it possible to define my own sound for notifying?
i couldnt find an option for that...

you could use the 'exec this command on new mails' together with aplay or another commandline player to do the same thing.

---

### Post by _Stevie_ on 2008-03-26
doh, didnt think of that yet, thanks!

---

### Post by jeremy on 2009-02-20
This is a nice little programme, but to make it a great app it needs to have a preview facility (see first few lines of mail) and the ability to delete mail directly from the server.

---

### Post by Nepherte on 2009-02-20
Looks like a nice application. I'm going to try it out as a replacement for mail-notification.

---

### Post by lenik on 2009-04-29
> **jeremy said:**
> it needs to have a preview facility (see first few lines of mail) and the ability to delete mail directly from the server.

try [http://server-pro.com/poptrayminus/](http://server-pro.com/poptrayminus/)
It previews and deletes, but works with POP3 accounts only, sorry.

---

