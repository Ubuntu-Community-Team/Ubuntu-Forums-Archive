---
title: "WinSCP question"
date: 2011-02-27
forum: Server Platforms
---

### Post by Reddoug on 2011-02-27
Hi All

Not sure if this is the correct place to post this question. I am learning ubuntu and I will be starting an Asterisk class in few weeks. From what I have learned about the class is we will be using WinSCP. Is there away to use ubuntu in terminal with out using WinSCP? Asterisk will be running on CentOS. I am trying to get by with out downloading WinSCP. I have setup a computer here at home with CentOS to do homework when class starts. 

Thanks, Doug

---

### Post by CharlesA on 2011-02-27
WinSCP uses sftp/scp. If you want, you can use filezilla instead or just use sftp from the terminal.

---

### Post by koenn on 2011-02-27
even simpler, 
you can "mount" the remote CentOS directory tree with Nautilus (Places -> "Connect to  a server" ; use SSH ; + credentials)

It's actually this sort of behavior -- a file browser to manage files on a remote linux system -- that winscp is trying to provide on Windows.

---

### Post by Vegan on 2011-02-27
I use Tera Term to connect via SSL to my server for a terminal session.

I use SAMBA to share folders.

I found this approach the easiest

---

### Post by Reddoug on 2011-02-27
Hi

Thanks for the reply's. I will give them a try.

Doug

---

