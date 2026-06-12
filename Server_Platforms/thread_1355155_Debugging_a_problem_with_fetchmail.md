---
title: "Debugging a problem with fetchmail"
date: 2009-12-14
forum: Server Platforms
---

### Post by straytalk on 2009-12-14
Hello everyone,
 
I am currently testing out Request Tracker for my company and I've run into some problems but I can't pinpoint exactly where the fault lies. 
 
The quick run down is Request Tracker is a ticketing system. I am using a third party plugin that allows you to login using an LDAP account. If you email it request tracker will create a ticket under the user linked with the email address. Request tracker is *supposed* to process emails that are not associated with an account by creating a generic account with that email address. I am using fetchmail to poll the support email accounts and then send them to request tracker to be processed. The problem I am running into is only some emails are being prcoessed. Running fetchmail in debug mode it gives me the error saying the RT server that handled your email did not behave as expected it said "(just a bunch of empty space)" then the next message from fetchmail is MDA returned nonzero status 75. 
 
Now the strange thing is some email addresses work fine. Initally the common link between these emails was that they were linked to an LDAP account that was already imported, but a recent test blew that theory out of the water. So far the emails that have worked are on the exchange server. The anaomly is there was a gmail account that was linked to an LDAP account that works fine, non ldap gmail accounts do not and other than the exchange serve emails, addresses linked to LDAP do not work. 
 
This is boggling my mind and it seems there is no documentation on a problem like this on the net, all the mda nonzero status 75s have an additional error message linked to them that mine doesnt, i.e. a 500 internal or a 404 not found. If anyone can help me pin point where the fault exists that would be wonderful, even if you have no experience with request tracker toss out ideas of what you think is the broken link and why. If you want any additional information just let me know. the syslogs are not helpful and everything is set the nosiest debug mode.
 
Thanks,
Scott T.

---

