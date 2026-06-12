---
title: "Linking mail groups from /etc/aliases to Mailman for archive purpose"
date: 2014-07-03
forum: Server Platforms
---

### Post by Arun_T_Raj on 2014-07-03
I have configured mail server with postfix as MTA and Dovecot as MDA. Ubuntu version is 12.04. Also created mail groups in /etc/aliases. Mailing is working perfect. For archiving purposes I have now installed 'Mailman'. The problem with me is, how I could link mail groups in /etc/aliases to mailman so that mail send to groups specified in /etc/aliases be archived in mailman. :(

Is it possible adding users to mail groups in /etc/aliases may reflect the same to groups in mailman. 

eg: I have a mail group with name 'all@domain.com' with users 'bob' 'das' and 'sob'. Entry in /etc/aliases is as follows:
------------------
     all: bob,das,sob
------------------
     What will be the steps I should do, to archive the mails I send to 'all@domain.com', using Mailman. In future I would like to add or remove users to 'all' in
     /etc/aliases. Whether I need to update the same in mailman also. 

Thanks in advance for your kind help.  :p

---

### Post by deadflowr on 2014-07-03
Thread moved to server platforms

---

### Post by SeijiSensei on 2014-07-03
Are you trying to convert the alias into a mailman listserver subscription list, or just include the people in the alias as subscribers?  

If the latter, the simplest solution is to subscribe the alias to the list.  If the former, you'll need to subscribe each member of the alias to the list.

Frankly, if you're only talking about small groups, and you don't need to let people subscribe themselves, something like Mailman is overkill.  I manage listservers for a couple of clients (using a heavily-modified version of the ancient majordomo and a less-modified version of the majordomo2 rewrite).  All these lists have between 50 and 500 subscribers.  They are all also "moderated" which means subscription requests must be approved by an administrator.  Listserver software is designed to manage these types of subscription arrangements.

In reality, most listserver software actually uses aliases to send out traffic.  The /etc/aliases format permits entries of the form:
```
alias:     :include:/path/to/some/list/of/addresses
```
Programs like Mailman manage the process of adding and deleting addresses from the list in the referenced file.

If you want to archive the traffic without using Mailman, just create another user, say "archive", and add it to the group in /etc/aliases.  If you also want to convert the archived messages into web pages, I suggest using [hypermail]("http://www.hypermail-project.org/").  It's in the repositories.  It expects the messages to be stored in mbox format, though.  If you're using Maildir, hypermail won't work with that.

---

### Post by Arun_T_Raj on 2014-07-07
Thanks SeijiSensei, for the reply. First of all sorry for the late posting as I were hospitalized for past two days. I will definitely reply after checking.

---

### Post by Arun_T_Raj on 2014-07-07
I have 15-20 mail groups with members, which I am managing in /etc/aliases file. Currently I have no archive facility, the mails are directly delivered to group members without archiving. 

My requirement is, I need to archive the mails which are send to some of those mail groups. It would be better if the mails get archived monthly and I can view those on browser, say firefox. Whether 'hypermail' have those features. 

Now I configured Mailman to archive mails.  As per your advice I have subscribed the alias which have members in `/etc/aliases`, to the Mailman list. The test mail I send to the mail-list in Mailman is archived :p. But the mail was not delivered to the group members in `/etc/aliases` :mad:.

`tail -f /var/log/mail.log`  returned following log:

```
[INDENT]Jul  7 10:42:27 box19 postfix/local[24521]: 76CC91082950: to=<test@abc.com>, relay=local, delay=0.2, delays=0.06/0/0/0.14, dsn=2.0.0, status=sent (delivered to command: /var/lib/mailman/mail/mailman post test)
[/INDENT]

```

If I am using other archiving client other than Mailman, whether I can shift all the data to the new server successfully. Please help. Thanks in advance.....

---

### Post by SeijiSensei on 2014-07-09
I have a highly-customized listserver that uses majordomo as the engine.  For archiving, I create a local account on the server and subscribe it to the list.  As I said before, this works well with mbox mailboxes and hypermail.  It won't work if you use Maildir.

Each hour I run a script that does various housecleaning tasks including running hypermail so the messages can be visible on the web.  A typical hypermail configuration file looks like this:
```

# mode for created files
set hm_filemode         = 0644
# where the mail is delivered
set hm_mbox             = /home/listowner/mail/listname/Current
# where the website archive is located
set hm_dir              = /var/www/listname/archive/Current
# other stuff
set hm_about            = "http://lists.example.com/listname/"
set hm_reverse          = 1
set hm_label            = "My Archived Listserver"
set hm_overwrite        = 1
set hm_defaultindex     = "thread"
ignore_types            = text/x-vcard application/ms-tnef

```
On the first of each month a script runs that repoints the symbolic link "Current" to the current year/month combination.  So this month, the mailbox file is /home/listowner/mail/listname/14/07, and the same is true for the website directory.

I don't know why mailman is not sending to the alias.  When you post a message to the list, do you see the consequent outbound traffic from Postfix?  You should see log entries for each delivery to the subscribed addresses.  What happens to the alias?  

I realized after I posted that suggestion that subscribing the alias means its members will not be able to post since their individual addresses are not subscribed to the list.  You probably need to disassemble the aliases and subscribe each individual address in Mailman. Take a look at the "add_members" command in the "bin/" directory under the mailman root, the same directory as commands like "newlist".  Running "bin/add_members --help" produces this:
```

Add members to a list from the command line.

Usage:
    add_members [options] listname

Options:

    --regular-members-file=file
    -r file
        A file containing addresses of the members to be added, one
        address per line.  This list of people become non-digest
        members.  If file is `-', read addresses from stdin.  Note that
        -n/--non-digest-members-file are deprecated synonyms for this option.

    --digest-members-file=file
    -d file
        Similar to above, but these people become digest members.

    --welcome-msg=<y|n>
    -w <y|n>
        Set whether or not to send the list members a welcome message,
        overriding whatever the list's `send_welcome_msg' setting is.

    --admin-notify=<y|n>
    -a <y|n>
        Set whether or not to send the list administrators a notification on
        the success/failure of these subscriptions, overriding whatever the
        list's `admin_notify_mchanges' setting is.

    --help
    -h
        Print this help message and exit.

    listname
        The name of the Mailman list you are adding members to.  It must
        already exist.

You must supply at least one of -r and -d options.  At most one of the
files can be `-'.

```

---

### Post by Arun_T_Raj on 2014-07-18
Thanks [**[COLOR=#000000]SeijiSensei   [/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")  for your reply, My issue is solved my creating system user, similar to the mail group name I had in '/etc/aliases' file. After creating the corresponding system user, mail is successfully delivered to it's group members.

Thanks again for your help.

---

