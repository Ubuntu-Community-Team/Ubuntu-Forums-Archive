---
title: "Getmail + Dovecot: How to filter spam with Spamassasin?"
date: 2011-05-02
forum: Server Platforms
---

### Post by Demented ZA on 2011-05-02
I have a system running at home that uses Getmail to retrieve mail from my ISP's pop server. Dovecot then offers that mail over IMAPs to my desktops running Thunderbird.

The reason I have resorted to using Getmail is because I don't have a static IP (from my ISP) for my server, and thus this server doesn't act as an MX.

I have implemented Spamassassin in my Getmail script as described [here]("http://www.howtoforge.com/debian_etch_getmail_p2").

From further research, I understand that in order to fully utilize Spamassassin 's potential, I have to resort to training it with SA learn.

Currently I still receive spam messages, but 50% of spam is marked as ****SPAM****, and the other half is not marked at all.

My question is this:

1) How do I get getmail to move messages marked as spam by spamassasin to be moved to a JUNK folder within my mailbox automatically?

2) I thought of creating a folder where my users can move messages they deem to be spam, and set up a crontab script to invoke salearn regularly on this folder to get the bayes engine to learn from it. Is this the correct way of doing it?

I'm open to suggestions.

---

### Post by SeijiSensei on 2011-05-02
> **Demented ZA said:**
> 1) How do I get getmail to move messages marked as spam by spamassasin to be moved to a JUNK folder within my mailbox automatically?

I've not used getmail, but if you can configure its "delivery agent" then see if you can use procmail for final delivery. (If getmail hands messages to sendmail or postfix, make the procmail the delivery agent for that program.) You can write rules in either the system-wide /etc/procmailrc or in users' ~/.procmailrc files that are triggered by regular expressions appearing in the headers or body of a message.  If you put this rule into /etc/procmailrc, for instance, it will route all SPAM messages to the user's spam folder:

```

:0
* ^Subject.*\*\*SPAM\*\*
$HOME/mail/spam

```

This looks through the headers of each message for the string "**SPAM**" in the Subject line.  Notice I had to escape the asterisks since they have a special meaning in regular expressions.

> 2) I thought of creating a folder where my users can move messages they deem to be spam, and set up a crontab script to invoke salearn regularly on this folder to get the bayes engine to learn from it. Is this the correct way of doing it?

That's a common method, yes.  You'll have to make the folder world-writable, of course, and symlink it to each user's folder collection.  You'll probably also want to use the "[sticky bit]("http://linuxdevcenter.com/pub/a/linux/lpt/22_06.html")" (chmod 1777) on the shared folder as /tmp does.  Make sure you also give the sa-learn script some "ham" as well.  In order for the inference engine to work properly, it needs to have a database of both "hammy" tokens and "spammy" tokens.

I wouldn't rely entirely on Bayes to find the other half of your spam.  You'll be much better off [writing custom SpamAssassin rules]("http://wiki.apache.org/spamassassin/WritingRules") for identifiable repeated spams.  You also might want to consider whether lowering the score threshold for tagging messages as spam might improve your filtering.  You have to be careful about false positives, of course, so you'll need to review a decent-sized corpus of these potentially-spam messages before making any changes.

---

### Post by Demented ZA on 2011-05-02
Thank you for your reply!

Is this what you had in mind? (Off the Getmail website)

> 
How do I use procmail with getmail?

Simply invoke procmail as an external MDA. procmail requires that one of the following be true:

    that the message begin with a Unix "From " line (the mbox message delimiter)
    that procmail is invoked with the -f option supplying the envelope sender, so that it may generate the "From " line 

To have getmail generate and prepend the "From " line to the start of the message, set the MDA_external parameter unixfrom to True:

```
[destination]
type = MDA_external
path = /path/to/procmail
unixfrom = True
```To supply the -f option to procmail, do something like this:

```
[destination]
type = MDA_external
path = /path/to/procmail
arguments = ("-f", "%(sender)")
```Of the above two code segments, I suppose I can use either one?

