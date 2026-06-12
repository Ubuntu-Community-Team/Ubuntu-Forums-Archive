---
title: "Recover Emails Ubuntu Server Dovecot Postfix"
date: 2010-04-27
forum: Server Platforms
---

### Post by Lukas1 on 2010-04-27
I tried searching the posts and have come up empty handed. I need to find an email I sent to myself (actually a forward of several other emails) that did not get delivered. Otherwise I need the original emails themselves. I have been using pop with dovecot on my ubuntu server Jaunty machine. 

I searched the mail logs and found that the reason the message might not have been delivered could be because my permissions were not set to administrator for that user. I changed the permissions and still nothing came back. 

I deleted the client mail account on the machine I used that had the messages but I was hoping they might still be somewhere on the server. Any ideas?

Thank you

---

### Post by Iker Etxebarria on 2010-04-27
Hi 
 
I'm not sure if this will be helpfull for you. 
If you know some word to find in that mail, maybe you can do the following to check if you have the mail in your postfix file:
 
```
 
grep wordtofind /var/mail/username

```
Where wordtofind is the word you wich identifies the email that you are looking for and username is the user's name of the mailbox where you are searching.
 
This code will return the lines of the mailbox where the wordtofind appears.
 
Good luck!

---

### Post by Lukas1 on 2010-04-27
Thank you I did attempt your search idea but to no avail. I'm afraid they are gone.

---

