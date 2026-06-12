---
title: "Dovecot and Sieve"
date: 2007-11-03
forum: Server Platforms
---

### Post by spectre_25gt on 2007-11-03
Has anyone got Dovecot working with Sieve? I'm trying to figure out the best way to do it. At the moment, it looks like Sieve needs to be compiled from source, which requires that Dovecot be compiled from source. I would really like to avoid this so that I can keep my packages managed by dpkg.

I'm running on 6.06. Has the sieve plugin been added in a later version of ubuntu?

---

### Post by asimon on 2007-11-03
> **spectre_25gt said:**
> Has anyone got Dovecot working with Sieve? 
Never tried it.
> **spectre_25gt said:**
> 
I'm running on 6.06. Has the sieve plugin been added in a later version of ubuntu?
Yes, the dovecot packages from feisty and current gutsy both contain the sieve plugin.

---

### Post by spectre_25gt on 2007-11-03
Ok, good to know. I'll just have to upgrade to a more recent version, then.

Thanks a bunch.

---

### Post by mwerlberger on 2007-11-05
> **spectre_25gt said:**
> Ok, good to know. I'll just have to upgrade to a more recent version, then.

Thanks a bunch.

I updated to Gutsy recently and set up the sieve support of dovecot. Worked after some tweeking. The only thing i forgot at first was changing the delivery agent to dovecots maildrop. There are quite good documentations on the dovecot homepage... Just read them and go step by step....


Rgds,
 Manuel

---

### Post by Versusnja on 2008-04-26
> **mwerlberger said:**
> I updated to Gutsy recently and set up the sieve support of dovecot. Worked after some tweeking. The only thing i forgot at first was changing the delivery agent to dovecots maildrop. There are quite good documentations on the dovecot homepage... Just read them and go step by step....


Rgds,
 Manuel

I upgraded to Gutsy, but still can not get the sieve plugin working. Tell me what did you do to make it work?

I uncommented mail_plugins = cmusieve string in the config. Then I created .dovecot.sieve file in user's directory. I have the following script:

```

require "fileinto";
if address :is "from" "myemail@ydomain.com" {
fileinto "sieve"
}

```
But it doesn't work. And since sieve doesn't have any logs I can't pin down the problem. 
Any ideas?

---

### Post by Versusnja on 2008-04-26
I also tried setting sieve variable via mysql and in dovecot config in "plugin" section. No result.

---

### Post by spectre_25gt on 2008-05-08
Since Ubuntu is including sieve support with Dovecot now, you should be able to find all you need at [http://wiki.dovecot.org/LDA/Sieve](http://wiki.dovecot.org/LDA/Sieve). 

To be more specific, though, what exactly is the problem? Are you getting an error or is it just not seeing your sieve script at all?

---

### Post by Versusnja on 2008-05-09
Thanks for the reply.
Actually Dovecot WIKI is missing a good FAQ on how to make sieve work. I did my best to improve the existing FAQ in that Wiki. 

Anyway, now my problem is solved.
The problem was that I didn't realise that I must switch my postfix to LDA-deliver. Postifix used it's own LDA and sieve plug-in (which is deliver's plug-in) simply didn't initialize at all.

The solution was as follows:
1. Make postfix ise "Deliver" LDA:
in /etc/postfix/main.cf I added
```
dovecot_destination_recipient_limit = 1
mailbox_transport = dovecot
virtual_transport = dovecot
mailbox_command = /usr/lib/dovecot/deliver

```2. The show postfix how the "dovecot" transport should be used.
In /etc/postfix/master.cf added
```
dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=virtual:virtual argv=/usr/lib/dovecot/deliver -f ${sender} -d ${recipient}
```3. To make sieve easy configurable I added the following to dovecot-sql configuration, to the user_query variable
```
CONCAT('/var/mail/sieve_scripts/','%u') as sieve
```Now all my sieve scripts are in /var/mail/sieve_scripts, each user has its own script with a name equal to e-mail address. I.e. e-mail [EMAIL="user@domain.com"]user@domain.com[/EMAIL] will have a sieve script named "user@domail.com"

I tweaked /etc/dovecot/dovecot.conf a bit as well, but I don't remember if it was sieve related.


Hope this helps somebody.

---

