---
title: "Spam with collection of my recent sent addresses"
date: 2012-01-14
forum: Security
---

### Post by barbablu on 2012-01-14
Just noticed a couple of disturbing spam emails in my inbox today: they had my email address in the FROM and TO fields (quite common), but there were also addresses of friends' of mine from different circles, ie, addresses I would never expect to see all together.  **It was like they were drawn directly from the address book on my workstation**. That took me by surprise since I run Ubuntu, rather than Windows, where this might be expected.

So I started looking into those two emails a bit more.  Spamcop.net told me they both came from the same IP address in Rumenia.  A sigh of relief, since I live in UK.  The timestamp on various email headers also placed my workstation in the clear (it was down for the day).   Both emails ended up being relayed by gmx.net, which appears to be an email provider in Germany.  I have since got some notifications from its mail servers suggesting that they are still trying to send "my" spam messages but they are being temporarily blocked by Yahoo due to user complaints about the sender or too many emails from the same sender.

The addresses in the spam messages were all from emails I sent over a recent week.  Not one day or one session, but several consecutive days.  It might even be all the addresses I sent to over that period.  I routinely shutdown my workstation when I no longer need it.  I also use a webmail interface when checking my emails from the office, but I usually just read.  

The email client on my workstation is Evolution and is configured to use TLS on both IMAP and SMTP.  Not sure if Evolution would automatically downgrade to plain connection, should the server temporarily stop supporting TLS.  All addresses involved are also on my Ubuntu One remote storage for contacts.

Where could the address snooping be happening?  Directly on my workstation seems most likely.  How to detect possible malware?

---

### Post by OpSecShellshock on 2012-01-14
What's the email provider? Is it just a gmail or similar account? It's entirely possible the email account was compromised rather than the computer.

---

### Post by lisati on 2012-01-14
gmx.com is an email provider, I have an account there that I don't use much. What could have happened is one of your contacts who has Windows has something nasty on their system.

One thing I sometimes see in my server logs is evidence of someone trying to use my server as a relay. Checking the IP address at places like [http://blacklistalert.org](http://blacklistalert.org), [http://debouncer.com](http://debouncer.com) or [http://whatismyipaddress.com/blacklist-check](http://whatismyipaddress.com/blacklist-check) usually has them flagged multiple times.

---

### Post by Ms. Daisy on 2012-01-14
> **barbablu said:**
>   I also use a webmail interface when checking my emails from the office...  

...

Where could the address snooping be happening?  Directly on my workstation seems most likely.  How to detect possible malware?
I am by no means an expert.  I do know that  browser exploits are more commonplace than malicious programs on a local Linux machine.  See the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity#Make_Your_Browser_More_Secure") browser section for a little more about that.  But in a very general sense, you could have visited a web page (legit or not) that was compromised to run a malicious script in your browser without your knowledge or consent. Then the bad guy would be able to steal your credentials and get access to your email account.

Change the password to your email account.  There's more about passwords in the basic security wiki as well.

---

### Post by barbablu on 2012-01-15
I am still intrigued by the fact that the stolen emails are all from messages I sent over a few days (I receive tons with a more varied range of addresses).  Those emails were sent with Evolution on Ubuntu.  If my email account or host was compromised, why not steal the whole address book?  Maybe some form of SMTP snooping (but TLS is on)? Or the malicious scripts/program picked up keywords that appear only in sent messages...

I will review security following the Basic Security Wiki (very interesting, thank you for point it out to me).  I changed the password on my email account (provided by mail.com).  When accessing the web interface on mail.com I will be more diligent about selecting the SSL option.  I will review plug-ins on my browsers (in particular that Firefox Flash one that keeps updating via scripts asking for sudo access...).  My home network should be reasonable safe already (Linksys WAG160N with NAT, firewall set with no port forwarding, wifi with WPA2).

Thank you for the help so far.

---

### Post by mattxhand on 2012-01-15
Can you please post the header info from one of the spam messages?

---

### Post by barbablu on 2012-01-15
Sure.  Attached as [2012-01-13_Spam2_sanitised.txt]("http://ubuntuforums.org/attachment.php?attachmentid=210920&stc=1&d=1326654903")

---

