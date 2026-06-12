---
title: "Default email client on 13.04 (Raring Ringtail)"
date: 2012-10-23
forum: Ubuntu Development Version
---

### Post by Repgahroll on 2012-10-23
Hey there.

Now that's confirmed Mozilla won't support Thunderbird after the second half of 2013, what is going to be the default email client on Ubuntu 13.04?

I bet it's gonna be Evolution again, because there's no alternative. I don't think they're going to ship TB.

What do you think? Are there any official words on this?

---

### Post by Sean Dewlin on 2012-10-23
I use Sylpheed and I think it's a wonderful mail client.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
> **Repgahroll said:**
> Hey there.

Now that's confirmed Mozilla won't support Thunderbird after the second half of 2013, what is going to be the default email client on Ubuntu 13.04?

I bet it's gonna be Evolution again, because there's no alternative. I don't think they're going to ship TB.

What do you think? Are there any official words on this?
source?
from what i can find, they are switching to security/stability updates not so much on feature updates

---

### Post by oldos2er on 2012-10-23
Moved to Ubuntu +1 (Raring Ringtail).

---

### Post by tista on 2012-10-24
> **Repgahroll said:**
> Hey there.

Now that's confirmed Mozilla won't support Thunderbird after the second half of 2013, what is going to be the default email client on Ubuntu 13.04?

I bet it's gonna be Evolution again, because there's no alternative. I don't think they're going to ship TB.

What do you think? Are there any official words on this?

Hi Repgahroll,

Evolution +1.
Then we have to concern that evolution would be needed in Gnome3 environments in most cases, since gnome-contacts, calendars and mails are surely depended on it even in Gnome-Shell... Well known, Google-Calendar could be useful with evolution extension too.

So anyway we might need to include evolution into our main repository in the future like Raring as well. I'm not sure how many people may or may not like evolution because evolution is now "personal information suite", so someone would not need such benefits as a local mail-client.

Personally, I'm enough using Balsa and Sylpheed... And now there's an only way to use evolution to setup local address-book working with gnome-shell easily...

Best Regards,
Tista

---

### Post by serdotlinecho on 2012-10-24
From Mozilla blog:

