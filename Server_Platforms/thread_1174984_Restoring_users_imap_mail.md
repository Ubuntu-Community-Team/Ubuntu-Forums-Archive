---
title: "Restoring users imap mail"
date: 2009-05-31
forum: Server Platforms
---

### Post by MrTweakin on 2009-05-31
Quick history:
I wanted to switch my companies mail server from a Gentoo install to an Ubuntu 8.04 LTS install. Gentoo is just getting to hard to manage these days, and I've liked Ubuntu for my personal desktop and home server. 

The Gentoo install was running dated versions of Postfix and Courier with imap / maildir configurations. Most users used a combination of SquirrelMail and Outlook to access their email.

I backed up all home directories from the Gentoo install (containing all the systems email in each respective user account) and cleared the machine for Ubuntu. 

I've now got a nice 8.04 LTS install running with Postfix and Dovecot with similar imap / maildir settings. Everything is working like a champ (after some initial headaches getting dovecot configured) and users are able to connect as expected and send/receive email.

The problem:
I am now at the point of restoring ~10 gigs of email. Me, clearly being naive, thought I could just restore the Maildir/ for each user. Outlook and Squirrel will both happily see what is in Maildir/cur/ and even Maildir/.Sent but all other folders created via imap by the user (and many have LOTS of folders) are not accessible. For example, a user might have Maildir/.TPS Reports containing cur/ new/ tmp/ all with appropriate privilege, but they can not see them in their clients.

How does one go about telling the new server to serve these old folders? I've done some extensive searching but can only come up with ways that either involve connecting to the old imap server (no longer exists) and pushing mail to the new server. Am I out of luck here?

Thanks for any help!

---

### Post by HermanAB on 2009-05-31
Chances are that your only problem is with owner:group and permissions.  Check it carefully.

---

### Post by Dr Small on 2009-05-31
I'll have to agree with Herman. If the directories actually do exist, then it's probably a permission problem, and the clients don't have permission to view these directories.

(Like, maybe you untarred (or whatever) the Maildir directories as root, and the permissions are for root and not the user?)

---

### Post by grantemsley on 2009-06-01
You probably already know this, but also make sure the client is configured to show the folders.  Outlook by default hides all extra folders.

---

