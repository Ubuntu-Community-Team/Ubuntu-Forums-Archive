---
title: "Squirrel-mail"
date: 2009-11-05
forum: Server Platforms
---

### Post by swampy1979 on 2009-11-05
Hello everybody.

I have finally done it and broken free from my Microsoft EULA £££ nightmare.

I have setup Ubuntu server x64, and followed the perfect server guide for Ubuntu 9.10.

I have successfully got squirrel-mail up and running, well to an extent.

I can send emails beautifully, and if I send an email to my squirrel-mail account the mail is sent as expected (no error messages), however the web interface shows no mail in the in-box, but if I look in /var/mail/ and vi user file, I can read the emails in the file.

I am still quite inexperienced with linux, I'm learning fairly quickly as I'm constantly trying new builds and hacking my installs to bits and starting over.

I am guessing here, so any help would be extremely greatly received. is it possible the browser is not allowed to read the file? and if so how do I go about fixing it...

And if its not file permissions I am at your mercy for ideas to fix this.

Please please help.

Thanks in advance!

---

### Post by swampy1979 on 2009-11-10
To clarify my problem a little better,

If I log into squirrel-mail through Firefox for example, and log in as user, I see no mail in my in-box, if I send an email to an msn email for example it sends the message beautifully.

If i send a message from an msn email to my squirrel-mail email it is sent without error.

However it does not show in my squirrel-mail in-box.

when I log into the server running squirrel-mail ISP-config etc it states "you have new mail in /var/mail/user".

If i open /var/mail/user with vi I can read the emails but still cannot see them from within squirrel-mail.

I've also made /var/mail/user readable to everyone as I thought it could be a problem with permissions this made no difference either.

I have read the documentation for squirrel-mail and ISPconfig but I'm truly lost for ideas.

If some kind soul could shed some much needed light on this I would be forever great full.

---

### Post by marulu on 2009-11-17
Did u manage to solve your problem? I am having the same problem!

---

### Post by swampy1979 on 2009-12-01
Nope sorry marulu, no one seems to want to touch this one but there must be loads of people failing at this point.

I've been wracking my brains for weeks for a work around or fix to this.

Theres a million and one posts on squirrel mail, courier etc but nothing that helps with this particular error.

I used the perfect server guide for ubuntu 9.10 and 9.04 for that matter and I always fall down at the same point.

To recap you can send mails to anywhere perfectly.
the server receives the mail perfectly, you can read it with VIM.
but squirrel mail shows no mail what so ever in the inbox. 

I just hope someone stumbles across this post thats been there and found the answer!

---

### Post by swampy1979 on 2010-01-19
bump

---

