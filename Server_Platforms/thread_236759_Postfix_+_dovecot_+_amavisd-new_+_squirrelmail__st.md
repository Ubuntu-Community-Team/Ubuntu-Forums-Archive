---
title: "Postfix + dovecot + amavisd-new + squirrelmail : strange box names"
date: 2006-08-15
forum: Server Platforms
---

### Post by die488 on 2006-08-15
Hi there,

I'm working since 2 days to get this working and it's almost done, one more problem persist, "inboxes" are duplicated :confused: 

When I use squirrelmail to see my mails, I have :
INBOX
  INBOX.Drafts
  INBOX.Sent
  INBOX.Trash
  Drafts
  Sent
  Sent Items
  Trash

as seen on the attached screenshot.

In the config.php of squirrel : 
$default_folder_prefix          = '';
$trash_folder                   = 'INBOX.Trash';
$sent_folder                    = 'INBOX.Sent';
$draft_folder                   = 'INBOX.Drafts';

user@local:~/mail$ ls
INBOX.Drafts  INBOX.Sent  INBOX.Trash

and when I click on each box without the "INBOX." prefix :
ERROR:
ERROR: Could not complete request.
Query: SELECT "Drafts"
Reason Given: Mailbox doesn't exist: Drafts

Where can I correct this ?

Thank you in advance :-P

---

### Post by MJN on 2006-08-15
Howcome you've got the folders as INBOX.Trash etc? Or is that part of your question?

In the Squirrelmail config tool (<mail>/config/conf.pl) go into Option D and enter *Dovecot* as the server type and this will set various defaults properly, including Trash etc falling under the root as opposed to the Inbox.

Give that a go and see if it makes any difference...

Mathew

---

### Post by felobros on 2007-02-20
Hi,
I tried to configure Squirrel in my local language, but I got no problems about duplicated dirs. I think you have to check configurations into "config_default.php", "config.php" also into "conf.pl", where you will find a specific "dovecot" configuration, because seems depends by the INBOX prefix. Verify these sections:

Into config.php:
--------------------
$trash_folder                   = 'INBOX.Trash';
$sent_folder                    = 'INBOX.Sent';
$draft_folder                   = 'INBOX.Drafts';
--------------------

Into conf.pl:
--------------------
        } elsif ( $server eq "dovecot" ) {
            $imap_server_type               = "dovecot";
            $default_folder_prefix          = "";
            $trash_folder                   = "Trash";
            $sent_folder                    = "Sent";
            $draft_folder                   = "Drafts";
            $show_prefix_option             = false;
            $default_sub_of_inbox           = false;
            $show_contain_subfolders_option = false;
            $delete_folder                  = false;
            $force_username_lowercase       = true;
            $optional_delimiter             = "detect";
            $disp_default_folder_prefix     = "<none>";

--------------------

Into config_default.php:
--------------------
$trash_folder = 'INBOX.Trash';
$sent_folder  = 'INBOX.Sent';
$draft_folder = 'INBOX.Drafts';
--------------------

Into config_local.php:
--------------------
$default_folder_prefix = 'INBOX.';
$imap_server_type = 'dovecot';
$trash_folder = 'Trash';
$sent_folder = 'Sent';
$draft_folder = 'Drafts';
--------------------

Also I found another problem with mail clients (Thunderbird and OE). 
Depending of clients internal names , when you use IMAP may be that the mail client create a duplicated "Sent" or "Trash" dir, but however my problem was not with a "INBOX.Trash", but with a "Trash" dir. Now I leaved original tags into squirrel because this is the better configuration.

Perhaps, with squirrel you have to obtain following names:
--------------------
- INBOX
  Drafts
  Sent
  Trash
--------------------

I hope you will find the problem, 'cause I haven't other ideas.
Bye

---

