---
title: "Remote subversion"
date: 2007-05-18
forum: Server Platforms
---

### Post by CandelaMedia on 2007-05-18
I'm trying to install/configure subversion on Feisty Fawn

I seem to have got basic svn working and now want to progress to accessing from a Windows XP client (stop laughing!).

So my approach was nice and simple, run up svnserve as a daemon and bobs your proverbial dad's bro. However, my daemon fails to start!!

If I start/stop the daemon manually I get the following message:
*svnserve: Can't bind server socket: Address already in use*

I've had a look with netstat (although I'm not sure I'm driving that right) and can't see anything thats using port 3690.

The svnserve script I'm using is per the How To by Jerome Gotangco as follows:

svnserve -d -r /usr/local/svn/svnrepo

Oddly, if I run this from a terminal, it appears to start ok, no binding message.

However, even starting like this I can't seem to connect in via TortoiseSVN. I'm using the connection URL of svn:///UBUNTU-DEV1/usr/local/svn/svnrepo but I get the following error:

*Can't connect to host*: No connection could be made because the target machine actively refused it

I can ping UBUNTU-DEV1 from the client machine so name res appears ok.

I'm sinking fast here so any assist greatfully received

Any clues?

p.s. cross posted on Install forum as well

---

### Post by Pionner on 2007-05-18
I think the easiest method to setup a public svn server is using Apache.

Try the recipe from Ubuntu server guide: [http://doc.ubuntu.com/ubuntu/serverguide/C/subversion.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/subversion.html")

---

### Post by CandelaMedia on 2007-05-21
I haven't got Apache installed and rather hoped to get away with not needing it by using the 'simple' svnserve approach.

---

