---
title: "Ubuntu Server - a good idea?"
date: 2014-07-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Terence_Parker on 2014-07-14
It's probably a stupid question to ask on an *Ubuntu* forum, given non-believers wouldn't be trawling through these forums in the first place, but i'm seeking reassurance that Ubuntu is a good choice of distro for a server. Note: i'm not here to rant or complain... this is a genuine question, and apologies in advance for the diatribe.

I'm not new to Linux. In fact, I used to run a number of Gentoo based servers until, more recently, I began deploying them with CentOS. For production server use, Gentoo was unreliably hardcore, and it was not uncommon for system updates to break something ; many users pissed off because a server won't boot anymore (udev structure changed without warning - thanks | or perhaps, nobody can check mail anymore because developers decided to change some default configuration without warning - again, thanks). CentOS was a godsend in the sense that everything seemed well tested. I can't remember a single incidence of a server failing to boot after an upgrade, or a critical service not working as a consequence.

Fast forward to two days ago... I failed to install CentOS on a new server I purchased (CentOS 7 installation was awful, and mdraid support removed ; 6.5 had other issues with my hardware) so decided to toy with Ubuntu. Installation was a charm. I was a bit thrown back by Ubuntu's nanny-like disabling of the root account by default (though I understand the reasons) - but nonetheless this was a small issue. I was surprised that after my first run of package updates - the system failed to boot. I had to add "nomodeset" to Grub boot parameters. After installing Dovecot (actually, it was already there) - I was surprised to see [FONT=Menlo]file_dotlock_create [/FONT]errors and that I had to manually add [FONT=Menlo]mail_privileged_group=mail [/FONT]to my dovecot config (if Dovecot was bundled, surely it should work out the box?). A [FONT=Menlo]loadparm.c:4864, leaking memory [/FONT]error, whilst benign, still lingers (I see some say it's an SMB bug), and right after GRUB boots I have some error (can't remember now) which delays for a few seconds unless I press a button.

Again - i'm not here to bash Ubuntu. I still love Gentoo despite my issues above, but I accept it for what it is and embrace the flexibility it offers. I accept that Ubuntu has many great uses and happy campers too. I merely want to clarify if it's a good choice for a server - and if the Ubuntu developers are focused on reliability over features/flexibility (perhaps my problem above were just me being unlucky?), or whether I should really stick with another distro for my requirements.

I must say, given its reputation, i've been surprised with those issues experienced so far - or perhaps i'm misunderstanding Ubuntu's positioning as a linux distribution...?

---

### Post by yancek on 2014-07-14
If Ubuntu seems to work fairly well for you, why not try Debian.  Has a very stable version and has been around much longer than Ubuntu.  The site below shows it is used on more web servers than any other Linux.  The article is a little over two years old so i don't know if it has changed.  You can see from the article Ubuntu isn't far behind.

[http://www.pcworld.com/article/247845/debian_linux_named_most_popular_distro_for_web_servers.html](http://www.pcworld.com/article/247845/debian_linux_named_most_popular_distro_for_web_servers.html)

A more recent survey indicates Debian/Ubuntu now in the lead, in that category at least. 

[http://w3techs.com/blog/entry/debian_ubuntu_extend_the_dominance_in_the_linux_web_server_market_at_the_expense_of_red_hat_centos](http://w3techs.com/blog/entry/debian_ubuntu_extend_the_dominance_in_the_linux_web_server_market_at_the_expense_of_red_hat_centos)

---

### Post by deadflowr on 2014-07-14
Moved to OS Chat

---

### Post by mastablasta on 2014-07-16
no OS is perfect. depends what you are after. and what kind of server(s).
ubuntu has commercial support and is fairly stable.

it is run as server by some big organisations. so it probably can run well in server farms.

nomodesetting is needed for some graphics cards. what server needs a graphics card? unless some specifically designed to harness their powers...

yes, root is disabled not to take care of users but for security reasons. and is not needed. you have sudo. pluses and minuses are described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