This is what any typical getmail rcfile will look like (correct me if I'm wrong):
```
[retriever]
type = SimplePOP3Retriever
server = pop3.mydomain.com
username = user@mydomain.com
password = M^q]B6;848{=2>2A[@#TZa0mG #Some password

#[destination]
#type = Maildir
#path = /home/user/Maildir/

[options]
delete = true
read_all = false

[filter]
type = Filter_external
path = /usr/bin/spamc
#arguments = ("-s 250000", ) This gave issues. I created /etc/spamassassin/spamc.conf and configured this there as well as host and port to get spamc (Spam Assassin client) to work.

[destination]
type = MDA_external
path = /usr/bin/procmail
unixfrom = True
```

Also, a sample /home/user/.procmailrc (per user filter = NICE!) file delivering ***SPAM*** to junk folder on Maildir to be visible for IMAP clients:

```
DROPPRIVS=YES
ORGMAIL=/home/user/Maildir/ #replace user with The name of the user where this file resides. Suppose a variable like %u could also work?
DEFAULT=${ORGMAIL}

:0
* ^Subject.*\*\*SPAM\*\*
.junk/


```Does that look correct? I'm gonna go hunt some spam and see what it does.

You mentioned:
>  You'll have to make the folder world-writable, of course, and symlink it to each user's folder collection.If I do that method, wouldn't every user be able to see each others (reported spam) mail? If I wanted to avoid a shared folder, could I not have a script running sa-learn on each individual folder? I suppose setting folder permissions would be a minor obstacle. If sa-learn needs all mails to be in the same folder, a script could copy them to a consolidate folder first?

I suppose I can apply the same principal to ham, and ask users to copy some non spam correspondence into a folder for training. I don't know if its wise using the inbox. Spam could have landed in there before a user had the opportunity to sort it. Or is it negligible? I suppose it depends on how much spam comes through.

> I wouldn't rely entirely on Bayes to find the other half of your spam.  You'll be much better off [writing custom SpamAssassin rules]("http://wiki.apache.org/spamassassin/WritingRules") for identifiable repeated spams.Good advice, but I suppose it would be good to get the basics working first, and worry about creating rules when the basics aren't good enough. At least that's what the introduction of your link suggests :-)

Once again, thank you for your response.

---

### Post by Demented ZA on 2011-05-03
This seems to work now. All that's left to do are the folders for spam and ham and the crontab entries for sa-learn.

Maybe when I'm done I could write up a guide for the above: A mail server that is not an MX, doing POP aggregation, but unlike The [Ubuntu Community POP3Aggregator]("https://help.ubuntu.com/community/POP3Aggregator"), I'm bringing the project back to a standard mail server model and is thus easier to modify and add capabilities to.

I'd still appreciate your insight on the spam nad ham folders, thanks!

---

### Post by SeijiSensei on 2011-05-03
> **Demented ZA said:**
> 
```
:0
* ^Subject.*\*\*SPAM\*\*
.junk/
```

If you're using mbox mailboxes, then omit the slash after "junk".  By putting a period before it, you're creating a hidden folder.  Is that what you want?  If not, just make the destination simply "junk".  If your using Maildir, then you probably want a directory like "junk/".  That's just a guess, though, since I use mbox folders.

> If I do that method, wouldn't every user be able to see each others (reported spam) mail? 

Then make the shared folder's permissions be:

```
chmod uga-r,uga+w found-spam
```

which lets everyone write to the file but no one (other than root, of course) is able to read it.

> If I wanted to avoid a shared folder, could I not have a script running sa-learn on each individual folder?

Sure.  Just iterate over /home/user/mail/found-spam and apply sa-learn to each one.

I'd consider creating a ham folder based on items that scored low (<=2 say) on SpamAssassin.

> is it negligible? I suppose it depends on how much spam comes through.

It's definitely a bad idea to include spams in the ham corpus.  The Bayes engine will start to associate message tokens with the wrong type of message.

Glad I could help!

---

### Post by Demented ZA on 2011-05-03
> **SeijiSensei said:**
> If you're using mbox mailboxes, then omit the slash after "junk".  By putting a period before it, you're creating a hidden folder.  Is that what you want?  If not, just make the destination simply "junk".  If your using Maildir, then you probably want a directory like "junk/".  That's just a guess, though, since I use mbox folders.


