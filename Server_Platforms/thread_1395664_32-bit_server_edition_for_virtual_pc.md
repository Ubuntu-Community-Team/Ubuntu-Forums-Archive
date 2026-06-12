---
title: "32-bit server edition for virtual pc?"
date: 2010-02-01
forum: Server Platforms
---

### Post by Timbothecat on 2010-02-01
Hi all.

I'm trying to set up a virtual web server using virtual pc and a net-tuts how to. So I went ahead and downloaded Ubuntu 9.10 Server Edition, but it only comes in 64-bit, and vpc doesn't handle 64-bit.

Do any of you wonderful people know how I can get around this? I have a machine that I could set up as a server, but that is also only 32-bit.

Any help would be brilliant.

All the best,

Tim.

---

### Post by nutznboltz on 2010-02-01
You are wrong.  There are 32 and 64-bit server editions.

Search for an ISO image named:

ubuntu-9.10-server-i386.iso

---

### Post by volkswagner on 2010-02-01
Click on the alternate download options under the download button.

[http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)


You not the first one who had difficulties finding it. ;)

---

### Post by Timbothecat on 2010-02-02
Thanks guys. I'll download that one now.

Appreciate your help.:D

---

### Post by Timbothecat on 2010-02-03
That worked a treat, thank you so much.

I'm now having another problem however. I'm trying to set up a testing web server using vmware. I have the server set up etc, and when I go to a browser in my main partition (running windows Vista) and put in the address for the web-server, it gives me the thumbs up. This tells me that apache2 is installed.

I then try to get in using filezilla, but I keep getting, "Network error: Connection refused".

I'm sure it's something simple, but I can't seem to find the problem. If any of you could point me in the right direction, I'd be grateful.

All the best,

Tim.

---

### Post by noway2 on 2010-02-03
It appears that you got the server installed and apache(?) up and running so that you can access web pages.  Congratulations.  Next you tried to use Filezilla (an FTP client) and got connection refused.  You didn't mention setting up an FTP server, which is different than a web page server and both applications listen on different ports.  With no application listening on the FTP port(s), you will get connection refused because the ports are closed.

Before you decide to install an FTP server you should think very carefully about it and the implications.  FTP has become somewhat deprecated, especially because it is relatively insecure in that it transmits plain text in the clear, including authentication.  These days there are usually other, secure, ways to accomplish the same functions.

---

### Post by Timbothecat on 2010-02-03
Hi noway.

Would FTP be a problem with a test server running on your own network? Like I said, it's using vmplayer on my own pc. I really only want it to be able to test websites in a php/mysql environment.

Filezilla is simply the program that I was using to put the files that I worked on with my machine on to the virtual machine that I'm using as a test server.

Anyway, you've given me something to look for, so thank you heaps. I'll go and see what I can find out.

All the best,

Tim.

---

