---
title: "Developing an Application Involving Ubuntu One"
date: 2010-09-05
forum: Ubuntu One (CLOSED)
---

### Post by DiegoTc on 2010-09-05
Hi guys.
I saw last night that dropbox allows user to develop applications that allow our mobile applications to work with online file browsing, synchronization, backup, and sharing features.

I was just wondering can these be posible with Ubuntu One¿?

Thanks

---

### Post by Ellipsis on 2010-09-05
Is this what you are looking for?

[https://wiki.ubuntu.com/UbuntuOne/ThirdPartyProjects](https://wiki.ubuntu.com/UbuntuOne/ThirdPartyProjects)

[http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars](http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars)

---

### Post by duanedesign on 2010-09-08
A community member is building an Android app that has many of the Ubuntu One features. I think mkarnickis' project is listed on the Third Party Applications wiki page. But I wanted to call attention to it because it sounds exactly like what you are asking about. 

[http://android-u1.blogspot.com/](http://android-u1.blogspot.com/)

also Diego, mkarnicki hangs out in #ubuntuone if you want to ask him any questions. Very nice fellow I am sure he would love to help you in any way he can.

---

### Post by mkarnicki on 2010-09-08
Thanks for the kind words duanedesign :)

Diego, in addition to the link duanedesign provided, you can also have a look at [http://wiki.ubuntu.com/AndroidU1](http://wiki.ubuntu.com/AndroidU1) . I use ubuntuone-java-storage-protocol to communicate with U1 servers for file transfers, however I will use REST API calls to publish and share files. There are quite a few technologies involved since Ubuntu is much more as a whole, than Dropbox. I think Dropbox transfers files over http(s) (a wild guess), whilst we need to establish a secure connection (session, so to speak) to access the files.

You might also be interested in
[https://launchpad.net/ubuntuone-storage-protocol](https://launchpad.net/ubuntuone-storage-protocol)
[https://launchpad.net/ubuntuone-client](https://launchpad.net/ubuntuone-client)

Catch me on Freenode if you like :)

---

