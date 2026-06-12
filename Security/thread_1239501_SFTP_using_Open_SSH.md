---
title: "SFTP using Open SSH"
date: 2009-08-13
forum: Security
---

### Post by East82 on 2009-08-13
Looking to transfer files securely via SFTP w/SSH on Ubuntu Server. My FTP client is Filezilla on Ubuntu Desktop.

I want  to the server to reject any connection that is not secure ...in other words reject any FTP request and only accept SFTP. Any help is appreciated.

---

### Post by doas777 on 2009-08-13
just install ssh. you don;'t have to install ftp itself. ssh won't allow a non-encrypted connection, so you should be fine by default. you may wanna use winscp for your client on windows though. never tried a traditional ftp client with scp.

---

### Post by dollarmenunaire on 2009-08-13
I suppose could use an SSH tunnel to tunnel the FTP traffic to where ever it is you are going, however there is a secure transfer method that uses SSH called scp on linux.

From which direction are you transferring files from, are you going to the Ubuntu machine, or from the Ubuntu to machine to say a Windows box?

---

### Post by East82 on 2009-08-13
> **dollarmenunaire said:**
> I suppose could use an SSH tunnel to tunnel the FTP traffic to where ever it is you are going, however there is a secure transfer method that uses SSH called scp on linux.

From which direction are you transferring files from, are you going to the Ubuntu machine, or from the Ubuntu to machine to say a Windows box?

Thanks. I will check into SCP ...new to me. I also have LAMP installed. Does Apache have FTP and, if so, how would I disable?

My environment is strictly Ubuntu. Would like to put and get files on the server.

---

### Post by dollarmenunaire on 2009-08-13
Apache will not come with an FTP server/client like for instance IIS does with FTPD if I remember correctly.
If you do not need the FTP server running then either remove it through *dpkg* or prevent it from starting up though the init script.

[I]dpkg --list

[/I]Find the name of the FTP server you have and: [I]
dpkg --remove [ftpserver-name][/I]

Using the purge option will remove the config files also.

To learn more about scp, *man scp *in a terminal. Its really simple.

---

### Post by XCan on 2009-08-13
> **East82 said:**
> Looking to transfer files securely via SFTP w/SSH on Ubuntu Server. My FTP client is Filezilla on Ubuntu Desktop.

I want  to the server to reject any connection that is not secure ...in other words reject any FTP request and only accept SFTP. Any help is appreciated.

> **doas777 said:**
> just install ssh. you don;'t have to install ftp itself. ssh won't allow a non-encrypted connection, so you should be fine by default. you may wanna use winscp for your client on windows though. never tried a traditional ftp client with scp.

You can use Filezilla fine. As mentioned above, if you don't install an FTP server you won't be able to connect through the FTP protocol anyway. You could try it out with Filezilla, unless you select the correct protocol (may be called SSH/SSH2/SFTP) your connection won't be accepted. Personally, I use gFTP to connect to my machines through sftp.

---

### Post by scorp123 on 2009-08-14
> **East82 said:**
>  ...in other words reject any FTP request That's easy. Don't install any FTP server. Voila, done.

> **East82 said:**
>  and only accept SFTP. You only installed OpenSSH server, right? OK then. That's it already. Case solved.

SFTP (a sub-protocol of SSH) and FTP (unsafe!) have nothing to do with each other except that both can transfer files and they share three letters "F", "T" and "P". That's what seems to confuse you? :)

---

### Post by Dr Small on 2009-08-14
> **scorp123 said:**
> That's easy. Don't install any FTP server. Voila, done.

 You only installed OpenSSH server, right? OK then. That's it already. Case solved.

SFTP (a sub-protocol of SSH) and FTP (unsafe!) have nothing to do with each other except that both can transfer files and they share three letters "F", "T" and "P". That's what seems to confuse you? :)
One stands for **S**ecure **F**ile **T**ransfer **P**rotocol, whereas the other one only stands for **F**ile **T**ransfer **P**rotocol. They both transfer files, only FTP transfers the login credentials along with all the data in plain text across the network(s), whereas SFTP has an encrypted tunnel through which everything travels.

Personally, when I'm on the commandline, I tend to use scp more than I ever do sftp. But, if I'm on an Ubuntu system with Gnome, I just use SFTP and connect to the remote host.

Dr Small

---

