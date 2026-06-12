---
title: "need to decide between ubuntu server or 2003"
date: 2008-02-28
forum: Server Platforms
---

### Post by brown_ghost on 2008-02-28
Hello every one, let me give you a quick background on me so you can understand my question, I work for a small company with three offices and I have learn on my own on how to run 2k3 server, I currently use two servers **1**. use as a file sharing and ftp and **2**. to host our two productivity softwares which my internal computers can access the database file and my other two offices can log in via remote desktop to run the software.
I wanted to get another server so I can split those two applications and wanted to move one server to another office. Like I said I work for a small company and it'll cost $$$ to get another server, operating system, CALS, terminal CALS. So to get to my question is it possible to install ubuntu server and have it host the application so that the other offices can log in and use the application, I have two computers at work with ubuntu desktop and have ran our software with wine and know I can get it to work but will it work with the server version?? can I have multiple clients log in their own independent desktop and run my application? any ideas would be greatly appreciated.

---

### Post by Cato2 on 2008-02-28
For file and FTP, Ubuntu can certainly do the job, there are various FTP servers out there.  For printing, Ubuntu works well particularly with common business laser printers, although some consumer printers are less well supported.  HP is generally very good with Linux.

For the "productivity softwares" - if these are running on a Citrix type terminal server you'd need something like that, using VMware or similar - there are various solutions out there.  Linux can host Linux apps like Citrix does, see LTSP - Edubuntu is a very easy way to try this all out (designed for schools but you could de-install the educational parts).

If the productivity apps are running on Windows clients then you are back to file sharing etc - you need to provide more info as to which applications, what they run on today, etc.

I would start by doing the file/FTP from Ubuntu as that's relatively low risk while you are learning - for a business migration like this you do need to have a good level of skill to ensure it succeeds.  Maybe you should contact a local Ubuntu support / integration company to help you do this successfully?  Probably still cheaper than all the Windows licenses etc and it would increase your chances of success.

---

### Post by HermanAB on 2008-02-28
Hmm, setting up a Win2003 serrver is initially easier, but as time goes on, it becomes expensive and restrictive.

If you are not familiar with Linux, then maybe you would be better served with a distribution that has better wizards, eg. Mandriva or PCLOS.  When you know Linux really well, then it doesn't matter what you use, but initially the Mandriva wizards will help you a lot.

If you install Linux as the host system, then you can always install VMware/Virtualbox and make a Win2003 Virtual Machine, to give you the best of both worlds.

---

