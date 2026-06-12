---
title: "E mail"
date: 2011-03-18
forum: Security
---

### Post by spiky001 on 2011-03-18
I have a little issue I would like some help with. I received a suspect E mail from paypal which I reported to them, I did'nt click on anything in the E mail. The Question I am asking is there any way that some one could get in to my email client Thunderbird or Firefox. When I used thunderbird to report the e mail I received  a problem  reporting that my email couldn,t be sent due to AOL smpt not excepting email because of ssl encrpyption. I checked the settings for the account all seemed ok ssl was still marked.
 Also while I was on the internet yesterday I got the popup regarding did I want to save a "file" I canceled as I didn,t click anything to download anything.

---

### Post by SeijiSensei on 2011-03-18
First, how did you know it was from PayPal?  The From address in any email can easily be forged.  The only way to know if it came from PayPal is if it was sent from one of their servers.  The way to determine that is to look at the complete headers of the email in question.

In Thunderbird, you can select View > Message Source to see the complete message in plain text with all headers included.  A legitimate message will contain a "Received" header that looks something like this:

```
Received: from outbound2.den.paypal.com(216.113.188.112), claiming to be "outbound1.den.paypal.com" via SMTP by mail.example.com, id smtpdUSwsx0; Fri Mar 11 10:34:42 2011
```

The server may be different, but they'll always be in the paypal.com domain.  Any message claiming to be from PayPal but not sent from a mail server in the paypal.com domain is a scam.

That said, simply forwarding a copy of the message to PayPal shouldn't have put you at risk.  Even opening an attachment probably wouldn't compromise your system if it's running Linux.  

However, if you're going to report potential scams, you need to send the entire message with all the headers intact.  Essentially this means viewing the Message Source, then copying and pasting it into the email you're sending off.  I'll just mention that such notices rarely matter to places like PayPal because there are literally thousands, if not millions, of scam messages sent each day that forge PayPal's domain.

Companies will never ask you to fix your account information or password via an email message.  A common scam is to send a message with a link that appears to take the victims to a page where they can update their account information.  No legitimate company will ever request that you make such a change by email.  Also it's often a giveaway that the scammer's form is hosted on some random server, not for instance, on a server in the paypal.com domain.

---

### Post by spiky001 on 2011-03-19
Thks for the reply I was worried as this is the 1st time this has happened to me, Yes I am using Ubuntu and I do read a lot in the forums which dose help to put my mind at rest. Just 1 thing if I was to reinstall system Would the reinstall, renew update firefox and thunderbird I do have a seperate home partition ( The reason for reinstall I,m on 9.10 ) Dose stuff get stored in home partition I mean will the folders be updated as nessecary  in home

---

### Post by SeijiSensei on 2011-03-19
> **spiky001 said:**
> Thks for the reply I was worried as this is the 1st time this has happened to me, Yes I am using Ubuntu and I do read a lot in the forums which dose help to put my mind at rest. Just 1 thing if I was to reinstall system Would the reinstall, renew update firefox and thunderbird I do have a seperate home partition ( The reason for reinstall I,m on 9.10 ) Dose stuff get stored in home partition I mean will the folders be updated as nessecary  in home

If you just want to start Firefox with a new profile, you can try this:

```

cd ~/.mozilla
mv firefox firefox.old

```

Then restart Firefox.  It will build a new profile.  You may want to import your bookmarks, which you can do by choosing "Organize Bookmarks" and using the Import tool.  Look in the firefox.old directory and find the "bookmarkbackups" directory.  Import the most recent .json file you find there.

---

