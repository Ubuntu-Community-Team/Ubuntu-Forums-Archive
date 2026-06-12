---
title: "Gmail and Thunderbird"
date: 2006-03-30
forum: The Cafe
---

### Post by BWF89 on 2006-03-30
So awhile ago I decided to try checking my mail useing Mozilla Thunderbird instead of just going to Gmail.com and checking it with Firefox.

So I download & setup Thunderbird but when I get it running it takes litterily every single email I have whether it's in my inbox, trash, spam, or starred folder and puts it as unread mail in my inbox foulder. This was unacceptable so I uninstalled it and went back to checking it with Firefox.

I went to addons.mozilla.org and looked under the Thunderbird addons for "Gmail" hoping to find something that would better integrate the web based Gmail service with the desktop based Thunderbird client. Like for instance while useing Gmail with Firefox I have the option of putting a star next to one of my emails and it goes into my starred folder where it's kept forever and not deleted. Thunderbird doesn't have this option.

Is there an extension or a way that I could get all the features I have useing Gmail on the web with the features of useing Thunderbird on the desktop? Also, when you sign into Thunderbird it says that it's downloading your emails. I'm a privacy freak so I was wondering if there is a way that I could read my emails with Thunderbird as fast as I could as if I used gmail.com without having to download them to my hard drive?

---

### Post by kwaanens on 2006-03-30
[QUOTE=BWF89]Is there an extension or a way that I could get all the features I have useing Gmail on the web with the features of useing Thunderbird on the desktop? Also, when you sign into Thunderbird it says that it's downloading your emails. I'm a privacy freak so I was wondering if there is a way that I could read my emails with Thunderbird as fast as I could as if I used gmail.com without having to download them to my hard drive?[/QUOTE]

(At least) 2 alternatives that might be interesting:

1. Use Synaptic and install gmail-notify. Go to System > User settings (or whatever it says) > Sessions. Tab: Start-up programs. Add gmail-notify.
You will now have a Gmail icon in your system tray, which turns blue when you get mail. (Right click to configure it)

2. Gmail has RSS-reads, doesn't it? So set up your Gmail-account in RSS. I think: <http://mail.google.com/mail/feed/atom> is the right feed. You will not be able to do anything but read your mails, but hopefully this will be better than your present situation.

- Ketil

---

### Post by BWF89 on 2006-03-30
That wasn't what I was looking for. I was looking for something that (and I don't know if this is possible) that will sort my messages into the same folders on Thunderbird as they are sorted on my Gmail through Firefox.

Like instead of sorting between all messages and messages recieved in the last 5 days it would sort as they are in my Gmail account which is like 5 in my inbox, 46 in my starred folder, 35 in my sent mail folder, and 240 in my spam folder. Is this possible?

EDIT: Also, when I exit out of Gmail and than I go back in eventhough it asks me to type in my password it still displays all my previousaly downloaded mail without needing a password. How do I make it so it either deleted all my mail when I sign off or I have to enter my password before it will show any of my mail?

---

### Post by kwaanens on 2006-03-30
[QUOTE=BWF89]That wasn't what I was looking for. [/QUOTE]
That's why I said:
[QUOTE=kwaanens](At least) 2 alternatives that might be **interesting**:[/QUOTE]
(My bolding)

[QUOTE=BWF89]I was looking for something that (and I don't know if this is possible) that will sort my messages into the same folders on Thunderbird as they are sorted on my Gmail through Firefox.

Like instead of sorting between all messages and messages recieved in the last 5 days it would sort as they are in my Gmail account which is like 5 in my inbox, 46 in my starred folder, 35 in my sent mail folder, and 240 in my spam folder. Is this possible?[/QUOTE]

If Google decided to let people access Gmail with IMAP, you would be able to this. Unfortunately they don't. Probably because they want you to log in to Gmail to see sponsored links.

[QUOTE=BWF89]EDIT: Also, when I exit out of Gmail and than I go back in eventhough it asks me to type in my password it still displays all my previousaly downloaded mail without needing a password. How do I make it so it either deleted all my mail when I sign off or I have to enter my password before it will show any of my mail?[/QUOTE]

With the Thunderbird Gmail-extension you're using?
I don't know, but you'll probably have to check with whoever made the extension. mozillazine.org might be an option. Check out the forums there, there are more Mozilla-geeks there than here.
The reason it shows your downloaded mail is that it is downloaded locally to your computer. Your password is needed for logging into Gmail to check for new messages.
(Disclaimer: I have never used or even seen the extension you're using, so these are (more or less qualified) guesses.

- Ketil

---

### Post by CameronCalver on 2006-03-31
wat is this error mean

---

### Post by Tipo on 2006-03-31
Okay, look at your screenshot...

It says it's having problems connecting to **smpt**.gmail.com.

You need to connect to **smtp**.gmail.com

---

### Post by CameronCalver on 2006-04-01
u so wat do i do to fix it

---

### Post by CameronCalver on 2006-04-06
can u answer me plz

---

### Post by Ubunted on 2006-04-06
I've set up my Gmail account in Thunderbird under both Windows and Linux more than once. I dunno what kind of settings you have, but all it ever gives me is what's in my inbox.

---

### Post by LinuxKid on 2006-04-06
[QUOTE=CameronCalver]u so wat do i do to fix it[/QUOTE]
go to Tools-->Account Settings-->Outgoing Server (SMTP)

edit the default server and make sure it it is configured as such:

Server Name: smtp.google.com
Port: 587
*username*
Use Secure Connection: TLS

that should be it and you're good to go

---

### Post by Stealth on 2006-04-06
> I'm a privacy freak so I was wondering if there is a way that I could read my emails with Thunderbird as fast as I could as if I used gmail.com without having to download them to my hard drive?

LOL, privacy-freak Gmail user, isn't that an oxymoron...hmmm :P

If you've gotten Thunderbird to access the Gmail account, you can have it sort different types of email (I don't know if they're tagged differently or anything) but for instance, you can create a folder in your Inbox, and move e-mails you want to keep forever there. Thunderbird can do a lot of things, I just don't know if G-mail will let it...

---

### Post by Luggy on 2006-04-06
[QUOTE=BWF89]
So I download & setup Thunderbird but when I get it running it takes litterily every single email I have whether it's in my inbox, trash, spam, or starred folder and puts it as unread mail in my inbox foulder. This was unacceptable so I uninstalled it and went back to checking it with Firefox.

I went to addons.mozilla.org and looked under the Thunderbird addons for "Gmail" hoping to find something that would better integrate the web based Gmail service with the desktop based Thunderbird client. Like for instance while useing Gmail with Firefox I have the option of putting a star next to one of my emails and it goes into my starred folder where it's kept forever and not deleted. Thunderbird doesn't have this option.
[/QUOTE]

Ok I think your problems are with how you have Gmail set up, not thunderbird and you don't need an extension to get it to do what you want it to do.
[[IMG]http://img211.imageshack.us/img211/9822/screenshotgmailspammozillafire.th.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshotgmailspammozillafire.png)
Now look at the image above and notice the area circled in red. If you don't want to have your old e-mails passed over set the second (middle) radio button.

If you do want your old e-mails to be passed forward but you don't want to have to set each one to read simply right click on the folder with your e-mails and select 'mark folder as read'; it's a really quick and painless way to deal with pop3 mail servers.

---

