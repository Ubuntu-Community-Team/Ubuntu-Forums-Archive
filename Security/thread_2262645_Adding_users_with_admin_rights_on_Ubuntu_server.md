---
title: "Adding users with admin rights on Ubuntu server?"
date: 2015-01-26
forum: Security
---

### Post by peter1897 on 2015-01-26
I am not very experienced with Ubuntu server but i want to rent a VPS and hire developers to build and manage a site on it. If i have to add admin rights to their user accounts am i risking someone to overtake over the root account or messing up the system in some other way. What precautions i can take to not let this happen?

Also, i installed Ubuntu server on a virtual machine and created one account with admin rights and i also set password for the root account with the command **sudo passwd root**, but when i login in the account with admin rights and type **sudo -s** it switches to the root account without asking for the password. Why it doesn't ask me for a password?

---

### Post by newbie-user on 2015-01-26
Any time you give someone admin rights to a server, you run the risk of them breaking it. That's just a given. I hope they would know what they are doing and you have proper documentation/procedures for doing stuff to the server. What kind of site are you building? If it's just a basic website, you could just give them access to the single folder which contains the site.

You should also disable the root account. There's no need to have it active, as you can use sudo for all your admin stuff. Also, it poses a security risk. Alternatively, you could disable root login if you absolutely need to have the root account active.

---

### Post by peter1897 on 2015-01-26
The site i am planing to build will not be basic website, but complicated with database that will contain sensitive information, like users email addresses. 
I guess it will be better to not give admin rights to any other user accounts.

---

### Post by SeijiSensei on 2015-01-26
You don't have to have root privileges to access a database either.  Just create a user in MySQL or PostgreSQL to own the database, then have the web application log into the database as that user.

If you are really concerned about protecting sensitive information, then you should discuss methods for encrypting the data records.  I've dealt with this problem building a site that handled medical appointments, where all the patient info had to be encrypted.  I ended up writing a couple of PHP functions to encrypt and decrypt the records when needed.  The database server was on a separate machine behind the organization's firewall, too.

---

### Post by peter1897 on 2015-01-27
Is it enough to create FTP accounts for the developers and give the accounts write privilege only for the directories where the site files are located? Also, is it recommended to install admin panel or it is better not installing it if i am concerned about security?

---

### Post by SeijiSensei on 2015-01-27
Use SFTP or SCP.  If they need a compatible client for Windows, tell them to use [WinSCP]("http://winscp.net/eng/index.php").

Is there some reason each developer needs a separate account?  Can they just share the account with rights to the web directory?

---

### Post by peter1897 on 2015-01-28
I don't know if i will need separate accounts, i never hired developers before, but the site i want to build will be big.
SFTP server is more secure to use than VSFTPD server, right? Also, if i install a desktop or web admin panel will this compromise the security and put additional load on the server?

---

### Post by mastablasta on 2015-01-28
> **peter1897 said:**
> I don't know if i will need separate accounts, i never hired developers before, but the site i want to build will be big.
SFTP server is more secure to use than VSFTPD server, right? Also, if i install a desktop or web admin panel will this compromise the security and put additional load on the server?


oh dear. ^^ the questions in this post...

if devs work on same site then they do not need spate accounts but you might want to create them. it will then be easier to revoke access to specific developer if necessary.

sftp is in OpenSSH package. learn it, use it. make keys, disable root.

desktop on big website server..... :lolflag:


hey it's your server... you can do whatever you want. but consider this - every additional app (as it's modern to say these days) will make an additional attack vector. and it will use additional system resources. personally I wouldn't advise the use of desktop. it is not necessary, it increases possible security risks and most important it will unnecessarily use plenty of system resources. now a web gui for server makes slightly more sense for us newbies. I chose a python based and very light Ajenti, but there are plenty others good ones out there. Zentyal is official Webgui for small business servers. it will help you configure many things via GUI. but there are lighter ones and also good GUIs available such as Nethserver (centos), ClearOS etc. have a look, try them out, try their demos, see if they have what you need.

or you have full webhosting package like zpanel and similar, but this is made more for hosts than users.

oh and since you are doing it all by yourself do not forget to read about how to secure the server. by default it's pretty much open. and I suggest also to read a bit about how to setup autoupdates to have at least security patches automatically made. 

learn the CLI, if you are primarily a windows desktop user (like me) have a look at putty, otherwise use terminal to connect remotely to server and administer it via CLI. Ubuntu is relatively easy to administer. once you know which program to use they are all quite informative.

---

### Post by peter1897 on 2015-01-28
Thanks, for the tips! I am still learning to use the command line, because i am mostly Windows user, but i think i will need to install web admin panel, because it will be more easier for me to manage the server.

---

### Post by mastablasta on 2015-01-29
> **peter1897 said:**
> Thanks, for the tips! I am still learning to use the command line, because i am mostly Windows user, but i think i will need to install web admin panel, because it will be more easier for me to manage the server.ž

sure. why make it hard on yourself. there are plenty of good web admin panels out there. you can safely try them out in virtualbox or if they have a demo available on their site. try them out, see what you like and if they have features you need (or if they are easily added - e.g. via plugins etc.). Zentyal is quite good and easy to use, but lately they started removing plenty of plugins to better focus on small business server. anyway it was an overkill for me so in the end I didn't use it. but if I needed more things on server then I would definitely use something like that.

---

