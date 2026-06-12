---
title: "Some Help with FTP"
date: 2008-03-26
forum: The Cafe
---

### Post by Pillager101 on 2008-03-26
Hi guys,

Kind of new to Linux and Unbuntu so bare with me pls.

I need to setup and test a mission critical FTP server.  Currently I am running it on a Windows 2003 box but i get issues, with droped connections, etc.

I want to try my luck with Linux, but I need to find a FTP server that will satisfy certain requirements.

It needs to be able to handle 10-20 simuntainous connections uploading 20 mb to 3 GB files at the same time as well as 10 connections downloading.
It needs to have the capability to delete broken uploads or incomplete uploads.
I would like to have the ability for bandwith throttling on a peruser case but its not a deal breaker if i can not.

This server will not have many users on it.

Any sugestions, ideas of what is would fulfill my needs?

Thanks.

---

### Post by keratos on 2008-03-26
The O/S is not your limiting factor - your hardware (network upstream and disk array etc) might be.

Any linux [LAMP] server O/S will do, its the H/W that you need to focus on.

Ever heard of GOOGLE. [www.google.co.uk](www.google.co.uk) ???
search terms: " linux server howto "
1st return is :

[http://howtoforge.com/perfect_server_ubuntu7.10](http://howtoforge.com/perfect_server_ubuntu7.10)


!!

---

