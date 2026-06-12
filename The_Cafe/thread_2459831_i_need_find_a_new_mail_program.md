---
title: "i need find a new mail program"
date: 2021-03-27
forum: The Cafe
---

### Post by Skaperen on 2021-03-27
i need find a new mail program to replace Thunderbird which just got less friendly by losing the "Send" button on the email being written.

---

### Post by Hagar Delest on 2021-03-27
What do you mean???
I do see the button in TB 78.7.1.

---

### Post by vanadium on 2021-03-27
New email programs are available in Ubuntu software if you do not want to use Thunderbird anymore. Launch "Ubuntu software", then search for "mail" to see available options.

In Thunderbird, the send button is not gone. You however need to fill out an addressee first before the button works. Otherwise, you can also hit Ctrl+Enter to send a message.

---

### Post by TheFu on 2021-03-27
I still see the "Send" button - upper left corner, just under the "File" menuitem.

Could be a font problem?

---

### Post by T6&amp;sfpER35% on 2021-03-27
look at [mailspring](https://getmailspring.com/)

---

### Post by Skaperen on 2021-03-27
> **Hagar Delest said:**
> What do you mean???
I do see the button in TB 78.7.1.

something must have reverted backwards for me.  i have version 68.10.0.  i wonder why.

---

### Post by T6&amp;sfpER35% on 2021-03-27
> [COLOR=#000000]i have version 68.10.0[/COLOR] 
i don't know, i would think any version should have a send button ?
:P

---

### Post by Skaperen on 2021-03-27
there is a "Send Now" selection in the "File" menu.  it works.  there used to be a "Send" button under "File".  i did an upgrade 2 days ago and yesterday late evening was the first time in a few days i need to send email from that address.  i just don't know what version was previously used.  i need to see if i can find it in my logs.

i should set up a cron script to do "dpkg -l" every day and compare it to the latest saved copy.  if it's the same, rm it.  if it's different, save it as the new latest.

i've been thinking of moving that domain to a paid account at protonmail.  i like their web mail interface.  moving there means not using Thunderbird, any more at all.

---

### Post by TheFu on 2021-03-27
> **Skaperen said:**
>  i should set up a cron script to do "dpkg -l" every day and compare it to the latest saved copy.  if it's the same, rm it.  if it's different, save it as the new latest.

Well, you could add a 
```
$dpkg --get-selections  > $local_backup/dpkg.list
```
to your nightly backups so you have a list of all package which can be fed into the restored system as part of the recovery process.  The problem with dpkg -l is that ALL packages are shown, not just the ones manually installed.
```
apt-mark showmanual  > $local_backup/manual-pkg.list
```
is better for restore needs.
BTW, why would any packages be updated without your approval?  That confuses me.

IMHO, webmail is an abomination and not secure.  But everyone has different requirements.  If you care about security of email, use a think client with gpg encryption/certs built-in ... er ... like thunderbird.  If you don't, use gmail or any webmail.  If the message leaves your computer unencrypted, it isn't secure.  

If running your 
[LIST]
[*]own mail server + thunderbird + gpg are 100 on the privacy/security scale and 
[*]using gmail+webmail are 30 (secure, but never private), then 
[*]protonmail is probably around 50 ; better than most, but still webmail with all the inherent flaws.
[/LIST]
Just depends on what you need.

---

### Post by Skaperen on 2021-03-27
i looked through my sent messages and found that the first that was sent from 68.10.0 was on 10 Jul 2020, more than 7 months ago.  yet the "Send" button disappeared yesterday.

---

### Post by Skaperen on 2021-03-27
i would rather be using an IMAP over SSL client.  if protonmail offers IMAP as a substitute for webmail then i'm sure they would do, if not require, one of the ways to engage SSL.  if that is the case, then goodbye zoho (not a bad service but its webmail had bugs).  but i like the way protonmail does things.  now to figure out if i can get apt-get to upgrade me to 78.7.1.

---

### Post by Skaperen on 2021-03-27
it looks like 68.10.0 is the latest for Ubuntu 18.04.

---

### Post by CharlesA on 2021-03-28
> **Skaperen said:**
> it looks like 68.10.0 is the latest for Ubuntu 18.04.

Do you have any addons installed? If one of them was updated, that might explain the loss of the send button. Or perhaps it's profile corruption - I've seen that with firefox, but not Thunderbird though.

With that said - I've been using Thunderbird for years, both with POP3 and IMAP. My hosted email is accessed via IMAP, but gmail is via POP3 because I don't really like how they tag stuff via IMAP.

---

### Post by deadflowr on 2021-03-28
Have you tried resetting the toolbar to the defaults?
(Right click on toolbar > select Customize > click on Button that says "Restore to Default Set")

---

### Post by Hagar Delest on 2021-03-28
Can you upload a screenshot when you write a message with at least an addressee or a fake one (a string with @)?

---

### Post by walts48 on 2021-03-28
> **Skaperen said:**
> it looks like 68.10.0 is the latest for Ubuntu 18.04.

Why, when Thunderbird 78.9.0 is the latest?

I'd be updating to 20.04 or a more modern with it distro that has at least TB 78.8.1.

---

### Post by SeijiSensei on 2021-03-28
The current version of Thunderbird running on my 20.04 laptop is 78.7.1.  If I open the message composition window, the "Send" button in the upper-left-hand corner is greyed out until a To: address is entered.

---

### Post by deadflowr on 2021-03-28
The issue isn't version related.
(That, of course, is a different issue)

---

### Post by Skaperen on 2021-03-28
> **deadflowr said:**
> Have you tried resetting the toolbar to the defaults?
(Right click on toolbar > select Customize > click on Button that says "Restore to Default Set")

just tried it, both on the main panel and on the write panel.  no change.

---

### Post by Skaperen on 2021-03-28
> **SeijiSensei said:**
> The current version of Thunderbird running on my 20.04 laptop is 78.7.1.  If I open the message composition window, the "Send" button in the upper-left-hand corner is greyed out until a To: address is entered.

that makes sense.  there is nothing to send until it knows where you want it to be sent.

---

### Post by Skaperen on 2021-03-28
> **deadflowr said:**
> The issue isn't version related.
(That, of course, is a different issue)

i've discovered that i've been using the same version before and after the Send button disappeared, so i agree it is not version related.  still, this has shown me that for the next problem i have that is not version related, i won't be able to quickly conform that.  so i went ahead and created a script to gather the installed package data.

```

#!/bin/bash
t=$(exec /bin/date +%Y%m%d.%H%M%S)
exec &>/home/root/logs/dpkg-list/$t.log
cd /home/root/dpkg-list||exit 1
l=$(/bin/ls -1|/usr/bin/tail -n1)
/usr/bin/dpkg -l|/usr/bin/xz -9 1>$t.xz
/usr/bin/cmp -s $t.xz $l && /bin/rm -f $t.xz
cd /home/root/logs/dpkg-list||exit 1
/bin/rm -f $(/bin/ls -1|/usr/bin/head -n-15)
exit 0

```

i run it at 5:05 every morning when i'm generally asleep.

---

### Post by rbmorse on 2021-03-28
Open the composition window (write message).  From the menu bar in that window:

View > toolbars > 

then click on "Composition Toolbar" to add the one with the "send" button on it.  The Composition toolbar will manifest directly below the menu toolbar at the top of the composition window.  The "send" button will be grayed out until there is content added to the composition Windows.

---

### Post by Skaperen on 2021-03-29
> **rbmorse said:**
> Open the composition window (write message).  From the menu bar in that window:

View > toolbars > 

then click on "Composition Toolbar" to add the one with the "send" button on it.  The Composition toolbar will manifest directly below the menu toolbar at the top of the composition window.  The "send" button will be grayed out until there is content added to the composition Windows.

that got the **Send** button back!! yay!!

how might it have gone away?

---

### Post by rbmorse on 2021-03-29
My _guess_ is that something disabled/failed to enable the composition toolbar option for the composition window, but what that might have been in beyond my ken.  I know of this only because I had the same issue a couple of years ago and a kind soul in another forum pointed out the solution. 

Glad you got it back. Please marked the thread "solved" in the usual manner.

---

### Post by Skaperen on 2021-04-01
> **rbmorse said:**
> Please marked the thread "solved" in the usual manner.

this thread is in The Cafe because it started as me looking to find another email program.  there isn't a "solved" tool in this forum like there is in General Help.

---

