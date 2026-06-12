---
title: "Sqwebmail Internal Error"
date: 2006-05-14
forum: Server Platforms
---

### Post by und3rtug4 on 2006-05-14
Hi there,

After installing and setting up all the components needed by a mail server, i wanted to install sqwebmail, for webmail services!

I just typed sudo apt-get install sqwebmail and it was done in seconds!

After that, i opened my browser and typed:

[http://myserver/cgi-bin/sqwebmail/](http://myserver/cgi-bin/sqwebmail/)

and the following output has given:

[B]Internal Error

The webmail system is temporarily unavailable. An error occured in function write: Transport endpoint is not connected
[/B]

Does anyone knows whats the problem ???
After many many searches, i still dont find anything related with the solution!

Thanks in advance

---

### Post by und3rtug4 on 2006-05-15
I'm still getting the " Internal Error .... "  message, and still doesnt get any luck on crawling for the answer to the bottleneck! 

anyone ever got this error, or knows how to solve this problem!?

thanks in advance!

---

### Post by und3rtug4 on 2006-05-15
> You've probably answered this by now, but I'll throw in what I found in case anyone else stumbles upon your post and also needs an answer.

I agree with what you found following the installation instructions. In the INSTALL file it says:

"Specify the URL to the sqwebmail binary to display the login page."

But it doesn't tell you how to do this.

Not where I would expect it, but on the original promo page, [http://www.inter7.com/sqwebmail.html](http://www.inter7.com/sqwebmail.html), it has the answer:

"Loading [http://yourwebsite/cgi-bin/sqwebmail](http://yourwebsite/cgi-bin/sqwebmail) will present the log-on page. "

Maybe the keeper of the INSTALL wants to put the info there as I'll bet you and I are not the only ones to trip on this.


I found this on one of my searches, but still havent found the answer to my problem!!

Im other search, i found a guy that has the same problem, and someone told him to start the authdaemon or sqwebmail..............
...... but my authdaemon and sqwebmail are already running, and still get the Internal error!

On the quote above, its mencioned to specify the correct URL to the sqwebmail binary, but, as the author told, theres no explanation on how to do it!

Does someone have any experience on sqwebmail, or knows how to especify the correct url or knows whats making the internal error???

I'm really needing some help solving this....

Kindly
und3rtug4

---

