---
title: "FTP servers"
date: 2006-01-11
forum: Server Platforms
---

### Post by i_am_socket on 2006-01-11
Hey all, I'm currently looking for a Linux FTP server that does one thing in particular: I want to be able to add users (and their subsequent configurations) on the fly without having to go through a particular interface or restarting the service.  Ideally, I want to do all the configuration and user administration automatically through scripting (php or otherwise).

I've gone through a bunch, from proFTPd and wzdftpd and wu-ftpd and pyftpd... I want something that's EASILY set to check a mySQL (or other) database for user settings.  Does such a varmint exist or is this something I should look into developing?

---

### Post by frodon on 2006-01-12
This doesn't exist i think. There are some easy ways to configure FTP server but they are all less secure, so if you wish a secure FTP server you have to take the time to make the configuration.
If you wish to configure easily proftpd you can use this gui, but i don't advice it because  it's less secure :  [http://mange.dynup.net/linux.html](http://mange.dynup.net/linux.html)

---

### Post by i_am_socket on 2006-01-12
The security is not so much an issue.  We're setting up a system where customers would have to log into our web site first, then from there be able to set up their own FTP accounts (should they not have one yet). Their own home directory would be created on the spot and cordoned off from every other, they can pick their own passwords and start using it immediately without having to boot off anybody who's currently transferring files.

I work in printing and it'll mostly be customers dropping off image files at all hours of the day and night.  I don't have any desire to work into the night waiting for all the other customers to finish transferring their files before I can set up a new user.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=frodon]This doesn't exist i think.[/quote]Umm, yes it does. All of the following can do virtual users off just about any data source you want:[list][*]ProFTPD[*]Pure-FTPD[*]vsftpd[/list]And probably several others I don't know about.

My buddy who has a lot of virtual users uses pure-ftpd.  YMMV.

> The security is not so much an issue. We're setting up a system where customers would have to log into our web site first, then from there be able to set up their own FTP accounts (should they not have one yet). Their own home directory would be created on the spot and cordoned off from every other, they can pick their own passwords and start using it immediately without having to boot off anybody who's currently transferring files.This seems extremely silly, overcomplicated, and well, stupid, to me.  Just create the FTP account and home directory when you create the account.  Why do they have a seperate folder for FTP in the first place from their website?  If you want them to enable access, just have a toggle that sets an 'enabled/disabled' flag for the account.

---

### Post by frodon on 2006-01-12
[QUOTE=LordHunter317]Umm, yes it does. All of the following can do virtual users off just about any data source you want:[list][*]ProFTPD[*]Pure-FTPD[*]vsftpd[/list]And probably several others I don't know about.[/QUOTE]lol, i just meant that a FTP server with a GUI which create user accounts, home directory, ... automaticaly doesn't seem to exist as far as i know.

By the way, what is your opinion about Gproftpd, useful or not ?

---

### Post by i_am_socket on 2006-01-12
They all need separate root directories for security reasons, none of our customers should see anyone else's files but their own.  The creation of the user's home directory will occur at the same time as their account is created, but through scripting instead of by hand.  Right now all our customers use the same login and dump their files in the same place; not exactly ideal for security.

If we have a customer who needs to drop off files in a hurry at 2:AM and doesn't have their FTP account set up, I don't want to get a phone call, have to log in remotely, set it up, restart, and email them their new username and password.

Complicated, maybe. Easier on me in the long run, absolutely.  Not a bad idea on a simple toggle to enable/disable though.

If I can script the setup of user accounts and not have to restart the service/boot everyone else off, that's what I consider ideal.  The documentation for ProFTPd and PureFTPd (I've been through both) really stinks as far as instructions for setting up virtual users and its mySQL access.  I tried for a week to get them to work to no avail. Maybe I was doing it wrong, but there is no step-by-step guide that I could find.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=i_am_socket]They all need separate root directories for security reasons, none of our customers should see anyone else's files but their own.[/quote]All of them support chroot, so that's a non-issue.

> If we have a customer who needs to drop off files in a hurry at 2:AM and doesn't have their FTP account set up, I don't want to get a phone call, have to log in remotely, set it up, restart, and email them their new username and password.You missed my point.  The customer already *has* an account, ergo, they should already have an FTP directory.  You can precreate them.  

If your existing accounts don't have them, then create them when the FTP server is setup.  That solves your problem, and is far simpler.

> Complicated, maybe. Easier on me in the long run, absolutely.No, eaiser is avoiding this hassle by creating the FTP home directory when you make the account.

---

### Post by i_am_socket on 2006-01-12
Very true on all accounts; I was too frustrated to yank my head out of the sand.  I concede the points :)

I hunted and found a something on the pure-ftp site that gives instructions on setting it up with mysql authentication of virtual users.  Huzzah!  I'll cease the whining and moaning till the next time I get stuck.

Thanks for the help guys :)

---

### Post by LordHunter317 on 2006-01-12
If you need help, post here. I'm no pure-ftpd expert, but I'll do what I can to help.

---

### Post by i_am_socket on 2006-01-16
*Edit* - took out that whole last one there.  I set up everything using the directions at [http://www.pureftpd.org/README.MySQL]("http://www.pureftpd.org/README.MySQL").  That really didn't do much and didn't really start the server or anything.

I searched for the error that came up (421 Configuration Error: Invalid SQL configuration file) and brought up another config tutorial: [http://www.howtoforge.com/pureftpd_mysql_virtual_hosting_p2]("http://www.howtoforge.com/pureftpd_mysql_virtual_hosting_p2")

That got the server started, but I can't seem to log in.  The error I get now is:> An established connection was aborted by the software in your host machine.
Server closed connection.
Cannot login...

Any ideas?

---

