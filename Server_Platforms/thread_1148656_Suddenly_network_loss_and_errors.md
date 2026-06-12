---
title: "Suddenly network loss and errors"
date: 2009-05-04
forum: Server Platforms
---

### Post by tazizhere on 2009-05-04
First, this is Ubunut Intrepid 8.10 server.

Everything has been working like a champ for the last month.  I was sooo happy to get away from Windows finally.  But today... and keep in mind, everything was working fine yesterday and last week (we have a home office of 4 users).

Also want to add before jumping to the easy conclusions, I have rebooted into Windows and everyone seem to be working fine now.

Problems are that the network connection kept going in and out.  Although most of the issues came down to connecting to the server.  The server hosts a our Quickbooks file and the two people using it kept losing connection.  The server is also a file server for storage but one user works off of it with her files.  

Along with the network loss issues we get "paths to deep" error messages.  And they are not they are simple folder/file names like dog\cat.doc - they are not to big or long.

Again, all of this happened over night.  

Side note - we produce consumer shows and for the last 4 years something painfully has happened right before every show.  Luckily, it usually happens 2 weeks before the show.  This time it is the week of the show.....help.

---

### Post by rickyjones on 2009-05-04
More information will be needed :)

What OS on the client PCs? What OS on the server? When does this error occur? What programs are using network resources when this occurs?

Thanks,
Richard

---

### Post by tazizhere on 2009-05-04
Your absolutely right - along with the networking stuff I am also the graphic artist, web designer so they were needing stuff there too running crazy today.

Os on all of the other machines is XP Pro.  Server is Ubuntu 8.10 server (I did install the desktop because of some errors earlier on.  Turned out I didn't need to).  No other resources are being utilized during the errors.  We are a home office of four people, nothing to fancy.

The error was pretty consistant starting late morning.  From what they were telling me everything was working fine earlier but after about an hours work it started going to ........

---

### Post by rickyjones on 2009-05-04
> **tazizhere said:**
> Your absolutely right - along with the networking stuff I am also the graphic artist, web designer so they were needing stuff there too running crazy today.

Os on all of the other machines is XP Pro.  Server is Ubuntu 8.10 server (I did install the desktop because of some errors earlier on.  Turned out I didn't need to).  No other resources are being utilized during the errors.  We are a home office of four people, nothing to fancy.

The error was pretty consistant starting late morning.  From what they were telling me everything was working fine earlier but after about an hours work it started going to ........

Is the Quickbooks file stored on the Ubuntu server? What kind of permissions does it have? Is this a shared file between the users? Did this error pop up using Quickbooks? Do users get this error message when browsing the SAMBA shares on the server? Are these local errors when looking at local files?

You also mention the network going down. How so? Are people unable to access other network resources like IP-enabled printers? Internet?

:)

Thanks,
Richard

---

### Post by tazizhere on 2009-05-04
I am putting my question on hold right now.  

Issue crept back up when everything was Windows so I am currently replacing all of the hardware (Router/NIC).  I was blaming Ubuntu since it seemed that everything was fixed when we went back to Windows. but apparently it was not.  Now I am eyeballing the wireless router which will be replaced at some point today.  Going to just backtrack from the server.  Just replaced the NIC.  If it dies again, replacing the router.  If it dies again.....ummmm..

---

