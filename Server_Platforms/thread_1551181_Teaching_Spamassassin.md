---
title: "Teaching Spamassassin"
date: 2010-08-12
forum: Server Platforms
---

### Post by duceduc on 2010-08-12
I have setup a mail server and is working. I want to teach spamassassin how to distinguish spam from ham. I used this [tutorial]("http://flurdy.com/docs/postfix/#config-adv-spam") along with [this one]("http://flurdy.com/docs/postfix/edition5.html#conf_cont_spam").  It briefly explains how to setup Spamassassin but I don't understand how to input the *sa-learn* command. 

I installed everything that was suggested on the tutorial. I am using squirrelmail at the moment to collect my spam mails. From here I don't know where the spam folder is kept on the server in which I have created in Squirrelmail.

---

### Post by edkasky on 2010-08-12
Try the docs at spamassassin.org -
[http://spamassassin.apache.org/full/3.3.x/doc/sa-learn.html](http://spamassassin.apache.org/full/3.3.x/doc/sa-learn.html)  

Very simply, the default to start a valid bayes database SA is to collect 200 spam messages and 200 ham messages.  Keep them in separate mailboxes on the server and then run sa-learn for each.  This is the command I use.  I specify the username as I use a mysql implementation of bayes and the db is owned by spamd.  And I like to see the dots ;) :

sa-learn --showdots --username=spamd --spam --mbox < [spam mail]
 or
sa-learn --showdots --username=spamd --ham --mbox < [ham mail]

HTH some -

Ed

---

### Post by duceduc on 2010-08-13
Thank. I ran sa-learn and it seems to learned 80% from the spam folder and 100% from the ham.
I was testing some of the actual emails from the spam folder by forwarding it using an internal user account. The email was coming through, however. Was this test valid since the sender was a trusted user?

I also noticed that I am getting s cron noticed email. How can I resolve this issue? 
```
bayes: cannot open bayes databases /etc/spamassassin/bayes_* R/O: tie failed: Permission denied
bayes: expire_old_tokens: locker: safe_lock: cannot create tmp lockfile /etc/spamassassin/bayes.lock.web-server.5042 for /etc/spamassassin/bayes.lock: Permission denied
```

---

### Post by duceduc on 2010-10-04
I had it working awhile back, but when I try it now to learn some spam emails, the output says 
'Learned tokens from 0 messages(s) (0 message(s) examined)'

I have a folder labeled 'Learn as Spam'

The script I use to teach spamassassin was this
sa-learn --spam --showdots --mbox /var/mail/virtual/noreply/Learn as Spam

Am I doing something wrong?

---

### Post by SeijiSensei on 2010-10-04
> **duceduc said:**
> The script I use to teach spamassassin was this
sa-learn --spam --showdots --mbox /var/mail/virtual/noreply/Learn as Spam


Get rid of the spaces in the mailbox name.  Unless you escape the spaces with \ or use quotes around the mailbox path, bash will treat "as" and "Spam" as additional command-line parameters, not as part of the mailbox name.  Rename the mailbox to something like learn-as-spam or learn_as_spam or use just a single word for the mailbox name.

---

### Post by duceduc on 2010-10-04
Thanks for your reply!! I think I got it working by renaming the folder to
```
Learn_as_Spam
Learn_as_Ham
```
I just need to run some tests to see if it is really classifying the emails as spam.

I named it that way because I was following a script to automatically scan for ham and spam emails.I followed this how to.

