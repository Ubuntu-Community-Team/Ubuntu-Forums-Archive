---
title: "sshfs desktop launcher not working"
date: 2006-11-20
forum: Server Platforms
---

### Post by ironfistchamp on 2006-11-20
Hey all

I just got sshfs working so I can mount my area from a mates server. That's great and all but I want to have a nice launcher on my desktop or perhaps in my menu. I have created one using the exact same command that I use from the terminal. If I select it as application a GUI pops up asking for the password. I enter it and it goes away but the folder is not mounted. If I select Application in terminal a terminal pops up asking for the password. The same thing happens. If I type the command from the terminal then it all works fine.

Why is this and how can I fix it?

Thanks

Ironfistchamp

---

### Post by Macchi on 2006-11-20
Which method for SSH file system connection are you using? The built in method on Ubuntu through "Places->Connect to Server..." will ask you the password and you may choose to store it on the keyring. 

But it seems like you are using a custom program launcher. Which command are you using on the launcher?

The sshfs is on user space and does not require the administrative password but of course you need the username and password for the remote server. One way to specify that is to use the notation protocol://user:password@server/directory/file, but this is less safe to store a password in clear text in your system.
Thus if the directory /mylocalmountpoint exists and you have permissions to write to it you can have the following command on the launcher or on "System->Preferences->Sessions->Startup Programs"
sshfs user:password@server.domain.com:port/directory /mylocalmountpoint

Hope it works, keep in touch!

---

### Post by ironfistchamp on 2006-11-21
Thanks for the reply I shall give it a go asap.

---

### Post by ironfistchamp on 2006-11-21
That Connect to Server thing is great. Really easy. One question though. How can I get it to connect on startup?

Thanks

Ironfistchamp

---

