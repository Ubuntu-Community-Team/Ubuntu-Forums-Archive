---
title: "automate creation of mail directorieson mailserver"
date: 2014-06-03
forum: Server Platforms
---

### Post by shad2 on 2014-06-03
with this setting in my dovecot.conf file;
namespace private {
    separator = .
    prefix = INBOX.
    inbox = yes
  mailbox Trash {
    auto = create #no
    special_use = \Trash
  }
  mailbox Drafts {
    auto = create #no
    special_use = \Drafts
  }
  mailbox Sent {
    auto = create #subscribe # autocreate and autosubscribe the Sent mailbox
    special_use = \Sent
  }
  mailbox Spam {
   auto = create #subscribe
   special_use = \Spam
  }
}
i get this error, how can i clear this problem??Any links to tutorials are welcome
 * Restarting IMAP/POP3 mail server dovecot                                     Error: Error in configuration file /etc/dovecot/dovecot.conf line 12: Unknown section type (section changed in /etc/dovecot/dovecot.conf at line 8)
Fatal: Invalid configuration in /etc/dovecot/dovecot.conf
                                                                         [fail]

---

