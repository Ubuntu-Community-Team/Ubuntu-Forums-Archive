---
title: "Postfix Woes"
date: 2006-05-23
forum: Server Platforms
---

### Post by hytek on 2006-05-23
Ok, I'm going to try to explain this as best as I can while hopefully not losing anyone.


Currently we have an intranet that has a server that is running:
Postfix (primary email server)
DNS
DHCP
Router (gateway to internet)

The postfix server has been the primary email server for some time now and IS working normal. We are switching to an exchange 2003 email server.

So lets say a normal users email is *user@work.com*. The ISP's DNS MX record for @work.com points to *server.work.com* which is actually the physical postfix server, which the hostname is *server* and the FQDN for the intranet is *server.intranet.internalwork.net*, IP address is *192.168.1.3*. So right now as said, users that are created unix accounts on server can send and receive email fine, both to other postfix accounts and external email.

Ok, so now we have a 2003 exchange server added to the same subnet. Name of the exchange server will be *exchange* and the IP is *192.168.1.250* and the FQDN is *exchange.intranet.internalwork.net*. The exchange server is soon going to be the primary mail server, but for right now we HAVE to have both the postfix server and the exchange server running. The exchange server also is running AD and a secondary DNS for now. I setup a test account named *test@work.com*. Ok, on *exchange* with the test account, I can send out email to other users on exchange, and I can ONLY send out emails outside of work.com. Meaning I can send email to yahoo.com, gmail.com, hotmail.com, ect... But I CANNOT send email to any user currently on the postfix *server* at the @work.com domain. I don't get any bounce messages, and I don't get any errors. The postfix server doesn't receive any errors, and does not get the email message at all.

Now on the postfix server, when [email]user@work.com[/email] tries to send an email to [email]test@work.com[/email] it gets a bounce message saying **unknown user: "test"**

I have tried adding the test user to /etc/postfix/virtual and to /etc/aliases but nothing is working.

I am not sure if this is a DNS issue or a postfix issue.

Basically to wrap this up, postfix server can't send to the exchange server on the same subnet but works with everything else, exchange server can't receive email from anything outside of itself (everything routes through the postfix server though), and the exchange server can't send only to the postfix server but can send email to outside domains.

Any hints, clues, ideas, directions, howtos, or anything would be helpful at this moment. Maybe I am missing something on the DNS in both domains, or the ISP has to add an extra MX record, or postfix is missing something.

IDK, I'll find a way to buy a beer to someone if they can figure this out. :D ](*,) ](*,)

---

### Post by Glut on 2006-05-25
I'm betting the issue is that exchange thinks it's the mail server for work.com, so if the user's not in the exchange database, it obviously doesn't exist. The same applies for postfix - if it's not in the postfix database it can't possibly be a user on work.com
I'd migrate to exchange as quickly as possible and update your MX records. You may be able to get away with setting up postfix virtual domains and pointing each alias to [email]user@exchange.intranet.internalwork.net[/email], but IMO this is wasted effort as once you've done that you're just going to turn the postfix server off anyway.

---

### Post by hytek on 2006-05-25
Here lies part of the problem, we can't move to exchange "all at once", and we have to have both mail servers running until everyone is moved over, which could take up to three weeks.

The good news is, so far I now have exchange being able to send mail "to" postfix. (although it takes about 10 minutes for that mail message to leave exchange) That part was a DNS issue on the exchange box itself, but it is now working nonetheless.

I am still having problems with postfix relaying any mail whatsoever to exchange. I have a few ideas I am going to try tonight or this weekend.

Question though about the /etc/aliases file, should there be an entry for my "test" user (that is the account on exchange) in aliases? If so what would be the proper syntax? 

test: test
or
test: test@exchange
or
....something else

I have the virtual file set right, just wondering if my aliases is wrong as in my bounce message I am getting "unknown user: test"

Thanks, cheers.

---

### Post by Glut on 2006-05-26
test:    [email]test@exchange.intranet.internalwork.net[/email]
Check that you're using the correct aliases file (usually /etc/aliases). That got me when moving from sendmail to postfix.

---

### Post by hytek on 2006-05-26
ok, I have added that to /etc/aliases but it is still coming up with user unknown.

Now here are two things, I have added test to both aliases and to virtual.

If I set the the below option in main.cf I get an error of
 "Server replied: 550 <test@work.com>: Recipient address rejected: User unknown in local recipient table
```

local_recipient_maps = hash:/etc/postfix/virtual

```

And if I set this option, I get the bounce message of "Unknown user"
```

local_recipient_maps =

```



So I keep getting unknown user because it is being forced to look only in the local recipient table, but I have the options set for virtual and aliases. 

any ideas?

---

