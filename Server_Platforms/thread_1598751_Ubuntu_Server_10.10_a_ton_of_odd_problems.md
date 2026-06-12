---
title: "Ubuntu Server 10.10 a ton of odd problems"
date: 2010-10-16
forum: Server Platforms
---

### Post by davetelex on 2010-10-16
I had Ubuntu Server 10.04 running for a while and I wanted to be able to have user accounts that people could log into their own accounts. I tried both ISPConfig2 as well as SysCP and they both would fail installation every time. By the time i got to the point where it failed a good portion of my day was used so i would end up putting the website back on the server and bringing things back online until i had the chance to try again the next weekend. I now have Ubuntu Server 10.10 installed and I still am running into the same issues.

I dont really care what program i end up using as long as it can do the control panel type thing. The point I always seem to get stuck at is installing the "mail server". No matter how i try to do it it fails every time. It seems to be something with "Courier"?

Anyone's help is greatly appreciated because I give up!! The machine is an HP Proliant and I have an Ubuntu Server 10.10 disk next to it. Thanks in advance for any help!

As a side note, a few minutes ago I tried to move the website back onto the sever using Filezilla and all I got were permission errors, nothing would transfer. Im not sure if this is a new 10.10 compatibility thing or if this is just another odd thing that the server wanted to annoy me with.

---

### Post by Ryan Dwyer on 2010-10-17
I strongly recommend you learn how everything works on a test server rather than production. Even if you don't have a spare computer, you can use a virtual machine.

You also need to decide what you want. You said you want "to have user accounts that people could log into their own accounts". You can already do this with a straight Ubuntu server install. Do you want them to be able to administrate the server remotely (via SSH)? Do you want a web hosting setup where people can use a web based manager to manage their websites? Do you want a mail server with POP or IMAP logins?

Decide what you want (one at a time), then research what software can do that and learn how to use it.

---

### Post by davetelex on 2010-11-12
thanks for your reply and i have found some things to use that work. and i will also do what you said about a test server, sounds like a much better option than taking the site down for a few hours! thanks again!

---

### Post by James78 on 2010-11-13
1. ISPConfig2 is outdated. You should use ISPConfig3.
2. You should use Webmin/Virtualmin over ISPConfig, as it's TONS better. [Here's how to install it]("http://wwww.ubuntuforums.org/showthread.php?t=1197883").
3. Webmin/Virtualmin really only supports LTS releases for a good reason, so you'll have to use Ubuntu Server 10.04.1. ISPConfig might only support LTS releases too, but I don't know their release habits. Using LTS releases is really the best thing you can do when using servers anyways. If you don't want to stick with LTS, then I suggest doing all your software installs, then upgrading from the LTS, that way compatibility is maintained. I don't think I could wait from 10.04 to 12.04 either, that's a long wait. The wait from 8.04 to 10.04 was forever too.
4. I'm going to let you figure out the user stuff on your own, but take a look at post #2 in this topic.

---

