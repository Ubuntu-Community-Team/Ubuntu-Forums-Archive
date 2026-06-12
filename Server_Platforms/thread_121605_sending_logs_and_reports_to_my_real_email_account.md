---
title: "sending logs and reports to my real email account"
date: 2006-01-25
forum: Server Platforms
---

### Post by philosophia on 2006-01-25
i'm interested in redirecting system messages to root to my real email account, as well as emailing logs to my real email account so that it will be more convenient to check logs daily.

1.  i edited /etc/aliases and changed the line to 

root: [email]my@email.com[/email]


then ran 'newaliases'

2. i installed postfix

sudo apt-get install postfix, i also checked /etc/postfix/main.cf - it looked ok so i haven't edited it.

3.  i installed logcheck
apt-get install logcheck, then edited /etc/logcheck/logcheck.conf, substituting my real email address.

i then ran logcheck manually

sudo su -s /bin/bash -c "/usr/sbin/logcheck -m [email]my@email.com[/email]" logcheck

i still do not seem to be receiving any mail from my machine.

have i done anything wrong? i have been trying to do this myself as i have not found much documentation related to this on the net.

---

### Post by philosophia on 2006-01-25
i tried something else:

sudo dpkg-reconfigure postfix

then set up postfix for 'internet with smarthost', plugging in my email address for root.  doesn't seem to be working - running logcheck manually, and i'm still not getting emails...

---

### Post by DeadEnd on 2006-01-25
lol,well keep reporting in how you doing, I am interested in doing such a thing also.
If I finish my other project before nights over, I shall be giving it a whirl .
Sorry cannot be any help.
However if your still unsuccesful when I get round to it and I have a lucky break ill give you a shout,though I am sure you will have this all fixed up by then.

---

### Post by DeadEnd on 2006-01-25
hmm I use webmin and there is postfix utility there and it seems root as alias paul.  paul can be replaced by E-mail address.
hope this might shed some light

---

### Post by DeadEnd on 2006-01-25
alias from  "root"  alias to   "Address [email]someone@gmail.com[/email]"

---

### Post by DeadEnd on 2006-01-25
Just to confirm its all working my end, getting E-mail from ubuntu machine to google account. 
Actually coming from windows I have found webmin to be a blessing in configuring my machine.

---

### Post by philosophia on 2006-01-25
i can't install webmin unfortunately

---

### Post by DeadEnd on 2006-01-25
Well I would assume you only have to do the same with your alias file.
my root inbox uses alias Paul so I assmume instead of just replacing root: paul ,  you need to add "Address someone@gmail" not  "someone@gmail.com" 
ill chk my alias file and see what changes it made l8r but cannot access box at moment.

---

### Post by MJN on 2006-01-25
You sure about that? According to the aliases man page the format takes the form:

[B]_name_: _value1_, _value2_, ...

[/B]where:

[I]name is a local address (no domain part). Use double quotes when the name contains any special characters such as whitespace, &#8216;#&#8217;, &#8216;:&#8217;, or &#8216;@&#8217;. The name is folded to lowercase, in order to make database lookups case insensitive.

[/I]and
[I]
The value contains one or more of the following:  _address_  Mail is forwarded to _address_, which is compatible with  the  RFC 822 standard.[/I]

Thus, **root: [EMAIL="someone@somewhere.com"]someone@somewhere.com[/EMAIL]** would be an example of the proper syntax.

Whether even this should achieve your aim is another story however given you've tried it... ;) (I've no experience of doing this so can't really help)

Mathew

---

### Post by DeadEnd on 2006-01-25
No actually I am not sure thats why I said I assumed, but thank you for posting the info 

I used the webmin tool to forward root inbox to my gmail account the changes I described appeared on my webmin form, I assumed they might also be reflected as such in the the alias file which appears not to be the case 

this is my alias file:   

root: [email]someone@gmail.com[/email]
webmaster: root


I have no linux experiance, only been using for several days so cannot say if webmin has changed anything other than the alias file,it just worked without me having to do anything apart from what I described.

---

### Post by thorndike on 2006-02-15
I have been trying the same thing.  

Unfortunately, when I try to run logcheck manually, I get prompted for a password that doesnt seem to match any password on the system.  I have tried the root password and the user passwords.

Any thoughts?

Thorndike

---

### Post by pwnfactory on 2006-07-19
have you tried running the command:
```
sudo newaliases
```
after modifying the /etc/aliases file

---

