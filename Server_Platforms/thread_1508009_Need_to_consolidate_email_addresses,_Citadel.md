---
title: "Need to consolidate email addresses, Citadel"
date: 2010-06-12
forum: Server Platforms
---

### Post by volkswagner on 2010-06-12
Sorry I know this isn't an Ubuntu issue.

My problem stems from my Nokia N95 only allows two email addresses to retrieve email automatically.

I have a few email addresses I'd like to get notifications when I have new email.  I have one gmail account and several addresses from my domains, using Citadel as my mail server.  In Citadel I have used one user with multiple aliases.  Problem with the alias solution is when I send mail, the sender is always my main account.

I have tried setting up multiple users on Citadel, and add their address to my main account alias list.  This does not work as, the mail goes to the main user not the aliased user.

How can I have multiple address, forward or sent to one main account?  I can set up multiple send accounts on my phone and in evolution.

So, do I need to go back to Postfix/courier/SquirrelMail?  I believe this can be set up with aliases+forward in Postfix.

Is there another solution?  I briefly looked into Funambol, but it seems system requirments are even higher than Citadel.  I'd need to run Citadel and the Funambol on my VPS which is only 384MB RAM.

Thanks for taking the time.

Edit:  Duh, It's only easy if you know how.  After writing the post, a light bulb flickered.  The answer may reside with forwarding.  The option to forward in Citadel was not immediately visible.  I have now found how to forward in Citadel with sort/filter.  I'll mark solved it I'm happy with results.

Edit-2:  Yes, forwarding is what I needed.  Found simple how to for [Citadel]("http://www.citadel.org/doku.php/faq:everydayuse:how_do_i_automatically_forward_all_mail_to_a_remote_email_address_somewhere").

---

