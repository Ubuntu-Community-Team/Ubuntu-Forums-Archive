---
title: "Running Microsoft Office 2013 on Ubuntu using FreeRDP"
date: 2015-01-08
forum: Virtualisation
---

### Post by Resilldoux on 2015-01-08
Hi all,

I made a (short) video explaining how you can use Microsoft Office 2013 on Ubuntu using VirtualBox and FreeRDP. You can check it here: [https://www.youtube.com/watch?v=cRoS2iJNGj8](https://www.youtube.com/watch?v=cRoS2iJNGj8) 
Let me know what you guys think!

Cheers

---

### Post by TheFu on 2015-01-09
What you've done is falsely advertise something that isn't true.

If you are using RDP, then you are NOT running MS-Office on Ubuntu. You are running it on Windows and accessing it from Ubuntu. Meh.
Why bother with any RDP? It isn't needed if you are using vritualbox and sitting behind the same machine. There is a VirtualBox setting to run a single application and show only that Window.

BTW, if you want to run MS-Office **on** Ubuntu, use WINE.  [http://www.howtogeek.com/171565/how-to-install-microsoft-office-on-linux/](http://www.howtogeek.com/171565/how-to-install-microsoft-office-on-linux/) Much lower overhead than running a full VM.

Or just use **LibreOffice** and be done.

---

### Post by Resilldoux on 2015-01-10
Thanks for your comment. Although I see how this could be seen as falsely advertising something that isn't true, I think I made it quite clear that it's using virtualization, instead of using Wine.

Yes, it's called VirtualBox Seamless mode, of which I too made a video (also about VMware Unity), but I thought of a different way how to achieve a similar result using RDP. Why, you ask? Simply because it's possible, but more importantly, using this you could also connect to a remote desktop server which uses RemoteApp to serve users their applications, like for instance Microsoft Office, and thus offloading your own system and instead using a central server for multiple users to connect to, whilst not relying on Wine which may not work as well as expected.

Yes, I will agree with you that you could simply use LibreOffice, which I actually prefer. I've written my bachelor's thesis using it and it was great. Nowadays I use LaTeX, simply because it saves time worrying about aesthetics and becasue it's also required for papers I produce for my masters degree.

---

