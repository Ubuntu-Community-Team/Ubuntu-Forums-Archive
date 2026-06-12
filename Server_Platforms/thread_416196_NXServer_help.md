---
title: "NXServer help"
date: 2007-04-20
forum: Server Platforms
---

### Post by stormchas3r on 2007-04-20
I am trying to understand the "jist" of nxserver and all, but I can't seem to grasp it.  Could someone please explain how it works and what it does.  

I installed the server on my server at home, but dont understand how to use it.  Do I connect to the server to remote into something else? or?

Any help is greatly appreciated.

TY

Rob

---

### Post by baastie on 2007-04-21
Hi,

A good explanation on what it is / does can be found on [http://www.nomachine.com/products.php](http://www.nomachine.com/products.php) ,

essentially it's a terminal server / remote access solution for Linux with a very good compression protocol
so that it can run thru very low bandwidth lines. And that with ssh so that it's secure. If you have an NXserver running you can also route RDP session thru it, which can be handy.

I personally use it for remote access of even local access for just administration ( with GUI ) on a headless box.

Cheers,

---

### Post by stormchas3r on 2007-04-21
I appreciate the reply, but I guess I am asking how do I configure the server?  I have searched everywhere for info on this, but cant seem to grasp it.

---

### Post by baastie on 2007-04-22
Owh.... me dumbass :D

Well installing is a breeze.

Download the debs from nomachine.

Install the debs with dpkg, first the nx client, than the nx node package and than the nx server.

done :)

Cheers,

---

### Post by serpentine on 2007-04-30
If you want to install the NX Free Edition or any variations on Ubuntu you can find the instructions here:

[URL="http://www.nomachine.com/ar/view.php?ar_id=AR12D00432"]
http://www.nomachine.com/ar/view.php?ar_id=AR12D00432[/URL]

:) 

/John

---

