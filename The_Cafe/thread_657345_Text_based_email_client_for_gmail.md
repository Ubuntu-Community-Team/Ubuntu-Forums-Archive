---
title: "Text based email client for gmail?"
date: 2008-01-03
forum: The Cafe
---

### Post by jgrabham on 2008-01-03
OK, I got bored so, Im seeing how much faster I can get things done from a terminal than in a GUI =]

(with fluxbox installed on a 2ghz dual core, with a gig of RAM and a geforce 8400 this PC flies)

Anyway, I want to do text based email, but dont have a clue how, I can set up thunderbird etc, but thats about as far as my knowledge of email goes.  I use gmail.

Please help.

James

---

### Post by fuscia on 2008-01-03
it works fine in elinks, as long as you select the non javascript version of gmail. it supposedly works well in mutt and i think i was able to receive gmail in pine (i never figured out how to send mail from pine, for any kind of email).

---

### Post by Sockerdrickan on 2008-01-03
I would recommend to not live in the past.

---

### Post by jgrabham on 2008-01-03
> **Tux0r said:**
> I would recommend to not live in the past.

Id recommend that constantly using web-based interfaces results in docility, Im doing this because Im 15, and want to work in IT, I spend all my time making things more difficult for myself for a reason; to LEARN.

I want to get more comfortable with UNIX commands.

---

### Post by jgrabham on 2008-01-03
> **fuscia said:**
> it works fine in elinks, as long as you select the non javascript version of gmail. it supposedly works well in mutt and i think i was able to receive gmail in pine (i never figured out how to send mail from pine, for any kind of email).

I read a couple of things on mutt and it was like being slapped in the face by a wet fish, I really was clueless about most of it.  :lolflag:

---

### Post by p_quarles on 2008-01-03
Try [Mutt]("http://packages.ubuntu.com/gutsy/mail/mutt"). Text-based mail reader, supports IMAP and POP.

---

### Post by mali2297 on 2008-01-03
I recommend [Alpine]("http://www.washington.edu/alpine/"). As for setting up gmail, ask [finferflu]("http://ubuntuforums.org/showpost.php?p=4025314&postcount=724").

EDIT: Or see [here]("http://recycledspace.com/2007/12/22/alpine-messaging-system-the-alternative-to-pine-gmail-included/").
> 
1. Type MSLA (Main> Setup> collectionLists> Add)

2. Enter something like the following but replacing the information with your gmail account

Nickname : Gmail
Server : imap.gmail.com/ssl/user=id@gmail.com
Path :
View :

3. Let&#8217;s setup SMTP to use the gmail server. You will be able to send email from you gmail account which is very useful if you have a hostname that doesn&#8217;t resolve to your computer.

SMTP Server (for sending) = smtp.gmail.com:587/tls/user=id@gmail.com


---

### Post by K.Mandla on 2008-01-03
> **jgrabham said:**
> Id recommend that constantly using web-based interfaces results in docility, Im doing this because Im 15, and want to work in IT, I spend all my time making things more difficult for myself for a reason; to LEARN.

I want to get more comfortable with UNIX commands.
=D>

I've also tried to use mutt with Gmail, with only meager results though. That was probably because I didn't try very hard though.

I think this is the page I used on my brief attempt.

[http://home.nyc.rr.com/computertaijutsu/mutt.html](http://home.nyc.rr.com/computertaijutsu/mutt.html)

There are Gmail instructions interspersed throughout it.

---

### Post by Onyros on 2008-01-03
I use mutt + getmail and it works flawlessly.

Getmail creates a .getmail directory, in which there's a dot file (getmailrc).

Mine's configured like this:

```
[retriever]
type = SimplePOP3SSLRetriever
server = pop.gmail.com
username = USERNAME@gmail.com
port = 995
password = PASS

```

Just replace USERNAME and PASS with your details, and you're good to go. You either have to create a chronjob for getmail (so that it fetches mail for you periodically), or whenever you want to check your email, you just type *getmail* at a terminal.

I use procmail to sort my mail out, too. I included the following in my dot config file (.getmailrc):

```
[destination]
type = MDA_external
path = /usr/bin/procmail
```

A barebones .procmailrc may have the following config:

```
MAILDIR=$HOME/Mail
DEFAULT=$MAILDIR/inbox/
LOGFILE=$MAILDIR/log
```

Maildir is the path directory where you want your mail stored. And then by default it'll send emails to a directory named inbox, inside your initial email path.

I then use msmtp to send email, with the following config (.msmtprc):

```
account default
host smtp.gmail.com
port 587
protocol smtp
auth on
from USERNAME@gmail.com
user USERNAME@gmail.com
password PASS
tls on
tls_starttls on
tls_trust_file /home/USERNAME/.cert.pem
```

Note the .cert.pem file. This is relatively new for mutt. You can use the one supplied with ca-certificates instead.

```
sudo apt-get install ca-certificates
```

That'll install a certificates file at /etc/ssl/certs/ca-certificates.crt. Just replace that at your .msmtprc file and you're set with that.

Final configuration is done at .muttrc level. Mutt creates a dot directory of itself (.mutt).

```
set sendmail="/usr/bin/msmtp"
set editor = "nano -t"

set pager_index_lines= 8

### Personal information ###
set realname="YOUR REAL NAME"
set from="USERNAME@gmail.com"
set use_from=yes
set signature="$HOME/.mutt/signature"

### Alias ### 
set alias_file=~/.mutt/aliases
set sort_alias= alias
set reverse_alias=yes

### Pager ###
ignore headers *
unignore headers subject: from: to: date: cc:
hdr_order date: from: subject: to:

### Index ###
set markers=no
set nomark_old
set confirmappend=no

set sort=reverse-threads
set sort_aux=last-date-received

### Auto views ###
auto_view text/html
auto_view application/msword

macro pager \cb <pipe-entry>'urlview'<enter> 'Follow links'

### Folders ###
set folder="$HOME/Mail"
set record="+sent"
set mbox="+inbox"
set postponed="+drafts"

set edit_headers=yes
set folder=~/Mail
set mbox=+inbox
set spoolfile=+inbox
set record=+sent
set postponed=+drafts
set mbox_type=Maildir

source ~/.mutt/aliases                    # Define aliases
source ~/.mutt/mailboxes              # Define mailboxes
source ~/.mutt/bindings                 # Define bindings

```

You can just use this one as a reference, and then check additional configuration possibilities at, say, Arch Wiki, which was were I got most of my info from, to start with ;)

---

### Post by andrew.46 on 2008-01-05
Hi,

 Perhaps either of these might help:

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)
[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

 mutt is still one of the better email clients around and I have used it with gmail for a long time now.

                    Andrew

---

### Post by tenpound on 2009-03-02
Excellent suggestions all around, great reasoning as well.  We dont always operate at runlevel 5.

:-)

---

### Post by sujoy on 2009-03-02
for what its worth, alpine does a reasonable job, i am a mutt user though, but alpine makes things comparatively easier to start with

---

### Post by MaxIBoy on 2009-03-02
> **jgrabham said:**
> Id recommend that constantly using web-based interfaces results in docility, Im doing this because Im 15, and want to work in IT, I spend all my time making things more difficult for myself for a reason; to LEARN.

I want to get more comfortable with UNIX commands.INX (**I**NX is **N**ot **X**) is supposed to be a good distro for that. It's Ubuntu with the GUI completely removed and some good tutorials installed.

[img]http://inx.maincontent.net/album/vga/vga_moc.themes.png[/img]

---

