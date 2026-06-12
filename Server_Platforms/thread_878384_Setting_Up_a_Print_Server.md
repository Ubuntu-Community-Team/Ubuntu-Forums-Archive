---
title: "Setting Up a Print Server"
date: 2008-08-02
forum: Server Platforms
---

### Post by Sef on 2008-08-02
My desktop is also the print server for 4 other computers.  The printer does work with my computer.  I have installed Hardy Heron (with Wubi.)  

I read the instructions on [Setting Up Samba]("https://help.ubuntu.com/community/SettingUpSamba") and want to make sure that I understand them.

To Set Up Samba:

A) Download Samba

B) Then open the Network (under Administration)

   1) Go to General
      a) Put in my host name and domain name  
      b) Question: **How do I find the host name of XP?**

   2) Windows Networking
       a) Tick Enable Windows networking
       b) Description:       <whateveryouwant>
       c) Domain/Workgroup:  <yourdomainorworkgroup>
       d) [B]Since those are on the Windows Computers, I would not do anything, since they are currently print off of my computer, correct or incorrect?
[/B]
C) Open Printing (under Administration)

   1) The Windows printers should being showing, so I would just click them, so they can print.
   2) Then select policies tab and make sure the Shared Box is off.  
   3) Question: **Why would I do that if I want to share the printer?**
   4) **Would I need to add the other computers as stated under 'Window Clients' since the computers are already networked?**

> Windows Client

1. Go to control panel -> Printers

2. Click "Add a printer" on the upper left. The printer wizard will start -> click forward. Select Network Printer and click "Next". Select "Browse for a printer" (Top button) and click "Next". In the next window, navigate to your Ubuntu Samba Print Server and click "Next". Continue with the printer and driver installation. 

Thank you in advance.

---

### Post by cariboo on 2008-08-03
To find your computer's name in WIn XP go To Control Panel-->System-->Computer Name.

---

### Post by Sef on 2008-08-05
bump

---

### Post by Sef on 2008-08-14
Any ideas?

---

