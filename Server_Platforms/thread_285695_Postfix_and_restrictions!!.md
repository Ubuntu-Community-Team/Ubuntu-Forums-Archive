---
title: "Postfix and restrictions!!"
date: 2006-10-27
forum: Server Platforms
---

### Post by epilas on 2006-10-27
Hello.What i would like to do is to add some recipient number restrictions to a mail server running postfix.I know i can restrict for all users the recipient number to  my desired number.However i want to see if i can do something more with all that.These are my questions:

1. Can i use seperate recipient number restriction for each user? For example user1 can send to 10 recipients and user2 to 5 etc.

2. If i restrict the number of recipients a user can send to in lets say 3 and i have a mail alias which translates into 5 addresses will the user with the 3 recipients permission  be allowed to send to that alias?

I really couldn't find satisfying info over the internet so i would like anybody that has a clue of all that to answer me because i really need to know if the things i ask are possible or not.I really dont care about how to do them right now,but i need to know if i am able to do these things.

Thanks very much in advance to anyone who will help.

---

### Post by kidders on 2006-10-27
Hi there,

I'm very doubtful about this. Your question is very unusual :-( I'd be very pleased if someone posted a message contradicting me, but I don't think postfix (or any other SMTP server, for that matter) would be capable of that degree of user-level control. There *is* something that might be worth a shot, but I'd be surprised if it worked. Here goes...

I wonder what would happen if you used regular expression pattern matching to detect a message with too many recipients being sent by a restricted user, and reject it. I seem to remember something about Postfix being reluctant to match patterns spread over more than one line though, so this may not cooperate.

The only realistic option I can see (and again, I'd be very pleased to be contradicted!) would be to pass most (if not all) of your mail through, say, a shell script that could do a more in-depth analysis of the message before accepting it. This would be a *total* performance killer, but at least it would probably work.

I hope that helps.

---

### Post by epilas on 2006-10-27
Thank you very much. To tell you the truth i kinda expected this answer. If anyone has any other opinion it really would be helpful (and surprising too).

---

### Post by kidders on 2006-10-27
No problem :-)

Can I ask the purpose of the postfix server? You see, depending on the mail volume, passing it all through a script may in fact be quite a reasonable thing to do. You'd still have to be a little cautious of DoS attack vulnerability though.

---

### Post by MJN on 2006-10-27
Out of interest can I ask why you want to do this? Are your users spammers or something?

---

### Post by kidders on 2006-10-27
> **MJN said:**
> Out of interest can I ask why you want to do this? Are your users spammers or something?

I've been itching to ask this too, hehe.

---

### Post by epilas on 2006-10-28
Well they aint spammers but if you got 3500 users and they send funny videos,mp3's etc to each other and you cannot cut video attachments then you got to do something else.Well now they can send to whoever they want and they send mail to 15 -30 people each. Thats why i wanna cut the number.I am working for bandwidth!!!!!:D

---

### Post by epilas on 2006-10-28
Oh and the mail server is already there!!!Thats the postfix reason.

---

### Post by MJN on 2006-10-28
If your users want to send to a hundred people they will - even if it means sending 10 seperate messages to 10 at a time.

---

### Post by kidders on 2006-10-28
I'm with MJN on this one :-( If your users really want to circumvent a recipient count restriction, they will. Depending on your organisation, there might be a few alternatives though.

[LIST]
[*]You could block video attachments. I presume you have spam filtration and anti-virus software running ... somewhere along the line, you should be able to intercept videos.
[*]You could introduce bandwidth quotas for certain users. If your in, say, a school, you could automatically lock out students who exceed their monthly quota, until they approach an administrator to be unlocked.
[/LIST]

Neither of these ideas is without flaws, and neither may be much good in your situation, but I thought I'd suggest them anyway. If we can find a strategy that works for you, we'll happily help you implement it :-)

---

### Post by epilas on 2006-10-30
Thanks a lot guys.You've really been helpful and kind.The project was cancelled from the company so i dont really need it anymore.Thanks again for all your help.

---

