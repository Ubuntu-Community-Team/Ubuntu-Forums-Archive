---
title: "where do i find my spam mails?"
date: 2012-03-31
forum: Server Platforms
---

### Post by gdtw on 2012-03-31
I cannot find anything under /etc/Maildir. i see my accounts in the folder, and there is "new", "cur", etc.
I see there is a folder called spamassassin under /etc/mail, but there is not much in the folder. the .cf file is basically empty.

Where can I find my spam mail? please help!
Thanks

---

### Post by Rex Bouwense on 2012-03-31
That's a new one.  Most people do not even want to see SPAM.  Who is your email provider?  There is probably something in the preferences that will tell you where your SPAM is located.  Mine is somewhere in Internet neverland hopefully.

---

### Post by Frogs Hair on 2012-03-31
I'm not sure I can help , but knowing what email client you are using may help someone to help you. I use Thunderbird on 11.10 and  junk mail from the Hotmail pop 3 account is not available . I have never received any junk mail / spam in over a year with the GMX account .

In Thunderbird under  Edit > Account Settings Junk Settings you can disable the Junk mail controls and that may allow you to download the contents of that folder .

---

### Post by gdtw on 2012-03-31
there are constantly emails wrongly placed in the spam folder. In my case, i was trying to retrieve forgotten password but could not get the responding replies.

Since i am running my own website on my own ubuntu server, i am my own email provider i guess. so i suppose the question is a ubuntu question.. about the file structure?

---

### Post by lisati on 2012-03-31
*Thread moved to **Server Platforms**.*
What is the general structure of your MTA? Postfix on its own? Postfix+Spamassassin? Something else?

---

### Post by gdtw on 2012-03-31
in my Thunderbird Junk settings, i now have
move junk messages to my inbox. that did not help.

how would Thunderbird know where my junk mails are? if they are already filtered by something like spamassassin?

---

### Post by gdtw on 2012-03-31
> **lisati said:**
> *Thread moved to **Server Platforms**.*
What is the general structure of your MTA? Postfix on its own? Postfix+Spamassassin? Something else?

Sorry, how do I find that out?
I know i am using postfix, and i know there is a spamassassin folder. i am not even sure the spamassassin is being used?

---

### Post by webservervideos on 2012-03-31
I am confused by your use of thunderbird. Is this a server and you are getting your mail via thunderbird or are you using a desktop?

 if you are using a server and your 'spam mail' is disappearing then one of two things is happening (well, maybe 3).

 1- You have spamassassin set up and running. Then something like procmail,mailscanner, or whatever you have is deleting things marked as spam.  

2- whoever set up your server made spam messages go to a separate folder somewhere (check all the home directories)

 3- you have greylisting and it is set for a very long period.   1- check your maillog (I use centos, not ubuntu, but I think they are the same location).../var/log/maillog. Look for the email address that something was sent from and see if you can see what is happening.  

Usually the log will add something like 'delivered to procmail' or some other mail handler that will pass it to spamassassin.
 That handler is deleting or moving your spam mails somewhere. Postfix and spamassassin do not delete your mail.

 best to look and see what services are running...then you know what to look for.

---

### Post by gdtw on 2012-04-01
i am using thunderbird to retrieve mail from my webserver/mail server which is on a ubuntu machine.

I am not sure that my spam mails are "disappearing" because I simply don't know where they are to start with. So I was trying to see if I can find them.

1, I looked in /home and see all the email accounts. in an account, there is an Maildir folder, in which there are "new", "cur", etc. I can see my mails in the cur folder, and I do not see the mails I was expecting/missing.

2, in /var/log, I looked at files mail.log and mail.info, and there is nothing like "spamassassin" or procmail. when I search for "delivered to", they are all "delivered to maildir".

3, i checked the /home folder, but do not see any special folder that can collect spam mails...

---

### Post by volkswagner on 2012-04-01
Open up your mail log and search by date and time of when you expected the password email to hit your server.

If you don't know or remember the date you can open the log in "real time" and request the password again.

```
tail -f /var/log/mail.log
```


Then request the password and watch the log to see if it's hitting your server and what is happening.

It is likely your server is just rejecting the spam.

---

### Post by gdtw on 2012-04-01
> **volkswagner said:**
> Open up your mail log and search by date and time of when you expected the password email to hit your server.

If you don't know or remember the date you can open the log in "real time" and request the password again.

```
tail -f /var/log/mail.log
```
Then request the password and watch the log to see if it's hitting your server and what is happening.

It is likely your server is just rejecting the spam.

I can see something when i send myself a message, but i get nothing at all in the file mail.log 20 minutes after i request the password..

---

### Post by webservervideos on 2012-04-01
1- check your thunderbird settings on your local computer to see if you have it set to 'delete' spam.

2- apparently you have checked and you are not running spamassassin or a middle delivery program designed to tag and delete things.

Therefore, your mail has to be getting through and your thunderbird is deleting it.

If your logs are saying it is delivered and not mentioning a program, just delivered to the maildir, and you are not running anything that deletes it, then the only plausible action is by your local thunderbird client.

I assume you have checked your postfix, dovecot settings to make sure there is no outside program they call...and checked for sure that spamassassin, maildrop, mailman, procmail, etc are not installed and not being used.

must be your local client...

Since you do not have a 'spam' setup on the server, your spam mail goes nowhere...all mail goes to your inbox. Unless there is something you are not telling us.

---

### Post by volkswagner on 2012-04-02
My guess is your password info is sent to a different address.

Check other logs such as error log.

---

### Post by gdtw on 2012-04-02
it turns out that they NEVER sent me the password, and i did not have my password wrong. They said they are reviewing my account and i cannot login before it's approved!

that's quite some high tech! By instinct, the "forgot password" link is supposed to be automated, isn't it?!

at least along the way I did learn something from you guys. I appreciate the help!

---

