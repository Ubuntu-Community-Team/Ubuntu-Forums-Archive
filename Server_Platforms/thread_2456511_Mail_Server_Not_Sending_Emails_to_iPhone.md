---
title: "Mail Server Not Sending Emails to iPhone"
date: 2021-01-12
forum: Server Platforms
---

### Post by Robert_Boutin on 2021-01-12
Hope this is an easy one.  I have a Ubuntu 16.04 mail server using the Perfect Server setup with Postfix, Apache, Amavis, Dovecot, Roundcube, ispConfig3.  In general it's worked great for years.  However, with one email account in particular, emails arrive in my inbox on the server but my iPhone only downloads perhaps 25% of the emails in that account.  The remainder sit there unread unless I go in through Roundcube and read them through the browser.

Any thoughts of where to look for the issue?  Or what information I can provide that might help?

Thanks

---

### Post by TheFu on 2021-01-13
Support for 16.04 ends in a few months.  Time to move to a new release?
Sorry, I don't have any specific knowledge. We don't have any apple stuff.

It is almost certainly a client-side problem.  Try deleting the account on the client, then re-setup the connection.
Might also try using a different email client. Saw an issue this week with an old android tablet that has the well-known SSL cert problem that just happened with LE certs. New android clients don't have the problem.

---

### Post by LHammonds on 2021-01-13
Is the 25% that can be seen the latest 25%?  Could it be a setting on the client that says only pull the last 4 days of email (for example)?

LHammonds

---

### Post by Robert_Boutin on 2021-01-14
Thanks both.  I _think _I may have found what's causing the issue but I haven't been able to fix it to see if it resolves my problem.

It was in fact happening with emails sent more recently (last couple months).  I went through my inbox to clean it out of junk and make sure I saw any important emails I may have missed.  I found a single email that gives me an error when I try to delete it in Roundcube.  Roundcube will open it but it's completely empty - everything is blank except the date.  I'm also getting an error when trying to search my inbox in Roundcube, I'm guessing because of this specific email.  When I go into my server and check that account inbox, I see there is no file for this particular email.  Roundcube shows 6 emails from 11/23/2020, my server only has 5 emails with this particular email missing.  So something is giving Roundcube the idea that this email exists when it doesn't (it was almost certainly deleted back in November), my guess is that is what is also screwing up downloading email to my phone when it connects to the server.

So I think I need to find what is making Roundcube believe that one email exists.  I don't know enough about this but I suspect this indication would be coming from Dovecot?

Thanks again.

***UPDATE I checked mail.err and saw hundreds, maybe thousands of this entry.  I'm sure this is referencing the missing email from Nov 23.  Does this help finding a direction to resolve?  By the way, my server is 18.04, not 16.04.

Jan 14 08:41:10 mail dovecot: pop3(user@tld.net): Error: open(/var/vmail/tld.net/user/Maildir/cur/1606156423.M633368P31862.mail,S=79154,W=80202:2,S) failed: Permission denied (euid=5000(vmail) egid=5000(vmail) missing +r perm: /var/vmail/tld.net/user/Maildir/cur/1606156423.M633368P31862.mail,S=79154,W=80202:2,S, we're not in group 4(adm))

---

### Post by rsteinmetz70112 on 2021-01-14
I haven't seen it recently but at one time I discovered certain malformed emails with strange stuff in headers would cause some email clients to freeze. Those emails were hard to delete. One I recall had an excessively long string in the a header field that caused the client to lock up. The server passed it along with no problem, the client received the email but it caused a serious problem. In time clients were updated and I was able to eventually get rid of the offending emails.

---

### Post by TheFu on 2021-01-14
Just brainstorming here.

1) Have you checked the file permissions? Is the error true? What might have changed those permissions? I have seen that 21.04 will change the default umask for all normal userids to 0750, but that shouldn't impact any 16.04 system.

2) Use a different IMAP client, perhaps thunderbird and move all the seen messages from the problem folder to a new folder.  Then remove the problem folder (however that is done), then move all those messages back? Don't just rename.

I haven't used dovecot in about 12 yrs.  We switched to a different IMAP solution which has different problems. ;(

At the beginning of every new year, MS-Outlook PST files (they used to become corrupted if over 1G size) taught me to always archive old stuff, including anything in my inbox.

---

### Post by rsteinmetz70112 on 2021-01-14
> **Robert_Boutin said:**
> 
***UPDATE I checked mail.err and saw hundreds, maybe thousands of this entry.  I'm sure this is referencing the missing email from Nov 23.  Does this help finding a direction to resolve?  By the way, my server is 18.04, not 16.04.

Jan 14 08:41:10 mail dovecot: pop3(user@tld.net): Error: open(/var/vmail/tld.net/user/Maildir/cur/1606156423.M633368P31862.mail,S=79154,W=80202:2,S) failed: Permission denied (euid=5000(vmail) egid=5000(vmail) missing +r perm: /var/vmail/tld.net/user/Maildir/cur/1606156423.M633368P31862.mail,S=79154,W=80202:2,S, we're not in group 4(adm))

You say you found "hundreds, maybe thousands" of this error - were they identical or did they refer to different messages, users or groups?

If only one user has this problem I'd look at that user very closely. Since the problem only occurs on an iPhone it may be the iPhone client. Can you try a different client? 

I don't do iPhone. I use an Android phone and have never found an email client I can use, all of the ones I've tried are either buggy or lack features I consider critical to me.

---

### Post by Robert_Boutin on 2021-01-14
All the file permissions in this /var/vmail/tld.net/user/Maildir/cur folder are 600/vmail:vmail so they seem to be in order.  I am just missing that one file that Roundcube thinks should be there.

Also, I erred, I am using 18.04, not 16.04.  I'm in the process of building a new mailserver VM on 20.04 Server LTS for more storage, maybe this will resolve itself when I migrate the files to that and get it online.  But I'd surely prefer to understand what this problem is.

---

### Post by rsteinmetz70112 on 2021-01-14
> **Robert_Boutin said:**
> All the file permissions in this /var/vmail/tld.net/user/Maildir/cur folder are 600/vmail:vmail so they seem to be in order.  I am just missing that one file that Roundcube thinks should be there.


What happens if you simply create (touch) the file?

---

### Post by Robert_Boutin on 2021-01-15
Ha ha, thanks, that did it!  I just created an empty file with the name Dovecot was wanting ([COLOR=#000000]*1606156423.M633368P31862.mail,S=79154,W=80202:2,S)*[/COLOR], changed ownership and permission to 600/vmail:vmail, and then was able to delete the file in Roundcube.  Hopefully this will solve my problem of emails downloading to my phone.  If so. I'll mark as solved.  As always, the community comes through, thanks!

---

### Post by Robert_Boutin on 2021-01-15
That one email appears to have been the problem.  Now that it's deleted,  my iphone seems to have no trouble downloading all messages from my  inbox.  

Appreciate the help! Although I still don't understand what was happening, Problem Solved!

---

### Post by jenniangl on 2021-06-20
How to fix email problems?

---

### Post by coffeecat on 2021-06-20
@jenniangl, this is an old thread, marked as solved. You will not be able to get help here. If you need help, please start your own thread. You will need to provide a lot more information, such as the nature of the problem(s), what operating system and release you are using, the email client, and so on. 

Thread closed.

---

