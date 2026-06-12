---
title: "Can't set thunderbird mail in protocol to pop3"
date: 2010-10-15
forum: Server Platforms
---

### Post by Jsdey on 2010-10-15
I'm run 10.10 desktop x64 and when I start setting up an account in thunerbird and enter name, email address and password in the first window and go on to the next next that window flashes pop and imap very quickly before stopping with a showing of imap.  There is no edit button and I have not been able to find out how to set the protocol to pop3.  Is there and error? Or am I missing something.  I like thunderbird and would like to continue using it but my email providers only support pop3.  I'm writing to this list because I'm thinking the problem may be specific to my version of ubuntu but I'm not sure.  Please help.  Thanks.

John

---

### Post by Jsdey on 2010-10-15
I found a work around.  Based on the root to the email address thunderbird tries to determine the protocol by looking it up in a database.  If it is not there (in my case mindspring.com), imap will be assumed.  The work around is to give it an email address to a large email provider (I used optonline.net) that supports pop3.  It then selects pop for the protocol.  I then can go back and change the email address and other settings.

Not a good state of affairs.  Thunderbird develops are well intentioned but they should provide a direct way to select the protocol.

---

### Post by Jsdey on 2010-10-15
It occurred to me that if the setting depends on the external database, I could shut down my network and create a pop account.  Sure enough when the network is down I then am given the option of the protocol.  But on the second screen the program needs to verify the connection to continue.  I then brought my Internet connection back up and re-verified which indicated success.

It looks like a bug to me but I have provided two work-arounds--this message and the previous.

---

