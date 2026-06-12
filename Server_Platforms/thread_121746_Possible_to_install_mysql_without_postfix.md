---
title: "Possible to install mysql without postfix??"
date: 2006-01-25
forum: Server Platforms
---

### Post by glave on 2006-01-25
I've been getting my new server up and running, and I just finished up installing qmail via instructions from qmailrocks.org. Now as I move on to getting mysql up and running, As soon as I try to do apt-get install mysql-server, it informs me that its going to install postfix, which will surely destroy my qmail installation.

I've looked all over, searched googled, but can't see where. Is it not possible to install mysql without having postfix? I ran mysql under slackware jsut fine without it... ?

---

### Post by LordHunter317 on 2006-01-25
It's needed for admin scripts that want to mail you.  You could equivs to create a null package that provides the mail-transfer-agent dependency.

---

### Post by glave on 2006-01-25
equivs ? That's a new term for me... What would I need to do? I definately don't want postfix, I'm much more familiar with qmail, plus its already setup!  :)

---

### Post by LordHunter317 on 2006-01-26
It's a package.

---

### Post by JackDog on 2006-01-26
If postfix isnt running, it wont harm qmail. 

Having used both, I strongly recommend postfix. Its far more configurable and portable. I use a mysql/postfix/courier-imap/tsl setup at home and it works great. No open relays and encryption works with everything. Been running like a champ for 3 years (on a gentoo system). I am sure this would even easier to setup on ubuntu. 

[http://www.gentoo.org/doc/en/virt-mail-howto.xml](http://www.gentoo.org/doc/en/virt-mail-howto.xml)

---

### Post by LordHunter317 on 2006-01-26
[QUOTE=JackDog]If postfix isnt running, it wont harm qmail.[/quote]No, that's not true.  Installing postfix will overwrite qmail's sendmail handler.

---

### Post by Zelut on 2006-01-26
I keep hearing about qmail as well.  right now I'm running just default ubuntu-server with postfix.  Can anyone point me to some reading about security/stability on this?  If postfix is the way to go I'll stick, but I'd like to understand the differences.

---

### Post by JackDog on 2006-01-26
[QUOTE=LordHunter317]No, that's not true.  Installing postfix will overwrite qmail's sendmail handler.[/QUOTE]

You may be right there. If so, someone should email the maintainers. Competing applications should usually be slotted and not interfere with eachother.

---

### Post by LordHunter317 on 2006-01-26
[QUOTE=JackDog]You may be right there. If so, someone should email the maintainers. Competing applications should usually be slotted and not interfere with eachother.[/QUOTE]And it's not a big.  Debian MTAs do conflict with one another so no two mailers try to fufill /usr/sbin/sendmail at the same time.

Qmail isn't packaged in Debian.  Why?  DJB is an asshole.

[quote=kuyaedz]I keep hearing about qmail as well. right now I'm running just default ubuntu-server with postfix. Can anyone point me to some reading about security/stability on this?[/quote]Qmail isn't to be used for new installations.  End of Story.  I can enumerate the reasons again, or you can just search for them, as I've stated them numerous times.  It really goes back to what I just said above, though.

---

### Post by JackDog on 2006-01-26
[QUOTE=kuyaedz]I keep hearing about qmail as well.  right now I'm running just default ubuntu-server with postfix.  Can anyone point me to some reading about security/stability on this?  If postfix is the way to go I'll stick, but I'd like to understand the differences.[/QUOTE]


Well is going to be a holy war as to which one is "better". I do recommend postfix as its more maintained, common and pluggable. Security wise, I am primarily concerned about people getting my user passwords and emails. Using 1024b SSL/TLS definitely helps in that arena. I would say both are equals when it comes to security level. But it depends on how you implement your mail server which will decide how secure your server will be. 

Another big concern is how you relay mail. if you are an open relay, that means anyone can bounce mail off your server and make it look like they can from you, or at least a user in one of your domains. Requiring a valid *from* does not work because they can still use your machine as a relay. You can setup most SMTP servers to only relay based on IP address ranges, but that quickly gets annoying. 

The best way is to allow plain text SMTP **only** when you are the destination and to force auth through over TLS (encrypted) when relaying mail. This prevents unauthorized users from sending email through your machine  (Making you a spam bot), unless they know your user/pass.  Users can then use your SMTP relay from anywhere in the world provided their client supports AUTH over TLS which nearly all clients do (Outlook, TBird, KMail, Evo).  

Setting up courier for encryption is far easier. I would highly recommend only allowing encryption for IMAP and POP as well. Takes a little extra setup, but you will have far less worries. 

Setting up your email server using the above gentoo guide gives you a simplified email server setup with a central authentication mechinism (mysql) for IMAP, POP, SMTP and even System if you want. 

Another recommendation is to keep your maildirs in a central location(/var/mail). Since your accounts will not link to system users unless you want them to, you could have users with no home directory. This is also nice because it prevents broken clients from screwing up the user's maildir. Setup a prefix in the mysql configuration file using the CONCAT SQL method. This will make it so you only have to specify the mailbox in the DB, not the whole path. :p

The only downside to this infrastructure is its a pain to setup. But the admin in the long term is very simple. You can support domains, users and aliases; all with a single SQL INSERT. Squirrelmail also plugs right in and allows the user to change their mysql passwords.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=JackDog]Well is going to be a holy war as to which one is "better".[/quote]No, it's not.  Qmail is obsolete. It doesn't support as many standards as Postfix does.  It's unmaintained, and the only person who can refuses to do so.  It's ultimately a liability because of that.

