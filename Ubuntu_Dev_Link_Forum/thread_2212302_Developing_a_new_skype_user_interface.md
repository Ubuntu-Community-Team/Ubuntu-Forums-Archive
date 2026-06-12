---
title: "Developing a new skype user interface"
date: 2014-03-20
forum: Ubuntu Dev Link Forum
---

### Post by nintendo-mat on 2014-03-20
Hello,

As many of you are probably aware, Skype for ubuntu is very much outdated. Generally speaking I think it runs OK. but I absolutly hate it's user interface, so I thought I'll undertake the task of seeing if I can fix the user interface.

I know that Skype is not 'free' or 'open' software in the sense it cannot be modified as the source code has not been released. Instead I am hoping to do something similar to Skype Wrapper, or Classic Shell (for windows).

Unfortunatly I do not have much experiance with developing software for ubuntu, but as a computing student, I am keen to learn.

Can anyone try to explain how I could go about doing this?

---

### Post by ian-weisser on 2014-03-21
I see two options for you to investigate:


1) Get hold of the (closed source, unavailable) Skype source code. That seems unlikely to work.


2) See if the Skype dbus API has enough functionality to use it to communicate with Skype.
Install skype and d-feet
Run Skype and d-feet
Interrogate the dbus API using d-feet while Skype is running.

Any application you write can use dbus.

---

