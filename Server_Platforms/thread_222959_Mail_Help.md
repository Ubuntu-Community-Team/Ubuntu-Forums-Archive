---
title: "Mail Help"
date: 2006-07-25
forum: Server Platforms
---

### Post by kaptainlange on 2006-07-25
Let me start by saying I know absolutely nothing about mail as it corresponds to sendmail and the like.

I have a dynamic IP and as such my IP block is flagged as spam by every watch list you can think of.  Up until now I haven't been using it for anything other than sending myself notifications of backups being completed.  I am however undergoing a project where people can elect to recieve email about updates to a community site.  I would like to be able to send them mail from the server without it being flagged as spam 99% of the time.

I had the idea that I could use a gmail account to send the mail to these people, by passing the outgoing mail onto the gmail smtp servers.  Question is how do I set that up.  How do I direct my outgoing mail to gmail servers and then onto their destinations.  If that is at all possible.  If not, any other suggestions would be appreciated.

Thanks ahead of time for any help.

---

### Post by MJN on 2006-07-25
This is very common. Usual solution is simply to relay your outgoing mail via your ISP's mail server. Hopefully they won't be on any blacklists.. ;) I'm not familiar with Gmail but I don't see why you couldn't use them instead - however they will likely require authenticating to whereas your ISP may not (they accept your 'anonymous' connection by virture of you connecting from one of their IP's).

If you're using Postfix, the 'relayhost' directive is what you're after e.g. **relayhost = [nameoraddress.ofyour.isp.mailserver] **(keep the square brackets)

Mathew

---

### Post by kaptainlange on 2006-07-25
Very good, this sounds like what I need to get started on getting this working.

Thanks for your quick response.

---

### Post by MJN on 2006-07-25
Just noticed you mentioned Sendmail - is that what you're using (and not Postfix)? If so, I'm afraid someone else will have to jump in with the Sendmail equivalent of *relayhost*.

Either way, the principle of what you're trying to do is quite straightforward..  just need to work out the practice!

Mathew

---

### Post by kaptainlange on 2006-07-25
I'm using postfix, I just mentioned sendmail because it was the first mailer I thought of and I'm a noob.

I've actually got it functioning with your help, so thank you very much.:-D

---

### Post by MJN on 2006-07-26
You're welcome.

---

