---
title: "conky and e-mail clients (Evolution or Thunderbird)"
date: 2009-11-08
forum: The Cafe
---

### Post by LinuxFanBoi on 2009-11-08
Okay let me first tell you what it is I want to do and why.  I amd attempting to have the object ${new_mails} return the number of unread e-mails in either my the evolution or Thunderbird Mbox spool file.

I do not want to see the number of unread mails on my ISP's POP3 server because I'm only interested in seeing the number of mails that are unread, not simply undownloaded.  I usualy leave my e-mail client open durring a session if it downloads my e-mail,  conky no longer returns a value for unread mail on the server.

Heres the problem I'm running into..

With the evolution spool file $(new_mails} returns the total number of mails that have ever existed in the inbox spool file.  Even if I delete them or otherwise move them from the Inbox, conky still shows this running total.

With Thunderbird, ${new_mails} returns a value of 2 if there is one unread mail in the inbox spool file, 1 if the e-mail has been read and 0 if it has been deleted or moved from the inbox.

Any help would be appreciated.

---

### Post by LinuxFanBoi on 2009-11-08
Well here it is in a nut shell,

Instead of using the ${new_mails} opperator I created a shell script that executes the following:

```
grep -c "X-Mozilla-Status: 0000" "/home/chris/.mozilla-thunderbird/kd5jdnpl.default/Mail/Local Folders/Inbox"
```

This counts the number of e-mails in the spool file that contain "X-Mozilla-Status: 0000." Then in conky, I can simply call that scripts with ${execi} to display the parsed output.

Please bear in mind that this only works for messages received by thunderbird.  When I identify how Evolution marks messages as 'unread' I'll post that solution as well.

---