### Post by Rob_H on 2009-08-14
> **scorp123 said:**
> That's easy. Don't install any FTP server. Voila, done.

 You only installed OpenSSH server, right? OK then. That's it already. Case solved.

SFTP (a sub-protocol of SSH) and FTP (unsafe!) have nothing to do with each other except that both can transfer files and they share three letters "F", "T" and "P". That's what seems to confuse you? :)

Right. The *SFTP* acronym is unfortunate because it's easily confused with traditional *FTP*, but they are very different. To make matters worse, *FTPS* _is_ related to FTP. Confused yet? ;-) In short:

SFTP = SSH file transfers
FTPS = FTP over SSL

---

### Post by scorp123 on 2009-08-14
> **Dr Small said:**
>  One stands for **S**ecure **F**ile **T**ransfer **P**rotocol, whereas the other one only stands for **F**ile **T**ransfer **P**rotocol. And this contradicts my posting how??? 

> **Dr Small said:**
>  They both transfer files Yes, and that's about it. They are totally different internally and have not much else in common except their intended functionality (transferring files) and three letters in their abbreviations. As I said above.

---

### Post by scorp123 on 2009-08-14
> **Rob_H said:**
>  To make matters worse, *FTPS* _is_ related to FTP.  Yes, that' true. Unfortunately. But I seriously would not recommend anyone to use this. Good ol' FTP (please note the sarcasm right here ...) as it was, was already bad enough and already had its fair share of troubles. Anyone who ever had the pleasure of being firewall administrator in a professional environment can tell you volumes about it. Configuring the firewalls so each and everyone's stupid FTP client would get through and not terminate any transfers prematurely was close to "black magic". But FTPS makes matters worse by introducing this SSL-layer on top in a very "hackish" way ... It's a pain.

So for anyone who wants to configure secure file transfers: Do yourself a favour and stick to SSH (easy to setup and yet totally secure!) and its sub-protocols SCP and SFTP. Avoid FTP (too unsafe!) and FTPS (= classic FTP with SSL on top ... too hackish, too much of a pain to get working).

---

### Post by XCan on 2009-08-14
> **scorp123 said:**
> Yes, that' true. Unfortunately. But I seriously would not recommend anyone to use this. Good ol' FTP (please note the sarcasm right here ...) as it was, was already bad enough and already had its fair share of troubles. Anyone who ever had the pleasure of being firewall administrator in a professional environment can tell you volumes about it. Configuring the firewalls so each and everyone's stupid FTP client would get through and not terminate any transfers prematurely was close to "black magic". But FTPS makes matters worse by introducing this SSL-layer on top in a very "hackish" way ... It's a pain.

So for anyone who wants to configure secure file transfers: Do yourself a favour and stick to SSH (easy to setup and yet totally secure!) and its sub-protocols SCP and SFTP. Avoid FTP (too unsafe!) and FTPS (= classic FTP with SSL on top ... too hackish, too much of a pain to get working).

There are a couple of daemons that run FTPS out-of-the box or almost-out-of-the-box. drftpd, glftpd, proftpd comes to mind. Actually that got me interested. In Windows I've been using ultrafxp and filezilla and they've been working flawlessly, with tons more commercial alternatives. What alternatives (graphical) are there in Ubuntu? I've found out that filezilla's been ported to linux, but haven't tried it yet. It seems like ftps is more about using a client that supports it rather than the ftpd itself.

---

### Post by lensman3 on 2009-08-14
They only problem I have found using sftp is that with the Filezilla program, I can go up a directory and see all the users who are under /home.  This isn't OK when you want secrecy and to keep users from snooping.   

There is a chroot sftp server that keeps the users "locked up", but the directory structure is not the default.

Hope this might help.

---

### Post by Dr Small on 2009-08-14
> **scorp123 said:**
> And this contradicts my posting how??? 

 Yes, and that's about it. They are totally different internally and have not much else in common except their intended functionality (transferring files) and three letters in their abbreviations. As I said above.
Lol, I never intended to contradict your post, just elaberate. :)

---

### Post by East82 on 2009-08-15
Scorp,
Thanks for clearing that up!

---

### Post by scorp123 on 2009-08-15
> **Dr Small said:**
> Lol, I never intended to contradict your post, just elaberate. :) My apologies. Not enough coffee .... :lolflag:

---

