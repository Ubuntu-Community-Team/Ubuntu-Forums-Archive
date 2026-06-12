---
title: "Is this an intruder?"
date: 2010-08-13
forum: Security
---

### Post by resander on 2010-08-13
I am using Ubuntu 10.04 (the latest) and classic yahoo.com for email. Today I sent an email to [email]gtk-list@gnome.org[/email], which is a email forum for asking and answering technical questions about Gtk. That email went there (I could see it in my incoming email(all list participants get a copy)).

But I also received an undelivered email notification saying that my Gtk email question could not be delivered to someone with an Indian name on a vodafone server. Here is the notification. I have shortened it and changed my email address to myemail and the Indians's email address to Indianfirstname.Indiansurname.    

+++++ notification text starts ++++++++++
Undelivered Mail Returned to Sender
From:
"Mail Delivery System" <MAILER-DAEMON@lwmtao1.webmail.sp.vodafone.com>
To:
[email]myemail@yahoo.com[/email]
Message contains attachments
2 Files (9KB) | Download All

    * Message001.txtMessage001.txt  <<< I did not click this to download
    * Any RGB macro in Gtk?.     <<< my email to the gtk-mail forum

This is the mail system at host lwmtao1.webmail.sp.vodafone.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<Indianfirstname.Indiansurname=webmail.sp.vodafone.com@lwmsms-cabo1.lit.de2.sp.vodafone.com>:   <<< did not click this link
    Protocol error: host 85.205.225.83[85.205.225.83] said: . BAD temporary
    authentication failure. 530 authentication required - for help go to
    [http://help.yahoo.com/help/us/mail/pop/pop-11.html](http://help.yahoo.com/help/us/mail/pop/pop-11.html) (in reply to MAIL FROM command)
Forwarded Message: Any RGB macro in Gtk?
Friday, 13 August, 2010, 11.40 AM
From:
<myemail@yahoo.com>
To:
Indianfirstname.Indiansurname=webmail.sp.vodafone.com@lwmsms-cabo1.lit.de2.sp.vodafone.com
>>> then followed the complete text I sent to the GTk forum
++++  end of notification text ++++

I sent one email to [email]gtk-list@gnome.org[/email] only and I did not put anything in the CC entry, yet the email went to a second email address unknown to me. 
Is there an intruder in the PC that is forwarding my email? I sent an email to myself to see if that would be duplicated too. It wasn't.  

I never click links in emails, so I have not brought it on myself by being careless. I do a lot of surfing, but not to sites that I have not been to before. 

I have read about trojans and rootkits, but I thought Linux would be too unfriendly to these. I have no knowledge of how to find these on Ubuntu.  
  
Your opinion and advice what to do would be appreciated.

---

### Post by cdenley on 2010-08-13
Well, you didn't send the e-mail to yourself, yet you received a copy. I bet the e-mail you received said it came from you. All the subscribers to that list got a copy of an e-mail that said it came from your e-mail address. Apparently someone subscribed with an invalid e-mail address, and your e-mail was sent to that address. The mail server for that invalid address saw the mail was coming from your address, so it sent the rejection notice to you.

---

### Post by resander on 2010-08-13
Cdenley,

Your answer fully explains it.

I ought to have seen it too, but I got into panic-mode and jumped to the wrong conclusion.

Many thanks.

---

