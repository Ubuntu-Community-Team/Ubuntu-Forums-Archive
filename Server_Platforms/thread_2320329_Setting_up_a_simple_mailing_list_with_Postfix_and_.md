---
title: "Setting up a simple mailing list with Postfix and PHP"
date: 2016-04-12
forum: Server Platforms
---

### Post by kyle48 on 2016-04-12
My requirement is pretty simple. I need to set up a server (bar.com), where you can send an email to that domain (e.g. [EMAIL="foo@bar.com"]foo@bar.com[/EMAIL]). I need the server to then examine the first part of the receiving email address ('foo'), send that value to a PHP script, have the script produce a list of email addresses that the email should be redirected to, and then send the email along to those addresses. The end recipient should see that the email was from the original sender and was sent to [EMAIL="foo@bar.com"]foo@bar.com[/EMAIL]. So basically, I need a very simple mailing list system that dynamically finds a list of recipients via a PHP script.

Full example:
- '[EMAIL="jack@sender.org"]jack@sender.org[/EMAIL]' sends an email to '[EMAIL="email-list@server.net"]email-list@server.net[/EMAIL]'
- Postfix on server.net receives this email, and calls a PHP script using the argument 'email-list'
- PHP script queries a database, does some filtering, and other custom stuff, and eventually comes up with a list of email addresses that should receive this email (this list might contain two email addresses, [EMAIL="james@recipient.ca"]james@recipient.ca[/EMAIL] and [EMAIL="jordan@receiver.net"]jordan@receiver.net[/EMAIL])
- Postfix gets this list of addresses and sends the email along to all of them, keeping the 'To:', 'From:', and 'Subject:' headers exactly the same as the original email
- [EMAIL="james@recipient.ca"]james@recipient.ca[/EMAIL] receives an email in his inbox that shows it was sent from [EMAIL="jack@sender.org"]jack@sender.org[/EMAIL] to [EMAIL="email-list@server.net"]email-list@server.net[/EMAIL]

Does anyone have any suggestions of the best way to do this?

Thanks!

---

