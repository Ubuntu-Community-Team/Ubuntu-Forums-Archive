---
title: "Anyone still using a text-based email client as primary client?"
date: 2012-03-27
forum: The Cafe
---

### Post by samalex on 2012-03-27
Just curious, is anyone still using a text based email client like GNU Emacs, Pine, Alpine, or similar as their primary email client?  I used Pine almost exclusively until about 5 years ago, and though I still have Alpine setup to connect to my Gmail account I've found myself using gmail.com most of the time though I'm seriously thinking of going back to Alpine via SSH.

So just curious of how many people, if any, still use a text-based email client.

---

### Post by Lucradia on 2012-03-27
Nope, and never have actually. I use GMail via Web. I used to use yahoo mail via the web a few years back.

---

### Post by chamber on 2012-03-27
I use Mutt and love it.

---

### Post by QIII on 2012-03-27
What's email?

---

### Post by Toz on 2012-03-27
I still access one of my email accounts with alpine.

---

### Post by jonathonblake on 2012-03-27
> **samalex said:**
> thinking of going back to Alpine via SSH.

Can procmail be configured to work with that setup on an Ubuntu desktop?  If so, I might switch to it. 

The sole reason I'm using Thunderbird, is that it almost works as an email client, unlike the other GUI email clients for *Nix, which don't work at all.

jonathon

---

### Post by drumsticks on 2012-03-27
I have offlineimap download (and sync) my emails locally, then use notmuch with an emacs interface to read/reply.

I hate webmail because I have to suffer network latency for every single email action.  With my setup, everything is local and fast, let offlineimap (or any other caching email client) deal with the network latency.

---

### Post by BeRoot ReBoot on 2012-03-27
If it can be done in Emacs, I try to do it in Emacs. So yes, definitely.

---

### Post by samalex on 2012-03-28
> **chamber said:**
> I use Mutt and love it.

I've never used Mutt, but I might have to give it a shake.  Pine was the standard client when I was in college during the 90's so that's what I learned, plus I still use pico for most things which is the default editor of Pine.

> **BeRoot ReBoot said:**
> If it can be done in Emacs, I try to do it in Emacs. So yes, definitely.

I've tried more then a few times to get into Emacs because I've heard it's like the most amazing thing since shell itself, but I just never could get into it.  I need to give it another shake, so any pointers?

---

### Post by spynappels on 2012-03-28
I use Mutt on one of my machines, using imap. I don't use it exclusively, but I do use it a lot.

---

### Post by BeRoot ReBoot on 2012-03-28
> **samalex said:**
> I've tried more then a few times to get into Emacs because I've heard it's like the most amazing thing since shell itself, but I just never could get into it.  I need to give it another shake, so any pointers?

Hold C-M-S and spell out your name. You'll either crash it horribly or discover a dozen new and interesting features.

Or, you know, just use the built-in tutorial.

---

### Post by SeijiSensei on 2012-03-28
> **jonathonblake said:**
> Can procmail be configured to work with that setup on an Ubuntu desktop?  If so, I might switch to it.

Procmail is a server-side solution.  You could cobble together a client implementation using fetchmail to get the mail from the server, a local MTA like sendmail or Postfix to handle the messages fetchmail obtains, and procmail as the local mail delivery agent.  Basically you'd be creating a small mail server on your client.

I use alpine from time to time for administration.  I get root privileges on the server, su to the username of the account having problems, and run alpine.  I especially like being able to mark quickly messages by date and move them to another folder or delete them entirely.  Alpine is a very powerful client and a useful tool for any mail administrator.

---

### Post by andrew.46 on 2012-04-03
Another mutt user here :). I also run a guide demonstrating how to use mutt with Gmail:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

which according to the server logs is very popular, so there must still be a lot of users out there...

---

### Post by jonathonblake on 2012-04-04
> **SeijiSensei said:**
> Procmail is a server-side solution.  You could cobble together a client implementation using fetchmail to get the mail from the server, a local MTA like sendmail or Postfix to handle the messages fetchmail obtains, and procmail as the local mail delivery agent.  Basically you'd be creating a small mail server on your client.

Hmm. 

Back when I used RedHat 5.0, I used Pine and procmail on my desktop, retrieving email from my ISP. All I did was install those programs, and told Pine where to grab my email from. No cobbling required.

jonathon

---

### Post by SeijiSensei on 2012-04-04
I've used pine to read mail on remote servers, too.  You may have installed procmail, but I doubt you actually used it.  As I said, procmail is a "mail delivery agent" that is invoked by a "mail transfer agent" like sendmail or Postfix to handle local delivery.  It would not be invoked by pine.

---

### Post by Duncan J Murray on 2012-04-04
I also have used Mutt exclusively for the past 2 years (with Gmail).

It is fast fast fast!!!  The number of emails I have to sort out after getting back from holiday made me look into finding a quicker way of clearing out my inbox.

I use:

"j" and "k" to browse up and down the emails
"enter" opens the email
"i" returns you to the overview
"d" deletes the email (in either view)
"y" archives the email (also in either view)

just by tapping "d" and "y" I can sort out 200 emails in an unobscene length of time.

It is slightly less good with links and attachments.  long links seem to break up, and adding attachments is fiddly.  A small price to pay.

D

---

### Post by jonathonblake on 2012-04-05
> **SeijiSensei said:**
> I've used pine to read mail on remote servers, too.  You may have installed procmail, but I doubt you actually used it.  

Something was using the filters I created for procmail, becuase nothing was delivered into the inbox. Everything was dealt with according to the procmail rules I wrote.



jonathon

---

### Post by smtp on 2012-04-23
Yes - alpine and mailx. Depend of the boxes.

---

