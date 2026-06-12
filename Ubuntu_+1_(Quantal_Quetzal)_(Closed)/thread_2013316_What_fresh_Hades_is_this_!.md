---
title: "What fresh Hades is this ?!"
date: 2012-06-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-30
Apport is going bananas.  It cancelled itself, told me that the bug was already reported and then gave me this:

---

### Post by MacUntu on 2012-06-30
It says what's going on: you don't have permission to access that bug report (it's marked private for now).

---

### Post by ventrical on 2012-06-30
> **MacUntu said:**
> It says what's going on: you don't have permission to access that bug report (it's marked private for now).

Why would it forward me to a bug page that I did not file or subscribe too? Is this too a bug ?

I filed this bug anyways.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1019629](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1019629)

---

### Post by ronacc on 2012-06-30
I got the same stupid message during precise , it eventually fixed itself .

---

### Post by mc4man on 2012-06-30
apport doesn't know the bug is private - it just forwarded you to the bug page, perfectly normal.

In this case it's an apt-xapian-index crash. If curious you could attempt to access the page every so often, ect.

What apport 'sees' (- shown from - 
 sudo apport-cli /var/crash/_usr_sbin_update-apt-xapian-index.0.crash , option V, sudo because this particular report is root owned
> ...clipped
== DistroRelease =================================
Ubuntu 12.10

== DuplicateOf =================================
[https://bugs.launchpad.net/bugs/1019581](https://bugs.launchpad.net/bugs/1019581)

== ExecutablePath =================================
/usr/sbin/update-apt-xapian-index
...clipped
== KnownReport =================================
[https://bugs.launchpad.net/bugs/1019581](https://bugs.launchpad.net/bugs/1019581)

== Package =================================
apt-xapian-index 0.44ubuntu5
...clipped
== Title =================================
update-apt-xapian-index crashed with ImportError in /usr/share/apt-xapian-index/plugins/software-center.py: cannot import name index_name

---

### Post by MacUntu on 2012-07-01
> **ventrical said:**
> I filed this bug anyways.

Why would you do that? Apport told you it has already been filed...

---

### Post by ventrical on 2012-07-01
> **MacUntu said:**
> Why would you do that? Apport told you it has already been filed...


But, then, subsequently, why send me to the link below? It makes absolutely no sense. And also I point out that it will only happen in rare cases ,(not all cases) as apport will just inform that the bug has already been reported and not make a CALL to firefox or other web browser.

What use is it to point me to a page that does not exist? many years back I did research for security and helped clean up webpages etc. Most often it was to try to parse message bases  and merge them with data bases. Often time there was this terrible redundancy and the data bases would become fractured.  Sometimes these hole_spaces in the data bases are usually treated with an "oh well, another f/p that I'm just suppossed to ignore" . Hence , although they are not necessarily program bugs or logic bugs they can become housecleaning bugs and greatly diminish  the ambiance of the reporting process as a whole.

---

### Post by mc4man on 2012-07-01
> What use is it to point me to a page that does not exist? 
The page does exist, you just don't have permission to view it & won't until it's 'cleaned up' & made public or the orig. reporter decides to make public

Edit: like it is now - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1019581](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1019581)

---

### Post by ventrical on 2012-07-02
> **mc4man said:**
> The page does exist, you just don't have permission to view it & won't until it's 'cleaned up' & made public or the orig. reporter decides to make public

Edit: like it is now - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1019581](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1019581)


Thank you for your detailed report on this. I have been doing beta testing of hardwares/softwares for several years but I must admit that  I am still a novice when it comes to Ubuntu and the workings of the apport process.  As you have described it and laid it out, it makes perfect sense , but, to a new comer or novice, it may initially catch them off guard.

Much appreciated.

I will of course mark this thread as <solved> being that the original problem was based on my misunderstanding of how the apport process should be working.

---

