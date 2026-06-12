---
title: "Is this what networking is about?"
date: 2011-01-15
forum: Server Platforms
---

### Post by garyed on 2011-01-15
This may sound stupid but I've got to ask.
Can I connect multiple computers running Ubuntu & run software from one computer from the other? I know how to connect using SSH & to copy files back & forth but I don't know how or if I can share programs.

---

### Post by Girya on 2011-01-15
> **garyed said:**
> This may sound stupid but I've got to ask.
Can I connect multiple computers running Ubuntu & run software from one computer from the other? I know how to connect using SSH & to copy files back & forth but I don't know how or if I can share programs.

I've never done it so take what I offer with a large grain of salt. 

I would think you could mount a remote directory and as long it was in your path the executables would run. I'll try it on a virtual machine and let you know.

---

### Post by stlsaint on 2011-01-15
If i understand you correctly, No. If you are asking if you can have computer A and computer B and if you can connect to computer B thru computer A, and run applications that are installed on computer A and run them on computer B?? If that is the answer, than as far as i understand that is not possible. Now you can connect to computer B using vnc from computer A and install apps and run them then. But other than that i would suggest you setup a application server to host your applications used by the clients.

---

### Post by garyed on 2011-01-15
> **stlsaint said:**
> If i understand you correctly, No. If you are asking if you can have computer A and computer B and if you can connect to computer B thru computer A, and run applications that are installed on computer A and run them on computer B?? If that is the answer, than as far as i understand that is not possible. Now you can connect to computer B using vnc from computer A and install apps and run them then. But other than that i would suggest you setup a application server to host your applications used by the clients.
I don't know what vnc is but when you say "application server" does that mean the server just keeps the apps for the clients to download or can the clients actually run those apps through the server.

---

### Post by tgalati4 on 2011-01-15
You can have 10 people logged into a machine with graphical desktops.  You'll need some RAM to support many users.

---

### Post by HermanAB on 2011-01-16
Yes, you can, provided that the machines are IDENTICAL. Do some Googling for 'NFS root'.  It will come up with a zoo of guides.  The best guides are on [http://tldp.org](http://tldp.org)

You can share any directory from a central NFS server.  It is common to share /usr and /lib, which allows all machines to run the same software, which is what you want to do.

If you also want users to be able to roam around from one machine to the next transparently, then also NFS mount /home.

So doing, a bunch of UNIX machines are much easier to support than a bunch of Windows machines.

---

### Post by SeijiSensei on 2011-01-16
If all you want to do is run a graphical application on one machine but show its display on another, you can use 'ssh -X' to accomplish this.  After logging into the remote, run the application from its command line.  The display will appear on your local machine.

In this case the application is running on the remote machine, so if it requires resources on the local machine, that won't work for you unless you share the filesystems over the network as well using NFS or a similar technology.

---

### Post by garyed on 2011-01-16
Thanks for the ideas everyone,
Now it looks like its a matter of learning how to do it.

---

