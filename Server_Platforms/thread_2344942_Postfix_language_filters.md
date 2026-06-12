---
title: "Postfix language filters"
date: 2016-11-29
forum: Server Platforms
---

### Post by ben-mad on 2016-11-29
Hi everyone,

I´m trying to configure some language filters on my Postfix server. I was checking on the internet about it but not solution found. It is not related to domain filters (for instance block e-mails from certains countries (.kr, .ru, .mx, etc.) I´m trying to detect some languages like English, Spanish, etc. to apply a filter. It is not possible to install another software like spamassassin (I need to solve it without software).

Does anyone a clue to do it? for instance using regular expressions. There are some examples:

/^From:.*\@.*\.ru/ REJECT (not useful, it is rejecting domains)
/^Subject: =?Windows-1252?/ REJECT (not useful, not only used for English language, it is used for many western languages)

Thanks in advance. ;)

---

### Post by SeijiSensei on 2016-11-29
There is no mechanism in the SMTP protocols that I know of that transmits the language of the message.  Remember that e-mail consists of both an "envelope" and its "contents."  Postfix sees only the envelope with "MAIL FROM" and "RCPT TO" addresses, and the FROM address need not match the "From:" header in the message body. The value of MAIL FROM is called the "envelope sender."

The contents of the message consists of the entire file you see when you view the "source" of an email.  It begins with a Return-Path header which contains the envelope sender, followed by Received headers from various mail servers, various other headers, the From:/To:/Subject: headers, and the message body itself.  You can sometimes discern language information from a Content-Type header if it has an entry for "charset," which might indicate it's in a language like Chinese or Arabic.  You can also look to see if there is a [Content-Language]("https://tools.ietf.org/html/rfc3282") header.  The various "parts" of [MIME]("https://tools.ietf.org/html/rfc1521") messages can have their own headers which might specify different languages and character-encodings.

Some messages specify no language at all.  I'm looking at a spam that uses merely "Content-Type: multipart-alternative" as the overall Content-Type, with "Content-Type: text/plain" and "Content-Type: text/html" for the two message parts.  Neither the character set nor the language is specified, which usually means it's in US-ASCII and English.

So the answer is no, Postfix cannot process mail based on language.  Your simplest solution is to install **procmail** on your server and create an /etc/procmailrc file to scan for "Content-Type" headers in messages and process them as you wish.  Procmail can deliver messages to mailboxes, forward them to other addresses, or pipe them to scripts.  Scan "[man procmailrc](https://linux.die.net/man/5/procmailrc)" for an overview of how procmail works then take a look at the examples in "[man procmailex](https://linux.die.net/man/5/procmailex)".

I know of no solution that will not require the installation of some other piece of software.  SpamAssassin is powerful but complex.  It also will not pipe the message to another process if that is what you need to do.  Procmail can, and you can install it with "sudo apt-get install procmail".

---