### Post by SeijiSensei on 2016-04-13
The traditional solution is to use aliases that are defined in the file /etc/aliases.  An alias can be one or more addresses or a reference to a file containing a list of addresses.  For instance, an entry like
```
email-list:      :include:/path/to/some/listfile
```
tells the mailer to look at /path/to/some/listfile when a message for [email]email-list@server.net[/email] arrives.  The "listfile" would consist of the addresses, one per line:
```

james@recipient.ca
jordan@receiver.net

```
When you make changes to /etc/aliases, you need to run "sudo newaliases" to rebuild the database Postfix uses.  For more details, see [http://www.postfix.org/aliases.5.html](http://www.postfix.org/aliases.5.html).  The addresses in the file can have full RFC822 formats like:
```

James Smith <james@recipient.ca>
"Jordan Q. Jones" <jordan@receiver.net>

```
Jordan's name is enclosed in quotation marks because it contains a non-alphameric character, the period.  A name like "Bill O'Neill" or "John Taylor, IV" would also require quotation marks.

This is by far the simplest and most common method of managing email lists.  The method you describe would require a lot of programming and only makes sense if the lists need to built dynamically each time a message arrives.  If [email]email-list@server.net[/email] always points to those two addresses, you're much better off using aliases.  At worst, you might need to write a little script to append or remove addresses from "listfile".

I manage email for my college alumni class and have set up a simple PHP-based web page to manage a PostgreSQL database containing the addresses.  I provided a simple form so that trusted persons can log into a website and add, remove or update addresses in the database.  When changes are made, the script rewrites the "listfile" with the updated address list.  Depending on your application, that might be a useful approach.

---

### Post by kyle48 on 2016-04-13
Thanks for the info. I'm relatively familiar with the aliases file, and had considered that solution. Unfortunately, the addresses that an email should get redirected to change rapidly, so using a static file like that doesn't work in this application. The list of addresses that should receive is quite complex to determine, including factors such as time received, other emails received recently, recent activity, etc., which is why I need to generate the list on-the-fly.

I understand that the method I require is difficult and requires a lot of programming, but I'm OK with that. I think it's the only way I can go about this. I'm just not sure what the best way to start with it is.

---

### Post by SeijiSensei on 2016-04-13
First, I'd install **procmail** and create a "recipe" in /etc/procmailrc like this:
```

:0
* ^TO.*email-list@server.net
| /usr/local/sbin/list_handler

```

That pipes every message sent to that address to the "list_handler" script.  If I need to do a little massaging I'll pass the message to a bash script that does its magic then pipes the result to a PHP script.  Or you could have procmail pipe the message directly to "php -q /usr/local/sbin/list_handler.php".  Either way, the message will arrive on STDIN in PHP and you can read it with
```
$msg=file_get_contents("php://stdin");
```
to put the whole message in a string, or store it as an array with
```
$msg=file("php://stdin");
```
The latter might be easier to work with if you need to parse each line.  Iterate over $msg and scan each line for relevant strings with strstr() or one of the grep() functions.  Once you've found a matching line, you can quickly parse it with
```
$lineparts=explode(" ",$msg[$i]);
```
and iterate over $lineparts to find the text(s) you need.

Presumably you'll have a database against which to run SELECT queries based on the contents of the lines.  Then you would rebuild the message from the array with the appropriate recipients in To: or perhaps Bcc: and pass it to Postfix.  You can use the mail() function, but sometimes it's easier to [open a Postfix socket]("http://php.net/manual/en/book.sockets.php") and write to that.

---

### Post by kyle48 on 2016-04-13
So interestingly, I actually do already have it so it sends all the content into a PHP script (using a Postfix filter). And I do have it set so it will send it to the right recipients. The problem is that when I send it from PHP with a "From:" header that shows the original sender's email, all of the spam filters get very upset because the "From:" header does not match where it was actually sent from. I was hoping that a solution involving aliasing or something might help avoid that.

Also, doing it this way makes it quite difficult to properly deal with attachments.

---

### Post by SeijiSensei on 2016-04-14
Services like Yahoo and AOL now use something called DMARC which means that messages with @aol.com or @yahoo.com From addresses must originate on their servers.  It wreaks havoc with listservers that try to preserve the From address.  For the listservers that I manage, I've adopted the solution of rewriting the From field as "user=yahoo.com@mydomain.com" since my server is authoritative for mydomain.com.  It's simply impossible to resend mail from services that use DMARC without rewriting the From address.

For all non-DMARC services, the usual solution is to separate the "envelope sender" and the From address.  In PHP you can use the mail() command to send additional parameters to the mailer program.  [See example three here]("http://php.net/manual/en/function.mail.php").  That example sets the envelope sender, the name used in the SMTP MAIL FROM command, to [email]webmaster@example.com[/email], regardless of the contents of From.  As long as your server is a legitimate sender for the example.com domain, those messages should go through.  If your script runs with root privileges it should work fine.  If it runs as an ordinary user, you may need to tell Postfix to trust that user.  (I don't use Postfix so I can't help with that.) A side effect of setting the envelope sender is that all nondeliverable and other bounce notices will be sent to that address, not to the address listed in the From field.

I'm not sure why you're having problems with attachments if you're forwarding the entire message intact with just a change in the To or Cc fields.

---

### Post by kyle48 on 2016-04-14
That's interesting, I wasn't familiar with DMARC.

The only issue I've found with the PHP mail() command is that you can't separate the envelope recipient from the displayed recipient. E.g. if an email is sent to the list [EMAIL="email-list@server.com"]email-list@server.com[/EMAIL], how do I use PHP to send that to [EMAIL="james@recipient.ca"]james@recipient.ca[/EMAIL] and [EMAIL="jordan@receiver.net"]jordan@receiver.net[/EMAIL] so that when they receive it, it shows the "To:" header as [EMAIL="email-list@server.com"]email-list@server.com[/EMAIL] instead of their individual addresses? I would want them to see that it's to the list address, so that they have the "Reply-List" option in clients like Thunderbird. Also, so they know that the entire list received the email, not just themselves.

---

### Post by SeijiSensei on 2016-04-14
Usually that would be handled by making [email]email-list@server.com[/email] an alias to a mailing list as I described originally.  Since the dynamic features of your application rules that out, you could generate a Bcc: header with all the recipient addresses and preserve the original To:.  If you want to force replies to the list address, add a
```
Reply-To: email-list@server.com
```
header to the mail you send as well.

---

### Post by kyle48 on 2016-04-15
I think I have it set up nicely now, thanks for all the help. Let me ask one more question about Postfix.

Is there any way to prevent all outgoing mail (including bounces) to a specific email address? The server receives important emails from an outside email address, but they get very upset if you send them any emails. So I need to make sure that my server never sends any email to that address. So even if I have an error in the configuration and it would normally send a bounce for that, it cannot send that bounce. Any ideas on the best way to configure this?

---

### Post by SeijiSensei on 2016-04-15
You sure do business with some weird people.

Is this just one address in a domain where other recipients accept the mail, or can you block the whole domain?  If the latter, you can try determining the MX hosts for that domain, then making them aliases for localhost on your machine.  You'd need to tell Postfix it is a legitimate server for that domain, though.

You can determine the MX hosts for "example.com" with the command
```
host -t mx example.com
```
then use "host servername.example.com" to determine its IP address.

```

$ host -t mx ubuntu.com
ubuntu.com mail is handled by 10 mx.canonical.com.
$ host mx.canonical.com
mx.canonical.com has address 91.189.95.10

```

Another option is to add iptables rules that block outbound connection to those servers like this:
```
sudo iptables -A OUTPUT -p tcp -d ip.of.banned.server --dport 25 -j REJECT
```
The problem is that any such messages will get stuck in the outbound queue of your server.

---

