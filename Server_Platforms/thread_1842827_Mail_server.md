---
title: "Mail server"
date: 2011-09-12
forum: Server Platforms
---

### Post by viperce on 2011-09-12
Hi I need some advise/help
I am currently using Mercury mail on windows server 2008 to retrieve my mail from my ISP and deliver it to my users mail boxs.

I have 1 main account (mainaccount@isp.com) that all my mail goes to and Mercury then sorts them out and everything works well.

I would like to set this all up on Linux, so emails sent to [EMAIL="user1@ISP.com"]user1@ISP.com[/EMAIL] which is delivered to my [EMAIL="mainaccount@isp.com"]mainaccount@isp.com[/EMAIL] and once linux downloads the emails it will put all mails going to [EMAIL="user1@isp.com"]user1@isp.com[/EMAIL] into user1's mailbox to be retrieved by user1 when he checks his email from his windows system (outlook express)

How would i go about this, could someone give me links to howto mailserver on linux for dummies or something :D

I have managed to get the postfix side working, but the pop3 side is still not functioning

Thanks in advance :D

---

### Post by zackwasa on 2011-09-12
Here's a howto that shows how to set this up on Ubuntu:
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

### Post by SeijiSensei on 2011-09-12
> **viperce said:**
> I have managed to get the postfix side working, but the pop3 side is still not functioning

For POP and IMAP services you need to install [dovecot]("http://www.dovecot.org/").

For fetching the mail from your ISP, I recommend [fetchmail]("http://www.fetchmail.info/").

Both of these are in the repositories.

---

### Post by viperce on 2011-09-13
thanks i will look into those, do you know of any guides to help me with this Sensei?

---

### Post by viperce on 2011-09-13
Just wanted to check something with you....So if i wasnt using a ISP and was only doing internal mailing server i would only use Postfix and dovecot? but since i am using a ISP i need Fetchmail as well.

So i will be using 3 apps to do the job of 1......

I tried to take a look at those packages, but i have no idea where to even start.

Do i install & setup dovecot first or fetchmail?

---

### Post by viperce on 2011-09-14
i installed fetchmail yesterday and setup a gmail account on it to test with, fetchmail downloads the emails and places it in the administrator home folder.

how can i change that so it puts it in a folder for my account, so if i send a mail to  [email]account@gmail.com[/email] it gets placed in a folder for account in the home folder so i can retrieve it from my windows machine somehow.

---

### Post by viperce on 2011-09-14
Please correct me if i am wrong with this.

Fetchmail gets its folder delivery settings from dovecot /etc/dovecot/dovecot.conf

> Example of my conf

