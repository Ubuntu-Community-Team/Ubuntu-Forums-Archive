---
title: "HELP! - netkit-inetd/xinetd, vsftpd/ftpd-ssl"
date: 2005-11-28
forum: Server Platforms
---

### Post by heftigrat on 2005-11-28
My head hurts.  Does anyone have a simple how-to for getting inetd and ftpd running?  Which package is right for each (netkit vs. xinetd, vsftpd vs ftpd-ssl, etc.)?  It's pretty easy to just throw up vsftpd and pretend my machine is "very secure" (yeah right), but I noticed I then had full access to "/", which is not a good idea.  And yeah, yeah, I know "very secure" only refers to the data x-fer and not what a user can do to the actual machine once they're logged in, but I thought it was ironic anyway.

Bottom line, PLEASE HELP!  Just a simple link will do, and I can _usually_ take it from there.  Thanks in advance.

---

### Post by heftigrat on 2005-11-28
Oh yeah, and as jdong "(hehe, no offense)" notes [here]("http://ubuntuforums.org/showthread.php?t=8256"), this forum isn't for "HOW-TO's", so anyone is welcome to smack me upside the head and kindly drop a link to the Ubuntu HOW-TO section while you're at it.

Furthermore, in an effort to contribute to the forum, I encourage anyone to share their pearls of wisdom regarding the pros and cons of each daemon I mentioned above.

I'm shivering with antici........






.....PATION...

---

### Post by hostile on 2005-11-28
> I'm shivering with antici........






.....PATION...

/me plugs in the DVD...  LOL! Haven't see that in a while. Very funny...

Anyhow, I have tried to use vsftpd in the past, but I cannot bring myself to do so, simply b/c I am not that well-versed with it, and do not trust myself to configure it as securely as I want.

Personally, I use ProFTPd and have used for 7 or 8 years. I have never done any fancy virtual hosting setups with it, b/c I simply have not had to, but now, I am very familiar with it, and I trust myself with configuration.

I like the flexibilty of it. I like how the conf file is akin to that of apaches in it's use of directives, which is something that I understand. I also like the use of .ftpaccess files to offer an even finer grain of control.

I have only ever been hacked once, and that was due to my own lack of knowledge/experience at serving FTP, and had little to do with ProFTPd itself.

There are others like PureFTPd and what not, but I cannot speak to them, as I have not even inquired. I have only given vsftpd a serious look.

Whatever you do, stay away from WU-FTPd.  :)

Hth.

---

### Post by heftigrat on 2005-12-01
hostile, thanks for the reply!  I'm glad I checked back on this post, I didn't get the usual email notification.

hehe yeah, I love that line.  I should really "start [that] f*ck!ng flick" again sometime soon.  :razz: 

I'm not too sure on FTP security either, other than making sure every user is chroot-ed to a path you don't care if they screw up, and don't allow anon logins.  After posting this thread i actually found an awesome [server guide]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") at [howtoforge.com]("http://www.howtoforge.com/").  The author of this guide recommends ProFTPd as well (on [page 5]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5") of the how-to).  I will probably end up using their recommended [ISPConfig]("http://www.ispconfig.org/index.htm") application.  Perhaps that will come in handy for others as well, or if anyone has any experience with it please comment.

---