[http://blog.mozilla.org/beyond-the-code/2012/07/09/about-the-future-of-thunderbird/](http://blog.mozilla.org/beyond-the-code/2012/07/09/about-the-future-of-thunderbird/)

---

### Post by grahammechanical on 2012-10-24
> Are there any official words on this?

You are asking for official words from a community forum? Wrong place. You give us FUD and expect official words in exchange.

This is where official words are discussed in Ubuntu:

[http://uds.ubuntu.com/event/]("http://uds.ubuntu.com/event/")

I do not think there is any need to discuss this matter next week because of this statement by the managing director of Thunderbird:

> We have a solid plan to support Thunderbird until the second half of 2013 and are discussing how we support it beyond that date. 

Evolution is in the 12.10 Software Centre. If anything changes it will be that there will not be a default email client. It will be user choice.

---

### Post by superhick on 2012-10-25
I hope they invest some time and include geary: [http://yorba.org/geary/](http://yorba.org/geary/)
compared to thunderbird it is really fast, however still missing some basic features like multiple accounts, preferences gui etc.

---

### Post by philinux on 2012-10-25
We'll have to wait for the outcome of the UDS.

---

### Post by mr john on 2012-10-26
If they go back to Evolution they really need to make it more beautiful. The GUI is very ugly compared to Outlook and other mail clients. Better exchange & global address book support would also help many businesses which are thinking about switching to Ubuntu.

But really, the GUI needs tidied up first.

I personally don't think it's a good idea to go forward with a client that we now know is minimizing development. There's not FUD going on here, just people being prudent in future planning. It makes perfect sense to start looking at other alternatives right now. Believe it or not some decisions do actually get made outside of the UDS ;-)

---

### Post by cariboo on 2012-10-26
I'm not sure why anyone thinks that mozilla should keep developing Thunderbird, it's an email client, and it does it's job quite well. 

I'm perfectly happy with the way it works now. As far as I'm concerned all Thunderbird need is bug fixes. What more does it need?

---

### Post by mr john on 2012-10-26
It's still missing alot of functionality. Full Exchange capability etc. For you it might be finished, but not for everyone. I would expect the default email client in Ubuntu to have the capability of plugging into corporate exchange-based networks. If you're only using pop or imap then that's not a problem, but a large number of business users need more capability to be compatible with existing corporate networks.

---

### Post by cariboo on 2012-10-26
Ubuntu is designed as a consumer operating system, for  corporate use, the [Ubuntu Business Remix]("http://www.ubuntu.com/business/desktop/remix") would be a better fit.

For the regular user in a non-corporate setting, Thunderbird does everything most of us need. 

I'm not sure about Apple, but Windows doesn't even have an email client in a default installation. You have to install either Windows Live Mail or Outlook, depending on your needs.

---

### Post by MacUntu on 2012-10-26
What's wrong with davmail?

---

### Post by grahammechanical on 2012-10-27
The way things are going:

[https://wiki.ubuntu.com/Nexus7/KnownIssues]("https://wiki.ubuntu.com/Nexus7/KnownIssues")

> LibreOffice and Thunderbird are removed in order to decrease the image size.

Regards.

---

### Post by cariboo on 2012-10-27
> **grahammechanical said:**
> The way things are going:

[https://wiki.ubuntu.com/Nexus7/KnownIssues]("https://wiki.ubuntu.com/Nexus7/KnownIssues")



Regards.

That's concerning Ubuntu on a Nexus 7" tablet, which is just in the really early stages of development. A full Ubuntu install takes about 4GiB+, and those devices only have 16/32GiB of internal storage, so I can see paring down the install size, by removing LibreOffice and Thunderbird.

---

### Post by VinDSL on 2012-10-27
> **cariboo907 said:**
> I'm perfectly happy with the way it works now. As far as I'm concerned all Thunderbird need is bug fixes.[...]
Agreed!


> **cariboo907 said:**
> What more does it need?
A calendar, task manager, and a good "skinning" always helps.  LoL!  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-oct-2012-1.png")[/INDENT]

---

### Post by ventrical on 2012-10-27
> **cariboo907 said:**
> Ubuntu is designed as a consumer operating system, for  corporate use, the [Ubuntu Business Remix]("http://www.ubuntu.com/business/desktop/remix") would be a better fit.

For the regular user in a non-corporate setting, Thunderbird does everything most of us need. 

I'm not sure about Apple, but Windows doesn't even have an email client in a default installation. You have to install either Windows Live Mail or Outlook, depending on your needs.

The Windows Live Mail and no default Outlook Express was a sticking point for a lot of old timers.

---

### Post by cariboo on 2012-10-27
> **ventrical said:**
> The Windows Live Mail and no default Outlook Express was a sticking point for a lot of old timers.

Actually I just bought my Mom a Gateway laptop for a ridiculously good deal, and it had Windows Live pre-installed, so the only things I had to do was remove the Office 2010 trial and Norton Security trial, and install MS Security Essentials.

---

### Post by VinDSL on 2012-10-28
> **cariboo907 said:**
> Actually I just bought my Mom a Gateway laptop for a ridiculously good deal, and it had Windows Live pre-installed, so the only things I had to do was remove the Office 2010 trial and Norton Security trial, and install MS Security Essentials.
Don't mean to be a sourpuss, but...

A friend of mine bought a high-end HP laptop @ Best Buys, a few years ago -- fanciest laptop I've ever seen -- glowed like a pinball machine, when it was running -- backlit keyboard, and all that sort of stuff.  Most have cost a fortune...

When the Norton trial version expired, she started getting pop-ups about having to pay, by such n' such date, if she wanted to keep her data secure, blah, blah, blah.  I told her to remove Norton, in the software manager (whatever MS calls it), and install the free version of Avast!

A few months later, she couldn't open emails, log into her bank accounts, and so forth and so on. Best Buys couldn't figure it out, nor the IT department at the place she works.  She was heart-broken, and asked me if she should buy a new laptop.

I told her, I'd take a look at it, if she didn't mind me keeping her laptop for a week or so...

After 2 days of fishing around, I traced it down to remnants of the Norton Security Trial Suite.

Long story short:  That #$@! thing is like a virus!  It injects itself into the core system DLL files.  Uninstalling Norton doesn't return these files to their original state.  

I'm afraid, you'll need to go to their website and download a very obscure, well hidden, utility to fully remove Norton from your mom's new laptop, and patch the system.

**EDIT**

Found it!  Do  search for "SymNRT".

There are 17 versions running around.  Choose wisely...  ;)

---

### Post by cariboo on 2012-10-28
> **VinDSL said:**
> Don't mean to be a sourpuss, but...

A friend of mine bought a high-end HP laptop @ Best Buys, a few years ago -- fanciest laptop I've ever seen -- glowed like a pinball machine, when it was running -- backlit keyboard, and all that sort of stuff.  Most have cost a fortune...

When the Norton trial version expired, she started getting pop-ups about having to pay, by such n' such date, if she wanted to keep her data secure, blah, blah, blah.  I told her to remove Norton, in the software manager (whatever MS calls it), and install the free version of Avast!

A few months later, she couldn't open emails, log into her bank accounts, and so forth and so on. Best Buys couldn't figure it out, nor the IT department at the place she works.  She was heart-broken, and asked me if she should buy a new laptop.

I told her, I'd take a look at it, if she didn't mind me keeping her laptop for a week or so...

After 2 days of fishing around, I traced it down to remnants of the Norton Security Trial Suite.

Long story short:  That #$@! thing is like a virus!  It injects itself into the core system DLL files.  Uninstalling Norton doesn't return these files to their original state.  

I'm afraid, you'll need to go to their website and download a very obscure, well hidden, utility to fully remove Norton from your mom's new laptop, and patch the system.

**EDIT**

Found it!  Do  search for "SymNRT".

There are 17 versions running around.  Choose wisely...  ;)

Already did it. :-D I've removed Norton often enough that I know to search for the right removal tool, as using the uninstall option in Windows doesn't remove it completely.

To help matters, don't even enable the trial version. As an experiment, I didn't enable Norton on my Dad's laptop, and just used the uninstall option, so far a year later it still hasn't shown it's ugly head.

---

### Post by ventrical on 2012-10-28
> **VinDSL said:**
> Don't mean to be a sourpuss, but...

A friend of mine bought a high-end HP laptop @ Best Buys, a few years ago -- fanciest laptop I've ever seen -- glowed like a pinball machine, when it was running -- backlit keyboard, and all that sort of stuff.  Most have cost a fortune...

When the Norton trial version expired, she started getting pop-ups about having to pay, by such n' such date, if she wanted to keep her data secure, blah, blah, blah.  I told her to remove Norton, in the software manager (whatever MS calls it), and install the free version of Avast!

A few months later, she couldn't open emails, log into her bank accounts, and so forth and so on. Best Buys couldn't figure it out, nor the IT department at the place she works.  She was heart-broken, and asked me if she should buy a new laptop.

I told her, I'd take a look at it, if she didn't mind me keeping her laptop for a week or so...

After 2 days of fishing around, I traced it down to remnants of the Norton Security Trial Suite.

Long story short:  That #$@! thing is like a virus!  It injects itself into the core system DLL files.  Uninstalling Norton doesn't return these files to their original state.  

I'm afraid, you'll need to go to their website and download a very obscure, well hidden, utility to fully remove Norton from your mom's new laptop, and patch the system.

**EDIT**

Found it!  Do  search for "SymNRT".

There are 17 versions running around.  Choose wisely...  ;)

I have done this so many times I think I could do it in the dark! :) lol.

Honestly VinDSL , I have had exactly the same problem with so many clients. The tough part is convincing clients to convert to Ubutnu. When they do I get the Ooohhhhss and Ahhhhs ! :) ha.

btw .. I just installed the Comodo CAV for Linux Debian per (Raring Ringtail). Then I did an EICAR test.  It detected ok but there is something wrong with the guard. However, to stay on topic, they have a real-time scanner-guard for  e-mail and I was going to experiment with that using Thunderbird app.

---

### Post by ventrical on 2012-10-28
> **cariboo907 said:**
> Actually I just bought my Mom a Gateway laptop for a ridiculously good deal, and it had Windows Live pre-installed, so the only things I had to do was remove the Office 2010 trial and Norton Security trial, and install MS Security Essentials.

They are practically giving away ASUS quad cores at Factory Direct with no OS.  Just waitng for Ubuntu ! :)

back a  few years ago it was always tough to get the Norton  Removal tool to work.  It was one of those 'regedit' scenarios that could take a whole 5 hour session.

---

### Post by zika on 2012-10-28
> **ventrical said:**
> They are practically giving away ASUS quad cores at Factory Direct with no OSCould You be more precise, please. Thank You.
P.S. I think I've found what You've meant...

---

### Post by screaminj3sus on 2012-10-30
Can we stop with the silly thunderbird fud, thunderbird's development isn't going to magically stop, people misunderstood that announcement.

---