It's also less performing, and doesn't have a sensical configuration at all.  It's obsolete.  End of story.

> Another recommendation is to keep your maildirs in a central location(/var/mail). Since your accounts will not link to system users unless you want them to, you could have users with no home directory.That is umm, the default behavior.  What is not standard is to deliver to virtual users in the first place.  No MTA in the world ships with virtual users enabled OOB.

---

### Post by JackDog on 2006-01-27
> **LordHunter317]Qmail is obsolete.[/QUOTE]

Well yeah  said:**
> That is umm, the default behavior. What is not standard is to deliver to virtual users in the first place.  

Virtual User - "I do not think it means what you think it means."


[QUOTE=LordHunter317]No MTA in the world ships with virtual users enabled OOB.[/QUOTE]

Wow.


Please troll elsewhere, thanks.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=JackDog]Virtual User - "I do not think it means what you think it means."[/quote]I know exactly what it means.  You obviously do not, however.  I'd love to here your definition.




> Wow.


Please troll elsewhere, thanks.Name one widespread MTA on the planet that ships with virtual users enabled so all I have to do is add the virtual users to a file.  None do on UNIX, because they all support a huge number of databases for virtual users, and as such, must be configured.  At the very least, you have to give them the UID/GID of the system user that owns the virtual mailboxes (unless you're using Cyrus or another MDA that stores stuff not in files, but in a DB).

So no, not only do I resent the trolling implication, I suspect you don't have the faintest idea about what you're talking about.

Your initial posts seems to suggest that, since it's an ugly morass of random topics under the heading "MTA" glued together in a stream-of-conciousness manner without any real value or apparent purpose.

---

### Post by JackDog on 2006-01-27
[QUOTE=LordHunter317]Your initial posts seems to suggest that, since it's an ugly morass of random topics under the heading "MTA" glued together in a stream-of-conciousness manner without any real value or apparent purpose.[/QUOTE]

[QUOTE=LordHunter317]
DJB is an *******.
[/QUOTE]


Are there any mods patrolling here? Is this type of behaviour acceptable in the Ubuntu Forums? :confused: 

If anyone needs more help with a home mail server please start a new thread. This one has gotten a little out of hand.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=JackDog]Are there any mods patrolling here? Is this type of behaviour acceptable in the Ubuntu Forums? :confused:[/quote]Well, you accused me of trolling first and started the personal attacks.  What did you expect in response?  Sunshine and kisses?

It would be hypocritical for you to call a moderate on me when I was nothing but civil to you until you were uncivil to me.  As for the swearing, yes it's considered inappropriate, but it's hardly strictly enforced here.  And frankly, there's not a more terse way to explain DJB's licensing and treatement of his users. 

> If anyone needs more help with a home mail server please start a new thread. This one has gotten a little out of hand.:rolleyes:  Can you even read?  **The thread was never about that in the first place.**

---

