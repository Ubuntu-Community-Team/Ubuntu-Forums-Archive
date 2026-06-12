---
title: "email server login!"
date: 2012-08-10
forum: Server Platforms
---

### Post by leejewitt on 2012-08-10
hi i need help with a dovecot imap server, i have set it up to receive mail for these 2 domains, 
xtcservers.co.uk
areet.co.uk

and both receiving mail fine for users.

but i just cant login to the server to view mail apart from the read user mail plugin on webmin.
i have set "[B]Disallow plaintext authentication in non-SSL mode?" to NO
[/B]
when i connect using mutt i get to password prompt and get login failed.

i have tried most of the auth methods e.g PAM, passwd, shadow. with no luck and cant seem to find any help elsewhere.

just ask what config files you would like to see as there seems to be a few for dovecot so not pasting them all here.


cheers lee

---

### Post by Bachstelze on 2012-08-10
Post the output of [font=monospace]doveconf[/font], as well as your .muttrc on the client-side.

(Also you should really not use webmin.)

---

### Post by leejewitt on 2012-08-10
[FONT=monospace]**[COLOR=Red]doveconf[/COLOR]**[/FONT]

can't get text to stay in format sorry link to text file>
[URL="http://xtcservers.no-ip.org/new.txt"]
[COLOR=Blue]http://xtcservers.no-ip.org/new.txt[/COLOR][/URL]

Not sure were the .muttrc file is.

---

### Post by Bachstelze on 2012-08-10
.muttrc is in your home directory, it is your personal mutt configuration file. If you have not modified it and are running on default settings, it's not surprising that you can't login. To login with IMAP+SSL you need something like

```
# Automatically log in to this mailbox at startup
set spoolfile="imaps://user@host/"
# Define the = shortcut, and the entry point for the folder browser (c?)
set folder="imaps://user@host/INBOX"
set record="=Sent"
set postponed="=Drafts"

# activate TLS if available on the server
set ssl_starttls=yes
# always use SSL when connecting to a server
set ssl_force_tls=yes
# Don't wait to enter mailbox manually 
unset imap_passive        
# Automatically poll subscribed mailboxes for new mail (new in 1.5.11)
set imap_check_subscribed
# Reduce polling frequency to a sane level
set mail_check=60
# And poll the current mailbox more often (not needed with IDLE in post 1.5.11)
set timeout=10
# keep a cache of headers for faster loading (1.5.9+?)
set header_cache=~/.hcache
# Display download progress every 5K
set net_inc=5

```

---

### Post by leejewitt on 2012-08-10
what i really am trying to achieve is use that imap server with roundcube but as am having trouble accessing it via outlook, thunderBird i need to get this sorted first. 

i dont really know what mutt is a just used it as a client to try connect to the server with 

lee@Services:~$ sudo mutt -f imap://lee@xtcservers.co.uk

i dont know if mutt is meant to be configured for dovecot to work but i have had imap server working in the past

---

### Post by Bachstelze on 2012-08-10
It shouldn't matter which client you are experimenting with. Normally, if one client work, they all do. That said, mutt provides an easy way to test. Put what I pasted above in your ~/.muttrc (create it if it doesn't exist), change user/host and run just

```
mutt
```

---

### Post by Bachstelze on 2012-08-10
I have to leave, so [here](http://paste.ubuntu.com/1139965/)'s a diff between my (working) doveconf and yours. (Red is yours, green is mine.)

Things that might be of interest are disable_plaintext_auth, mail_location and mail_privileged_group. In particular, you can disregard the SQL stuff since you don't use SQL authentication.

---

### Post by leejewitt on 2012-08-10
ok thanks will have a look

---

### Post by SeijiSensei on 2012-08-10
You don't need a mail client to test a plain-text IMAP connection; just use telnet:

```

$ telnet localhost 143
[dovecot banner]
1 login username password

```

Either you'll get logged in or rejected.  If you're rejected, look in /var/log/mail.log to see why.  To logout enter the command "2 logout", then use Ctrl-] and "quit" to exit telnet.

---

### Post by leejewitt on 2012-08-11
thanks i tried that and this is the error in mail.log

Aug 11 14:33:50 Services dovecot: imap-login: Aborted login (auth failed, 2 attempts): user=<l.jewitt>, method=PLAIN, rip=192.168.1.3, lip=192.168.1.3, TLS

---

### Post by leejewitt on 2012-08-11
ok strange i can now login with outlook, thunderbird but not mutt. 
well at least its working now think it was a mailbox location problem, i changed postfix to /maildir

---

