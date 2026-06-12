---
title: "vsFTPd server integration help"
date: 2011-03-17
forum: Server Platforms
---

### Post by Daedalus_357 on 2011-03-17
So I'm trying to set up a secure FTP server that is user-based login. i've got the basic FTP started and up, which ties the user to ONLY their home directory, the thing i'm trying to do now is this:

Basically I want to create users using the credentials in my mySQL database through a script that compares the current user names in linux to the users in the database, if the user does not exist on linux but does in the database then the script will create a basic non-admin account using that user's credentials (username / password) from the database.

The database is on an external site (website), so i would need to connect to it somehow.

so my question is, is this possible; and how can i do it? i'm not asking for the entire code, just pointing me in the right direction and/or snippits of code would suffice :)

Thanks, and happy St.Patty's day!

---

### Post by Daedalus_357 on 2011-03-17
I'm thinking about doing the "script" in Java, since it's multi-platform. my only concern is whether or not is has the ability to create users through the linux command line (as opposed to just appending the passwd file, which is shadowed).

---

### Post by Lars Noodén on 2011-03-18
That sounds very complex.  What is missing from [SFTP](http://howtoforge.com/node/5928) that you're going back to FTPS?

---

### Post by Daedalus_357 on 2011-03-18
> **Lars Noodén said:**
> That sounds very complex.  What is missing from [SFTP]("http://howtoforge.com/node/5928") that you're going back to FTPS?

most of my clients are basic windows end-users (id-10-t's when it comes to technology), so it would be too complicated for them to set up their FTP clients to accept SSL over SFTP, so i'm having to stick with just using the standard FTP protocol.

the FTP isn't the issue though, its how to coordinate my SQL user database with my Linux user list. 

As I said, i'm trying to have my linux box create user accounts (jailed to their home dirs) based on the list of users in my SQL database, and compare the database to the linux user list for new users. The script will be running 24/7 on the linux box so when a new user signs up, it will check every hour or so for new users (since the user doesn't need access to their FTP folder until we upload their data), and will then add that user & password to linux as a restricted user.

---

### Post by Daedalus_357 on 2011-03-22
Bumping the thread due to lack of replies..

---

### Post by Lars Noodén on 2011-03-23
> **Daedalus_357 said:**
> ... it would be too complicated for them to set up their FTP clients to accept SSL over SFTP {sic}...
FTP over SSL would be FTPS not SFTP.

SFTP is its own protocol and many clients have built-in support.  
FileZilla is one with built-in SFTP support.

Please give SFTP a try because it is secure and FTP is not, and because it is pre-configured and, as you are finding out, FTP is a pain.

---

### Post by Daedalus_357 on 2011-03-23
> **Lars Noodén said:**
> FTP over SSL would be FTPS not SFTP.

SFTP is its own protocol and many clients have built-in support.  
FileZilla is one with built-in SFTP support.

Please give SFTP a try because it is secure and FTP is not, and because it is pre-configured and, as you are finding out, FTP is a pain.


I'm using vsFTPd, but how do I configure it to be secure (non-plain text transmission)? i've looked up numerous tutorials, but they all point to using SSL with it, which causes problems with most of the FTP clients i try to connect with.

---

### Post by Lars Noodén on 2011-03-24
> **Daedalus_357 said:**
> I'm using vsFTPd,

That will get you FTP. And if you spend the time to configure vsFTP for SSL/TLS, you can also get FTPS.  [FTP**S** is not **S**FTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS).  

To get **S**FTP, you have to use OpenSSH server or another SSH server.

> **Daedalus_357 said:**
>  but how do I configure it to be secure (non-plain text transmission)? i've looked up numerous tutorials, but they all point to using SSL with it,

That would be FTP**S**, also known as FTP tunneled over SSL/TLS.
The tutorials are misleading in that the don't discourage the use of FTP and FTPS enough.  

> **Daedalus_357 said:**
>  which causes problems with most of the FTP clients i try to connect with.

Right.  It's difficult to set up FTPS -- and you need special clients.  
**S**FTP may already be on your machine.  If not, it is easy to set up **S**FTP by installing [OpenSSH server](http://packages.ubuntu.com/maverick/openssh-server).  It's part of the package and you can use [regular clients](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients)

---

