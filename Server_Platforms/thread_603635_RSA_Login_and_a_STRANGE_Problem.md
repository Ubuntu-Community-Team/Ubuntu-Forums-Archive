---
title: "RSA Login and a STRANGE Problem"
date: 2007-11-05
forum: Server Platforms
---

### Post by pfbroome on 2007-11-05
Greetings all,

I have a small cluster of ubuntu servers (7.0.4) all configured to provide auto-login via RSA keys. On 3 of the 4 servers, this works just fine.  On ONE server, all the enabled users can login via RSA EXCEPT ONE! (the root user)  And the worst thing is that our records show that as of last Friday (at least) ALL the users were logging in via RSA just fine including the one that suddenly can't...

I have tried recreating the keys for the  user, I have restarted the ssh service, I can take the login (I am using Private Shell as the client) and change the user name of the account to log into on this one server to another RSA enabled user and it works fine!

It looks, for all the world, like the RSA key (public or private) is somehow corrupted or "in error" for this one user but given how many times we have deleted and then recreated the keys I find this hard to believe.  Does anyone know if the SSH process keeps logs of the logins? (I have to believe it does; SOMEWHERE).  If anyone has any brilliant ideas PLEASE let me know. This is one of those silly problems where it just gets worse the longer you look at it so any help will be appreciated.

Many thanks,

Pete

---

### Post by pfbroome on 2007-11-08
Ok Folks,

Finally figured it out...as I suspected, it was a problem with the nut behind the steering wheel.

At some point (and don't ask when) the permissions on the root directory for root were changed to 777. All I had to do was reset them to 755 and all is well.  I need to follow this up as it seems counter intuitive that too "generous" permissions cause the auto-login to fail...

Anyway, all is well.

Thanks,

Pete

---

