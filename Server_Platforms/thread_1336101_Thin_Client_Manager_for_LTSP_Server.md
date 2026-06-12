---
title: "Thin Client Manager for LTSP Server"
date: 2009-11-24
forum: Server Platforms
---

### Post by Denbert on 2009-11-24
Hi,

I've installed Ubuntu 9.10 LTSP server and it's running great.

In order to manage users I've installed the Thin Client Manager, but I cant see any clients, all though a client is up and running.

[IMG]http://hegnstoften.net/pictures/Sk%C3%A6rmbillede-Thin%20Client%20Manager.png[/IMG]

Anyone who can point me in right direction?

---

### Post by BezNalogov on 2010-04-10
I have the same problem. It seems that this control panel is unmaintained since gutsy. Ubuntu 9.10 uses LTSP 5, so I think that is the reason why it doesn't work.

I don't know if it's a matter of adjusting or if there is another control panel available that works with LTSP 5.

---

### Post by kiwicito22 on 2010-04-28
I Sorry my english, i wrote a lot better in spanish :P

That problem its a bug, to solve simply edit the file ltcm.py
should be in /usr/lib/python2.6/dist-packages/studentcontrolpanel/ or search for it.

look for the line:
[COLOR="RoyalBlue"]listtmp = subprocess.Popen(['ps eaxww|grep "bash -c"|grep "LTSP_CLIENT"|grep PPID|grep -v grep'],shell=True, stdout=subprocess.PIPE)[/COLOR]

replace for this:
[COLOR="Red"]listtmp = subprocess.Popen(['ps eaxww|grep "bash -c"|grep "LTSP_CLIENT"|grep -v grep'],shell=True, stdout=subprocess.PIPE)

#listtmp = subprocess.Popen(['ps ax|grep "bash -c LTSP_CLIENT"|grep -v grep'],shell=True, stdout=subprocess.PIPE)[/COLOR]

I think the second line it's allready in the file, dont duplicate.

[good luck]("http://tuxxeando.blogspot.com")

---

### Post by Rakeshvijayan on 2011-07-05
> **kiwicito22 said:**
> I Sorry my english, i wrote a lot better in spanish :P

That problem its a bug, to solve simply edit the file ltcm.py
should be in /usr/lib/python2.6/dist-packages/studentcontrolpanel/ or search for it.

look for the line:
[COLOR=RoyalBlue]listtmp = subprocess.Popen(['ps eaxww|grep "bash -c"|grep "LTSP_CLIENT"|grep PPID|grep -v grep'],shell=True, stdout=subprocess.PIPE)[/COLOR]

replace for this:
[COLOR=Red]listtmp = subprocess.Popen(['ps eaxww|grep "bash -c"|grep "LTSP_CLIENT"|grep -v grep'],shell=True, stdout=subprocess.PIPE)

#listtmp = subprocess.Popen(['ps ax|grep "bash -c LTSP_CLIENT"|grep -v grep'],shell=True, stdout=subprocess.PIPE)[/COLOR]

I think the second line it's allready in the file, dont duplicate.

[good luck]("http://tuxxeando.blogspot.com")
How can i set up ltsp thin clint and 
could you share the configuration of ltps

---

