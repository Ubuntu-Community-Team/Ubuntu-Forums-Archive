---
title: "Protocol fixes for email"
date: 2011-07-05
forum: The Cafe
---

### Post by ki4jgt on 2011-07-05
So, I've started this thread to discuss protocol fixes to email systems.

My fist idea is: Email tokens for email servers (to prevent spoofing)

When the sending server sends an email, it will attach a randomly generated alpha numeric sequence to the email. When the receiving server gets the email, it will give return the token to the sending server. If the sending server verifies that token, then the email was sent from that server, no spoofing allowed.

Any other ideas on how to fix email protocol?

EDIT: This is only a discussion enhancer, it is not intended to be real. Please reference ([http://sourceforge.net/projects/smashindex/files/E3%20Protocol/E3%20Protocol.txt/download](http://sourceforge.net/projects/smashindex/files/E3%20Protocol/E3%20Protocol.txt/download)) for an open email protocol.

---

### Post by Grenage on 2011-07-05
I'm not sure how that would help; with such a system, when would a token *not* be verified? ;)

There are various decent ideas out there, and I imagine that the reason they aren't implemented is backwards-compatibility.

---

### Post by ki4jgt on 2011-07-05
> **Grenage said:**
> I'm not sure how that would help; with such a system, when would a token *not* be verified? ;)

There are various decent ideas out there, and I imagine that the reason they aren't implemented is backwards-compatibility.

If the sending server didn't send the email, the token the receiving server gives to the sending server will be invalid. The receiving server in turn knows to trash the message.

EDIT: That is also true. Wonder if there is a way to built on this to make it backwards compatible.

---

### Post by Grenage on 2011-07-05
The sending server will always have sent the e-mail, it will have initiated the connection.  If you're talking about a post-delivery communication, then I imagine you expect the source to be derived from the domain name?  That in itself would cause various problems.

That would also, of course, not stop spam on the internet.  There are many compromised home (and business) machines, sending seemingly legitimate mail.

---

### Post by ki4jgt on 2011-07-05
What if the user was allowed to decide if they wanted the server to use tokens or not for their emails and the tokens were part of the email message? Then it would simply appear in the email somewhere (for servers which didn't know how to check tokens). If the server knew what a token was, it could check the original server and remove the token from the email (if the user requested the server to use tokens that is)

---

### Post by ki4jgt on 2011-07-05
> **Grenage said:**
> then I imagine you expect the source to be derived from the domain name?  That in itself would cause various problems.

That would also, of course, not stop spam on the internet.  There are many compromised home (and business) machines, sending seemingly legitimate mail.

That is what I was talking about. It would however stop spoofing wouldn't it? If said (problems) had solutions. Compromised businesses are the problem of the user, not of the email server hosting said user's email address. Or, in better phrasing (the email protocol in general)

---

### Post by Grenage on 2011-07-05
As an optional thing, it could be made to work.  Unfortunately in the case of things such as e-mail, the system is only as strong as the weakest link.  It would also be an easy way to DOS an e-mail system, but there are plenty of ways to do that anyway.

---

### Post by ki4jgt on 2011-07-05
> **Grenage said:**
> As an optional thing, it could be made to work.  Unfortunately in the case of things such as e-mail, the system is only as strong as the weakest link.  It would also be an easy way to DOS an e-mail system, but there are plenty of ways to do that anyway.

I just thought about that one. If one person sends 1000 emails (supposedly) from a server, the server's gonna get flooded with token verification requests. What if every server had a public gpg key, and sent all emails using the private one? Each server would keep an index of public keys, if they didn't have one, they would request it from the sending server. If they had already encountered that server, they wouldn't request it again.

EDIT: Until the key expired.

---

### Post by Bachstelze on 2011-07-05
The problem with that is of course mainly that not every domain provides an outgoing mail server, and even when they do, it is generally more convenient to just use your ISP's SMTP server to send mail with all your addresses.  Being able to send email with any address from any server is a feture, not a bug.  It it the recipent's responsibility to ensure that the sender is really who they claim to be, just like for snail mail where you can write any address on the envelope.

---

### Post by ki4jgt on 2011-07-05
> **Bachstelze said:**
> The problem with that is of course mainly that not every domain provides an outgoing mail server, and even when they do, it is generally more convenient to just use your ISP's SMTP server to send mail with all your addresses.  Being able to send email with any address from any server is a feture, not a bug.  It it the recipent's responsibility to ensure that the sender is really who they claim to be, just like for snail mail where you can write any address on the envelope.

Yes, but doesn't your ISP's outgoing server stamp the email header with it's own email address? But to reference what started this question

[http://www.hackforums.net/showthread.php?tid=1384923](http://www.hackforums.net/showthread.php?tid=1384923)

> Hey guys,

Just wanted to share a little story with you that happened very recently (today actually). I'm going into my senior year of high school, and because i am taking 4 Advanced Placement (AP) classes, i have been given an absolute ton of homework to do. So, because of this, i made a prank to hopefully catch a few of the less-competent kids in the class.

At the end of the school year, my future A.P. U.S. History teacher told us to write our email addresses down on a notepad so that he could give us our homework assignment online when he was ready.

Only a couple days ago, he sent that email telling us some basic info as to what we had to do for homework. I quickly checked the email and saw that he sent the message en-masse using that list of addresses. Needless to say, i grabbed the page source of the message and started writing a script that would parse through it for that list and send a message using a spoofed email address.

Here's my script:
[CODE]***PYTHON SCRIPT NOT SHOWN TO STAY IN CHECK WITH FORUM POLICIES***[CODE]

I'm hoping that i can catch at least a few 'WTF???' from my classmates using this prank.
Btw, i blocked out any pieces of personal identification when pasting the script.


The email sent, is as follows:
message = """From: ?? <??@gmail.com>
Subject: Update on A.P. U.S. History Homework

Hello future students of the A.P. U.S. History Class (2011-2012) !

I hope you are having a great summer vacation! I have a very special update to make to you all.

I have just talked to ??, the librarian, about your textbooks:
    --Out of Many
    --People's History of the United States by Howard Zinn.

Unfortunately, these textbooks may not be ready by tomorrow(6/16) or Friday(6/17).
Because of the setback, I have decided that there will not be ANY SUMMER HOMEWORK!

Thanks for your attention and have a great week.

Sincerely,
Mr.??
"""

---

### Post by Bachstelze on 2011-07-05
> **ki4jgt said:**
> Yes, but doesn't your ISP's outgoing server stamp the email header with it's own email address?

"its own email address"?  A server doesn't have an email address. ;)  It has a hostname, and yes, it adds its hostname to the headers (it also adds the IP address from which I connected to it).  So if the recipient has doubts about whether the email is legit, they can send a mail to the sender address asking "is this your IP?"

---

### Post by jhonan on 2011-07-05
This is sounding a lot like Sender Policy Framework [http://www.openspf.org/](http://www.openspf.org/)

Minimizing spam and fraudulent emails will need a multi-faceted approach; Technical, legal, and social.

For example, the fraudulent email to the students that you quote above would be better prevented under the 'legal' aspect. If the college had a policy in place to punish or expel students who attempt to gain academic advantage by impersonating a lecturer, then this would deter this kind of email in the first place.

---

### Post by ki4jgt on 2011-07-05
> **jhonan said:**
> This is sounding a lot like Sender Policy Framework [http://www.openspf.org/](http://www.openspf.org/)

Minimizing spam and fraudulent emails will need a multi-faceted approach; Technical, legal, and social.

For example, the fraudulent email to the students that you quote above would be better prevented under the 'legal' aspect. If the college had a policy in place to punish or expel students who attempt to gain academic advantage by impersonating a lecturer, then this would deter this kind of email in the first place.

The professor actually threatened to boot the student from the class if he ever found him :-)

---

### Post by ki4jgt on 2011-07-05
> **Bachstelze said:**
> "its own email address"?  A server doesn't have an email address. ;)  It has a hostname, and yes, it adds its hostname to the headers (it also adds the IP address from which I connected to it).  So if the recipient has doubts about whether the email is legit, they can send a mail to the sender address asking "is this your IP?"

This is true, but no one wants to bother with that. Especially since most email clients don't bother to show the user the IP anyway, that would mean the user would have to check the IP of every email got personally.

---

### Post by Bachstelze on 2011-07-05
> **ki4jgt said:**
> This is true, but no one wants to bother with that.

Then the problem is with people, not with the protocol.

> **ki4jgt said:**
> Especially since most email clients don't bother to show the user the IP anyway, that would mean the user would have to check the IP of every email got personally.

Not really.  I don't know about you, but for the most part, wen I get an email, I exoected to get it and had an idea  of what would be in there.  Whenever you receive an unexpected email, you should turn your brains on ans ask yourself whether it is legit or not.  In the case you descriped, the email should have flashed a red light in the mind of any sensible person.

---

### Post by ki4jgt on 2011-07-05
> **Bachstelze said:**
> Then the problem is with people, not with the protocol.



Not really.  I don't know about you, but for the most part, wen I get an email, I exoected to get it and had an idea  of what would be in there.  Whenever you receive an unexpected email, you should turn your brains on ans ask yourself whether it is legit or not.  In the case you descriped, the email should have flashed a red light in the mind of any sensible person.

Though it should have. . . It doesn't with a lot of people. Especially with computer noobs, (Older users, young children, computer illiterate people in general)

EDIT: and how does this work exactly? In the above mentioned example putting an address on the snail mail, the snail mail is routed through the post office, which tells the reader which city the mail came from and some post offices are considering marking letters with invisible ink for individual markings.

---

### Post by Bachstelze on 2011-07-05
> **ki4jgt said:**
> Though it should have. . . It doesn't with a lot of people. Especially with computer noobs, (Older users, young children, computer illiterate people in general)

Not a reson to change the protocol.  Educate people, discipline the guy, or do whatever you want, but keep your hands off my protocol!

---

### Post by ki4jgt on 2011-07-05
> **Bachstelze said:**
> Not a reson to change the protocol.  Educate people, discipline the guy, or do whatever you want, but keep your hands off my protocol!

;-) ROTFLMBO ;-) Wow, someone wants "Precious" pretty badly. (LOTR)

It wouldn't be a change of your protocol. It would be a change of the user's protocol who chose to do enable it through their email server. You would receive your email as normal if you didn't enable it.

---

### Post by Bachstelze on 2011-07-05
> **ki4jgt said:**
> ;-) ROTFLMBO ;-) Wow, someone wants "Precious" pretty badly. (LOTR)

It wouldn't be a change of your protocol. It would be a change of the user's protocol who chose to do enable it through their email server. You would receive your email as normal if you didn't enable it.

Then as jhonan pointed out, several things exist that do just that...

---

### Post by ki4jgt on 2011-07-05
> **Bachstelze said:**
> Then as jhonan pointed out, several things exist that do just that...

I get that:
> Minimizing spam and fraudulent emails will need a multi-faceted approach; Technical, legal, and social.


He's right :-) but he just pointed out the legal side of the problem. This is the technical one. The social of course will have to be figured out by someone else.

---

### Post by jhonan on 2011-07-05
This part:

> **jhonan said:**
> This is sounding a lot like Sender Policy Framework [http://www.openspf.org/](http://www.openspf.org/)

> Even more precisely, *SPFv1* allows the owner of a  domain to specify their mail sending policy, e.g. which mail servers  they use to send mail from their domain.  The technology requires two  sides to play together: *(1) the domain owner publishes* this information in an *SPF* record in the domain's [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") [zone]("http://en.wikipedia.org/wiki/DNS_zone"), and when someone else's mail server receives a message claiming to come from that domain, then *(2) the receiving server can check*  whether the message complies with the domain's stated policy.  If,  e.g., the message comes from an unknown server, it can be considered a  fake.

---

### Post by ki4jgt on 2011-07-25
An open email protocol has been added to the initial post. Please reference it, to get a general idea as to how it would work.

---

### Post by koenn on 2011-07-25
> **ki4jgt said:**
> An open email protocol has been added to the initial post. Please reference it, to get a general idea as to how it would work.

I had a look at your "protocol". It needs work, on several levels :

1- 
you're apparently aiming to replace (E)SMTP, POP3, IMAP and possibly LMTP.
Here are some specs for those : since you're going to replace them, you might want to know what problmes they solved so you can develop your own solutions in your alternative protocol:

[http://tools.ietf.org/html/rfc5321](http://tools.ietf.org/html/rfc5321)
[http://tools.ietf.org/html/rfc2033](http://tools.ietf.org/html/rfc2033)
[http://tools.ietf.org/html/rfc3501](http://tools.ietf.org/html/rfc3501)

this will also give you some background knowledge so you can replace the wording "original email protocol" by a more accurate and precise indication. There haven been several other (e-)mail protocols before SMTP, so "original" isn't even correct.


2- If you're considering compatibility with SMTP et.al. your protocol should be clear, in detail,  about how an E2 server should behave when it talks to an SMTP server, amongst others. 

3- since you're planning to solve the problem of address spoofing, you should, imo, study the current available solutions/attempts to tackle that problem (reverse DNS lookup, SPF, several sender signing schemes, ...), find out their flaws, and make sure your protocol fixes or works around those flaws. Otherwise you're just reinventing the wheel, poorly. 


4- as an aside :  you should also have a plan on how to get this protocol implemented and widely adopted. Unless, of course, this is just an intellectual exercise. Or a pipe dream. 


Have fun.

---

### Post by ki4jgt on 2011-07-25
> **koenn said:**
> I had a look at your "protocol". It needs work, on several levels :

1- 
you're apparently aiming to replace (E)SMTP, POP3, IMAP and possibly LMTP.
Here are some specs for those : since you're going to replace them, you might want to know what problmes they solved so you can develop your own solutions in your alternative protocol:

[http://tools.ietf.org/html/rfc5321](http://tools.ietf.org/html/rfc5321)
[http://tools.ietf.org/html/rfc2033](http://tools.ietf.org/html/rfc2033)
[http://tools.ietf.org/html/rfc3501](http://tools.ietf.org/html/rfc3501)

this will also give you some background knowledge so you can replace the wording "original email protocol" by a more accurate and precise indication. There haven been several other (e-)mail protocols before SMTP, so "original" isn't even correct.


2- If you're considering compatibility with SMTP et.al. your protocol should be clear, in detail,  about how an E2 server should behave when it talks to an SMTP server, amongst others. 

3- since you're planning to solve the problem of address spoofing, you should, imo, study the current available solutions/attempts to tackle that problem (reverse DNS lookup, SPF, several sender signing schemes, ...), find out their flaws, and make sure your protocol fixes or works around those flaws. Otherwise you're just reinventing the wheel, poorly. 


4- as an aside :  you should also have a plan on how to get this protocol implemented and widely adopted. Unless, of course, this is just an intellectual exercise. Or a pipe dream. 


Have fun.

As stated by the document, (currently) it's just an intellectual exercise. I believe it handles the problems of email spoofing very well.

As stated by the document also, it does not intend to replace original email systems. That's NOT the goal. The goal is to provide an alternative. That's why the ":" is used. There are certain functionalities available to other email protocols which this one handles differently. Lastly, I've only been working on this for one night. Give me a break :-) and if you have suggestions please join in. It's all in the name of fun, and intellectual exercise.

---

### Post by koenn on 2011-07-26
> **ki4jgt said:**
> As stated by the document, (currently) it's just an intellectual exercise. I believe it handles the problems of email spoofing very well.

IMO this sort of intellectual exercise is more fun if you try to make it realistic. The closer to reality you try to bring it, the more you'll find interesting problems to solve. 
So far what you have is just a reasonably good idea ... and then it stops. 

> **ki4jgt said:**
> 
As stated by the document also, it does not intend to replace original email systems. That's NOT the goal. The goal is to provide an alternative. That's why the ":" is used. There are certain functionalities available to other email protocols which this one handles differently. 
The message format and initial dialogue between server and client, as you specified them, are not compatible with SMTP. So you're either planning to replace SMTP, or work alongside it. If you plan to work alongside it in stead of replace it, your protocol needs to address interoperability with SMTP, or provide a mechanism so that clients/users know in advance which protocol the mail server of their addressees are using.
(That's the sort of interesting problems you encounter when you make things 'more real')


> **ki4jgt said:**
> 
Lastly, I've only been working on this for one night. Give me a break :-) and if you have suggestions please join in. It's all in the name of fun, and intellectual exercise.

If I would set out to fix the problem of email address spoofing, i'd probably look into extending SMTP rather than starting from scratch (X-headers offer an interesting entry point there), if only to more easily manage interoperability issues, and (as mentioned in my previous post) I'd look at current attempts, analyse their shortcomings, and take if from there. 
Standing on the shoulders of giants, and all that. Starting from scratch and trial-and-error my way through all the errors that someone else already made before me is not [always] my idea of fun.

---

