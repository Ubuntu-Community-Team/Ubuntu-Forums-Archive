---
title: "[SOLVED] thunderbird and enigmail doesnt work !"
date: 2008-12-24
forum: Security
---

### Post by lesve on 2008-12-24
I have upgraded from ubuntu 8.4 to 8.10 and of cource even the
application thunderbird (and it's plugin enigmail was updated)

When I try to encrypt en email I got the following error
when trying to send it.
[IMG]http://img.lesve.org/enigmail.png[/IMG]

I have several nodes and one is not upgraded to 8.10 and
there will the combination  thunderbird  and enigmail work out very well

Is there a solution on this problem ?

               Regards
               Penguinfriend

---

### Post by Nepherte on 2008-12-24
It looks like there's something wrong with your key, more spefically your expiration. Try another key and see if that works.

---

### Post by lesve on 2008-12-24
Whatever key I choose enigmail add in the command line the same key
....  --encrypt-to 0xE3FB1BDD .....   -u 0xE3FB1BDD

That key exist in my key manager (expired) but the problem exist even
if I delete this key in the keymanager.

So there must be some error in the enigmail plugin. The plugin
must cache this id and always use it.

            
I still hope for a solution ......

---

### Post by lesve on 2008-12-24
I found the solution on enigmail forum

[http://www.nabble.com/Invaild-Key-td10325061.html](http://www.nabble.com/Invaild-Key-td10325061.html)

Change in Thunderbird -> edit -> account --> openPGP security

         

           S O L V E D ! !

---