[http://hash-pipe.com/2008/09/im-teaching-spam-assassin-about-the-spam-in-my-maildirs/](http://hash-pipe.com/2008/09/im-teaching-spam-assassin-about-the-spam-in-my-maildirs/)

It also mentioned that the emails will be deleted after 30 days. However, my emails have not been deleted. The script I used is here. I am not sure where in the script to look for for having scanned emails deleted after 30 days.

```
#!/usr/bin/env python

"""learn_spam_and_ham

Train spam assassin on the messages in particular Maildir folders,
then move the spam to the Junk folder, and (some of) the ham to the
Trash.

On success produces no output, making it suitable to be run by cron.

Eric Wollesen <ericw at xmtp dot net>
2008-09-04
"""

import os
import pwd
import sys
from mailbox import Maildir
from tempfile import NamedTemporaryFile
from subprocess import Popen, PIPE, STDOUT

__version__ = "0.1"

DEBUG = False
INBOX_FOLDER = "/var/spool/mail/virtual/noreply"
SPAM_FOLDER = "/var/spool/mail/virtual/noreply/.Junk"
TRASH_FOLDER = "/var/spool/mail/virtual/noreply/.Trash"
SPAM = [
    "Learn_as_Spam",
]
HAM_THEN_TRASH = [
    "Learn_as_Ham",
]
HAM = [
    "INBOX.Commits",
    "INBOX.NASIOC",
    "INBOX.DIAG",
    "INBOX.RailsCore",
    "INBOX.URUG",
    "INBOX.SLLUG",
]
SPAMASSASSIN_USER = "spamd"
SPAMASSASSIN_BAYES_DIR = "/etc/spamassassin"

def GenerateFoldersFile(inbox):
    """Generate a "folders" file

    The folders file is a temporary file appropriate for use with the
    --folders flag of sa-learn.  See sa-learn(1p) for more info.
    """

    folders_file = NamedTemporaryFile(prefix="learn_spam_and_ham-")
    for folder in sorted(inbox.list_folders()):
        dir = "%s/.%s" % (INBOX_FOLDER, folder)
        if folder in SPAM:
            folders_file.write("spam:detect:%s/cur\n" % dir)
            folders_file.write("spam:detect:%s/new\n" % dir)
        elif folder in HAM or folder in HAM_THEN_TRASH:
            folders_file.write("ham:detect:%s/cur\n" % dir)
            folders_file.write("ham:detect:%s/new\n" % dir)
    folders_file.flush()
    if DEBUG:
        folders_file.seek(0)
        print folders_file.read()

    return folders_file

def RunSaLearn(folders_file):
    """Run the sa-learn program

    Runs sa-learn, passing a file that lists each of the Maildir
    directories to be learned as spam or ham.

    If sa-learn returns non-zero, redirect its output to our stderr.

    Returns sa-learn's return value.
    """

    args = ["sudo", "sa-learn", "--folders=%s" % folders_file.name]
    if DEBUG:
        args.insert(0, "echo")
    p = Popen(args, stdin=None, stdout=PIPE, stderr=STDOUT)
    ret = p.wait()
    if ret:
        print >>sys.stderr, "Error running sa-learn:"
        print >>sys.stderr, p.stdout.read()

    return ret

def ChownBayesFiles():
    """Chown the bayesian records files to spamassassin."""

    # we use system rather than os.chown, because sudo can be setup to
    # allow and restrict it's use.
    args = ["sudo", "/bin/chown", SPAMASSASSIN_USER,]
    if DEBUG:
        args.insert(0, "echo")
    for file in os.listdir(SPAMASSASSIN_BAYES_DIR):
        if file.startswith("."):
            continue
        path = os.path.join(SPAMASSASSIN_BAYES_DIR, file)
        p = Popen(args + [path], stdin=None, stdout=PIPE, stderr=STDOUT)
        ret = p.wait()
        if ret:
            msg = p.stdout.read()
            if re.search("No such file or directory$", msg):
                continue # suppress this error
            print >>sys.stderr, "Error running chown:"
            print >>sys.stderr, p.stdout.read()

def MoveAndClearMessages(source, dest, dest_str="the bit bucket"):
    """Move messages, and clear their source Maildir

    Move the messages in the source Maildir to the destination
    Maildir, then remove all messages from the source Maildir.
    """

    for idx, msg in source.items():
        if DEBUG:
            print "Move to %s: %s" % (dest_str, msg["subject"])
        else:
            dest.add(msg)
    if not DEBUG:
        source.clear()

def MatchingFolders(inbox, list):
    """Return a list of matching Maildir directories

    Finds which of the folders in the list exist within the inbox
    Maildir.
    """

    ret = []

    for folder in inbox.list_folders():
        if folder in list:
            ret.append(inbox.get_folder(folder))

    return ret


if "__main__" == __name__:
    inbox = Maildir(INBOX_FOLDER, factory=None, create=False)
    junk = Maildir(SPAM_FOLDER, factory=None, create=False)
    trash = Maildir(TRASH_FOLDER, factory=None, create=False)

    ret = RunSaLearn(GenerateFoldersFile(inbox))
    if ret:
        print "Errors running sa-learn, not moving any messages."
        sys.exit(ret)
    for folder in MatchingFolders(inbox, SPAM):
        MoveAndClearMessages(folder, junk, "Junk")
    for folder in MatchingFolders(inbox, HAM_THEN_TRASH):
        MoveAndClearMessages(folder, trash, "Trash")
    ChownBayesFiles()
)
```

---

