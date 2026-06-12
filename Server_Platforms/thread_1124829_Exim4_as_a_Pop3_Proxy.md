---
title: "Exim4 as a Pop3 Proxy?"
date: 2009-04-13
forum: Server Platforms
---

### Post by joejvj on 2009-04-13
I am an Ubuntu (and Linux is general) newbie, so please bear with me.

I recently set up Ubunto 8.10 server for our small office. We have 4 employees who are now using the server mostly to share company files (via samba) and support our company website.

It turns out that each employee has multiple email addresses that they are accessing through Outlook, Eudora, etc. on their win XP boxes. What I would like to do is consolidate all these external email accounts and have them go through the server. 

I have installed Exim4 and have set it up to basically forward root/postmaster mail to me to keep an eye on things. But here's what I want to do:

1- Have the server go out from time to time and cache up emails from all the various pop3 accounts that the employees use. I could then set up their email clients so they only have a single pop3 incoming account (the ubuntu box).

2- Allow the ubuntu box to be the only smtp outgoing server for these people.

3- Eventually, allow the server to do anti-spam and anti-virus screening.

I have gone through the Exim4 man pages and documentation and can't figure out how to do this. Obviously, somewhere in the server I need to enter the usernames and passwords of all the employees email accounts so their mail can be "prefetched" and ready to be read, but I don't know where to start.

I'm not looking for hand-holding. If someone can explain all this or point me to applicable web pages, I would be forever grateful. I realize that the anti-spam/anti-virus stuff will require additional packages, but if I can accomplish steps 1 & 2, I can probably figure out step 3 on my own.

Thank you for your responses.

---

