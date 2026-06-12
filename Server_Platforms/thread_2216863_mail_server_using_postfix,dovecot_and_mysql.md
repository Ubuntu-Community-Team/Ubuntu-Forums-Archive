---
title: "mail server using postfix,dovecot and mysql"
date: 2014-04-14
forum: Server Platforms
---

### Post by shad2 on 2014-04-14
I have set up a mialserver on my computer.when I test it, it shows the message below on the terminal
 telnet bab-laptop 25
Trying 127.0.1.1...
Connected to bab-laptop.
Escape character is '^]'.
220 babel-laptop ESMTP
ehlo babel-laptop
250-babel-laptop
250-PIPELINING
250-SIZE 10485760
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

but when i check the connection to pop3, i get
telnet babl-laptop pop3
Trying 127.0.1.1...
Connected to bab-laptop.
Escape character is '^]'.
+OK Dovecot ready.
user [EMAIL="aretab@babel-laptop.localh"]aretab@bab-laptop.localh[/EMAIL]ost
+OK
pass getinabcd
-ERR [IN-USE] Temporary authentication failure.
 What is the problem here,what can i do to be able to send email,and check mail?

---

### Post by SeijiSensei on 2014-04-14
You probably didn't enable [plain-text passwords in dovecot]("http://wiki2.dovecot.org/Authentication/Mechanisms").

---

### Post by shad2 on 2014-04-15
Thanks sensei
I have followed this [tutorial]("http://www.tummy.com/software/vpostmaster/recipes/dovecotsasl.html") but now Iam getting
telnet bab-laptop pop3
Trying 127.0.1.1...
Connected to bab-laptop.
Escape character is '^]'.
+OK Dovecot ready.
user [email]aretab@bab-laptop.localh[/email]ost 
+OK
pass getinabcd
-ERR Authentication failed.

Where is the problem now???

---

### Post by shad2 on 2014-04-15
Thanks sensei
I have followed this [tutorial]("http://www.tummy.com/software/vpostmaster/recipes/dovecotsasl.html") but now Iam getting
telnet bab-laptop pop3
Trying 127.0.1.1...
Connected to bab-laptop.
Escape character is '^]'.
+OK Dovecot ready.
user [EMAIL="aretab@bab-laptop.localh"]aretab@bab-laptop.localh[/EMAIL]ost 
+OK
pass getinabcd
-ERR Authentication failed.
Also why is it that Iam not able to send email  locally from the terminal to another email?

Where is the problem now???
in etc.dovecot/dovecot-sql.conf ,I have:
driver = mysql
connect = host=127.0.0.1 dbname=mail user=areta_admin password=areta_kab
default_pass_scheme = CRYPT
password_query = SELECT email as user, password FROM users WHERE email='%u';

---

### Post by SeijiSensei on 2014-04-15
I was talking about the password exchange between the IMAP client and dovecot, not between dovecot and the back end authenticator, your MySQL database in this case.  Did you read the section from the dovecot manual I linked to before?

What is the value for "auth_mechanisms"?

---

### Post by shad2 on 2014-04-15
which is the imap client you are refferinf to?currently iam trying it out at the terminal.

---

### Post by SeijiSensei on 2014-04-15
Yes, and you're using telnet to accomplish the same task that a program like Thunderbird does.  You are typing your password in plain text, so dovecot needs to have plain-text authentication enabled.

Once again, what is the value for "auth_mechanisms"?

---

### Post by shad2 on 2014-04-16
this is my dovecot.conf:
protocols = imap imaps pop3 pop3s
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/home/bab/vmail/%d/%n/Maildir

ssl_cert_file =  /etc/ssl/certs/01.pem
ssl_key_file = /etc/ssl/private/bab-laptopserver.key

namespace private {
    separator = .
    prefix = INBOX.
    inbox = yes
}

protocol lda {
    log_path = /home/bab/vmail/dovecot-deliver.log
    auth_socket_path = /var/run/dovecot/auth-master
    postmaster_address = postmaster@babel-laptop
    mail_plugins = sieve
    global_script_path = /home/bab/vmail/globalsieverc
}

protocol pop3 {
    pop3_uidl_format = %08Xu%08Xv
}

auth default {
    user = root
    mechanisms = plain login cram-md5
    passdb sql {
        args = /etc/dovecot/dovecot-sql.conf
    }

    userdb static {
        args = uid=5000 gid=5000 home=/home/bab/vmail/%d/%n allow_all_users=yes
    }

    socket listen {
        master {
            path = /var/run/dovecot/auth-master
            mode = 0600
            user = babel
        }

        client {
            path = /var/spool/postfix/private/auth
            mode = 0660
            user = postfix
            group = postfix
        }
    }
}

Also i just found this in my pam.d/smtp file
auth    required   pam_mysql.so user=mailadmin passwd=newpassword host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1
account sufficient pam_mysql.so user=mailadmin passwd=newpassword host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1

it also doesn't have to be encrypted iguess

---

### Post by Ms_Angel_D on 2014-04-17
By far the easiest way I've found to get Mail plus other servers up and running is to install [virtualmin]("http://www.virtualmin.com/download.html") on a fresh server setup...just thought I would pass this along for future reference.

---

