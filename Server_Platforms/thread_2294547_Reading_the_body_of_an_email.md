---
title: "Reading the body of an email"
date: 2015-09-11
forum: Server Platforms
---

### Post by aaron50 on 2015-09-11
Hello all,

I am hoping someone can help me here, if i have placed this question in the wrong place please let me know. I am very new to Ubuntu and bash scripting, but what i am trying to do is read the body of an email and use that in another script. I would like to be able to email my server's email (one that i set up dedicated for my server to send me warnings about temp, etc.) from my personal email and have the server automatically pick up the email and determine what to do with it. An Example would be that I will be sending a list of items to the server with the subject "To Do List", the server will go through all of the emails in the inbox and look for the "To Do List" email, then it will read the body of the email and put that into a file, then delete the email. This file will then be used by another script to read it and parse out key words that i want to do. I think i found on how to read the file and do what i want it to do, but i need to get the body of the email out into another file in order to read it. Is there a tool out there that can help me with this?

Also, I was thinking of using a cronjob to run the script to check the emails, but if there is a sweeper program that can notify the server that there is an email, that would be great too. Any help is greatly appreciated.

---

### Post by QIII on 2015-09-11
*Moved to **Server Platforms***

---

### Post by SeijiSensei on 2015-09-11
First place to start is with **procmail**, the Swiss-army-knife of mail processing.  Skim the [procmailrc]("http://linux.die.net/man/5/procmailrc") man page, then spend some time studying the examples in "[man procmailex]("http://linux.die.net/man/5/procmailex")".  You can write complex "recipes" to handle messages based on their content.  For instance, the recipe
```

:0
* ^Subject:.*to-do-list
| /path/to/some/script

```
will scan (ignoring case) every incoming message for that subject line and hand any that match over to the script.

If you need to read the passed message line-by-line, that can get a [bit]("http://www.unix.com/shell-programming-and-scripting/80840-reading-stdin-shell-script.html") [tricky]("http://stackoverflow.com/questions/6980090/how-to-read-from-file-or-stdin-in-bash").

---

### Post by aaron50 on 2015-09-11
Okay, I will spend some time reading these. Thanks!

---

### Post by MAFoElffen on 2015-09-13
Break it down into logical steps:
- Declare empty variable to hold body of text
- Open file 
 - - Read File (parse) 
 - - Until condition is met, what is read is ignored
   - - - Condition is met, Body of text starts
   - - - Look for condition that ID's the body of text. 
   - - - Until end of body condition is met, what is read is added/appended to variable...
   - - - End of Body is found or EOF, break out of Loop
- Variable, if not null, is Body

The trick to most programmatic expression is being able to create conditions that eval to true or false with dependable frequency.

---

### Post by SeijiSensei on 2015-09-13
Parsing a message is actually pretty complicated, especially multi-part messages composed of plain-text and HTML versions and maybe some attachments.  For these MIME-encoded messages I use the munpack command that comes with the [**mpack** package](http://packages.ubuntu.com/trusty/mpack).

I scan the message for a 
```
Content-Type: multipart
```
header (usually something like "multipart/alternative" but there can be other variations).  If I find one, I hand the message to munpack to extract the parts to temporary files then act accordingly.  If there is no "multipart" header, you can treat the message as a single plain-text item.

That's actually a good example of using procmail.  Suppose I have a script called "multipart-handler" and another called "onepart-handler."  In procmail you can write the recipes:
```

:0
* ^Content-Type:.*multipart
| /path/to/multipart-handler

:0
| /path/to/onepart-handler

```
assuming every message should be passed to one of these two scripts.

---

