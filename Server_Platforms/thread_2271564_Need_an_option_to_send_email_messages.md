---
title: "Need an option to send email messages"
date: 2015-03-31
forum: Server Platforms
---

### Post by mastablasta on 2015-03-31
I currently have sSMTP installed. I only want to be able to send messages. I configured it to use gmail and it worked well for about 6 months. until Google decided to block my mail account. no reason given. I am sure it wasn't spamming, since it only had 2 or 3 messages per week.

how could I configure this using something else maybe? any alternatives to gmail? perhaps I should use my website host? I just want it to be able to send some messages but not receive any. e.g. about updates waiting, fail2ban messages, break in attempts etc.

---

### Post by TheFu on 2015-03-31
If you have a VPS, then you can run an email server, most likely. Shared webhosting won't allow that, but most do support email added onto the contract.
Never used sSMTP before, so can't help. Sorry.  A few days ago, someone here was looking for help with msmtp - is that an option?  I use postfix and think a few of the forum moderators have theirs connected to gmail. Look for howtos.

---

### Post by nerdtron on 2015-03-31
> **mastablasta said:**
> I currently have sSMTP installed. I only want to be able to send messages. I configured it to use gmail and it worked well for** about 6 months**. until Google decided to block my mail account. no reason given. I am sure it wasn't spamming, since it only had 2 or 3 messages per week.

how could I configure this using something else maybe? any alternatives to gmail? perhaps I should use my website host? I just want it to be able to send some messages but not receive any. e.g. about updates waiting, fail2ban messages, break in attempts etc.

Really? just 6 months? I just had this setup with ssmtp and it's been running for more than a month. 5 emails a day. 
Man, now I'm worried if this is not a permanent solution.

I'll leave a comment just to see other alternative free mail relays.

---

### Post by mastablasta on 2015-04-01
they blocked it with no explanation. and then i used the form to tell &#65279;them I am not breaching any ToS and even linked to their own website explaining how to use google's service in that way. they unblocked it but about a month later for no reason given it was blocked again. I am not sure how but as soon as I have some time I will escalate this. I mean at least they should give you a reason for why it was blocked or at least review a complain and a reply. not block again.

---

### Post by nerdtron on 2015-04-17
I'm going to bump this thread. 

My gmail was also blocked after 2 months of run. Any alternatives?

---

### Post by TheFu on 2015-04-17
Would fetchmail be an option for pulling from gmail?  Fetchmail allows control of the periodic poling - perhaps doing it every 30 min would work?

---

### Post by nerdtron on 2015-04-18
> **TheFu said:**
> Would fetchmail be an option for pulling from gmail?  Fetchmail allows control of the periodic poling - perhaps doing it every 30 min would work?

HHmm you mean, fetching my messages from gmail?

What I would like to do is use a bash script to send emails by logging into my gmail account and send out emails alerts to other people.
I already have this setup berfore
```
echo "email body" | mailx -s "subject here" -a "attachment.txt" -- touser@gmail.com
```

And it's working for about two months, then gmail blocked my account because of sending suspected spam emails. i was just sending 5 emails a day. :(

---

### Post by TheFu on 2015-04-18
I can't speak for google's spam recognition, but I know if the source IP and claimed domainname don't match, I call it "spam."  I use some real-time anti-spam detection sites and sometimes gmail is flagged as a spammer based on the content of the messages - "buy drugs now" or "Get Bigger *****" - for example.  Perhaps google is using those same services and seeing which messages are being marked as spam?

Yes - fetching your messages from gmail. That is what fetchmail does.

I use "Mail" from the heirloom-mailx package, of course, a postfix MTA is setup on every server as a satellite system which forwards all email to the central mail server on the same subnet for handling. I've never connected to a gmail account for email ... besides telling our Zimbra server to pull all my gmail local for better management, control over the messages and better search controls.

I can only suggest that you make certain the "FROM" matches your gmail userid.

---

### Post by steeldriver on 2015-04-18
I remember finding ssmtp's configuration VERY non-intuitive when I played with it (especially the /etc/ssmtp/revaliases)

I can't vouch for it but there's a howto here --> [http://www.howtogeek.com/51819/how-to-setup-email-alerts-on-linux-using-gmail/](http://www.howtogeek.com/51819/how-to-setup-email-alerts-on-linux-using-gmail/)

---

### Post by nerdtron on 2015-04-18
> **steeldriver said:**
> I remember finding ssmtp's configuration VERY non-intuitive when I played with it (especially the /etc/ssmtp/revaliases)

I can't vouch for it but there's a howto here --> [http://www.howtogeek.com/51819/how-to-setup-email-alerts-on-linux-using-gmail/](http://www.howtogeek.com/51819/how-to-setup-email-alerts-on-linux-using-gmail/)

hhmmmm reverse aliases..ssmtp is already setup so...let me try and update back.
Thanks much.

---

### Post by nerdtron on 2015-04-18
Like the tutorial said. It's working on Ubuntu. I don't know how long this setup will hold up.
On my Centos machine, it's not working at all. Maillog still says bounced from gmail due to possible spamming...

---

### Post by SeijiSensei on 2015-04-18
These machines are on different IP addresses, I presume?  Did you run tests for the CentOS one at [mxtoolbox.com](http://mxtoolbox.com/blacklists.aspx) to see if your IP has been blacklisted or tagged as an open relay?

---

### Post by nerdtron on 2015-04-18
> **SeijiSensei said:**
> These machines are on different IP addresses, I presume?  Did you run tests for the CentOS one at [mxtoolbox.com]("http://mxtoolbox.com/blacklists.aspx") to see if your IP has been blacklisted or tagged as an open relay?


They are the same, I only have a single public IP. I think it has something to do with certificates or identity which is already configured too. 

If the ubuntu solution lasts, then I'll probably stick with it.

---

### Post by mastablasta on 2015-04-20
i wonder if really "revaliases" has anything to do with it.

it's not that the ssmtp is not working. it was actualyl easy to setup, but the issue is it got blocked.

and lately Google is just running me in circles. before when i received their message to try again all i did was try to loging again and then authenticate i am huiman by tying in the letters. this time however it just throws me back to their page when i can again request the account to be unlocked.

---

