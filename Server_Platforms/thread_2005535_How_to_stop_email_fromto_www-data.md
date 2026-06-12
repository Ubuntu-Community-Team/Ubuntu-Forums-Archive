---
title: "How to stop email from/to www-data"
date: 2012-06-17
forum: Server Platforms
---

### Post by clay7 on 2012-06-17
Hello,

I have a 12.04 LAMP server with Postfix. I keep seeing emails in my syslog that are from and to [email]www-data@*mydomain.com[/email]*. 

How can I stop emails being sent from and to this address? I'd rather have the messages dumped into a log file.

Thanks!

---

### Post by SeijiSensei on 2012-06-17
Are you running scripts that send emails to visitors?  If so, that's the source of the messages from the www-data user.  There are ways around this problem but they require using something other than simply PHP's mail() function.  

The fundamental issue concerns security, in particular prohibiting users from spoofing the identity of other users when sending mail.  E-mail distinguishes between two types of senders, the *message sender* whose address appears in the "From:" field of a message, and the "*envelope sender*," the username under which the SMTP session with the recipient's inbound mail server takes place.  

A simple analogy to postal mail might help make this clear.  Suppose I send you a letter signed with my name and address, but I use a different name and address for the return address on the outside of the envelope.  The From field in the message is the equivalent of the name on the letter itself, while the SMTP "envelope sender" is the equivalent of the return address.

So what does this mean for a PHP script?  Well, you can modify the message sender by including a "From:" header in the optional fourth field of the mail() function like this:

```

$from="joe@example.com";
$to="bill@somewhere.net";
$subj="An exciting new product just for you!";
$msg="Buy this product now!";

mail($to,$subj,$msg,"From: $from");

```

When Bill gets this message, his mail client will report "joe@example.com" as the sender in the From field.  However if you look at the complete message source, you'll see at the very top a "Return-Path" header that probably reads 

```
Return-Path: www-data@example.com
```

That's the envelope sender, and it's determined by the name of the user running the program that sent the message.  In this case it's the user under which Apache is running, the "www-data" user.

It's possible to construct a method to force the envelope sender to match the message sender, but how you do that depends on the mail software you're using.  I use sendmail rather than Postfix as my "mail transfer agent".  Sendmail allows you to designate "trusted users" who are allowed to manipulate the envelope sender address.  I typically include the Apache user in this list.  However that by itself isn't sufficient if you're sending messages with PHP's mail() function.  You actually have to invoke the MTA from within the script and pass it the message with the appropriate command-line parameter to force a specific envelope sender.  With sendmail, for instance, I can use the exec() function like this:

```

$fullmsg="From: $from\nTo: $to\nSubject: $subj\n$msg";
exec("echo $fullmsg | /usr/sbin/sendmail -f joe@example.com bill@somewhere.net");
```

If the www-data user is trusted, then sendmail will use the value assigned to the -f switch as the envelope sender.  I'm sure there must be a way to accomplish the same task with Postfix, but I can't help with that.

Why this matters is that remote SMTP servers will send administrative messages, like non-delivery notices, to the envelope sender, not the address in the From field of the message.  The inbound messages coming to the www-data user are probably notices like these.

On the outbound side, you have to jump through hoops like the ones I described above to force the envelope sender to be something other than [email]www-data@example.com[/email].  On the inbound side, though, you can use "aliases" to forward messages sent to the www-data user to some other real person.  

Edit the file /etc/aliases as root with sudo and add a line like this:

```
www-data:     joe@example.com
```

then run the command "sudo newaliases" after saving the file.  Now mail sent to [email]www-data@domain.name[/email] will be forwarded to [email]joe@example.com[/email].

This might seem an unnecessarily long-winded answer to your question, but you're not the first person to raise this issue.  So I thought it was worthwhile to provide a complete answer to your question to help other people who might search the forum for this information in the future.

---

### Post by clay7 on 2012-06-18
Wow - thank you for such a great answer. Your answers are usually very good anyway, but this one takes the cake. Hopefully this will help others as well.

Thanks very much!

---

### Post by SeijiSensei on 2012-06-19
When I first started building applications like mass mailers, I had to invest some time in arcana like this.  I might as well share some of it with you!

While I gave the example above of forwarding mail for www-data to a real person, you might find letting the server continue to deliver administrative mail to the www-data user more useful.  You can write a script in bash or PHP to read the mailbox and extract the address that bounced from each message.  There are a small number of errors that get reported; even a simple:

```
sudo grep -i 'user unknown' /var/spool/mail/www-data
```

will net you a good chunk of the lines reporting bad addresses.  You have to massage the output to extract just the addresses themselves, eliminate duplicates, etc. Once you have the bad addresses, you can run a script that deletes them from the database.  I'll leave all that as an "exercise to the reader," as the textbooks say. :D

---

