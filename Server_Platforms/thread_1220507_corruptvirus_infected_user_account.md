---
title: "corrupt/virus infected user account"
date: 2009-07-22
forum: Server Platforms
---

### Post by jeralyne on 2009-07-22
we are using postfix and dovecot for our email server and outlook express as a medium for reading mails. one of the users encountered an error in outlook which says "Message Could not be displayed - Outlook Express Encountered an Unexpected Problem while Displaying this message. Check your Computer for low Memory or Low Disk Space and try again.". same error appears if the user uses another machine. an advise that the user's mail account is either corrupted or infected with a virus. the solution offered is to create a new user, copy all the mails (inbox,outbox,drafts,sent, etc.) to the new user's folder, make sure that the new user is working fine, delete the old user and finally to rename the new user to the old user's name. my problem is, after copying all the old user's files by cp -R command outlook express says something about unable to locate the inbox. what can i do to fix this? tia

---

### Post by enz1m3 on 2009-07-24
You probably have to rename the user's inbox directory in the config files (I don't know where they are for dovecot, but you can probably find them googling).

About the error, if the user is viewing on different machines, it's not a local virus, and it sure doesn't look like a virus of some sort on the server.

The corrupted email, it could be, but I hardly doubt it unless there was some human intervention (intentional or not), so the copying of the inbox wouldn't really work.

What do you get on /var/log/mail.log about that error?

Have you tried using thunderbird to access the account? when there's an error, it usually prints out something more useful than outlook.

---

### Post by jeralyne on 2009-07-26
I tried accessing the emails using Microsoft Outlook and it worked fine. But the user is more familiar with Outlook Express and wants to retain using it as email reader. If i have to access all the emails just so i can delete that suspicious email, how will i know that it will be the right email to delete? Or is there any other simpler way to solve since the user has more than 20 thousand important emails both in inbox and outbox and will take a lot of time to browser to look for the suspicious email? thanks again

---

### Post by LepeKaname on 2009-07-27
Does the client is accessing as POP3 or IMAP?

---

### Post by jeralyne on 2009-07-28
we have an imap setup.

---

### Post by windependence on 2009-07-28
I doubt it's "suspicious" at all. The likelyhood of a virus infecting a Linux machine while possible, is not something I have ever personally seen, and I have been in this biz since 1982. Most likely, the mail is corrupted and moving the entire mail store just because you think it's malicious is not something I would recommend. As another poster mentioned above, learn to read the mail logs. Your clue will most likely be in there and if it's a corrupt file, it will tell you exactly what file it is and you can delete it. Remember, Linux !=Windoze.  Linux is secure by design. Not that it can't be hacked like anything else but infected? I think not.

-Tim

---

### Post by jeralyne on 2009-07-28
i'm such a newbie at this. how can i filter the log for the specific account with corrupted email and showing older logs? the mail.log displays everything for all users and for the current day only. thanks for the patience in explaining.

---

### Post by LepeKaname on 2009-07-29
> the iexplorer gets stucked and it closes

Sorry but this is not a Windows Forum... or are you using wine?, otherwise I think your question is not at the right place.

---

### Post by enz1m3 on 2009-08-07
> **jeralyne said:**
> i'm such a newbie at this. how can i filter the log for the specific account with corrupted email and showing older logs? the mail.log displays everything for all users and for the current day only. thanks for the patience in explaining.

I think you should consider getting expert help (try your hosting company or someone here at the forums) as this is not as easy to explain and understand as you may think. You may have to pay for this help as it does require some time to identify the problem and it may not be fixable.

@LepeKaname

It's not a Windows forum but I think we could all contribute to help, no? No need to be rude, man.

---

### Post by windependence on 2009-08-08
@LepeKaname,

He's only using Windoze to read the mail. In order to survive and show alternatives to Windoze, we have to be able to integrate with it. I do Linux/Unix/BSD for a living and I can tell you Windoze is in EVERY client I have. We all have to live with it for quite some time. Helping him out gets him one step closer to Windependence. ;)

-Tim

---

### Post by jeralyne on 2009-08-10
thank you, guys.. i'm really a windows user ever since and still in the learning phase of understanding linux. i need all the help i can get.

---