auth default {
  mechanisms = plain cram-md5
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
  socket listen {
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
protocols = imap pop3 imaps pop3s
mail_location = maildir:/home/vmail/Maildir
Postfix then gets the email from my vmail account and sorts it, so if i send a email to my [EMAIL="accounts@gmail.com"]accounts@gmail.com[/EMAIL] account postfix will collect the mail from my /home/vmail/Maildir and move it to the folder /home/vmail/gmail.com/accounts/

Example of my /etc/postfix/main.cf
> 
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mynetworks = 127.0.0.0/8 192.168.0.0/24
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noplaintext,noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
Example of my vhost file
> 
gmail.com
webmail.co.za
Example of my vmaps
> 
[EMAIL="accounts@gmail.com"]accounts@gmail.com[/EMAIL] gmail.com/accounts/
ok that should be all the conf's
i have checked using telnet the mails are being delivered to the correct folder.

However now when i try to collect the mail from the server using outlook it asks me for the username and password which is correct then says the pop3 server has rejected my login can someone please tell me where i am going wrong???

Thanks again for the help

---

### Post by viperce on 2011-09-14
Found the problems checked the logs and found i had duplicated the user, & after that i found i had not used SSL on client side.

---

### Post by viperce on 2011-09-19
I seem to have jumped the gun a little, this is still not working :(

If i send a mail using "mail [email]user@domain.com[/email]"  the email is delivered to /home/vmail/Maildir/domain/user/new works no problem.

If the mail is recieved by fetchmail it gets delivered to the vmail account /home/vmail/Maildir/new it does not get distributed to the correct mail box :(

Can someone please help me with this.

Thanks again

---

### Post by SeijiSensei on 2011-09-20
I haven't used fetchmail for quite some time now, but if mail for multiple users is delivered to a single remote mailbox (so-called "multidrop" mailboxes in the documentation), you need to add some directives in fetchmailrc to tell it how remote users and local users match up.  Take a look at [this]("http://www.linuxquestions.org/questions/linux-networking-3/multidrop-fetchmail-2260/") and [this](http://www.axigen.com/forum/showthread.php?t=7911) for some help.

The second article uses this command, which may work for you:

```
is * here and wants mda "/usr/sbin/sendmail -i -- %T"
```

That tells fetchmail to take a message addressed to [email]bill@domain.com[/email] in the remote mailbox and deliver it to local user bill using sendmail. You may need to massage the latter command if you use postfix, though it may work correctly as it stands since postfix is designed to emulate sendmail.  (I use sendmail, so I can't help with postfix configurations.)

---

### Post by viperce on 2011-09-26
Thanks Sensei i will look into it just a question, is sendmail better? if i am going to be setting up a mail server i want to do it right the first time :D

also i have been reading a few articles if i send multiple emails to ppl on the domain will they all receive them or will it only send to one and drop the rest?

---

### Post by viperce on 2011-09-26
ok so i been looking around everyone has there preference when it comes to mail pop3/smtp.....
if you wouldnt mind could you guide me through getting this working? 

Could you tell me where to start & what to use i would really appreciate it.

Thanks

---

### Post by viperce on 2011-10-03
OK so after a lot of messing around with settings i have sort of come right
 
added to fetchmailrc
aka mydomainname.com
is *
 
now it downloads the emails gives me this error
 
[EMAIL="user@localhost"]user@localhost[/EMAIL]>: Recipient address rejected: User unknown in local recipient table
the accounts i have setup locally are for [EMAIL="user@domainname.com"]user@domainname.com[/EMAIL] but they are getting renamed to [EMAIL="user@localhost"]user@localhost[/EMAIL] i think this is a simple problem (or should i say i hope so.
Does anyone have a solution for me please.

---

### Post by HermanAB on 2011-10-03
Hmm, once you are tired of faffing around with the mail system, you can install Citadel.  It takes about 20 minutes, does everything and Just Works (TM).

---

### Post by viperce on 2011-10-03
lol not helping but i will check that out as well thanks

---

### Post by SeijiSensei on 2011-10-04
> **viperce said:**
> [EMAIL="user@localhost"]user@localhost[/EMAIL]>: Recipient address rejected: User unknown in local recipient table

If you're using sendmail, check the file referenced by the line starting with Fw in /etc/mail/sendmail.cf.  It usually points to a file that contains all the host and domain names that are considered local.  On my CentOS servers, that file is /etc/mail/local-host-names.  I don't know what it's called in Ubuntu.

Make sure localhost is in that list.  Usually it's the first entry by default, but maybe something is different about your implementation.

If you're using Postfix I can't really help you other than to suggest making sure the Postfix considers user@localhost a proper reference for a local user account.

---

### Post by viperce on 2011-10-04
thanks for steering me in the right direction i made a few changes to fetchmailrc
 
poll pop3.isp.co.za
proto pop3
localdomains domain.co.za
user "[EMAIL="allusers@domain.co.za"]allusers@domain.co.za[/EMAIL]"
pass "password"
is *
keep
 
now when i fetchmail i am getting this :(
 
fetchmail: SMTP> RCPT TO:<user1@domain.co.za>
fetchmail: SMTP< 550 5.1.1 <user1@domain.co.za>: Recipient address rejected: User unknown in local recipient table
fetchmail: SMTP error: 550 5.1.1 <user1@domain.co.za>: Recipient address rejected: User unknown in local recipient table
fetchmail: SMTP listener doesn't like recipient address `user1@domain.co.za'
 
if i send a mail to local user from local it works
 
mail [EMAIL="user1@domain.co.za"]user1@domain.co.za[/EMAIL]
 
message gets delivered to the virtual mailbox under /home/vmail/domain.co.za/user1/new
 
any idea as to what i need to do now??

---

### Post by viperce on 2011-10-05
thanks guys for all the help, i finally seem to have it working
I modified my /etc/fetchmailrc and it is fine now all mails seem to be going to the correct recipient.

> 
poll pop3.isp.co.za
        proto pop3
       ** aka domain.co.za**
        **localdomains domain.co.za** (adding this to my fetchmailrc sorted the problem)
        user "allusers@domain.co.za"
        pass "password"
        is *
        keep

thanks again Sensei for putting up with me :D

---

### Post by SeijiSensei on 2011-10-05
> **viperce said:**
> thanks again Sensei for putting up with me :D

You're welcome.  Sorry I wasn't here to answer every inquiry, but it seems like you put things together yourself, which is obviously the best solution for everyone.

---

