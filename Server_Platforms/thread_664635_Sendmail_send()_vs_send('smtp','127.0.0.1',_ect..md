---
title: "Sendmail send() vs send('smtp','127.0.0.1', ect."
date: 2008-01-11
forum: Server Platforms
---

### Post by hpfan12342004 on 2008-01-11
What is the difference between MIME::Lite -> send('smtp', '127.0.0.1', Timeout=>60) and MIME::Lite -> send()?

I am trying to create a script that will send out email messages. In the beginning, I used the following in order to achieve this:

MIME::Lite -> send('smtp', '127.0.0.1', Timeout=>60)

at this point, this worked and MIME::Lite -> send() did not.

 Then I had to reboot the machine. MIME::Lite -> send('smtp', '127.0.0.1', Timeout=>60) wouldn't work anymore. After quite a bit of confusion, I found that if I used

MIME::Lite -> send() instead, it worked just fine.

After another reboot, I am back to needing to use MIME::Lite -> send('smtp', '127.0.0.1', Timeout=>60). 

I am confused about which is correct and which one I should be using. Is there a program that is not getting started like it should occasionally?

I am using SendMail for my mail client, and it was running in all cases.  

Thank you.

---

### Post by MJN on 2008-01-11
I haven't got a clue what you're on about - my ignorance for sure - but if you are wanting to send e-mail from within a script why not just use the 'mail' command? See **man mail** for details.

If I've got the wrong end of the stick (quite likely!) then please do feel free to ignore this post.

Mathew

---