I use Maildir. Using .junk/ is actually the correct method. I found it somewhere in the Procmail documentation, and it already works. Just googling for it I cant find the exact source, but I found another site, [here]("http://blog.dreamhosters.com/kbase/index.cgi?area=2626"), where this is discussed as well.

Considering your advice, I've decided I'd like to do the following:


[LIST]
[*]Create a folder in a users Maildir Mailbox for Ham, and ask users to _COPY_ non spam mail to these folders for non-spam training.
[*]Create a folder in a users Maildir Mailbox for Spam, and ask users to _MOVE_ spam to this folder.
[*]I will set up a per user crontab entry for sa-learn->ham and sa-learn-spam to traverse non-spam and spam respectively on say a daily basis, using a per-user bayes database, stored in a hidden folder per user.
[/LIST]
My reasoning for the abovementioned is:


[LIST]
[*]It is simple to explain to my users, and easy for them to carry out.
[*]Their directories are still private, with full rw access allowing them to
[*]Make mistakes, such as moving an important message to spam by accident. They can still go in and retrieve it, without having to ask me to do it for them.
[*]Such mistakes won't affect the bayes learning as is stated in the docs that  Spamassassin will make the correct association on the next pass(if they remove the mail out of spam folder and move it or a copy to ham folder allowing sa-learn to rectify it on the next pass).
[*]Having per user bayes databases, will allow for a more accurate and  tailored spam filter, as not every user gets the same kind of mail.
[*] It also means that one user's mail patterns are not affecting the entire domain.
[*]Its simple to set up, and I don't even have to set permissions.
[/LIST]
Users will have to do their own emptying of messages in spam and ham folders after training happened. Doing this automatically has the potential of getting important mail (false positives that havn't been read by the user) deleted, and ultimately I'll get blamed. If they do their own clearing out, I can't take the blame. I even thought of having my script perform a backup of all mail including spam when it runs. This way I reduce risk of losing mail, but also keep a copy of spam for each user in case bayes hasn't learned as I want it to, and want to re-train bayes in future. Spam is always hard to come by when your looking for it, lol.

Thank you for your help. I'll continue with my plan, and post back here for the benefit of others.

---

### Post by Demented ZA on 2011-06-23
I know its been almost two months since I visited this thread, but I've been busy and havn't had much time to look into this until now.

To recap, I have my setup working for the most part. Postfix is checking for ***SPAM*** headers added by spamassasin, and moves them to the users Junk folder in his Maildir mailbox. Under the Users Junk folder resides the following two sub folders:

[LIST]
[*]Learn Ham
[*]Learn Spam
[/LIST]
At Midnight, I have a cron script running for each user that invokes sa-learn on the Learn Ham forlder to train non spam, and then again on the Learn Spam folder to train Spam.

Once done, the script notifies the user by mail of the result.

This is my cron entry:
```
1 4 * * * /var/scripts/./spam | mail -s "Spam Report" owner@address.com
```The script:
```
echo "Learned Spam:"
sa-learn --no-sync --spam ~/Maildir/.Junk.Learn Spam/{cur,new}
echo "Learned Non-Spam:"
sa-learn --no-sync --ham ~/Maildir/.Junk.Learn Ham/{cur,new}
```This all works fairly well, however, I'd like to simplify some things:

[LIST=1]
[*]**Most important:** Once messages in the "Learn Ham" folder have been learned, I'd like the  script to remove spamassasin markup. It would also be nice to move these  messages once processed to the inbox, but I'm not sure if this is the  right thing to do or if its practical?
[*]Once messages in the "Learn Spam" folder have been learned, I'd like the script to move these messages to the Junk folder (the parent folder), and maybe even add the ***SPAM*** markup.
[/LIST]
How do I go about accomplishing the above two points? Reading up about it, I'm supposed to invoke spamassasin -d or with --remove-markup, but I cannot find anything on doing this with Maildir type mailboxes. Wouldn't it be better to use the MDA for this purpose? 

Maybe I'm going about it wrong, so I thought I'd ask you guys first to point me in the right direction :tongue:

---

