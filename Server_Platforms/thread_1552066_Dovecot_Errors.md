---
title: "Dovecot Errors"
date: 2010-08-13
forum: Server Platforms
---

### Post by bailewen on 2010-08-13
Still struggling to learn how to set up a mail server....hope you guys can help. :D

Been working through a postfix-dovecot setup as described on this blog:
[http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/comment-page-1/](http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/comment-page-1/) 

Seemed like all was well until I got to the very last step, restarting postfix and dovecot.Postfix seems to work ok but Dovecot gives me the following error:

>  * Restarting IMAP/POP3 mail server dovecot                                     Error: Error in configuration file /etc/dovecot/dovecot.conf line 1115: Unknown section type (section changed in /etc/dovecot/dovecot.conf at line 1077)
Fatal: Invalid configuration in /etc/dovecot/dovecot.conf

line 1115-1124 of my dovecot.conf looks like this:
> 
   master {
      # Master socket provides access to userdb information. It's typically
      # used to give Dovecot's local delivery agent access to userdb so it
      # can find mailbox locations.
      path = /var/run/dovecot/auth-master
      # Default user/group is the one who started dovecot-auth (root)
      mode = 0600
      user = vmail
      group = mail
}

And 1075 - 1077 looks like this:> 
userdb sql {
  args = /etc/dovecot/dovecot-sql.conf
  }


Can anyone tell me what is wrong with those lines or where else to look for the problem?

p.s.
Just out of curiosity I went and checked what my /var/run/dovecot/auth-master file looks like since it's listed there as a path and it looks like it doesn't exist. ??? 
> /var/run/dovecot$ ls
dict-server  login

---

### Post by SlugSlug on 2010-08-13
mine looks like this - note user / group 

  # It's possible to export the authentication interface to other programs:
  socket listen {
    #master {
      # Master socket provides access to userdb information. It's typically
      # used to give Dovecot's local delivery agent access to userdb so it
      # can find mailbox locations.
      #path = /var/run/dovecot/auth-master
      #mode = 0600
      # Default user/group is the one who started dovecot-auth (root)
      #user =
      #group =
    #}
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth
      mode = 0660

user = postfix
group = postfix
    }
}



&&

  # SQL database </usr/share/doc/dovecot-common/wiki/AuthDatabase.SQL.txt>
  #userdb sql {
    # Path for SQL configuration file
    #args = /etc/dovecot/dovecot-sql.conf
  #}

---

