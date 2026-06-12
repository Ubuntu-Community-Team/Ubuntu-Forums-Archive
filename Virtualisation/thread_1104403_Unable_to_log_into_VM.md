---
title: "Unable to log into VM"
date: 2009-03-23
forum: Virtualisation
---

### Post by BradleyAtkins on 2009-03-23
Hi all

Not sure if this is because of the error in my last post on installing VMWare but I have hit a couple of problems on trying to log into the web ui for VMWare.

1)I had a message stating that the web service was unavailable after entering my login details. A search of the forum led me to a thread telling me how to restart the service.

Now I get: -

2) "The server was unable to process your log in request.  Please check with your server administrator." That is trying to log in as me or root.

Any help appreciated 

thanks

Brad

---

### Post by bodhi.zazen on 2009-03-23
Yes, the web ui is , err, a bit of a pain.

What user did you specify when you installed ? You need to use that user to log in.

If you specified root, re-run the install script and specify you user.

---

### Post by BradleyAtkins on 2009-03-23
Hi Bodhi

Love that signature graphic :D

Yes I have tried accepting the empty quotes as the user and my own login as user. 

The documentation says I should sudo to root to do the install, is that correct? Should I log in as me and just install via sudo?

Regards

Brad

---

### Post by BradleyAtkins on 2009-03-24
Shame I really wanted to install vmware as they are adopting it at work and it would have been really helpful to have used it at home.

I did find out from the VMWare site forums that the C Headers issue was irrelevent so was optimistic for a while there.

I know its not my firewall because I still cannot connect even when it is switched off. 

I have also persuaded IE and Firefox to add the certificate from the server (Add the exception in the case of Firefox) but still cannot get past the login box. Firefox won't even display that.

Perhaps I will think of another use for the server!

---

### Post by bodhi.zazen on 2009-03-24
Well, I suggest you use Server 1.x

Server 2.x is buggy and I have had issues with the web ui as well.

And, yes you must install vmware as root, either with sudo -i or sudo does not matter.

---

### Post by BradleyAtkins on 2009-03-25
Maybe that's best for now, at least I can get started with it and maybe the bugs will be fixed in the near future. 

Thanks

Brad

---

