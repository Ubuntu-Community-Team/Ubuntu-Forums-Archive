---
title: "Download email and forward to one online inbox (hotmail, yahoo, gmail)"
date: 2007-10-29
forum: Server Platforms
---

### Post by victorbrca on 2007-10-29
Anyone knows of a tool (daemon) that I can use to forward emails from hotmail and yahoo to gmail? 

I've installed "freepops" but it does not fill my needs. 

I wanted to have all emails forwarded to one so I can access just that one (on-line). I will not be using any e-mail client, but a browser. 

Windows has a tool called GetMail, but I really don't want to go there.

Thanks for any input! :)

Vic.

---

### Post by thelocust on 2007-10-30
In gmail you can download your mail using pop3. and there is an option in gmail to forward all your emails to any other account you want, I think yahoo has the forward thingy also but you'll have to check it out.

---

### Post by victorbrca on 2007-10-30
Yahoo has a forward, but it doesn't work well.

Gmail has a forward and a pop retriever, but it takes too long. I think it checks like every 15 mins, I need something that doesn't take that long.

I also would like to forward my hotmail and yahoo to my gmail, so gmail forwarding would not be used.

Hotmail doesn't support pop, it's web login only.

There's gotta be one tool on Linux, just need to find which. :)

Vic.

---

### Post by HermanAB on 2007-10-30
As for the download side - I dunno.  As for the forwarding, try nullmailer.  Nullmaler does only that - it forwards mail and is therefore easy to set up.

---

### Post by kentl on 2007-11-03
> Gmail has a forward and a pop retriever, but it takes too long. I think it checks like every 15 mins, I need something that doesn't take that long.
Gmail seems to check once per hour. Here is the log from my POP retrival:
> Sat, Nov 3, 2007 at 11:28 AM 	No mails fetched.
Sat, Nov 3, 2007 at 10:28 AM 	No mails fetched.
Sat, Nov 3, 2007 at 9:28 AM 	No mails fetched.
Sat, Nov 3, 2007 at 8:28 AM 	No mails fetched.
Sat, Nov 3, 2007 at 7:28 AM 	No mails fetched.
You don't want to check too often. In which case you *might* get blacklisted by the server.

If it would check once every 15 minutes, the average wait for a new mail would be around 7 minutes. If you can't wait that long I would suggest using some kind of IM. You can also press "Check mail now" if you're waiting for something important to arrive.

---

