---
title: "Problem: ERROR: Connection dropped by IMAP server."
date: 2005-12-01
forum: Server Platforms
---

### Post by ddr400 on 2005-12-01
Hi!

I'm using ubuntu as a server in a scool project (UA - University of Aveiro) and i am having this error mensage when i try to log in squirrelmail in my server:


ERROR: Connection dropped by IMAP server.


I do the test using /src/configtest.php file and i don´t have any errors.


I Use:

Ubuntu 5.10
Apache 2
PHP4
Mysql-server with Phpmyadmin
Courrier-IMAP
Exim4
and for webmail, i try to use squirrelmail.


Did someone had the same problem?

Please Help Me!

Thanks in advice.

Daniel Ribeiro (Cet IMRSI - OAZ - U.Aveiro - Portugal)

---

### Post by nexuslite on 2005-12-10
I was having a similar error to find out the real error i logged in via telnet and logged in that way it gave me a better error message

telnet localhost 143

A001 LOGIN "username" password


replacing username and password of course

---

### Post by nexuslite2 on 2005-12-10
This line is what i got from the server after logging in
	* BYE [ALERT] Fatal error: Maildir: No such file or directory

Fixed by adding Maildir to my home/user directory as user not as root
where user = the user you want to have email


Squirrelmail new error
	ERROR: Could not complete request.
	Query: SELECT "INBOX"
	Reason Given: Unable to open this mailbox.

	ERROR: Connection dropped by IMAP server.
	Query: SUBSCRIBE "INBOX.Sent"

Fixed by adding to the Maildir subdirectories tmp, new, cur

You have to do this for every user so there is probably a better way

Good Luck!

---

