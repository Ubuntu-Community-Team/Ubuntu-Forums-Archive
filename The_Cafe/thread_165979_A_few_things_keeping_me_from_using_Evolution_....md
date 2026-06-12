---
title: "A few things keeping me from using Evolution ..."
date: 2006-04-25
forum: The Cafe
---

### Post by el3ktro on 2006-04-25
I'm using Thunderbird currently, but I'd really like to use Evolution for two reasons mainly:

1. it's more gnomeish, it fits better into the desktop
2. Beagle can search trough Evolution e-mails

But there a few annoyances (as I see them) that prevent me from using Evolution:

1. There's no way to have Trash, Junk & Sent folders saved on the IMAP server. Thunderbird does it. Well I don't care for Trash actually, but the Sent & Junk folders should be on the server definitely. Junk, because I have a cron job running once a day scanning those Junk folders & make spamassassin learn from them, and the Sent folder should be on the server simply because the main intention for using IMAP is to have ALL e-mails available all times (also from somewhere else via Squirrelmail for example). I know I can create a "Sent" folder within the Inbox of my mail account, but this doesn't really make any sense, and Evolution doesn't even give this Sent folder a special icon, so it's just one folder between all my other Inbox folders - not very nice. The best way would be if Sent, Junk & Trash would be displayed BESIDES Inbox - just as Evolution does it with the latter two right now, but that they would be stored on the server instead locally.

2. Why, oh why the hell do you have to customize the e-mail folder list for EVERY SINGLE e-mail folder? I don't want some of the columns, and the "date" column takes up 30% of the space, although a really small column would be enough to display the date of the e-mail. I know there's a "Best fit" option, but it's not working, the "date" column is still way too big. This is soooo annoying! I'd have to re-configure all of my 50+ folders one by one if I want them to look the same. Imho, this really MUST be changed!

3. The third and one of the worst things - and the original reason why I also never used Kmail when I was a KDE user - you can't have seperate e-mail filters for seperate mail accounts. This makes it impossible for me to filter my e-mails. One example: Both me & my girlfriend have our mail account in Evolution. We both know the same people more or less. We both have a "Friends" folder, and I want mails from my friends sorted into my Friends folder, and my girlfriend does the same. With the present filtering system, this is not possible! I'd have to create a new filter for each friend, both for me & for my girlfriend. In Thunderbird, I have ONE filter for all of my friends within my mail account, and my girlfriend has ONE filter for all her friends (some of which are also my friends) within her mail account. I begged the Kmail people so much to really allow me to have SEPERATE e-mail accounts, and now the same happens again with Evolution :-( I want my mail accounts to be REALLY SEPERATED, I mean thats the whole reason why I actually have TWO e-mail addresses, if I didn't want them to be seperated, I could also just have one, single e-mail address right?

Well I just had to tell this somebody, those 3 things are some of the things that MANY e-mail clients do wrong imho, and I hope Evolutio will do this better sometime, because otherwise it's a great app and I'd REALLY like to use it.


Tom

---

### Post by zubrug on 2006-04-25
Opera rules.

---

### Post by varunus on 2006-04-25
Number one at least, works in evolution.  Just set it in the Account Options dialog box where your trash, junk, and sent folders are...it puts them on my IMAP server for me.

Two, try filing a bug...

Three, evolution is designed the way GNOME is; multiple people = multiple users.  Evolution will store filters differently if you have a different user for each person...so its just a mindset difference.  I can see your point, though...maybe file a bug?

---

### Post by ShanghaiTeej on 2006-04-25
I wish evolution had an easy way to access contacts like Thunderbird's extension: "contact list"...where it's right there in front of you.

---

### Post by briancurtin on 2006-04-25
i dont use evolution because there are simply better alternatives.

---

### Post by oliverb on 2006-08-24
I liked the look of it and it seemed to work well at first but in the last few days it's started hanging. I think the IMAP server I'm using may be uncooperative but that's not really an excuse when the program won't even close down.

---

### Post by cevans on 2006-08-24
> **oliverb said:**
> I liked the look of it and it seemed to work well at first but in the last few days it's started hanging. I think the IMAP server I'm using may be uncooperative but that's not really an excuse when the program won't even close down.

You were using the IMAP receiving option instead of IMAP4rev1, weren't you? Despite the fact not being mentioned anywhere in documentation, IMAP4rev1 is not supported and has apparently been broken for over a year. 

Evolution just isn't polished or very mature yet. I would use Thunderbird instead.

---

### Post by %hMa@?b&lt;C on 2006-08-24
I dont use evolution because I have a broadband internet connection, and I love gmail's interface!

---

### Post by jISh on 2006-08-24
Evolution is just a really big memory hog. That, and as said above, Gmail's interface is tough to beat.

---

### Post by Rhubarb on 2006-08-24
As I'm not infront of my Ubuntu machine now, I could be a bit wrong but:

To fix up your problem RE using Evolution filters, would it not be possible to set up filters containing two rules, one to differentiate email being sent to yourself or your girlfriend, and another rule that filters the "from" field.

ie: If the "To" field contains [email]girlfriend@whatever.com[/email]
And "From" field = [email]barry@whatever.com[/email]
Then move email to folder inbox/girlfriend/barry

You'd have to make a filter for every friend folder you have in your inbox.

Hope this is of help.

---

