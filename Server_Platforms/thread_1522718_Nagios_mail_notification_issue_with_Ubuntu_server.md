---
title: "Nagios mail notification issue with Ubuntu server"
date: 2010-07-02
forum: Server Platforms
---

### Post by black_ice on 2010-07-02
[B][FONT="Book Antiqua"][SIZE="2"]Hello all 
I have setup a new nagios server running on ubutu server 10 and every thing is running smoothly without any problem . I decided to make nagio server to send mails if any thing went wrong so i did the following steps : 

1 .) configuring the postfix to act as a mail server with a smart host to be able to send mails through this host .. this step was successful as iam now able to send a messages through my nagios server using mail command and it delivered well 

2 .) configure nagios commands.cfg to point to the new command for sending mails  

3 .) configure contacts file to add my contacts including the mails 

4 .) configure at the service definition and the host definition the contacts and the name of the contact 

I think now every thing running fine ...      


unfortunately

i didn't got any mails from nagios even there is no any event happened at the mail log indicates any type of message delivery .. 

Any body can help about this and i would be thankful 

Thanks in advance  

[/SIZE][/FONT][/B]

---

### Post by greg_ory on 2010-07-02
Well, it is hard to say without any log-files showing what the problem could be. I would look into the nagios.log file to see is there maybe something odd. 

-greg

---

### Post by black_ice on 2010-07-02
I already did that bu i find the problem finally ,, the problem acually was i didn't install mailx program . any ways after installing it i starting receiving notifications by email ,, now iam working on the notification sending period ,, thanks for your response . :)

---

### Post by voxtechsupport on 2010-07-07
I feel your pain OP. 

1. Check that you can send emails via terminal to your work account or gmail. You may run into issues like me where I can only send emails to gmail :( 

2. One you've tested that emails are able to be sent from the box then double check all your confgs as I had a typo as well.

The biggest hurdle for me was getting emails out. once sendmail was re-installed it worked... just for gmail accounts.

let me know if that helps or if you need more direction as I'm a noob at this as well and could use a few pointers myself.

---