### Post by Dr Small on 2009-08-16
> **scorp123 said:**
> My apologies. Not enough coffee .... :lolflag:
No problem, mac. I know how it is :D

---

### Post by kevdog on 2009-08-16
Hmm, seems like the utility of this thread has waned.  I wish linux had a good gui app like winscp or something to do sftp

---

### Post by XCan on 2009-08-16
There are quite a few FTP apps supporting it and providing enough usability, and I find that they are in no way inferior to winscp.

---

### Post by kevdog on 2009-08-16
> **XCan said:**
> There are quite a few FTP apps supporting it and providing enough usability, and I find that they are in no way inferior to winscp.

References?

---

### Post by scorp123 on 2009-08-16
> **kevdog said:**
>  I wish linux had a good gui app like winscp or something to do sftp Nice joke. :lolflag:

But seriously, maybe nobody has told you: But pretty much any filemanager here on Linux "speaks" SSH/SFTP.

If you have GNOME:

Open your filemanager (which is called "Nautilus" here). You usually find it under ***Places > Home Folder***

Now hit the "Location Button" so it toggles from "button view" into "text field view" so you can type addresses into the text field. (It's the button that looks like a pencil writing on a sheet of paper directly below the "File" menu but above the left "Places" pane ....)

And now simply type a remote SFTP location into that field:
sftp://remote-username@ssh-server.your-domain.net

Voila, working with SFTP is as simple as using your normal file manager.


If you have KDE:

Same principle, except here they call it "fish://" (short for "SSH **fi**le **sh**are" or something like that?). So you'd type this into the KDE file manager:
fish://remote-username@ssh-server

Voila. It just works.

And it's definitely better than WinSCP or FileZilla on Windows.

Other SCP/SFTP GUI programs that work:
[LIST]
[*]gftp
[*]filezilla
[/LIST]

You will find those in the repositories (e.g. via the "Synaptic" package manager).

One really nice text-mode tool is "yafc" ... You could give that one a try too. It's useful on servers that don't run a GUI. Or if "Norton Commander" is more your thing you'll love "mc". It can handle SCP/SFTP too and it pretty much feels like "good old" Norton Commander on ancient MS-DOS.

Enough SFTP GUI tools for ya?

Quod erat demonstrandum. :D

---

### Post by XCan on 2009-08-17
> **kevdog said:**
> References?

? 

[http://gftp.seul.org/screenshots.html](http://gftp.seul.org/screenshots.html) Select SSH2 as protocol instead of FTP. I'm sorry, I didn't write an article on it. But filezilla and ultrafxp on Windows have worked great for sftp, and so has gftp on Ubuntu.

Bottom line is that winscp isn't any kind of black magic. The underlying parts are easy enough to implement in an FTP app.

---

### Post by Rob_H on 2009-08-17
> **kevdog said:**
> Hmm, seems like the utility of this thread has waned.  I wish linux had a good gui app like winscp or something to do sftp

Nautilus and Dolphin (the GNOME and KDE file managers) handle this right out of the box.

**EDIT:** Oops, sorry, I somehow missed the subsequent replies that said the same thing. One clarification, though: You don't need to use "fish:" in KDE. It supports "sftp:" directly now.

---

### Post by scorp123 on 2009-08-17
> **Rob_H said:**
> You don't need to use "fish:" in KDE. It supports "sftp:" directly now. Thanks for adding that. I haven't really seen or used KDE since I left the world of SUSE (as it was called back then) back in 2004 ...

---

### Post by Rootong on 2009-08-18
It sounds like FTP+TLS what you want to implement. SFTP is the sub-protocol of SSH. You can try TLS first. It's good enough.

---

### Post by scorp123 on 2009-08-18
> **Rootong said:**
> It sounds like FTP+TLS what you want to implement. NO! How did you come to *that* conclusion?? 

Haven't you read the previous posts? FTP+anything is seriously broken and a pain in the bowels. Why in the world would anyone do that when SFTP simply works out of the box with far less troubles??

---

### Post by bear24rw on 2009-08-18
> **scorp123 said:**
> NO! How did you come to *that* conclusion?? 

Haven't you read the previous posts? FTP+anything is seriously broken and a pain in the bowels. Why in the world would anyone do that when SFTP simply works out of the box with far less troubles??

I agree openssh-server and filezilla are all your need, forget FTP

---

